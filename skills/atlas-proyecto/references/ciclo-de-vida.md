# Ciclo de vida y flujos de trabajo

## 16. Ciclo de vida del proyecto

| # | Etapa | Qué se hace | Notas y plantillas | Carpeta |
|---|---|---|---|---|
| 1 | **Captura** | Anotar la idea o necesidad sin analizarla | `Idea` | `00_Inbox` |
| 2 | **Evaluación inicial** | Valor, esfuerzo, encaje; seguir, esperar o descartar | Sección *Primera evaluación* | `00_Inbox` |
| 3 | **Creación** | Duplicar el esqueleto, crear el hub, asignar ID | `Proyecto`, esqueleto | `02_Proyectos` |
| 4 | **Objetivos y alcance** | Rellenar secciones 1 a 3 del hub; `estado: planificacion` | Hub | Raíz del proyecto |
| 5 | **Planificación** | Fases, hitos, requisitos, riesgos | `Planificacion`, `Riesgos` | `01_Gestion` |
| 6 | **Preparación de recursos** | Fuentes, herramientas, accesos | `Referencia`, `Investigacion` | `02_Conocimiento`, `03_Conocimiento/Referencias` |
| 7 | **Ejecución** | Producir; `estado: activo` | Tareas, notas de trabajo, técnicas | `03_Trabajo`, `02_Conocimiento` |
| 8 | **Seguimiento y control** | Revisión semanal; informe de estado | `Seguimiento` | `01_Gestion/Seguimiento` |
| 9 | **Cambios y problemas** | Registrar incidencias y decisiones | `Incidencia`, `Decision` | `01_Gestion` |
| 10 | **Entregables** | Producir, revisar y aceptar | `Entregable` | `04_Entregables` |
| 11 | **Evaluación** | Previsto frente a logrado; criterios de calidad | Entregables aceptados | `04_Entregables` |
| 12 | **Cierre** | Informe final, lecciones, conocimiento a promover | `Cierre` | `05_Cierre` |
| 13 | **Archivo** | `estado: archivado`, mover carpeta, extraer conocimiento | Lista de cierre | `05_Archivo` |

**Puertas de decisión:**

| Puerta | Condición |
|---|---|
| Idea → Proyecto (2 a 3) | Valor claro y capacidad real de dedicarle tiempo |
| Planificación → Ejecución (5 a 7) | Objetivos, alcance y primeras tareas definidos |
| Ejecución → Cierre (10 a 12) | Entregables aceptados o descartados explícitamente |
| Cierre → Archivo (12 a 13) | Lista de cierre completa y conocimiento extraído |

## 17. Flujos de trabajo operativos

### A. Capturar una idea

1. Añade el contenido a `00_Inbox` o indica cómo capturarlo.
2. Conserva el texto original si puede contener matices.
3. Resume en una frase e identifica el tipo de elemento.
4. Propón el siguiente paso o la pregunta que falta.

### B. Crear un proyecto

1. Comprueba que el resultado no esté ya representado.
2. Determina el tamaño (Mini, Estándar o Mayor) y la disciplina.
3. Define resultado esperado, alcance y criterios de finalización.
4. Asigna estado, prioridad y `categoria` con datos reales.
5. Propón el ID (`PRJ-AAAA-NNN`, siguiente correlativo del año tras comprobar los existentes).
6. Divide el trabajo en fases e hitos cuando aporte claridad.
7. Define una `siguiente_accion`.
8. Indica carpetas y notas que se crearán; **pide autorización antes de escribir o modificar archivos**.

### C. Planificar la semana

1. Revisa fechas límite y compromisos reales.
2. Identifica tareas vencidas y próximas.
3. Revisa bloqueos, incidencias abiertas y dependencias.
4. Considera la capacidad disponible que indique el usuario.
5. Selecciona pocos resultados importantes.
6. Propón una secuencia realista con margen para imprevistos.

### D. Cerrar un proyecto

1. Comprueba los criterios de finalización y que los entregables estén aceptados.
2. Identifica tareas pendientes: cancelar, transferir o conservar.
3. Redacta el informe de cierre con lecciones aprendidas.
4. Identifica notas que deben **promoverse** a `03_Conocimiento`.
5. Recomienda `estado: completado` solo si el resultado está realmente terminado.
6. Propón mover la carpeta a `05_Archivo/Proyectos/AAAA/`.
7. No archives ni cambies estados sin autorización.

### E. Incorporar un proyecto existente

1. Elige **un solo** proyecto activo; no migres todo de golpe.
2. Crea su carpeta desde el esqueleto y su hub.
3. Mueve los archivos existentes a `03_Trabajo/` o `02_Conocimiento/` tal cual, sin reescribirlos.
4. Añade solo `tipo`, `proyecto` y `estado` a las notas que se sigan usando.
5. Los documentos que no se vuelvan a tocar quedan como están y se archivan con el proyecto.
6. Proyectos ya finalizados: solo si interesa conservar su memoria, crea un hub mínimo directamente en `05_Archivo` con `estado: archivado`.

### F. Auditar o reorganizar un vault

1. Audita primero; no empieces moviendo archivos.
2. Identifica duplicados, convenciones contradictorias, propiedades inconsistentes (mismo nombre con tipos distintos) y notas huérfanas.
3. Presenta hallazgos con ejemplos y rutas.
4. Propón cambios por lotes pequeños.
5. Explica riesgos, enlaces afectados y plan de reversión.
6. Espera aprobación antes de ejecutar.

