# Estándar ATLAS (compartido por las tres skills)

> Este archivo es **idéntico** en `atlas-proyecto`, `atlas-plantillas` y `atlas-mantenimiento`. Si cambias una convención (propiedades, estados, nombres, carpetas), cámbiala en los tres archivos a la vez; si no, las skills se contradirán.

## 3. Modelo mental del sistema

No confundas estas entidades:

- **Inbox:** material recién capturado, sin clasificar. Dura como máximo 7 días.
- **Proyecto:** resultado concreto que requiere varias acciones y tiene un estado de finalización. Se representa con una carpeta y una nota **hub**.
- **Tarea:** acción ejecutable, con verbo. Tiene tres niveles (sección 11).
- **Idea:** propuesta sin decidir. Puede adoptarse, evaluarse o descartarse.
- **Decisión:** elección registrada con contexto, alternativas y consecuencias. Nunca se borra; se reemplaza.
- **Incidencia:** problema, bloqueo o cambio no previsto, con causa y resolución.
- **Entregable:** resultado comprometido, con criterios de aceptación.
- **Referencia:** ficha de una fuente externa, reutilizable entre proyectos.
- **Concepto:** idea atómica reutilizable, escrita en palabras propias.
- **Procedimiento:** cómo se hace algo repetible.
- **Entidad:** persona u organización.
- **Registro temporal:** nota diaria o revisión periódica.
- **Archivo:** proyectos cerrados y conocimiento obsoleto.

### Criterio para decidir qué crear

- Resultado definido con varias acciones, **o** más de unos pocos días de trabajo → proyecto.
- Una sola acción → tarea (línea dentro de otra nota).
- Tarea con subtareas, adjuntos o varios días → tarea-nota.
- Algo que debe decidirse y justificarse → decisión.
- Un problema que afecta al trabajo → incidencia.
- Información externa a conservar → referencia (en `03_Conocimiento/Referencias`).
- Conocimiento que sirve a más de un proyecto → concepto o procedimiento global.
- Responsabilidad continua sin fecha final → proyecto con `modalidad: continuo`.
- Si todavía no se entiende qué es → permanece en `00_Inbox` hasta aclararlo.

### Tamaño del proyecto

| Tamaño | Duración típica | Estructura |
|---|---|---|
| **Mini** | menos de 2 semanas | Hub + `Tareas` + `04_Entregables` |
| **Estándar** | 1 a 3 meses | Núcleo completo; Reuniones, Decisiones e Investigación según necesidad |
| **Mayor** | más de 3 meses o varias personas | Núcleo completo + Riesgos, Seguimiento, Incidencias, Requisitos y Cierre formal |

## 4. Principios de diseño y regla de los tres mecanismos

Principios: universalidad, modularidad, escalabilidad, consistencia, flexibilidad, claridad, mantenibilidad, navegabilidad, interconectividad, independencia tecnológica y profesionalismo. Aplícalos así:

| Mecanismo | Responde a | Úsalo para | No lo uses para |
|---|---|---|---|
| **Carpetas** | ¿Dónde vive y en qué fase de vida está? | Proyecto de pertenencia, activo o archivo, adjuntos | Tipo de nota, estado, tema |
| **Propiedades (YAML)** | ¿Qué es y en qué situación está? | Tipo, estado, prioridad, fechas, proyecto, responsable | Texto largo |
| **Enlaces `[[ ]]`** | ¿Con qué se relaciona? | Decisión → incidencia, tarea → entregable, nota → referencia | Clasificación masiva |
| **Etiquetas `#`** | ¿De qué tema trata, transversalmente? | `#tema/seguridad`, `#bloqueada`, `#revisar` | Estado, tipo o proyecto |

**Regla práctica:** si dudas entre carpeta, etiqueta y propiedad, elige la propiedad.

**Qué evitar siempre:** carpetas por tipo de nota (salvo tipos de alto volumen: reuniones, decisiones, incidencias), más de cuatro niveles de profundidad, copiar el mismo dato en varios sitios y propiedades "por si acaso".

## 5. Arquitectura del vault

Recomendación: **un único vault** con arquitectura híbrida. Solo se usa un vault satélite si hay confidencialidad contractual o adjuntos de varios GB; en ese caso se copia `90_Sistema` para que nazca con la misma estructura.

```text
Atlas/
├── 00_Inbox/
├── 01_Dashboard/
├── 02_Proyectos/
│   └── PRJ-AAAA-NNN_Nombre/
├── 03_Conocimiento/
│   ├── Referencias/
│   ├── Conceptos/
│   ├── Procedimientos/
│   └── Entidades/
├── 04_Diario/
│   ├── Diario/AAAA/
│   └── Revisiones/
├── 05_Archivo/
│   ├── Proyectos/AAAA/
│   └── Conocimiento-obsoleto/
├── 90_Sistema/
│   ├── Plantillas/
│   ├── Bases/
│   ├── Guia/
│   └── Esqueleto-Proyecto/
└── 99_Adjuntos/
```

| Carpeta | Propósito | NO contiene |
|---|---|---|
| `00_Inbox` | Captura rápida sin decidir destino. Siempre plana. | Nada que lleve más de 7 días |
| `01_Dashboard` | `Home.md` y paneles (`.base` y `.md` con consultas) | Contenido de proyectos |
| `02_Proyectos` | Una carpeta `PRJ-…` por proyecto vivo | Proyectos terminados; conocimiento reutilizable |
| `03_Conocimiento` | Biblioteca compartida entre proyectos | Notas que solo sirven a un proyecto |
| `04_Diario` | Notas diarias y revisiones semanales y mensuales | Documentación de proyecto |
| `05_Archivo` | Memoria histórica fuera del camino diario | Material activo |
| `90_Sistema` | Plantillas, bases reutilizables, guías, esqueleto de proyecto | Contenido de trabajo |
| `99_Adjuntos` | Archivos usados por varios proyectos o sin proyecto | Adjuntos de un solo proyecto |

**Criterio para subdividir:** una carpeta se subdivide al superar unas 15 notas **y** existir un criterio natural de agrupación. Nunca por anticipado. Subcarpetas por año en `02_Proyectos` solo con más de ~30 proyectos activos.

## 6. Estructura interna de un proyecto

```text
PRJ-AAAA-NNN_Nombre/
├── PRJ-AAAA-NNN_Nombre.md                  ← hub (obligatorio)
├── 01_Gestion/                             ← obligatoria
│   ├── PRJ-AAAA-NNN_Planificacion.md
│   ├── PRJ-AAAA-NNN_Tareas.md              (opcional)
│   ├── PRJ-AAAA-NNN_Riesgos.md             (opcional)
│   ├── Reuniones/                          (al primer acta)
│   ├── Decisiones/                         (al primer registro)
│   ├── Incidencias/                        (al primer problema)
│   └── Seguimiento/                        (proyectos de más de 4 semanas)
├── 02_Conocimiento/                        (opcional)
│   ├── Investigacion/
│   ├── Tecnica/
│   └── Ideas/
├── 03_Trabajo/                             (según disciplina)
├── 04_Entregables/                         ← obligatoria
├── 05_Cierre/                              (se crea al cerrar)
└── _adjuntos/
```

**Nombres únicos:** las notas fijas de gestión llevan el ID del proyecto como prefijo para que los enlaces `[[ ]]` no sean ambiguos entre proyectos. Nunca crees `Planificacion.md` o `Tareas.md` sin prefijo.

**Regla de ubicación del conocimiento:** lo que solo sirve al proyecto va en su `02_Conocimiento`; lo que sirve a varios proyectos va en `03_Conocimiento`. Las referencias bibliográficas siempre son globales.

### Qué forma parte del núcleo y qué se activa

| Elemento | Dónde vive | Núcleo o activable |
|---|---|---|
| Identificación, objetivos, alcance | Hub | **Núcleo** |
| Planificación, cronograma, fases | `Planificacion` | **Núcleo** |
| Tareas | Checkboxes en notas (+ `Tareas`) | **Núcleo** |
| Recursos (lista breve) | Hub | **Núcleo** |
| Entregables | `04_Entregables` | **Núcleo** |
| Requisitos y especificaciones | `Planificacion` (sección) | Activable: resultado con condiciones verificables |
| Investigación y documentación | `02_Conocimiento/Investigacion` | Activable |
| Referencias y fuentes | `03_Conocimiento/Referencias` + enlaces | Activable |
| Ideas y propuestas | `02_Conocimiento/Ideas` | Activable |
| Diseño y planificación técnica | `02_Conocimiento/Tecnica` | Activable |
| Desarrollo y ejecución | `03_Trabajo` | Activable |
| Seguimiento del progreso | `01_Gestion/Seguimiento` | Activable |
| Reuniones y comunicaciones | `01_Gestion/Reuniones` | Activable |
| Decisiones | `01_Gestion/Decisiones` | Activable |
| Problemas e incidencias | `01_Gestion/Incidencias` | Activable |
| Riesgos y mitigación | `Riesgos` | Activable: proyectos con incertidumbre |
| Evaluación y calidad | Criterios de aceptación en el entregable | Activable |
| Conclusiones, documentación final, cierre | `05_Cierre` | Se activa al cerrar |

## 7. Tipos de nota y relaciones

| `tipo` | Función | Dónde vive |
|---|---|---|
| `proyecto` | Hub: identidad y puerta de entrada | Raíz del proyecto |
| `plan` | Planificación, fases, cronograma, requisitos, riesgos | `01_Gestion` |
| `tarea` | Tarea compleja con entidad propia | `01_Gestion` o `03_Trabajo` |
| `reunion` | Acta, acuerdos y acciones | `01_Gestion/Reuniones` |
| `investigacion` | Pregunta, método, hallazgos | `02_Conocimiento/Investigacion` |
| `referencia` | Ficha de fuente externa | `03_Conocimiento/Referencias` |
| `tecnica` | Diseño, especificación, documentación técnica | `02_Conocimiento/Tecnica` |
| `procedimiento` | Cómo se hace algo repetible | `03_Conocimiento/Procedimientos` |
| `decision` | Qué se decidió, por qué y alternativas | `01_Gestion/Decisiones` |
| `incidencia` | Problema, causa, resolución | `01_Gestion/Incidencias` |
| `idea` | Propuesta sin decidir | `02_Conocimiento/Ideas` o `00_Inbox` |
| `aprendizaje` | Lo aprendido | `02_Conocimiento` o `03_Conocimiento/Conceptos` |
| `seguimiento` | Estado periódico | `01_Gestion/Seguimiento` |
| `entregable` | Resultado comprometido | `04_Entregables` |
| `resultado` | Datos o resultados obtenidos | `03_Trabajo` o `04_Entregables` |
| `cierre` | Informe final y lecciones | `05_Cierre` |
| `concepto` | Idea atómica reutilizable | `03_Conocimiento/Conceptos` |
| `entidad` | Persona u organización | `03_Conocimiento/Entidades` |
| `diario` / `revision` | Registro temporal | `04_Diario` |
| `dashboard` | Panel de navegación | `01_Dashboard` |

### Cadena de relaciones

```text
Idea ──► Decisión ──► Tarea ──► Entregable ──► Cierre
  │         │            │          │
  │         └──► Incidencia ◄───────┘
  └──► Referencia / Concepto (conocimiento compartido)
Reunión ──► Decisiones + Tareas (acciones)
```

### Cómo evitar duplicaciones, dispersión y huérfanas

- **Duplicados:** una referencia = una nota global. Buscar antes de crear un concepto.
- **Dispersión:** el hub enlaza todo lo relevante y embebe el panel del proyecto.
- **Huérfanas:** toda nota nace con `proyecto` o con un enlace entrante. La revisión semanal incluye la vista de grafo o una búsqueda de notas sin enlaces entrantes.
- **Tareas repetidas:** la tarea vive en un solo lugar (donde surge) y los paneles la consultan.
- **Estado desactualizado:** el estado vive solo en la propiedad `estado`; el resto lo muestra por consulta.

## 8. Convenciones de nombres e identificadores

| Elemento | Convención | Ejemplo |
|---|---|---|
| Carpetas de raíz y módulo | `NN_Nombre`, sin espacios | `02_Proyectos`, `01_Gestion` |
| Carpeta y hub de proyecto | `PRJ-AAAA-NNN_Nombre-con-guiones` | `PRJ-2026-001_App-reservas` |
| Notas fijas de gestión | Prefijo = ID del proyecto | `PRJ-2026-001_Planificacion.md` |
| Notas con ID | `TIPO-NNN_Titulo-corto` | `DEC-003_Usar-PostgreSQL.md` |
| Notas por fecha | `AAAA-MM-DD Tema` | `2026-11-09 Kickoff.md` |
| Notas semanales | `AAAA-Wnn Tema` | `2026-W46 Seguimiento.md` |
| Referencias | `@apellidoAAAA` (letra si hay colisión) | `@garcia2024.md` |
| Plantillas | `Plantilla - Tipo` | `Plantilla - Decision.md` |
| Adjuntos | `AAAA-MM-DD_descripcion.ext`, minúsculas | `2026-11-09_diagrama.png` |

| Identificador | Formato | Alcance |
|---|---|---|
| Proyecto | `PRJ-AAAA-NNN` | Correlativo anual |
| Entregable | `ENT-NNN` | Correlativo dentro del proyecto |
| Decisión | `DEC-NNN` | Correlativo dentro del proyecto |
| Incidencia | `INC-NNN` | Correlativo dentro del proyecto |
| Referencia | `@apellidoAAAA` | Global |

Reglas generales:

- Evita `# ^ [ ] | \ /` y `:` en nombres; evita acentos y eñes en **carpetas y adjuntos**.
- **Fechas siempre ISO 8601** (`AAAA-MM-DD`), al principio del nombre cuando el orden temporal importa. No pongas fechas en notas que se actualizan.
- **Etiquetas:** minúsculas, sin acentos, jerárquicas con `/`; solo para temas transversales y para `#bloqueada` y `#revisar`; menos de 40 etiquetas distintas.
- `categoria` usa una lista corta y cerrada: `gestion`, `desarrollo`, `investigacion`, `diseño`, `contenido`, `docencia`, `comercial`, `aprendizaje`, `administracion`.
- **Adjuntos:** configurar Obsidian para guardarlos en una subcarpeta `_adjuntos` bajo la carpeta actual, con actualización automática de enlaces internos activada. Imágenes de más de ~1 MB se redimensionan; vídeos de más de ~50 MB se enlazan, no se guardan; los documentos externos finales van a `04_Entregables` o `_adjuntos`.
- **Enlaces externos:** con texto descriptivo; fuente, fecha de consulta y motivo en la nota de referencia; copia en PDF de las fuentes importantes.
- **Control de versiones:** propiedad `version` y tabla de historial en documentos importantes; Recuperación de archivos de Obsidian para borrados accidentales; Git solo si se necesita historial completo.

## 9. Propiedades y metadatos (YAML)

### Reglas de oro

1. Nombres en minúsculas, sin acentos ni espacios, en español.
2. **Un nombre, un tipo en todo el vault.** No reutilices un nombre de propiedad con otro sentido.
3. Valores controlados para `tipo`, `estado` y `prioridad`.
4. Fechas ISO 8601.
5. Enlaces dentro de propiedades entre comillas: `proyecto: "[[PRJ-2026-001_App-reservas]]"`.
6. No dupliques lo que Obsidian ya sabe: no hay propiedad `modificado` obligatoria (existe `file.mtime` en Bases).
7. `tags`, `aliases` y `cssclasses` son nombres reservados por Obsidian.
8. No rellenes campos con datos inventados. Si no se conoce el valor, déjalo vacío.

### Nivel 1: globales (todas las notas)

```yaml
---
tipo: tarea
creado: 2026-11-09
tags: []
---
```

### Nivel 2: compartidas por las notas de proyecto

```yaml
---
proyecto: "[[PRJ-2026-001_App-reservas]]"
estado: pendiente
prioridad: 2
vence: 2026-12-01
responsable: Ana
categoria: desarrollo
fuentes: ["[[@garcia2024]]"]
---
```

- `proyecto` es **obligatoria** en toda nota dentro de `02_Proyectos`.
- `prioridad` es numérica: `1` crítica, `2` alta, `3` media, `4` baja (para ordenar correctamente).
- `vence` solo existe cuando hay una fecha real.
- `fuentes` solo en notas con apoyo documental.
- El hub puede incluir `siguiente_accion` (texto breve con el siguiente paso verificable) para detectar proyectos activos sin próxima acción.

### Vocabularios de `estado`

| Tipo | Estados permitidos |
|---|---|
| `proyecto` | `idea` · `evaluacion` · `planificacion` · `activo` · `pausa` · `bloqueado` · `completado` · `cancelado` · `archivado` |
| `tarea`, `entregable` | `pendiente` · `en-curso` · `bloqueada` · `hecha` · `cancelada` (entregable añade `en-revision` · `aceptado`) |
| `decision` | `propuesta` · `aceptada` · `rechazada` · `reemplazada` |
| `incidencia` | `abierta` · `en-analisis` · `resuelta` · `cerrada` |
| `idea` | `nueva` · `evaluando` · `adoptada` · `descartada` |
| `investigacion`, `tecnica`, `plan` | `borrador` · `vigente` · `obsoleta` |
| `referencia` | `por-leer` · `leyendo` · `leida` |

### Nivel 3: específicas por tipo

```yaml
# reunion
fecha: 2026-11-09
asistentes: ["[[Ana Perez]]"]

# decision
id: DEC-003
decidido: 2026-11-09
reemplaza: ""

# incidencia
id: INC-004
gravedad: 2        # 1 crítica ... 4 menor
causa_raiz: ""

# entregable
id: ENT-001
aceptacion: ""

# referencia
citekey: garcia2024
autores: ["García, M."]
anio: 2024
fuente_tipo: articulo   # articulo | libro | web | informe | video
url: ""
doi: ""

# seguimiento
periodo: 2026-W46
salud: verde            # verde | ambar | rojo
```

### Nivel 4: especializadas por disciplina (solo si el proyecto las necesita)

```yaml
# Software
repo: ""
version: 0.1.0
entorno: dev          # dev | test | prod
stack: ""

# Investigación
hipotesis: ""
metodo: ""
conjunto_datos: ""
repetible: true

# Tesis
capitulo: 1
palabras_objetivo: 0
palabras_actuales: 0
tutor: ""

# Empresarial
cliente: ""
presupuesto: 0
coste_real: 0
sponsor: ""

# Contenido
canal: ""
formato: video        # video | articulo | podcast | libro
fecha_publicacion:
etapa: idea           # idea | guion | produccion | edicion | publicado

# Aprendizaje
habilidad: ""
nivel: 1              # 1 a 5
horas_dedicadas: 0
```

Si el vault ya usa otras propiedades (por ejemplo en inglés, `status`, `due_date`), **no las renombres masivamente**: propón una tabla de equivalencias y migra por lotes pequeños solo con autorización.

