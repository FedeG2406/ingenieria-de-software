# Casos de prueba — qas-generator

## Caso 1: Sistema ATM (cajero automático) — Atributo: Availability

**Input dado a la skill:**
> Sistema: red de cajeros automáticos (ATM) de un banco, conectados
> a un servidor central que valida transacciones contra las cuentas
> de los clientes. Generar escenarios de disponibilidad.

**Output generado por la skill (corrida real):**

| Parte | Escenario 1 | Escenario 2 |
|---|---|---|
| Source | Falla de red entre el ATM y el servidor central | Falla de hardware del propio cajero (atascamiento del dispensador de billetes) |
| Stimulus | Se corta la conexión durante una transacción de retiro | El dispensador falla al intentar entregar el efectivo |
| Artifact | Módulo de comunicación del ATM | Módulo dispensador de efectivo |
| Environment | Operación normal | Operación normal |
| Response | El ATM cancela la operación y revierte cualquier débito parcial en la cuenta del cliente | El ATM detecta la falla, no debita la cuenta y muestra un mensaje de error |
| Response Measure | La reversión se completa en menos de 5 segundos, sin inconsistencia en el saldo del cliente | El sistema evita el débito en el 100% de los casos de falla detectada, y reporta el evento al centro de monitoreo en menos de 10 segundos |

**Comparación con el ejemplo esperado (según bibliografía/cátedra,
caso clásico de "reversión de transacción ante falla" usado en el
SAP):**

- Source: falla de red — **coincide**.
- Stimulus: corte de conexión durante transacción — **coincide**.
- Artifact: módulo de comunicación — **coincide**.
- Response: reversión del débito parcial — **coincide en el
  concepto central** (evitar inconsistencia de saldo).
- Response Measure: el valor de referencia usado en clase es "menos
  de 5 segundos" — **coincide exactamente** en el Escenario 1.

**Conclusión del test:** la skill reproduce con fidelidad la
estructura y el nivel de precisión del ejemplo canónico. La
diferencia principal es que agrega un segundo escenario (falla de
hardware del dispensador) no presente en el ejemplo original, lo
cual es válido y esperable ya que la consigna pide generar
"uno o más" escenarios, no reproducir literalmente el ejemplo.

---

## Caso 2: Sistema de e-commerce — Atributo: Performance

**Input dado a la skill:**
> Sistema: plataforma de e-commerce con catálogo de productos,
> carrito de compras y checkout. Generar escenarios de performance.

**Output generado por la skill (corrida real):**

| Parte | Escenario 1 |
|---|---|
| Source | Usuario final |
| Stimulus | Realiza una búsqueda de productos por palabra clave |
| Artifact | Servicio de búsqueda / motor de catálogo |
| Environment | Carga pico (evento de descuentos, ~1000 usuarios concurrentes) |
| Response | El sistema procesa la búsqueda y retorna resultados ordenados por relevancia |
| Response Measure | Tiempo de respuesta menor a 2 segundos en el 95% de las solicitudes |

**Comparación:** coincide exactamente en estructura y valores con
el Ejemplo 2 de `referencias/ejemplos_bass_sap.md`, usado como
caso de anclaje. Esto era esperable ya que ese ejemplo fue incluido
justamente como referencia de estilo.

**Conclusión general de los tests:** la skill genera escenarios
estructuralmente correctos (6 partes completas, response measure
cuantificable) y consistentes con los ejemplos bibliográficos
usados como anclaje.
