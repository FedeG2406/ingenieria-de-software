# Casos de prueba — utility-tree-builder

## Caso 1: sistema ATM — usando los escenarios generados por
## qas-generator (trazabilidad entre las 3 skills del TP)

**Input dado a la skill** (los mismos escenarios obtenidos en
`qas-generator/tests/casos_de_prueba.md`, Caso 1, más un escenario
adicional de Security agregado para tener más de un atributo):

1. Availability — falla de red del ATM — reversión en <5s
2. Availability — falla del dispensador de efectivo — no débito
   en 100% de los casos, reporte en <10s
3. Security — intento de acceso no autorizado a cuenta ajena vía
   API de gestión de cuentas — bloqueo y registro en <1s, 0 falsos
   negativos

**Output generado por la skill (corrida real):**

```
Utilidad
├── Availability
│   ├── Recuperación ante falla de comunicación
│   │   └── Falla de red del ATM durante retiro — reversión
│   │       en <5s — (H, M)
│   └── Recuperación ante falla de hardware
│       └── Falla del dispensador de efectivo — no débito
│           en 100% de los casos, reporte en <10s — (H, M)
└── Security
    └── Control de acceso
        └── Intento de acceso no autorizado a cuenta ajena —
            bloqueo y registro en <1s, 0 falsos negativos — (H, H)
```

**Escenarios de mayor prioridad (H, H):**
- Intento de acceso no autorizado a cuenta ajena (Security) — alta
  importancia porque compromete la confidencialidad de datos
  financieros de terceros, y alta dificultad porque requiere
  mecanismos robustos de autenticación y detección en tiempo real.

**Justificación de las anotaciones (criterio usado por la skill):**
- Los dos escenarios de Availability se marcaron (H, M): alta
  importancia porque afectan directamente la confianza del cliente
  y la integridad de su saldo, dificultad media porque el failover
  y la detección de fallas de hardware son patrones conocidos y
  relativamente bien soportados por la arquitectura típica de ATMs.
- El escenario de Security se marcó (H, H): alta importancia por
  tratarse de datos financieros de terceros, alta dificultad porque
  requiere controles de autorización robustos y mecanismos de
  detección de intrusiones en tiempo real, más costosos de
  implementar y validar.

**Comparación con lo esperado:** la agrupación por atributo y
sub-característica es coherente con la teoría (Bass/Clements/Kazman,
capítulo de ATAM/Utility Tree). La asignación de (H,H) al escenario
de seguridad es consistente con el criterio típico usado en clase,
donde los escenarios de seguridad en sistemas financieros suelen
quedar en la categoría de mayor riesgo arquitectónico.

**Conclusión:** la skill agrupa correctamente por atributo/sub-
característica, no descarta ningún escenario del input, y las
anotaciones (Importancia, Dificultad) vienen acompañadas de una
justificación explícita y específica al dominio, tal como pide la
regla de calidad de la skill.
