---
name: qas-completeness-checker
description: Revisa si un escenario de atributo de calidad dado (redactado en prosa libre o parcialmente estructurado) contiene las 6 partes del template SEI (source, stimulus, artifact, environment, response, response measure), indica cuáles faltan o son ambiguas, y propone una redacción concreta para completarlas. Usar cuando el usuario pida revisar, validar, auditar o completar un escenario de calidad ya existente.
---

# QAS Completeness Checker

## Material de referencia
- `referencias/sei_qas_template.md` — definición canónica de cada
  parte, usada como criterio de evaluación.

## Instrucciones paso a paso
1. Leer el escenario dado por el usuario, sea cual sea el formato
   en que venga (prosa, lista, tabla parcial).
2. Para cada una de las 6 partes, clasificar su estado en una de
   tres categorías:
   - **OK**: está presente y es específica/no ambigua.
   - **Ambigua**: está presente pero es vaga o no verificable
     (ej. un response measure como "debe ser rápido").
   - **Falta**: no aparece en absoluto en el escenario dado.
3. Para toda parte "Falta" o "Ambigua", proponer una redacción
   concreta que la complete o corrija, coherente con el resto del
   escenario (no una respuesta genérica de relleno). La propuesta
   debe poder insertarse directamente en el escenario.
4. Si el escenario tiene el artifact como "el sistema" en general
   y no hay más contexto disponible, marcarlo como Ambigua y
   sugerir que se identifique el componente específico si es
   posible, aclarando que es aceptable dejarlo general en etapas
   tempranas de brainstorming.
5. Entregar el resultado en la tabla de "Formato de salida", y
   al final, el escenario reescrito completo incorporando todas
   las propuestas.

## Reglas de calidad
- Un response measure sin número, porcentaje o umbral SIEMPRE se
  marca como Ambigua, nunca como OK.
- No inventar información que contradiga lo que el usuario ya
  especificó; solo completar lo que falta.
- Las propuestas deben ser específicas al dominio del escenario
  dado (si el sistema es un ATM, no proponer un response measure
  genérico de "sistema web").

## Formato de salida
| Parte | Estado (OK / Ambigua / Falta) | Contenido actual | Propuesta de completado |
|---|---|---|---|

Seguido de:

**Escenario completo reescrito:**
(las 6 partes ya completas, listas para usar)
