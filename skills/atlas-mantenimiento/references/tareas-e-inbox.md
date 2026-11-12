# Gestión de tareas e Inbox


### Principio: una tarea, un hogar

Una tarea se escribe **una vez**, donde surge (reunión, incidencia, entregable, diario). Los paneles la consultan; nunca se copia a una lista maestra.

### Tres niveles

| Nivel | Qué es | Cuándo | Metadatos |
|---|---|---|---|
| **N1: línea** | `- [ ] Texto` dentro de cualquier nota | 90% de las tareas: pequeñas, de un paso | Solo texto |
| **N2: línea con metadatos** | Misma línea con fecha, prioridad o recurrencia | Tareas con vencimiento | Sintaxis del plugin Tasks |
| **N3: tarea-nota** | Nota `tipo: tarea` con propiedades | Más de 3 subtareas, documentos propios o más de dos días | YAML consultable con Bases |

**Promoción:** una N1 pasa a N3 cuando supera esos umbrales. La ruta del archivo ya indica el proyecto de una tarea en línea.

### Estados en línea

| Símbolo | Significado | Equivale a `estado` |
|---|---|---|
| `- [ ]` | Pendiente | pendiente |
| `- [/]` | En curso | en-curso |
| `- [x]` | Hecha | hecha |
| `- [-]` | Cancelada | cancelada |

`[/]` y `[-]` son estados personalizados; en el plugin Tasks se definen en sus ajustes de estados. Bloqueo: etiqueta `#bloqueada` más enlace a la incidencia (`- [ ] Desplegar 📅 2026-12-01 #bloqueada [[INC-004_Fallo-sync]]`). Las tareas hechas **no se borran**.

### Comparación de mecanismos

| Mecanismo | Veredicto |
|---|---|
| Checkboxes nativos | Base obligatoria; sin metadatos estructurados |
| Propiedades + Bases (tarea-nota) | Para tareas N3; Bases consulta notas, no líneas |
| Plugin **Tasks** | Recomendado: único que consulta líneas con fecha; usa siempre `limit` en las consultas |
| Dataview | Alternativa; no necesario si se usa Tasks y Bases |
| Kanban | Opcional, solo si se prefiere flujo visual |

El sistema funciona sin Tasks: pierde la consulta de líneas con fecha, que se sustituye por tareas-nota y la búsqueda nativa **[probar]**.

### Sintaxis del plugin Tasks

```markdown
- [ ] Redactar informe preliminar 🔺 📅 2026-11-20
- [ ] Revisar copias de seguridad 🔁 every week 📅 2026-11-16
- [ ] Enviar presupuesto ⏫ ⏳ 2026-11-12 📅 2026-11-14
```

`📅` vencimiento, `⏳` programada, `🔁` recurrencia, `🔺 ⏫ 🔼 🔽 ⏬` prioridad de mayor a menor, `✅` fecha de hecho. Si una instrucción de consulta falla, añade `explain` al bloque para ver cómo la interpreta el plugin; la documentación oficial está en publish.obsidian.md/tasks.

### Reglas de calidad

- Empieza con un verbo y describe una acción ejecutable.
- Evita tareas vagas (`Avanzar proyecto`, `Investigar`, `Organizar cosas`); descompón las grandes.
- Fecha límite solo cuando existe una fecha real. Separa fecha límite de fecha deseada o recordatorio.
- Prioridad solo cuando sirve para decidir.
- Identifica dependencias y bloqueos.
- Si una tarea está vencida, **no la marques como hecha ni cambies su fecha**: solicita decisión o recomienda una nueva fecha.

### Priorización

Evalúa en este orden:

1. Compromisos con fecha límite real.
2. Acciones que desbloquean otro trabajo.
3. Trabajo alineado con objetivos importantes.
4. Alto impacto y esfuerzo razonable.
5. Tareas rutinarias o de bajo impacto.

Recomienda una lista corta de próximos pasos, no una lista interminable.

### Detección de bloqueos y retrasos

| Señal | Cómo detectarla |
|---|---|
| Tarea vencida | Panel «Vencidas» de `Tareas.md`; `Fechas-limite.base` con días negativos |
| Tarea bloqueada | Búsqueda de `#bloqueada`; incidencias `abierta` en el panel del proyecto |
| Proyecto estancado | `Proyectos.base` ordenada por `file.mtime`; hubs sin modificar en 14+ días |
| Entregable en riesgo | Entregables con `vence` próximo y estado distinto de `en-revision` |

## 12. Inbox: captura y procesamiento

El Inbox es una bandeja temporal, no un archivo permanente. Máximo 7 días.

Al procesar cada elemento:

1. Lee el contenido y conserva su intención.
2. Identifica si es tarea, idea, proyecto, referencia, concepto, procedimiento o descartable.
3. Busca notas relacionadas antes de crear otras nuevas.
4. Si es una tarea, redacta una acción concreta y propón su proyecto.
5. Si es un proyecto, define resultado y siguiente paso; si falta información, deja preguntas pendientes.
6. Si es referencia o concepto, recomienda su destino en `03_Conocimiento`.
7. Si no se puede clasificar, mantenlo en Inbox y explica qué falta.
8. **No elimines ni muevas nada sin autorización.**

Al informar del Inbox, diferencia entre: elementos procesables, elementos que necesitan una decisión, duplicados o posiblemente obsoletos, y elementos sin contexto.

