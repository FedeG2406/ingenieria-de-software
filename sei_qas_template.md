# Template de 6 partes - SEI Quality Attribute Scenario (QAS)

Fuente teórica: Bass, L.; Clements, P.; Kazman, R. "Software
Architecture in Practice", y material del método QAW (Quality
Attribute Workshop) del SEI.

Un escenario de atributo de calidad bien formado tiene 6 partes:

1. **Source of stimulus**: la entidad (una persona, un sistema
   computacional, u otro actor) que genera el estímulo. Debe ser
   identificable, no "el sistema" en general.

2. **Stimulus**: la condición que llega al sistema y que requiere
   una respuesta cuando arriba. Es un evento discreto y concreto
   (una petición, una falla, un cambio de carga), no una necesidad
   difusa.

3. **Artifact**: la parte del sistema que es estimulada. Puede ser
   el sistema completo, o (preferentemente, para que sea más útil
   arquitectónicamente) un componente/servicio/dato específico.

4. **Environment**: el conjunto de circunstancias en las que ocurre
   el estímulo. Ejemplos: operación normal, sobrecarga, modo
   degradado, arranque/apagado, mantenimiento.

5. **Response**: la actividad que se realiza como consecuencia de la
   llegada del estímulo, a través del artefacto afectado.

6. **Response measure**: cuando la respuesta ocurre, debe ser posible
   medirla de alguna manera, para que el escenario pueda ser
   testeado. Debe ser CUANTIFICABLE (tiempo, porcentaje, cantidad de
   errores admitidos, throughput, etc.)

## Regla de oro
Si el Response Measure no se puede convertir en un criterio
pasa/no-pasa medible, el escenario está mal escrito. Frases como
"debe ser rápido", "debe ser seguro" o "debe ser fácil de usar" NO
son response measures válidos por sí solas.

## Atributos de calidad típicos a cubrir
- Performance (tiempo de respuesta, throughput, uso de recursos)
- Availability (disponibilidad, tiempo de recuperación, MTBF/MTTR)
- Security (confidencialidad, integridad, detección de intrusiones)
- Modifiability (tiempo/costo de implementar un cambio, acoplamiento)
- Usability (tiempo de aprendizaje, tasa de error del usuario)
- Testability (tiempo/esfuerzo para detectar una falla inyectada)

## Escenarios "generales" vs "concretos"
- General: describe una clase de estímulos/respuestas posibles para
  el sistema (útil en brainstorming).
- Concreto: es una instancia específica y no ambigua de un escenario
  general, con valores concretos en cada una de las 6 partes. Es el
  formato que debe entregar esta skill.
