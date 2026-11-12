---
name: atlas-mantenimiento
description: Mantiene el orden y la salud de un vault ATLAS en Obsidian con revisiones diarias, semanales y mensuales, procesamiento del Inbox, gestión de tareas, auditorías, cierre y archivo de proyectos, seguridad y copias de seguridad. Auto-activate on /atlas-mantenimiento o cuando el usuario pida revisar su semana, procesar el inbox, priorizar tareas, ver qué está vencido o estancado, auditar o limpiar el vault, cerrar o archivar un proyecto en Obsidian.
---

# Skill: atlas-mantenimiento

## Qué hace

Mantiene ATLAS funcionando **después** de montarlo. Hace revisiones, procesa el Inbox, ordena tareas y prioridades, detecta bloqueos y proyectos estancados, audita el vault, guía el cierre y archivo de proyectos y recuerda lo esencial de seguridad y copias.

Esta skill **revisa y propone**. El diseño de la arquitectura es de `atlas-proyecto` y las piezas (plantillas, Bases) son de `atlas-plantillas`.

## Reglas

1. **No modifiques, muevas, renombres ni elimines archivos** sin autorización explícita. Propón cambios y espera aprobación.
2. **No cambies fechas ni estados por tu cuenta.** Si una tarea está vencida, no la marques como hecha ni la reprogrames: pide decisión o recomienda una nueva fecha.
3. **No inventes datos.** No fabriques recuentos, rutas, fechas ni hallazgos. Si no hay hallazgos, dilo.
4. **No afirmes haber revisado el vault** si no tienes acceso real. Sin acceso, entrega una **lista de comprobación manual** y di qué no pudiste ver.
5. No declares abandonado un proyecto solo por su antigüedad: cita la evidencia (última modificación, falta de `siguiente_accion`, estado incoherente).
6. No elimines notas por parecer duplicadas: compara contenido, enlaces y contexto.
7. Antes de cualquier operación masiva, exige **copia de seguridad y plan de reversión**.
8. No ejecutes scripts ni automatizaciones sin explicar su efecto y recibir permiso.
9. Una sola pregunta como máximo, y solo si es esencial.
10. Mantén las respuestas proporcionadas: cortas para consultas rápidas, estructuradas para revisiones y auditorías.

## Qué pide el usuario y qué hago

| Petición | Procedimiento | Detalle |
|---|---|---|
| «Revisión diaria» / «qué hago hoy» | Máximo 3 prioridades según fechas reales, bloqueos y capacidad | `references/revisiones.md` |
| «Revisión semanal» | Informe con tareas, proyectos sin movimiento e Inbox | `references/revisiones.md` |
| «Revisión mensual» | Proyectos en pausa, archivo, etiquetas, copias | `references/revisiones.md` |
| «Procesa mi inbox» | Clasificar cada elemento sin mover nada | `references/tareas-e-inbox.md` |
| «Prioriza / planifica mi semana» | Ordenar por fecha real, desbloqueo, objetivo e impacto | `references/tareas-e-inbox.md` |
| «Mis tareas están hechas un lío» | Revisar calidad de las tareas y proponer los niveles N1, N2 o N3 | `references/tareas-e-inbox.md` |
| «Audita / ordena el vault» | Auditoría primero, lotes pequeños después | `references/cierre-y-auditoria.md` |
| «Cierra / archiva el proyecto X» | Criterios, informe de cierre, promoción de conocimiento | `references/cierre-y-auditoria.md` |
| «Copias de seguridad / seguridad» | Recomendaciones propias de Obsidian y externas | `references/revisiones.md` |

## Cómo hacer una revisión (resumen)

1. **Confirma qué puedes ver:** vault completo, una carpeta, pegados del usuario o nada. Anótalo en «Cobertura de la revisión».
2. **Tareas:** vencidas, próximas a vencer, compromisos importantes sin fecha.
3. **Proyectos:** sin actualización reciente, sin `siguiente_accion`, bloqueados sin decisión, con estado que no coincide con el contenido.
4. **Inbox:** pendientes, duplicados posibles, elementos que requieren decisión.
5. **Acciones:** 3 a 5 recomendaciones concretas y ordenadas.
6. **Cobertura:** qué revisaste, qué no pudiste ver y limitaciones.

Usa el formato de informe semanal de `references/revisiones.md`.

## Qué mirar en una auditoría

- Nombres de propiedad con tipos mezclados o con variantes (`prioridad` frente a `priority`).
- Notas en `02_Proyectos` sin `proyecto`, o con `estado` fuera del vocabulario.
- Notas fijas de gestión sin el prefijo del ID del proyecto.
- Notas huérfanas (sin enlaces entrantes ni salientes).
- Duplicados reales (misma referencia, mismo concepto en dos sitios).
- Adjuntos fuera de `_adjuntos` o de `99_Adjuntos`.
- Proyectos completados que siguen en `02_Proyectos`.
- Etiquetas que repiten propiedades, o más de ~40 etiquetas distintas.
- Propiedades que ninguna vista usa.

Presenta los hallazgos con ejemplos y rutas, ordénalos por impacto y propón **lotes pequeños**. Explica riesgos, enlaces afectados y cómo revertir.

## Qué no hacer

- No mover ni borrar «para ayudar».
- No normalizar todo el vault de golpe.
- No rellenar propiedades con valores supuestos.
- No dar una lista interminable de mejoras: prioriza las de mayor impacto.
- No presentar una propuesta como si ya se hubiera ejecutado.

## Formato al proponer cambios

Para cada cambio indica: archivo afectado, cambio propuesto, motivo, efecto posible en enlaces, Bases o plugins, y si requiere aprobación.

## Cuándo pasar a otra skill

- «Voy a empezar un proyecto nuevo» → `atlas-proyecto`.
- «Dame la plantilla o el panel…» → `atlas-plantillas`.

## Referencias

- `references/estandar.md`: propiedades, estados, nombres y arquitectura (compartido).
- `references/revisiones.md`: rutinas diaria, semanal y mensual; informe semanal; seguridad; lista de calidad.
- `references/tareas-e-inbox.md`: niveles de tarea, calidad, priorización y Inbox.
- `references/cierre-y-auditoria.md`: cierre de proyecto, incorporación y reorganización.
