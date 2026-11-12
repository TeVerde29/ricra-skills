# Dashboards y Bases


Los paneles son **consultas, nunca copias**: no contienen información propia y no hay nada que mantener salvo los filtros. Diseña paneles para responder preguntas operativas, no para decorar.

### Tres niveles de navegación

| Nivel | Pieza | Responde a |
|---|---|---|
| Vault | `Home.md` y paneles de `01_Dashboard` | ¿Qué requiere mi atención hoy? |
| Proyecto | Hub con panel embebido | ¿Cómo va este proyecto? |
| Detalle | Backlinks, propiedades, enlaces | ¿Qué se relaciona con esto? |

### Paneles

| Panel | Archivo | Filtro principal |
|---|---|---|
| Índice de proyectos | `Proyectos.base` | `tipo == "proyecto"` |
| Panel de proyecto | `Proyecto - Panel.base` (embebido en cada hub) | Carpeta del proyecto |
| Tareas pendientes y completadas | `Tareas.md` | Plugin Tasks, o tareas-nota con Bases |
| Prioridades | `Prioridades.base` | `prioridad <= 2` |
| Fechas límite | `Fechas-limite.base` | `vence` no vacío |
| Reuniones | `Reuniones.base` | `tipo == "reunion"` |
| Documentación | `Documentacion.base` | `plan`, `tecnica`, `investigacion`, `procedimiento` |
| Recursos y referencias | `Recursos.base` | `tipo == "referencia"` |
| Archivados | `Archivo.base` | `estado == "archivado"` o carpeta `05_Archivo` |

### Reglas para proponer una Base

- Comprueba que las notas tengan propiedades consistentes.
- Define qué pregunta responde la vista y evita vistas redundantes.
- Documenta filtros y ordenamientos.
- No inventes sintaxis: usa solo las claves raíz `filters`, `formulas`, `properties`, `summaries` y `views`; vistas `table`, `cards`, `list` (y `map` con el plugin Maps). **No uses `from:` ni `where:` (sintaxis de Dataview).**
- No referencies `formula.X` en `order` sin definir `X` en `formulas`.
- Un filtro con una sola clave lógica: `and`, `or` o `not`.
- Si Bases no está disponible, ofrece una alternativa compatible (búsquedas guardadas, Dataview si ya está instalado). No presupongas que un plugin está instalado.

### `Proyectos.base`

```yaml
filters:
  and:
    - 'tipo == "proyecto"'
formulas:
  dias_restantes: 'if(vence, (date(vence) - today()).days, "")'
properties:
  formula.dias_restantes:
    displayName: "Días restantes"
views:
  - type: table
    name: "Activos"
    filters:
      and:
        - 'estado != "archivado"'
        - 'estado != "completado"'
        - 'estado != "cancelado"'
    order:
      - file.name
      - estado
      - prioridad
      - responsable
      - vence
      - formula.dias_restantes
    sort:
      - property: prioridad
        direction: ASC
  - type: cards
    name: "Por estado"
    groupBy:
      property: estado
      direction: ASC
    order:
      - file.name
      - prioridad
      - vence
```

### `Proyecto - Panel.base` (embebido en cada hub con `![[Proyecto - Panel.base]]`)

```yaml
filters:
  and:
    - file.inFolder(this.file.folder)
    - 'tipo != "proyecto"'
formulas:
  dias: 'if(vence, (date(vence) - today()).days, "")'
properties:
  formula.dias:
    displayName: "Días"
views:
  - type: table
    name: "Trabajo abierto"
    filters:
      and:
        - or:
            - 'tipo == "tarea"'
            - 'tipo == "entregable"'
            - 'tipo == "incidencia"'
        - 'estado != "hecha"'
        - 'estado != "cancelada"'
        - 'estado != "cerrada"'
        - 'estado != "aceptado"'
    order:
      - file.name
      - tipo
      - estado
      - prioridad
      - vence
      - formula.dias
    sort:
      - property: prioridad
        direction: ASC
  - type: table
    name: "Decisiones"
    filters:
      and:
        - 'tipo == "decision"'
    order:
      - file.name
      - estado
      - decidido
  - type: table
    name: "Reuniones"
    filters:
      and:
        - 'tipo == "reunion"'
    order:
      - file.name
      - fecha
    sort:
      - property: fecha
        direction: DESC
  - type: table
    name: "Documentos"
    filters:
      or:
        - 'tipo == "plan"'
        - 'tipo == "tecnica"'
        - 'tipo == "investigacion"'
    order:
      - file.name
      - tipo
      - estado
      - file.mtime
```

**[probar]** `this.file.folder` en una base incrustada y `date(vence) - today()` dependen de la versión. Alternativa robusta: un `.base` por proyecto con filtro fijo `file.inFolder("02_Proyectos/PRJ-2026-001_Nombre")`.

### `Fechas-limite.base`

```yaml
filters:
  and:
    - 'vence'
    - 'estado != "hecha"'
    - 'estado != "cancelada"'
    - 'estado != "cerrada"'
    - 'estado != "archivado"'
    - 'estado != "completado"'
formulas:
  dias: '(date(vence) - today()).days'
properties:
  formula.dias:
    displayName: "Días"
views:
  - type: table
    name: "Próximos vencimientos"
    order:
      - file.name
      - tipo
      - proyecto
      - vence
      - formula.dias
    sort:
      - property: vence
        direction: ASC
    limit: 40
```

`Prioridades.base`, `Reuniones.base`, `Documentacion.base`, `Recursos.base` y `Archivo.base` se construyen igual cambiando filtros y `order`.

### `Home.md`

````markdown
---
tipo: dashboard
creado: 2026-11-09
---
# 🏠 Home

**Captura:** [[00_Inbox]] · **Hoy:** [[{{date:YYYY-MM-DD}}]] · **Revisión semanal:** [[04_Diario/Revisiones/]]

## Proyectos activos
![[Proyectos.base]]

## Vencimientos
![[Fechas-limite.base]]

## Tareas de hoy
![[Tareas]]

## Accesos
[[Prioridades.base|Prioridades]] · [[Reuniones.base|Reuniones]] · [[Documentacion.base|Documentación]] · [[Recursos.base|Referencias]] · [[Archivo.base|Archivo]]
````

### `Tareas.md` (requiere el plugin Tasks)

````markdown
---
tipo: dashboard
---
# Tareas

## Vencidas
```tasks
not done
due before today
sort by due
group by filename
limit 50
```

## Hoy
```tasks
not done
due today
sort by priority
limit 30
```

## Próximos 7 días
```tasks
not done
due after today
due before in 8 days
sort by due
limit 50
```

## Terminadas recientemente
```tasks
done
sort by done reverse
limit 25
```

## Solo un proyecto (copiar a su hub y ajustar la ruta)
```tasks
not done
path includes PRJ-2026-001
sort by due
group by filename
```
````

Añade `Home` y los hubs activos a **Marcadores**.

