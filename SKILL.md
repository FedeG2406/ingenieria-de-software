---
name: qas-generator
description: Genera escenarios de atributos de calidad (Quality Attribute Scenarios) en el template de 6 partes del SEI (source, stimulus, artifact, environment, response, response measure), a partir de una descripción de un sistema y un atributo de calidad de interés (performance, availability, security, modifiability, usability, testability). Usar cuando el usuario pida generar QAS, escenarios de calidad, o aplicar la fase de brainstorming del método QAW del SEI.
---

# QAS Generator (SEI 6-part scenarios)

## Material de referencia
Antes de generar cualquier escenario, consultar y usar como fuente
de verdad:
- `referencias/sei_qas_template.md` — definición canónica de cada
  una de las 6 partes y reglas de estilo.
- `referencias/ejemplos_bass_sap.md` — ejemplos validados que fijan
  el nivel de precisión y el formato esperado.

No inventar definiciones alternativas de las 6 partes: usar
siempre las de `sei_qas_template.md`.

## Instrucciones paso a paso
1. Identificar el sistema descripto por el usuario y el/los
   atributo(s) de calidad pedidos. Si no se especifica un atributo,
   preguntar cuál interesa antes de generar (performance,
   availability, security, modifiability, usability, testability).
2. Generar entre 2 y 3 escenarios distintos para el atributo
   pedido. Deben variar entre sí en al menos el source o el
   environment, para evitar escenarios redundantes.
3. Completar las 6 partes para cada escenario, siguiendo el
   formato de `ejemplos_bass_sap.md`.
4. Validar cada escenario contra este checklist antes de
   entregarlo:
   - ¿El source es una entidad concreta e identificable?
   - ¿El stimulus es un evento discreto (no una necesidad vaga)?
   - ¿El artifact es un componente específico del sistema descripto
     (no "el sistema" en general, salvo que no haya más detalle)?
   - ¿El response measure es cuantificable (tiempo, %, cantidad)?
   Si algún ítem falla, corregir el escenario antes de mostrarlo.
5. Presentar el resultado en la tabla de "Formato de salida".

## Reglas de calidad
- Nunca usar como response measure adjetivos sueltos como "rápido",
  "seguro", "fácil" sin un número o umbral asociado.
- Un escenario = un solo estímulo. No mezclar dos eventos distintos
  en un mismo escenario.
- El artifact debe ser coherente con el sistema descripto por el
  usuario (no genérico ni copiado literal de los ejemplos de
  referencia).

## Formato de salida
Tabla markdown, una columna por escenario:

| Parte | Escenario 1 | Escenario 2 | Escenario 3 |
|---|---|---|---|
| Source | ... | ... | ... |
| Stimulus | ... | ... | ... |
| Artifact | ... | ... | ... |
| Environment | ... | ... | ... |
| Response | ... | ... | ... |
| Response Measure | ... | ... | ... |
