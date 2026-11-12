# Biblioteca de plantillas


Las plantillas viven en `90_Sistema/Plantillas/` y se llaman `Plantilla - <Tipo>.md`. Usan solo la sintaxis del plugin nativo **Templates**: `{{title}}`, `{{date:YYYY-MM-DD}}`, `{{time:HH:mm}}`. Los IDs (`PRJ-…`, `DEC-…`) se escriben a mano, salvo que el usuario use Templater.

Todas comparten el encabezado `tipo`, `creado`, `proyecto`, `estado`. **La plantilla de proyecto nuevo y la del índice del proyecto son la misma nota** (el hub): mantener dos sería redundancia.

Para crear un proyecto, el usuario **duplica `90_Sistema/Esqueleto-Proyecto/`** en `02_Proyectos/` y la renombra; las carpetas opcionales vacías pueden borrarse en proyectos Mini. Si el sistema de sincronización ignora carpetas vacías, añadir una nota mínima o `.gitkeep`.

Al entregar plantillas en un mensaje, puedes presentarlas completas o solo las necesarias para la tarea del usuario. No las apliques ni crees archivos sin autorización.

### Proyecto (hub e índice)

`Plantilla - Proyecto.md`, se guarda como `PRJ-AAAA-NNN_Nombre.md` en la raíz del proyecto.

````markdown
---
tipo: proyecto
id: PRJ-AAAA-NNN
creado: {{date:YYYY-MM-DD}}
estado: idea
prioridad: 3
inicio:
vence:
responsable:
categoria:
modalidad: finito
siguiente_accion:
tags: []
---
# {{title}}

> **En una frase:** qué se va a lograr y para quién.

## 1. Descripción
Contexto, necesidad que cubre y motivo de existir (3 a 6 líneas).

## 2. Objetivos y resultados esperados
- [ ] Objetivo 1 (medible)
- [ ] Objetivo 2

**Criterio de éxito:** cómo sabré que terminó bien.

## 3. Alcance
**Incluye:**
-

**No incluye:**
-

**Limitaciones y supuestos:**
-

## 4. Fases e hitos
Ver [[PRJ-AAAA-NNN_Planificacion]].

## 5. Recursos
- Personas:
- Herramientas:
- Presupuesto / tiempo disponible:

## 6. Navegación
- Gestión: [[PRJ-AAAA-NNN_Planificacion]] · [[PRJ-AAAA-NNN_Tareas]] · [[PRJ-AAAA-NNN_Riesgos]]
- Conocimiento: carpeta `02_Conocimiento`
- Entregables: carpeta `04_Entregables`

## 7. Panel del proyecto
![[Proyecto - Panel.base]]

## 8. Estado en 3 líneas (actualizar en la revisión semanal)
- Hecho:
- En curso:
- Bloqueos:
````

### Planificación (incluye requisitos y cronograma)

`Plantilla - Planificacion.md` → `PRJ-AAAA-NNN_Planificacion.md`

````markdown
---
tipo: plan
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: borrador
tags: []
---
# Planificación: {{title}}

## Fases
| Fase | Objetivo de la fase | Inicio | Fin | Estado |
|---|---|---|---|---|
| 1. Definición | | | | pendiente |
| 2. Diseño | | | | pendiente |
| 3. Ejecución | | | | pendiente |
| 4. Evaluación y cierre | | | | pendiente |

## Hitos
- [ ] Hito 1 📅 AAAA-MM-DD
- [ ] Hito 2 📅 AAAA-MM-DD

## Requisitos (solo si el resultado debe cumplir condiciones verificables)
| ID | Requisito | Prioridad | Verificación |
|---|---|---|---|
| R1 | | alta | |

## Dependencias
-

## Plan de comunicación
- Quién recibe qué información y con qué frecuencia.
````

### Tarea (tarea-nota, nivel 3)

`Plantilla - Tarea.md`

````markdown
---
tipo: tarea
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: pendiente
prioridad: 3
vence:
responsable:
entregable: ""
tags: []
---
# {{title}}

**Resultado esperado:** una frase.

## Subtareas
- [ ] Paso 1
- [ ] Paso 2
- [ ] Paso 3

## Contexto y enlaces
- Relacionado con: [[ ]]
- Documentos: [[ ]]

## Bloqueos
Ninguno.

## Registro
- {{date:YYYY-MM-DD}}: creada.
````

### Reunión

`Plantilla - Reunion.md` → `AAAA-MM-DD Tema.md`

````markdown
---
tipo: reunion
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
fecha: {{date:YYYY-MM-DD}}
asistentes: []
tags: []
---
# {{title}}

**Objetivo de la reunión:**

## Orden del día
1.
2.

## Notas

## Decisiones
- [[DEC-NNN_]] (enlazar, no repetir el contenido)

## Acciones
- [ ] Acción — @responsable 📅 AAAA-MM-DD

## Próxima reunión
````

### Investigación

`Plantilla - Investigacion.md`

````markdown
---
tipo: investigacion
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: borrador
fuentes: []
tags: []
---
# {{title}}

## Pregunta de investigación

## Contexto

## Método
Cómo se busca o se obtiene la información.

## Hallazgos
- Hallazgo 1 (fuente: [[@autorAAAA]])

## Análisis

## Conclusiones provisionales

## Preguntas abiertas
- [ ]

## Siguientes pasos
- [ ]
````

### Referencia bibliográfica

`Plantilla - Referencia.md` → `03_Conocimiento/Referencias/@apellidoAAAA.md`

````markdown
---
tipo: referencia
creado: {{date:YYYY-MM-DD}}
estado: por-leer
citekey:
autores: []
anio:
fuente_tipo: articulo
url:
doi:
tags: []
---
# {{title}}

**Cita completa:** formato elegido (APA, IEEE…).

## Resumen en mis palabras

## Ideas clave
-

## Citas textuales (con página)
>

## Utilidad para mis proyectos
- Usada en: [[ ]]

## Valoración
Fiabilidad y limitaciones.
````

### Documento técnico

`Plantilla - Tecnica.md`

````markdown
---
tipo: tecnica
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: borrador
version: 0.1
tags: []
---
# {{title}}

## Propósito y alcance

## Contexto y requisitos que cubre
- Requisitos: [[PRJ-AAAA-NNN_Planificacion]]

## Diseño / especificación

## Alternativas consideradas
| Alternativa | Pros | Contras |
|---|---|---|

## Decisiones relacionadas
- [[DEC-NNN_]]

## Riesgos técnicos

## Pruebas / validación

## Historial de cambios
| Versión | Fecha | Cambio |
|---|---|---|
| 0.1 | {{date:YYYY-MM-DD}} | Primera versión |
````

### Decisión

`Plantilla - Decision.md` → `DEC-NNN_Titulo-corto.md`. Sigue el patrón de registro de decisiones (ADR). Una decisión **nunca se borra**: si cambia, la nueva incluye `reemplaza` y la antigua pasa a `reemplazada`.

````markdown
---
tipo: decision
id: DEC-NNN
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: propuesta
decidido:
responsable:
reemplaza:
tags: []
---
# DEC-NNN: {{title}}

## Contexto
Qué problema o disyuntiva existía. Enlaces: [[INC-NNN_]], [[AAAA-MM-DD Reunion]].

## Opciones consideradas
1. **Opción A:** ventajas / desventajas.
2. **Opción B:** ventajas / desventajas.

## Decisión
Se elige **…** porque …

## Consecuencias
- Positivas:
- Negativas o riesgos aceptados:
- Tareas derivadas: [[ ]]

## Condiciones de revisión
Cuándo habría que reconsiderarla.
````

### Incidencia

`Plantilla - Incidencia.md` → `INC-NNN_Titulo-corto.md`

````markdown
---
tipo: incidencia
id: INC-NNN
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: abierta
gravedad: 3
prioridad: 3
vence:
responsable:
causa_raiz:
tags: []
---
# INC-NNN: {{title}}

## Descripción y síntomas

## Impacto
Qué afecta y a quién.

## Análisis de causa

## Acciones
- [ ] Contención inmediata
- [ ] Corrección definitiva
- [ ] Prevención

## Resolución
Qué se hizo. Decisión asociada: [[DEC-NNN_]]

## Lección aprendida
````

### Idea

`Plantilla - Idea.md`. Puede nacer en `00_Inbox` sin `proyecto`.

````markdown
---
tipo: idea
creado: {{date:YYYY-MM-DD}}
estado: nueva
proyecto: ""
tags: []
---
# {{title}}

**La idea en una frase:**

## Problema que resuelve

## Primera evaluación
- Valor (1 a 5):
- Esfuerzo (1 a 5):
- ¿Encaja con un proyecto existente?:

## Siguiente paso
Adoptar (crear tarea o decisión) · Evaluar más · Descartar (con motivo).
````

### Seguimiento

`Plantilla - Seguimiento.md` → `AAAA-Wnn Seguimiento.md`

````markdown
---
tipo: seguimiento
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
periodo: AAAA-Wnn
salud: verde
tags: []
---
# Seguimiento {{title}}

**Salud global:** verde / ámbar / rojo (propiedad `salud`)

## Logros del período
-

## Pendiente para el próximo período
-

## Bloqueos, riesgos e incidencias
- [[INC-NNN_]]

## Desviaciones
Plan vs real (tiempo, alcance, coste).

## Decisiones necesarias
-
````

### Entregable

`Plantilla - Entregable.md` → `ENT-NNN_Titulo.md`

````markdown
---
tipo: entregable
id: ENT-NNN
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: pendiente
prioridad: 2
vence:
responsable:
aceptacion:
tags: []
---
# ENT-NNN: {{title}}

## Descripción

## Criterios de aceptación (control de calidad)
- [ ] Criterio 1
- [ ] Criterio 2

## Tareas que lo producen
- [[ ]]

## Versión final
Enlace o archivo: ![[archivo.pdf]]

## Revisión y aceptación
- Revisado por / fecha:
- Observaciones:
````

### Informe final y cierre

`Plantilla - Cierre.md` → `05_Cierre/`

````markdown
---
tipo: cierre
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: borrador
tags: []
---
# Informe de cierre: {{title}}

## Resumen ejecutivo

## Objetivos: previsto frente a logrado
| Objetivo | Resultado | Cumplido |
|---|---|---|

## Entregables
- [[ENT-001_]] — aceptado

## Plan frente a realidad
Tiempo, coste, alcance.

## Lecciones aprendidas
- Qué funcionó:
- Qué no funcionó:
- Qué haría distinto:

## Conocimiento a conservar
Notas a promover a `03_Conocimiento` (conceptos, procedimientos, referencias).

## Lista de cierre
- [ ] Entregables aceptados
- [ ] Tareas abiertas cerradas o trasladadas
- [ ] Conocimiento reutilizable extraído
- [ ] `estado: completado` en el hub
- [ ] Carpeta movida a `05_Archivo/Proyectos/AAAA/`
````

### Complementarias

**Riesgos** (`Plantilla - Riesgos.md`, opcional):

````markdown
---
tipo: plan
proyecto: "[[PRJ-AAAA-NNN_Nombre]]"
creado: {{date:YYYY-MM-DD}}
estado: vigente
tags: [riesgos]
---
# Registro de riesgos

| ID | Riesgo | Probabilidad (1-3) | Impacto (1-3) | Mitigación | Responsable | Estado |
|---|---|---|---|---|---|---|
| RSK-1 | | | | | | abierto |

> Puntuación = probabilidad × impacto. Revisar semanalmente los ≥ 6.
````

**Diario** (`Plantilla - Diario.md`, para el plugin nativo Notas diarias):

````markdown
---
tipo: diario
creado: {{date:YYYY-MM-DD}}
---
# {{date:dddd, D [de] MMMM [de] YYYY}}

## Prioridades de hoy (máximo 3)
- [ ]

## Registro

## Proyectos tocados hoy
- [[ ]]

## Captura rápida
````

**Revisión semanal** (`Plantilla - Revision.md`):

````markdown
---
tipo: revision
creado: {{date:YYYY-MM-DD}}
periodo: AAAA-Wnn
---
# Revisión {{title}}

## Checklist
- [ ] Inbox vacío
- [ ] Cada proyecto activo con estado actualizado
- [ ] Tareas vencidas revisadas
- [ ] Notas sin proyecto ni enlaces revisadas
- [ ] Próximas 3 prioridades de la semana definidas

## Lo más importante de la semana

## Ajustes al sistema
````

**Procedimiento** y **Concepto** siguen el mismo patrón: `tipo: procedimiento` con secciones *Cuándo usarlo · Pasos · Comprobación · Errores frecuentes*, y `tipo: concepto` con *Definición en una frase · Explicación · Ejemplos · Relacionado*.

