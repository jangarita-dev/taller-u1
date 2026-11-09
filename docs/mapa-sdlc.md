# Mapa de uso de IA en el SDLC · Pedidos Web

> Contexto: equipo que heredó Pedidos Legado (Delphi + DBISAM) y lo evoluciona hacia Pedidos Web (.NET + PostgreSQL).
> Regla general: Claude propone, una persona decide. Nada entra al repo sin que alguien haya leído el diff.

| Etapa | Delega a Claude | Artefacto | Revisa (persona) | Riesgo | Evento Scrum |
|-------|-----------------|-----------|------------------|--------|--------------|
| Requisitos | Convertir una historia de usuario vaga en criterios de aceptación verificables y listar preguntas abiertas para el negocio | `docs/specs/<feature>/spec.md` | El Product Owner valida los criterios; el dev confirma las reglas de negocio contra el código legado | Criterios inventados que suenan bien pero no reflejan cómo opera la distribuidora | Refinamiento del backlog / Sprint Planning |
| Diseño | Proponer un plan técnico con alternativas y trade-offs, y un diagrama Mermaid del flujo legado → web | `docs/specs/<feature>/plan.md` | El líder técnico aprueba el plan en plan mode antes de escribir código | Sobreingeniería o una arquitectura que no convive con el legado durante la migración | Sprint Planning |
| Código | Implementar una tarea de `tasks.md` a la vez, en incrementos pequeños (una tarea, un commit) | Código en rama de feature + commits | El dev lee cada diff antes de aceptar la edición | Código que compila pero rompe una regla de negocio, o cambios fuera del alcance pedido | Durante el sprint (impedimentos en la Daily) |
| Pruebas | Proponer casos borde y generar un test xUnit por criterio de aceptación | `tests/` | El dev comprueba que cada test falla si el código está mal | Tests que siempre pasan o que confirman el bug; cobertura alta sin calidad | Durante el sprint, como parte de la Definition of Done |
| Revisión y despliegue | Primer pase de revisión del PR y borrador de la descripción a partir del diff | Pull request + `REVIEW.md` | Un par humano responde cada hallazgo y aprueba el merge; un responsable autoriza el despliegue | Aprobar por confianza en la IA; secretos o permisos excesivos en el pipeline | Antes de la Sprint Review |
| Mejora continua | Resumir los hallazgos repetidos en revisiones y proponer cambios a las reglas del proyecto | `AGENTS.md` actualizado | El equipo decide en la retro qué reglas se agregan o se quitan | `AGENTS.md` crece sin control o acumula reglas contradictorias | Sprint Retrospective |

## Evidencia del paso 3

| Ronda | Sin IA | Con Claude Code |
|-------|--------|-----------------|
| Tiempo (min) | _completar_ | _completar_ |
| Errores encontrados | _completar_ | _completar_ |
| Qué tuve que corregir | _completar_ | _completar_ |

**Conclusión:** _completar en 1–2 líneas qué te mostró la comparación, por ejemplo qué casos borde detectó cada ronda._