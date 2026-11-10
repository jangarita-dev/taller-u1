# Mapa de uso de IA en el SDLC · Pedidos Web

> Contexto: equipo que heredó Pedidos Legado (Delphi + DBISAM) y lo evoluciona hacia Pedidos Web (.NET + PostgreSQL).
> Regla general: Claude propone, una persona decide. Nada entra al repo sin que alguien haya leído el diff.

**Autor:** jangarita-dev
**Fecha:** 2026-11-09

| Etapa | Se delega a Claude | Artefacto versionado | Revisa (persona) | Riesgo | Evento Scrum |
|-------|--------------------|----------------------|------------------|--------|--------------|
| Requisitos | Convertir una regla de negocio escrita en lenguaje natural (por ejemplo, las reglas del folio del README) en criterios de aceptación Dado/Cuando/Entonces y listar las preguntas abiertas para el negocio | `docs/specs/<feature>/spec.md` | El Product Owner valida los criterios; el dev confirma las reglas de negocio contra el código legado | Claude no ve el código Delphi: las restricciones del legado que no están escritas (por ejemplo, el campo ASCII de 4 caracteres de la sucursal) quedan fuera o se inventan (regla 8 de `AGENTS.md`) | Refinamiento del backlog / Sprint Planning |
| Diseño | Proponer un plan técnico para una funcionalidad que debe coincidir con el legado (por ejemplo, generar folios en el portal idénticos a los de Pedidos Legado), con alternativas y trade-offs, y un diagrama Mermaid de ese flujo | `docs/specs/<feature>/plan.md` | El líder técnico aprueba el plan en plan mode antes de escribir código | Un diseño que rompe la compatibilidad con los datos del legado: si el portal genera folios distintos, los clientes no encuentran sus pedidos antiguos | Sprint Planning |
| Código | Implementar una tarea de `docs/specs/<feature>/tasks.md` a la vez, en incrementos pequeños, dejando el cambio listo para que una persona haga el commit (regla 3 de `AGENTS.md`) | Código en rama de feature (el commit lo hace una persona) | El dev lee cada diff antes de aceptar la edición | Código que compila pero rompe una regla de negocio, o cambios fuera del alcance pedido (`src/`, `tests/` y `docs/`, regla 6 de `AGENTS.md`) | Durante el sprint (impedimentos en la Daily) |
| Pruebas | Proponer casos borde y generar un test xUnit por criterio de aceptación | `tests/` | El dev comprueba que cada test falla si el código está mal | Tests que siempre pasan o que confirman el bug, sobre todo si Claude escribe el código y sus tests en el mismo turno; los 3 tests base del folio pasaban aunque faltaran las reglas R1 a R5 | Durante el sprint, como parte de la Definition of Done |
| Revisión y despliegue | Primer pase de revisión del PR y borrador de la descripción a partir del diff; los hallazgos quedan en `REVIEW.md` (hallazgo, archivo y línea, respuesta de la persona) | Pull request + `REVIEW.md` | Un par humano responde cada hallazgo y aprueba el merge; un responsable autoriza el despliegue | Aprobar por confianza en la IA, o que el mismo modelo que escribió el código sea el que lo revisa; secretos o permisos excesivos cuando se agregue el pipeline de CI (unidades siguientes) | Antes de la Sprint Review |
| Mejora continua | Resumir los hallazgos repetidos en revisiones y proponer cambios a las reglas del proyecto en un documento de `docs/` (Claude no edita `AGENTS.md`, regla 6) | Propuesta en `docs/`; `AGENTS.md` lo edita una persona | El equipo decide en la retro qué reglas se agregan o se quitan | `AGENTS.md` crece sin control o acumula reglas contradictorias (por ejemplo, un mapa que pide a Claude hacer commits cuando la regla 3 lo prohíbe) | Sprint Retrospective |

## Evidencia del paso 3

| Ronda | Sin IA | Con Claude Code |
|-------|--------|-----------------|
| Tiempo (min) | _completar_ | _completar_ |
| Errores encontrados | _completar_ | Ninguno al ejecutar: 15 de 15 tests en verde al primer intento (de 3 tests base se pasó a 15, cubriendo R1 a R5) |
| Qué tuve que corregir | _completar_ | _completar_ (ojo: Claude escribió la implementación y los tests en el mismo turno; revisar que los tests no solo confirmen el código) |

**Conclusión:** _completar en 1–2 líneas qué te mostró la comparación, por ejemplo qué casos borde detectó cada ronda._
