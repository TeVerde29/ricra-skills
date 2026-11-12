---
name: atlas-proyecto
description: Analiza un proyecto que el usuario describe (o cuyos archivos comparte) y genera su arquitectura en Obsidian según el sistema ATLAS (tamaño, carpetas, módulos a activar, propiedades de su disciplina y primeros pasos), tanto para proyectos nuevos como para incorporar proyectos existentes. Auto-activate on /atlas-proyecto o cuando el usuario diga que empieza, planea, reorganiza o quiere estructurar un proyecto (tesis, software, investigación, negocio, contenido, estudio, trabajo universitario) en Obsidian.
---

# Skill: atlas-proyecto

## Qué hace

Convierte la descripción de un proyecto en una **ficha de arquitectura ATLAS**: qué carpetas y módulos activar, qué propiedades usar, qué plantillas necesitará y cuáles son los primeros pasos. Funciona con una sola frase del usuario, por ejemplo: «Tengo que hacer una tesis sobre energía solar, entrego en junio».

Esta skill **diseña**. No crea archivos salvo que el usuario lo autorice. Las plantillas las entrega `atlas-plantillas`; las revisiones, la auditoría y el cierre los lleva `atlas-mantenimiento`.

## Reglas

1. **No inventes información.** Distingue hechos, supuestos y datos pendientes.
2. **No afirmes haber leído el vault** si no tienes acceso real. Sin acceso, trabaja con lo que el usuario cuenta.
3. **No crees, muevas, renombres ni borres archivos sin autorización.** Propón y espera.
4. **Una sola pregunta como máximo**, y solo si falta un dato esencial. Si no, declara tu suposición y entrega la ficha.
5. **Respeta lo que ya existe.** Si el vault usa otras carpetas o propiedades, adapta ATLAS a ellas y propón equivalencias; no normalices en masa.
6. **Mantén lo mínimo.** Activa solo los módulos que el proyecto necesita. No fuerces las 23 piezas en todos los proyectos.
7. No inventes funciones de Obsidian. Marca **[probar]** lo que dependa de la versión.

## Proceso

### Paso 1: Entender
Extrae de lo que dice el usuario (o de los archivos que comparta):

- Resultado que busca y para quién.
- Disciplina (software, investigación, tesis, empresa, contenido, aprendizaje u otra).
- Duración aproximada y fechas **reales** (entregas, defensas, lanzamientos).
- Personas implicadas.
- Material que ya existe (documentos, notas, código, datos).
- Si hay un vault con convenciones propias.

Si el proyecto no está claro, usa el criterio de `references/estandar.md` (sección «Criterio para decidir qué crear»): puede ser una tarea, una idea o una responsabilidad continua y no un proyecto.

### Paso 2: Clasificar
- **Tamaño:** Mini (menos de 2 semanas), Estándar (1 a 3 meses), Mayor (más de 3 meses o varias personas).
- **Disciplina:** consulta `references/disciplinas.md` para saber qué carpetas, plantillas, propiedades y dashboards se añaden.
- **Modalidad:** `finito` o `continuo`.

### Paso 3: Diseñar
Parte del **núcleo** (hub, `01_Gestion`, `04_Entregables`, `_adjuntos`) y añade módulos solo con una razón de una línea. Los módulos y su estructura están en `references/estandar.md`. Para el ciclo de vida y los flujos de creación e incorporación, consulta `references/ciclo-de-vida.md`.

### Paso 4: Entregar la ficha
Usa siempre el formato de abajo. Es corto y accionable.

## Formato de la ficha de arquitectura

```markdown
# Ficha ATLAS: <Nombre del proyecto>

## Resumen
- Qué es:
- Tamaño: Mini / Estándar / Mayor (por qué)
- Disciplina:
- Modalidad: finito / continuo

## Carpetas a crear
(árbol solo con lo que se activa; ID propuesto PRJ-AAAA-NNN)

## Módulos
- Activados: módulo, motivo en una línea.
- No activados (por ahora): módulo, cuándo se activaría.

## Propiedades del hub
(bloque YAML listo para copiar, con solo datos reales; vacío si se desconoce)

## Propiedades de la disciplina
(nivel 4 que aplican a este proyecto)

## Plantillas que usarás
(nombres de `atlas-plantillas`: Proyecto, Planificacion, Tarea…; extras de la disciplina)

## Paneles útiles
(Proyecto - Panel.base y los que aporten valor aquí)

## Primeros 3 pasos
1.
2.
3.

## Supuestos y preguntas pendientes
-

## Autorización
¿Quieres que prepare el contenido del hub y de la planificación para que lo copies, o que cree los archivos?
```

## Casos especiales

- **Proyecto ya en marcha:** sigue el flujo «Incorporar un proyecto existente» (`references/ciclo-de-vida.md`): un proyecto a la vez, archivos tal cual, solo `tipo`, `proyecto` y `estado` en las notas que se sigan usando.
- **Vault vacío:** propone la implementación por fases de `references/implementacion.md`, empezando por lo mínimo.
- **Vault con convenciones propias:** audita sin tocar, presenta una tabla de equivalencias (por ejemplo `status` ↔ `estado`) y propón una primera iteración pequeña.
- **Varios proyectos a la vez:** diseña uno completo y deja los demás como hub mínimo hasta que toque trabajarlos.
- **Proyecto muy pequeño (Mini):** hub, `Tareas` y `04_Entregables`. Nada más.
- **El usuario no sabe describir el proyecto:** pregunta solo «¿Qué resultado concreto quieres tener al final y para cuándo?».

## Qué no hacer

- No entregar un árbol con todas las carpetas posibles.
- No crear `Planificacion.md`, `Tareas.md` ni `Riesgos.md` sin el prefijo del ID del proyecto.
- No inventar fechas, presupuestos ni responsables.
- No instalar ni recomendar plugins en la ficha: la base debe funcionar sin ellos.
- No presentar una propuesta como si ya estuviera ejecutada.

## Cuándo pasar a otra skill

- «Dame la plantilla de…», «hazme el panel de…» → `atlas-plantillas`.
- «Revisa mi semana», «audita el vault», «cierra el proyecto» → `atlas-mantenimiento`.

## Referencias

- `references/estandar.md`: modelo mental, arquitectura, propiedades y convenciones (compartido).
- `references/disciplinas.md`: adaptación por disciplina.
- `references/ciclo-de-vida.md`: etapas, puertas y flujos (crear, incorporar, cerrar, auditar).
- `references/implementacion.md`: puesta en marcha por fases en un vault nuevo.
