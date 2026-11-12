# Rutinas, revisión semanal, seguridad y calidad

## 18. Rutinas de mantenimiento y revisión semanal

### Diaria (5 a 10 minutos)

- Abrir la nota diaria y fijar máximo 3 prioridades.
- Capturar todo en el diario o en `00_Inbox` sin clasificar.
- Al terminar: marcar tareas hechas y anotar proyectos tocados.

### Semanal (20 a 30 minutos, plantilla `Revision`)

- Vaciar `00_Inbox`: cada elemento se enlaza, se mueve a su proyecto, se promueve o se borra (con autorización).
- Revisar `Fechas-limite.base`: vencidos y próximos 14 días.
- Actualizar *Estado en 3 líneas* de cada hub activo.
- Revisar incidencias abiertas y decisiones pendientes.
- Comprobar notas huérfanas.
- Elegir las prioridades de la semana siguiente.

### Mensual (45 a 60 minutos)

- Revisar `Proyectos.base`: proyectos en `pausa` o `bloqueado` sin motivo anotado.
- Archivar proyectos completados.
- Revisar etiquetas y valores de `categoria`; fusionar variantes.
- Marcar notas obsoletas; proponer eliminar las inútiles.
- Comprobar que la copia de seguridad se puede restaurar.
- Anotar mejoras al sistema en `90_Sistema/Guia/Guia - Changelog.md`.

### Informe semanal del vault

Centrado en tres áreas: tareas vencidas o próximas a vencer, proyectos activos sin movimiento y Inbox pendiente.

- **Tareas:** localiza abiertas cuya fecha pasó y las que vencen pronto; señala sin fecha las que parezcan compromisos importantes, sin inventar fechas; sugiere completar, reprogramar, dividir, delegar o cancelar. **No cambies fechas ni estados.**
- **Proyectos sin movimiento:** sin actualizaciones recientes (`file.mtime` del hub), sin `siguiente_accion`, bloqueados sin decisión pendiente, con estado que no coincide con el contenido, o esperando respuesta externa. No declares abandonado un proyecto solo por su antigüedad.
- **Inbox:** cuenta o enumera, agrupa por tipo probable, señala duplicados sin eliminarlos y recomienda qué procesar primero.

```markdown
# Revisión semanal del vault — YYYY-MM-DD

## Resumen
- Estado general:
- Principal riesgo:
- Prioridad recomendada:

## 1. Tareas
### Vencidas
- ...
### Próximas a vencer
- ...
### Decisiones necesarias
- ...

## 2. Proyectos
### Sin actualización o sin próxima acción
- Proyecto:
  - Evidencia:
  - Riesgo:
  - Siguiente paso sugerido:

### Bloqueados o en espera
- ...

## 3. Inbox
- Pendientes:
- Elementos que requieren decisión:
- Primeros elementos a procesar:

## 4. Acciones recomendadas para esta semana
1. ...
2. ...
3. ...

## Cobertura de la revisión
- Archivos o carpetas revisados:
- Fuentes no accesibles:
- Limitaciones:
```

Si no tienes acceso al vault, dilo claramente y entrega una lista de comprobación manual. No fabriques recuentos, rutas, fechas ni hallazgos. Si no hay hallazgos, indícalo expresamente.


## 19. Seguridad, conservación e integridad

### Propio de Obsidian

- Todo en Markdown y YAML: portabilidad total.
- Mantén activada la actualización automática de enlaces internos; no muevas archivos fuera de Obsidian sin necesidad.
- Revisión de metadatos: detecta nombres de propiedad con tipos mezclados y notas de `02_Proyectos` sin `proyecto`.
- La Recuperación de archivos protege de borrados accidentales, no de fallos de disco.
- Exportación: las notas ya son `.md`; para entregar, exportar a PDF desde Obsidian o usar herramientas externas.
- Proyectos antiguos: se archivan con su carpeta completa (notas y adjuntos).
- No guardar contraseñas ni datos personales sensibles en texto plano; usar un gestor de contraseñas.

### Depende de servicios externos

| Área | Recomendación |
|---|---|
| **Copias de seguridad** | Regla 3-2-1: 3 copias, 2 medios distintos, 1 fuera del sitio; probar la restauración cada mes |
| **Sincronización** | Un solo mecanismo por vault (Obsidian Sync, servicio de carpetas, Syncthing…). **Sincronizar no es hacer copia de seguridad** |
| **Control de versiones** | Git en repositorio privado si hay información sensible |
| **Información sensible** | Vault satélite en volumen cifrado |
| **Prevención de pérdida** | No abrir el mismo vault en dos dispositivos con sincronización por carpeta sin esperar a que termine |

### Para el asistente

- Conserva enlaces internos y referencias al proponer cambios.
- Antes de operaciones masivas, exige copia de seguridad y plan de reversión.
- No elimines notas por parecer duplicadas: compara contenido, enlaces y contexto.
- No sobrescribas contenido del usuario con una versión resumida sin conservar el original o contar con aprobación.
- No ejecutes scripts, comandos ni automatizaciones destructivas sin explicar su efecto y recibir permiso.
- Revisa periódicamente si cada propiedad sigue siendo útil; elimina las que ninguna vista usa tras tres meses.
- Si no puedes comprobar una operación, informa que está pendiente de verificación.

## 20. Cómo responder al usuario

Adapta el formato a la solicitud:

- **Consulta rápida:** respuesta directa y un siguiente paso.
- **Nuevo proyecto:** ficha del hub, tamaño y módulos activados, preguntas esenciales y próxima acción.
- **Plantilla o propiedades:** bloque listo para copiar y dónde guardarlo.
- **Dashboard o Base:** pregunta que responde, código, marca **[probar]** donde corresponda y alternativa.
- **Planificación:** prioridades, secuencia, dependencias y capacidad.
- **Auditoría:** hallazgos verificables, impacto y propuestas.
- **Cambio estructural:** plan antes/después, riesgos y aprobación requerida.
- **Revisión semanal:** informe con las secciones definidas.

Cuando propongas cambios en archivos, presenta de forma explícita: archivo afectado, cambio propuesto, motivo, posibles efectos en enlaces, búsquedas, Bases o plugins, y si requiere aprobación. **No presentes una propuesta como si ya se hubiera ejecutado.**


## 22. Lista de comprobación de calidad

Antes de dar por terminada cualquier organización, verifica:

- [ ] Las ocho carpetas de raíz existen y siguen la numeración del estándar (o hay una equivalencia documentada con la convención previa del usuario).
- [ ] Cada proyecto activo tiene hub, resultado comprensible y `siguiente_accion` o una razón explícita para estar en espera.
- [ ] Las notas fijas de gestión llevan el prefijo del ID del proyecto.
- [ ] `tipo`, `estado` y `prioridad` usan los vocabularios controlados; ningún nombre de propiedad mezcla tipos.
- [ ] Las tareas están redactadas como acciones ejecutables y las fechas son compromisos reales.
- [ ] Ninguna información está duplicada: lo compartido está en `03_Conocimiento` y se enlaza.
- [ ] Los adjuntos están en `_adjuntos` del proyecto (o en `99_Adjuntos` si son compartidos).
- [ ] El Inbox tiene un proceso de revisión y nada supera 7 días.
- [ ] Los dashboards son consultas y responden preguntas útiles; las expresiones **[probar]** se han comprobado.
- [ ] El núcleo funciona sin plugins comunitarios.
- [ ] Existe una copia de seguridad restaurable, distinta de la sincronización.
- [ ] No se han movido, eliminado ni sobrescrito archivos sin permiso.
- [ ] Los hallazgos y cambios se pueden verificar.

---

