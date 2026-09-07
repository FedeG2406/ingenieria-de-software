# Ejemplos de referencia (Bass, Clements & Kazman - Software
# Architecture in Practice)

Estos ejemplos se usan como "anclaje de estilo": la skill debe
producir escenarios con este mismo nivel de precisión y este mismo
formato.

## Ejemplo 1 — Availability

- Source: falla de hardware
- Stimulus: un servidor de base de datos deja de responder
- Artifact: servidor de base de datos de reservas
- Environment: operación normal
- Response: el sistema detecta la falla y conmuta (failover) a un
  servidor de respaldo, sin perder transacciones ya confirmadas
- Response Measure: el sistema queda disponible nuevamente en menos
  de 3 segundos, con cero pérdida de transacciones confirmadas

## Ejemplo 2 — Performance

- Source: usuario final
- Stimulus: envía una solicitud de consulta al catálogo de productos
- Artifact: servicio de búsqueda/motor de catálogo
- Environment: carga pico (1000 usuarios concurrentes)
- Response: el sistema procesa la solicitud y retorna resultados
- Response Measure: tiempo de respuesta menor a 2 segundos en el
  95% de las solicitudes

## Ejemplo 3 — Modifiability

- Source: desarrollador
- Stimulus: se solicita agregar un nuevo método de pago
- Artifact: módulo de procesamiento de pagos
- Environment: tiempo de diseño (no en producción)
- Response: el cambio se implementa y se despliega sin afectar
  otros módulos del sistema
- Response Measure: el cambio se completa en menos de 3
  días-persona y no requiere modificar más de 2 módulos existentes

## Ejemplo 4 — Security

- Source: usuario no autorizado (atacante externo)
- Stimulus: intenta acceder a datos de cuentas de otros usuarios
- Artifact: API de gestión de cuentas
- Environment: operación normal, sistema en producción
- Response: el sistema deniega el acceso y registra el intento
- Response Measure: el intento es bloqueado y registrado en menos
  de 1 segundo, con 0 falsos negativos en el set de pruebas de
  penetración usado
