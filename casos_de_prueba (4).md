# Casos de prueba — qas-completeness-checker

## Caso 1: escenario incompleto de disponibilidad (ATM)

**Input dado a la skill (escenario incompleto, redactado en prosa
por un stakeholder en una sesión de brainstorming típica de QAW):**

> "Si se cae la conexión del cajero con el banco, el sistema tiene
> que reaccionar rápido para que no se pierda plata."

**Output generado por la skill (corrida real):**

| Parte | Estado | Contenido actual | Propuesta de completado |
|---|---|---|---|
| Source | Ambigua | "se cae la conexión" (no se especifica el origen de la falla) | Falla de red entre el ATM y el servidor central del banco |
| Stimulus | OK | Corte de conexión durante la operación | (se mantiene, es un evento discreto) |
| Artifact | Falta | No se menciona | Módulo de comunicación del ATM |
| Environment | Falta | No se menciona | Operación normal (durante una transacción de retiro en curso) |
| Response | Ambigua | "reaccionar rápido para que no se pierda plata" (vago, no define la acción) | El ATM cancela la operación en curso y revierte cualquier débito parcial ya aplicado a la cuenta del cliente |
| Response Measure | Falta (mezclado con Response de forma ambigua) | "rápido", sin número | La reversión se completa en menos de 5 segundos, sin inconsistencia en el saldo del cliente |

**Escenario completo reescrito (generado por la skill):**
- Source: falla de red entre el ATM y el servidor central del banco
- Stimulus: se corta la conexión durante una transacción de retiro
- Artifact: módulo de comunicación del ATM
- Environment: operación normal
- Response: el ATM cancela la operación y revierte cualquier débito
  parcial ya aplicado
- Response Measure: la reversión se completa en menos de 5 segundos,
  sin inconsistencia en el saldo del cliente

**Comparación con el resultado esperado (mismo caso usado como
referencia en la skill i, sección Availability):** el escenario
reescrito coincide con el ejemplo canónico de "reversión ante falla
de red" usado en la bibliografía/cátedra, tanto en estructura como
en el valor del response measure (5 segundos).

**Conclusión:** la skill detectó correctamente 2 partes totalmente
ausentes (Artifact, Environment) y 2 ambiguas (Source, Response
mezclada con Response Measure vago), y las propuestas de completado
son coherentes con el dominio del escenario, no genéricas.

---

## Caso 2: escenario ya completo (control negativo)

**Input dado a la skill:**
> Source: usuario final. Stimulus: envía una solicitud de búsqueda
> de productos. Artifact: servicio de búsqueda. Environment: carga
> pico de 1000 usuarios concurrentes. Response: el sistema retorna
> resultados. Response Measure: en menos de 2 segundos para el 95%
> de las solicitudes.

**Output generado por la skill:** todas las 6 partes marcadas como
**OK**, sin propuestas de completado, ya que el response measure es
cuantificable y todas las partes son específicas.

**Conclusión:** la skill no "sobre-corrige" un escenario ya bien
formado — importante para verificar que no genera ruido innecesario
cuando no hace falta.
