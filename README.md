# TP — Skills estilo Claude para el método QAW / templates SEI

## Contenido de la entrega

Este repositorio/zip contiene 3 skills (estilo Claude, formato
`SKILL.md`) desarrolladas a partir del material bibliográfico del
método QAW (Quality Attribute Workshop) del SEI y del libro
*Software Architecture in Practice* (Bass, Clements & Kazman):

| Carpeta | Qué hace |
|---|---|
| `qas-generator/` | Genera escenarios de atributos de calidad en el template de 6 partes del SEI (source, stimulus, artifact, environment, response, response measure), a partir de la descripción de un sistema. |
| `qas-completeness-checker/` | Recibe un escenario (posiblemente incompleto/ambiguo) y determina qué partes de las 6 faltan o son vagas, proponiendo cómo completarlas. |
| `utility-tree-builder/` | Organiza un conjunto de escenarios en un árbol de utilidad (atributo → sub-característica → escenario), con anotación de Importancia y Dificultad. |

## Estructura de cada skill

Cada carpeta sigue el mismo esquema:

```
<nombre-skill>/
├── SKILL.md              ← definición de la skill (frontmatter +
│                            instrucciones + reglas + formato)
├── referencias/           ← material complementario bibliográfico
│                            usado para "enfocar" la skill, en vez
│                            de depender solo del conocimiento
│                            general del modelo
└── tests/
    └── casos_de_prueba.md ← ejemplos conocidos usados para testear
                              la skill, con el output real obtenido,
                              comparación contra el resultado
                              esperado y conclusión
```

## Material complementario usado

El material de referencia (`referencias/`) resume:
- La definición canónica del template de 6 partes del SEI.
- Ejemplos de escenarios ya validados en la bibliografía de cátedra
  (Bass/Clements/Kazman), usados como "anclaje de estilo" para que
  las skills generen output con el mismo nivel de precisión.
- La estructura y notación del árbol de utilidad (SEI/ATAM).

## Testeo

Cada skill fue corrida contra al menos un caso conocido (sistema
ATM y/o sistema de e-commerce, casos típicos usados en la
bibliografía), documentando en `tests/casos_de_prueba.md`:
- El input exacto dado.
- El output real obtenido al correr la skill.
- La comparación contra el resultado esperado según la bibliografía.
- Una conclusión sobre el grado de acierto.

Las tres skills fueron testeadas de forma encadenada sobre el mismo
sistema (ATM) en `utility-tree-builder/tests/casos_de_prueba.md`,
para mostrar la trazabilidad: los escenarios generados por
`qas-generator` son los mismos que luego se organizan en el árbol
de `utility-tree-builder`.

## Cómo se usan (Claude)

Cada carpeta es una skill válida para Claude: el frontmatter YAML
(`name` + `description`) permite que el modelo la reconozca y la
active automáticamente cuando el pedido del usuario coincide con la
descripción. Los archivos de `referencias/` son leídos por la skill
como fuente de conocimiento de dominio antes de generar cualquier
output.
