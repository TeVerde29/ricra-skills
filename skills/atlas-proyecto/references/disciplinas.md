# Disciplinas: cómo adapta ATLAS cada tipo de proyecto


En todos los casos se **conserva el núcleo**: hub, `01_Gestion`, `04_Entregables`, `_adjuntos`, propiedades globales y de proyecto, y los dashboards globales. Cambian los módulos dentro de `02_Conocimiento` y `03_Trabajo`, las plantillas extra y las propiedades de nivel 4.

| Disciplina | Carpetas añadidas | Plantillas específicas | Propiedades | Dashboards útiles |
|---|---|---|---|---|
| **Software** | `02_Conocimiento/Tecnica` activo desde el día 1; en `03_Trabajo`: `Arquitectura/`, `Runbooks/`, `Releases/` | Release, Runbook, Historia de usuario | `repo`, `version`, `entorno`, `stack`; `gravedad` en incidencias | Incidencias abiertas por gravedad; decisiones (ADR) por estado; releases por versión |
| **Investigación científica** | `Investigacion/Revision-bibliografica/`, `Protocolos/`; en `03_Trabajo`: `Experimentos/`, `Datos/`, `Analisis/` | Experimento, Protocolo, Dataset | `hipotesis`, `metodo`, `conjunto_datos`, `version_datos`, `repetible`, `doi` | Experimentos por estado; referencias `por-leer`; hipótesis abiertas |
| **Tesis / trabajo universitario** | `03_Trabajo/Capitulos/`, `Esquema.md`; `02_Conocimiento/Marco-teorico/`; `Revisiones-tutor/` en gestión | Capítulo, Revisión del tutor | `capitulo`, `palabras_objetivo`, `palabras_actuales`, `tutor` | Capítulos por estado; observaciones del tutor sin atender; cuenta atrás a la entrega |
| **Empresarial** | `Riesgos` activo; `Presupuesto.md`, `Interesados.md`; `Mercado/`, `Competencia/` | Presupuesto, Interesados, DAFO, Propuesta comercial | `cliente`, `presupuesto`, `coste_real`, `margen`, `sponsor` | Presupuesto frente a coste real; riesgos ≥ 6; entregables en revisión |
| **Creación de contenido** | `03_Trabajo/Guiones/`, `Borradores/`, `Calendario-editorial.md`; una nota por pieza en `04_Entregables` | Pieza, Guion, Analítica | `canal`, `formato`, `fecha_publicacion`, `etapa` | Calendario editorial; piezas por etapa; ideas sin evaluar |
| **Aprendizaje personal** | `02_Conocimiento` como eje, `Practica/`; las notas útiles se **promueven** a `03_Conocimiento/Conceptos` | Sesión de estudio, Concepto, Revisión de progreso | `habilidad`, `nivel`, `horas_dedicadas`, `recurso` | Horas por semana; conceptos por nivel; recursos por estado |

Para un trabajo de asignatura o un proyecto personal pequeño, usa un proyecto **Mini**. No importes estructuras de una disciplina a otra sin que el usuario lo necesite.

