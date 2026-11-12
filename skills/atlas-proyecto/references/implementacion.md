# Implementación y puesta en marcha

## 21. Protocolo de inicio en un vault nuevo

1. Pregunta o detecta si tienes acceso real al vault.
2. Con acceso de solo lectura: inventario sin modificar nada. Con acceso de escritura: trabaja en modo de propuesta hasta recibir permiso.
3. Identifica carpetas principales, plantillas, propiedades y plugins existentes, y compáralos con ATLAS.
4. Resume la arquitectura actual y sus convenciones.
5. Detecta los problemas de mayor impacto, no una lista indiscriminada de mejoras.
6. Si el vault está vacío, propón la implementación por fases:
   - **Fase 0:** crear el vault, configurar adjuntos (`_adjuntos` bajo la carpeta actual, enlaces automáticos, ruta más corta) y activar los plugins nativos (Plantillas, Notas diarias, Marcadores, Bases, Recuperación de archivos, Backlinks, Búsqueda, Propiedades).
   - **Fase 1:** las ocho carpetas de raíz.
   - **Fase 2:** carpeta de plantillas y las plantillas empezando por Proyecto, Tarea, Reunión, Decisión y Entregable; configurar Notas diarias (`04_Diario/Diario`, formato `YYYY-MM-DD`).
   - **Fase 3:** `Esqueleto-Proyecto`.
   - **Fase 4:** `Proyecto - Panel.base`, `Proyectos.base`, `Fechas-limite.base` y `Home.md`; probarlos con datos reales.
   - **Fase 5:** primer proyecto real desde el esqueleto.
   - **Fase 6:** incorporar proyectos existentes de uno en uno.
   - **Fase 7:** rutinas semanales y mensuales; añadir módulos solo cuando el dolor sea real; anotar cambios en `Guia - Changelog`.
7. Espera aprobación antes de cambios estructurales o masivos.

