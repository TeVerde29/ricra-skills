# Plugins y funcionalidades nativas


**Criterio:** un plugin solo entra si resuelve un problema que lo nativo no resuelve, y el sistema debe seguir siendo utilizable si se desinstala. Explica siempre: qué problema resuelve, qué aporta frente a lo nativo, qué mantenimiento añade, qué datos o permisos necesita y cómo evitar dependencia innecesaria.

### Nativas indispensables

Plantillas (Templates), Propiedades, **Bases**, Notas diarias, Backlinks y enlaces salientes, Búsqueda (operadores `path:`, `tag:`, `file:`, `task-todo:` y bloques de consulta), Conmutador rápido y paleta de comandos, Marcadores, Vista de grafo (herramienta de diagnóstico de huérfanas), Recuperación de archivos, Etiquetas y Esquema. **Canvas** es útil pero no indispensable: como mucho uno por proyecto, nunca sustituye al hub.

### Plugins comunitarios

| Plugin | Categoría | Cuándo | Inconvenientes |
|---|---|---|---|
| **Tasks** | Recomendado | Hay tareas con fecha repartidas por el vault | Sintaxis propia con emojis; consultas grandes ralentizan |
| **Templater** | Recomendado (tras el mes 2) | Automatizar el alta de proyectos: IDs correlativos, mover archivos, aplicar plantilla al crear | Las plantillas dejan de ser texto puro |
| Dataview | Opcional | Cálculos que Bases no cubre | Lenguaje propio; solapa con Bases |
| Kanban | Opcional | Preferencia por flujo visual | Formato propio |
| Calendar / Periodic Notes | Opcional | Navegar notas diarias y periódicas | Duplica en parte a Notas diarias |
| QuickAdd | Opcional | Capturas con un atajo | Configuración inicial |
| Obsidian Git | Opcional (conservación) | Historial de versiones | Requiere conocer Git; conflictos con sincronización |
| Zotero Integration / Citations | Especializado (investigación, tesis) | Importar fichas desde Zotero | Depende de Zotero |
| Excalidraw | Especializado (diseño) | Diagramas dibujados | Archivos pesados |

**Verificado en documentación oficial:** Bases (archivos `.base` con YAML, vistas tabla, tarjetas, lista y mapa), Tasks, Templater y Notas diarias. **El resto no está verificado en profundidad:** antes de instalar o dar instrucciones detalladas, comprueba la página del plugin, su fecha de última actualización y su compatibilidad con la versión de Obsidian del usuario.

### Orden de adopción

| Fase | Plugins |
|---|---|
| 0 (día 1) | Ninguno comunitario |
| 1 (semanas 2 a 4) | Tasks |
| 2 (meses 2 a 3) | Templater o QuickAdd |
| 3 (según disciplina) | Zotero Integration, Excalidraw, Obsidian Git |

**No instales, conectes ni configures plugins o servicios externos sin autorización del usuario.**

