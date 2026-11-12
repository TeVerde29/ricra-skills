---
name: atlas-plantillas
description: Entrega, adapta y crea plantillas de notas, bloques de propiedades YAML, Bases (.base) y dashboards listos para copiar en Obsidian, siguiendo el estándar ATLAS. Auto-activate on /atlas-plantillas o cuando el usuario pida una plantilla, un bloque de propiedades, una Base, un panel o un dashboard para Obsidian (reunión, tarea, decisión, entregable, referencia, cierre, panel de proyecto, fechas límite, etc.).
---

# Skill: atlas-plantillas

## Qué hace

Es la **biblioteca de piezas** de ATLAS. Entrega plantillas, propiedades YAML, Bases y dashboards **listos para copiar**, adapta una plantilla a la disciplina del usuario y crea plantillas nuevas que encajan con el estándar.

Esta skill **entrega piezas**. No decide la arquitectura de un proyecto (eso es `atlas-proyecto`) ni hace revisiones (eso es `atlas-mantenimiento`).

## Reglas

1. **Solo sintaxis nativa de Templates** en las plantillas: `{{title}}`, `{{date:YYYY-MM-DD}}`, `{{time:HH:mm}}`. Los IDs (`PRJ-…`, `DEC-…`) se escriben a mano, salvo que el usuario use Templater y lo pida.
2. **Todas las plantillas comparten el mismo encabezado:** `tipo`, `creado`, `proyecto`, `estado`. Los valores salen de los vocabularios de `references/estandar.md`.
3. **Bases: solo sintaxis verificada.** Claves raíz `filters`, `formulas`, `properties`, `summaries` y `views`; vistas `table`, `cards`, `list` (y `map` con el plugin Maps). **Nunca uses `from:` ni `where:` (son de Dataview).** Define toda `formula.X` que uses en `order`.
4. Marca **[probar]** lo que dependa de la versión (por ejemplo `this.file.folder` en una base incrustada, o `date(vence) - today()`) y ofrece la alternativa robusta.
5. **No crees ni modifiques archivos sin autorización.** Entrega el bloque y di dónde guardarlo.
6. Un nombre de propiedad, un tipo en todo el vault. No reutilices nombres con otro sentido. Nombres en minúsculas, sin acentos ni espacios.
7. No inventes funciones de Obsidian ni de plugins. Si no estás seguro de una instrucción, dilo y recomienda comprobarla en la documentación oficial.
8. Si el usuario ya tiene propiedades propias, adapta la pieza a ellas en lugar de imponer las de ATLAS.

## Cómo trabajar

1. **Identifica qué pide:** plantilla de nota, bloque de propiedades, Base, dashboard, adaptación o plantilla nueva.
2. **Busca en el catálogo** de abajo y abre el archivo de referencia correspondiente.
3. **Entrega la pieza** con: el bloque completo, dónde guardarla, cómo usarla (qué se rellena y qué es automático) y un ejemplo breve.
4. **Si adapta:** parte de la plantilla base, cambia solo lo necesario, conserva el encabezado común y añade las propiedades de nivel 4 de la disciplina.
5. **Si crea una nueva:** sigue las reglas de «Plantilla nueva» y propón añadirla al catálogo.

## Catálogo de plantillas

Todas están completas en `references/plantillas.md`.

| Plantilla | `tipo` | Se guarda como | Para qué |
|---|---|---|---|
| `Plantilla - Proyecto` | `proyecto` | `PRJ-AAAA-NNN_Nombre.md` (hub) | Ficha y página principal del proyecto |
| `Plantilla - Planificacion` | `plan` | `PRJ-AAAA-NNN_Planificacion.md` | Fases, hitos, requisitos, dependencias |
| `Plantilla - Tarea` | `tarea` | Nota en `01_Gestion` o `03_Trabajo` | Tarea compleja con subtareas |
| `Plantilla - Reunion` | `reunion` | `AAAA-MM-DD Tema.md` | Acta, decisiones y acciones |
| `Plantilla - Investigacion` | `investigacion` | `02_Conocimiento/Investigacion` | Pregunta, método, hallazgos |
| `Plantilla - Referencia` | `referencia` | `@apellidoAAAA.md` global | Ficha de una fuente |
| `Plantilla - Tecnica` | `tecnica` | `02_Conocimiento/Tecnica` | Diseño y especificación |
| `Plantilla - Decision` | `decision` | `DEC-NNN_Titulo.md` | Decisión con contexto y alternativas |
| `Plantilla - Incidencia` | `incidencia` | `INC-NNN_Titulo.md` | Problema, causa y resolución |
| `Plantilla - Idea` | `idea` | `00_Inbox` o `Ideas/` | Propuesta sin decidir |
| `Plantilla - Seguimiento` | `seguimiento` | `AAAA-Wnn Seguimiento.md` | Estado periódico |
| `Plantilla - Entregable` | `entregable` | `ENT-NNN_Titulo.md` | Resultado con criterios de aceptación |
| `Plantilla - Cierre` | `cierre` | `05_Cierre/` | Informe final y lecciones |
| `Plantilla - Riesgos` | `plan` | `PRJ-AAAA-NNN_Riesgos.md` | Registro de riesgos |
| `Plantilla - Diario` | `diario` | `04_Diario/Diario` | Nota del día |
| `Plantilla - Revision` | `revision` | `04_Diario/Revisiones` | Revisión semanal |
| `Plantilla - Procedimiento` / `Concepto` | `procedimiento` / `concepto` | `03_Conocimiento/…` | Conocimiento reutilizable |

## Catálogo de Bases y dashboards

Completos en `references/bases.md`.

| Pieza | Para qué |
|---|---|
| `Proyectos.base` | Índice general de proyectos |
| `Proyecto - Panel.base` | Panel embebido en cada hub |
| `Fechas-limite.base` | Vencimientos de todo el vault |
| `Prioridades.base` | Lo crítico y lo alto |
| `Reuniones.base`, `Documentacion.base`, `Recursos.base`, `Archivo.base` | Se construyen con el mismo patrón cambiando filtro y `order` |
| `Home.md` | Dashboard principal |
| `Tareas.md` | Paneles de tareas (requiere el plugin Tasks) |

## Plantilla nueva (para una disciplina o necesidad propia)

1. Usa el encabezado común (`tipo`, `creado`, `proyecto`, `estado`).
2. El `tipo` y el `estado` salen de los vocabularios del estándar; si hace falta un valor nuevo, propón añadirlo al estándar.
3. Añade solo las propiedades que alimenten alguna vista o filtro.
4. Secciones cortas y útiles: no más de las que se usarán.
5. Nombre de archivo: `Plantilla - <Tipo>.md`.
6. Entrega junto con la Base o consulta que la aprovecha, si procede.

## Plugins

Si la pieza depende de un plugin (por ejemplo Tasks para `Tareas.md`), dilo claramente y ofrece la alternativa sin plugin. Detalle y orden de adopción en `references/plugins.md`. No instales ni configures plugins sin autorización.

## Formato de respuesta

- **Pieza pedida:** bloque listo para copiar + dónde guardarla + cómo usarla.
- **Base o dashboard:** qué pregunta responde, código, marca **[probar]** si procede.
- **Adaptación:** qué cambió respecto a la base y por qué.

## Cuándo pasar a otra skill

- «¿Cómo organizo mi proyecto?» → `atlas-proyecto`.
- «Revisa, audita, cierra o archiva» → `atlas-mantenimiento`.

## Referencias

- `references/estandar.md`: propiedades, estados, nombres e IDs (compartido).
- `references/plantillas.md`: las plantillas completas.
- `references/bases.md`: Bases, dashboards y consultas de tareas.
- `references/plugins.md`: plugins nativos y comunitarios.
