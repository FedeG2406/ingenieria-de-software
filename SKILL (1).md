---
name: utility-tree-builder
description: Construye un árbol de utilidad (utility tree) del método QAW/ATAM del SEI a partir de una lista de escenarios de atributos de calidad, agrupándolos por atributo y sub-característica, y anotando cada escenario hoja con su Importancia y Dificultad de implementación (H/M/L). Usar cuando el usuario pida armar, generar o priorizar un árbol de utilidad a partir de un conjunto de escenarios.
---

# Utility Tree Builder

## Material de referencia
- `referencias/utility_tree_template.md` — estructura de 4 niveles
  y notación (Importancia, Dificultad) usada como fuente de verdad.

## Instrucciones paso a paso
1. Recibir la lista de escenarios (pueden venir en formato de 6
   partes completo, o resumidos en Stimulus + Response Measure).
2. Agrupar los escenarios por atributo de calidad (Nivel 2):
   performance, availability, security, modifiability, usability,
   testability, u otro que corresponda según el dominio del sistema.
3. Dentro de cada atributo, definir sub-características (Nivel 3)
   relevantes según el contenido real de los escenarios (no usar
   una lista fija; inferir de los datos, ej. "tiempo de respuesta"
   vs "throughput" dentro de Performance).
4. Ubicar cada escenario como hoja bajo su sub-característica
   correspondiente.
5. Para cada hoja, asignar (Importancia, Dificultad) en escala
   H/M/L:
   - Si el usuario ya indicó estos valores, respetarlos.
   - Si no los indicó, inferirlos razonadamente del contenido del
     escenario y explicitar brevemente el criterio usado (ej. "alta
     importancia porque afecta la integridad de transacciones
     financieras").
6. Presentar el árbol completo en el formato de salida, y agregar
   un resumen de los escenarios (H, H) — los de mayor riesgo/
   prioridad arquitectónica.

## Reglas de calidad
- No dejar ningún escenario recibido fuera del árbol.
- No inventar escenarios nuevos: esta skill solo organiza y prioriza
  los que se le dan como input (a diferencia de qas-generator).
- Si dos escenarios son prácticamente idénticos, señalarlo como
  posible duplicado en vez de listarlos dos veces sin comentario.

## Formato de salida
Texto indentado:

```
Utilidad
├── [Atributo 1]
│   ├── [Sub-característica 1.1]
│   │   └── [Escenario resumido] — (Importancia, Dificultad)
│   └── [Sub-característica 1.2]
│       └── [Escenario resumido] — (Importancia, Dificultad)
└── [Atributo 2]
    └── ...
```

Seguido de una sección "Escenarios de mayor prioridad (H, H)" con
la lista de los que caen en esa categoría.
