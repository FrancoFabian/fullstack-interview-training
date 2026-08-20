# Progress Tracker

Este archivo registra progreso **observable**. ChatGPT puede actualizarlo después de revisar commits, PRs, tests y explicaciones.

**Inicio real del entrenamiento: 19 de agosto de 2026.** No existe progreso previo contabilizado.

## Escala por sesión

Cada categoría vale 0–2:

| Categoría | 0 | 1 | 2 |
|---|---|---|---|
| Comprensión | No identifica el problema | Parcial | Comprende requisitos y riesgos |
| Correctness | Falla casos principales | Funciona con huecos | Correcto + edge cases |
| Fundamentos | Dependencia de memoria/IA | Manejo parcial | Explica y aplica con precisión |
| Debugging/tests | Prueba al azar | Diagnóstico parcial | Hipótesis → evidencia → tests |
| Comunicación/autonomía | No puede defender solución | Explica parcialmente | Defiende trade-offs sin ayuda |

**Máximo: 10 puntos.**

La puntuación es una métrica interna de entrenamiento, no una equivalencia con procesos de contratación.

## Registro

| Fecha | Track | Challenge | Score /10 | IA máx. | Tiempo | Repetir | Observación |
|---|---|---|---:|---:|---:|---|---|
| 2026-08-20 | Java | W01-D01 — fundamentos, referencias, Collections y testing | 5 | 5 | 75m+ | Sí | El algoritmo principal terminó correctamente planteado, pero requirió ayuda alta para testing y comparación de variantes; hubo dificultad importante para recuperar conceptos básicos y traducir requisitos a estructuras de datos. |

## Estado por track

### Java

Baseline W01-D01 completado como diagnóstico, no como dominio.

**Lo que sí quedó razonablemente comprendido o recuperado:**

- diferencia práctica entre conservar la última y la primera aparición de un duplicado;
- uso de `HashSet<String>` para registrar emails normalizados ya vistos;
- recorrido inverso + `Collections.reverse(...)` para conservar la última aparición manteniendo el orden relativo;
- recorrido normal para conservar la primera aparición;
- filtrado de email `null` o blank;
- idea de normalizar casing antes de comparar emails;
- diferencia general entre `List`, `Set` y `Map` aplicada al challenge;
- idea de usar `HashMap<String, User>` cuando el orden no importa y una aparición posterior debe reemplazar a una anterior;
- noción inicial de complejidad: una pasada con estructuras hash frente a un enfoque cuadrático;
- riesgo conceptual de mutar un campo que participa en `equals()`/`hashCode()` cuando el objeto se usa como key de `HashMap`.

**Dificultades observadas:**

- costó convertir simultáneamente los requisitos de filtrado, deduplicación, última aparición y preservación de orden en un algoritmo antes de pensar en Streams;
- tendencia inicial a elegir Streams antes de tener claro el algoritmo imperativo;
- confusión entre índice de una `List` y el `id` de un objeto (`users.get(i)` vs `user.getId()`);
- dificultad para recordar API básica de Collections y decidir qué estructura corresponde al problema;
- `equals()`/`hashCode()` y mutabilidad de keys de `HashMap` no estaban disponibles de forma automática y necesitaron explicación;
- testing unitario con JUnit no estaba disponible de forma autónoma: fue necesario introducir desde cero `@Test`, Arrange/Act/Assert y assertions;
- no hubo autonomía suficiente para resolver sin ayuda la comparación completa de implementaciones de la Parte 4;
- el nivel de ayuda llegó a 5 cuando fue necesario mostrar implementaciones completas para poder comparar y entender las variantes.

**Adaptación para próximas sesiones de Java:**

1. Priorizar primero algoritmos imperativos simples (`for`, condiciones, `List`, `Set`, `Map`) antes de introducir Streams.
2. Empezar cada sesión Java con 10–15 minutos de recuperación activa de APIs y conceptos básicos, sin apuntes.
3. Incluir ejercicios cortos específicos sobre índices vs identidad/ID de objetos y recorrido de colecciones.
4. Repetir `equals()`/`hashCode()` con ejemplos observables de `HashMap` y `HashSet` hasta poder explicarlos sin ayuda.
5. Introducir JUnit progresivamente: primero Arrange/Act/Assert y assertions básicas; después diseño de edge cases; Mockito queda fuera hasta que exista una dependencia real que simular.
6. Pedir primero una solución verbal o pseudocódigo propio antes de permitir Streams.
7. Repetir un challenge de deduplicación más pequeño en una sesión futura con nivel IA 0–1 para verificar que el concepto quedó retenido.

**Objetivo de la siguiente repetición:** resolver una variante pequeña con `List`/`Set` sin ayuda de implementación, escribir al menos tres tests JUnit propios y explicar `equals()`/`hashCode()` y la elección de estructura de datos.

### React / TypeScript
Pendiente de baseline.

### Spring Boot
Pendiente de baseline.

### Spring Security
Pendiente de baseline.

### Inglés profesional
Pendiente de baseline.

## Regla de actualización

Después de cada sesión, conservar evidencia del resultado y actualizar este archivo únicamente con observaciones justificables mediante código, tests, respuestas del usuario o repetición posterior.