# W01-D01 — Java Baseline: fundamentos que deben volver a ser automáticos

Fecha: **19 de agosto de 2026**
Tiempo objetivo: **75 min**
Nivel inicial de ayuda permitido: **0–2**

## Objetivo

Medir tu estado real en Java básico sin apoyarnos todavía en Spring. Queremos recuperar fluidez con referencias, igualdad, Collections y razonamiento sobre datos.

## Parte 1 — Warm-up (10 min)

Sin ejecutar primero, predice el resultado y explica por qué:

```java
String a = new String("java");
String b = new String("java");

System.out.println(a == b);
System.out.println(a.equals(b));
```

Después ejecútalo y compara tu predicción.

Escribe en tu reporte:

- qué compara `==` aquí;
- qué compara `equals`;
- qué cambiaría si usáramos literales de String.

## Parte 2 — Challenge principal (30 min)

Usa este modelo:

```java
public record User(long id, String email, boolean active) {}
```

Implementa:

```java
List<User> normalizeUsers(List<User> users)
```

Requisitos:

1. eliminar usuarios con `email == null` o en blanco;
2. considerar duplicados los emails ignorando mayúsculas/minúsculas;
3. conservar **la última aparición** de cada email;
4. preservar el orden relativo resultante;
5. no modificar la lista recibida;
6. devolver una lista nueva.

Ejemplo conceptual:

```text
A@example.com (id=1)
b@example.com (id=2)
a@example.com (id=3)
```

Debe conservar el usuario con `id=3` para `a@example.com`.

No se especifica si debes usar `List`, `Map`, `Set`, loops o Streams: esa decisión es parte del ejercicio.

## Parte 3 — Tests y edge cases (15 min)

Escribe tests para al menos:

- lista vacía;
- email nulo;
- email blank;
- duplicado con distinto casing;
- tres duplicados del mismo email;
- orden de salida;
- comprobación de que la lista original no fue modificada.

## Parte 4 — Comparación de implementaciones (10 min)

Sin reescribir todo necesariamente, explica cómo cambiaría tu solución si:

- tuvieras que conservar la **primera** aparición;
- el orden no importara;
- hubiera un millón de usuarios;
- `User` fuera una clase mutable usada como key de un `HashMap`.

## Parte 5 — Explicación oral (10 min)

Sin leer, explica:

1. `==` vs `equals`;
2. para qué sirve `hashCode`;
3. cuándo usarías `List`, `Set` y `Map`;
4. por qué mutar una key de `HashMap` puede romper búsquedas;
5. por qué elegiste tu estructura de datos.

## Regla de ayuda

Durante los primeros 30 minutos no pidas código ni pseudocódigo a una IA.

Si te bloqueas:

- nivel 1: aclaración del requisito;
- nivel 2: pista conceptual;
- nivel 3 o superior: se registra como concepto a repetir.

## Criterio de terminado

- solución compilando;
- tests pasando;
- explicación oral realizada;
- `REPORT.md` completado;
- nivel máximo de ayuda IA registrado.

No buscamos una solución elegante. Buscamos medir qué fundamentos siguen disponibles sin asistencia.