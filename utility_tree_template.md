# Árbol de utilidad (Utility Tree) — SEI / método QAW

Fuente teórica: Bass, Clements & Kazman, "Software Architecture in
Practice"; material del método ATAM/QAW del SEI.

## Estructura
El árbol de utilidad organiza y prioriza los escenarios de calidad
recolectados (típicamente en la fase de brainstorming del QAW), en
4 niveles:

1. **Raíz**: "Utilidad" (utility) — representa la calidad global
   del sistema.
2. **Nivel 2 — Atributos de calidad**: performance, availability,
   security, modifiability, usability, testability, etc.
3. **Nivel 3 — Sub-características (refinamientos)**: por ejemplo,
   dentro de Performance: "tiempo de respuesta", "throughput";
   dentro de Availability: "tiempo de recuperación", "detección de
   fallas".
4. **Hojas — Escenarios concretos**: cada uno en formato de 6 partes
   (o al menos resumido en Stimulus + Response Measure), anotado
   con dos valores:
   - **Importancia** (H/M/L — High/Medium/Low): qué tan crítico es
     este escenario para el negocio/stakeholders.
   - **Dificultad de implementación** (H/M/L): qué tan costoso es
     arquitectónicamente lograrlo.

## Notación estándar
Cada hoja se anota como (Importancia, Dificultad), ej: (H, M) para
un escenario de alta importancia y dificultad media.

## Uso del árbol
El árbol sirve para **priorizar**: los escenarios (H, H) — alta
importancia y alta dificultad — son los que más deben guiar
decisiones arquitectónicas tempranas, porque son los de mayor
riesgo. Los (L, L) suelen descartarse o postergarse.

## Formato de representación
Puede representarse como texto indentado (árbol ASCII) o como
diagrama. Para esta skill se usa texto indentado por simplicidad
y facilidad de comparación en los tests.
