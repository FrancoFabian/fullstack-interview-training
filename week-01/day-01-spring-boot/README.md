# W01-D01 — Spring Boot Baseline

Fecha: 12 de agosto de 2026
Tiempo objetivo: 75 min
Nivel inicial de ayuda permitido: 0–2

## Objetivo

Recuperar el modelo mental básico de Spring Boot mediante una API pequeña y debugging, no memorizando anotaciones.

## Escenario

Tienes que construir o adaptar una API mínima de usuarios con estos endpoints:

```text
POST /users
GET /users/{id}
```

Requisitos:

- crear un usuario con `name` y `email`;
- `name` y `email` son obligatorios;
- el email debe tener formato válido;
- responder `201 Created` al crear;
- responder `200 OK` al consultar uno existente;
- responder `404 Not Found` cuando el usuario no existe;
- no exponer directamente la entidad de persistencia desde el controller;
- incluir al menos tests para creación válida, validación y 404.

## Restricciones

Durante los primeros 30 minutos:

- no usar ChatGPT para código;
- sí usar IDE, debugger, documentación oficial, logs y tests;
- antes de implementar escribir tu flujo esperado desde la request hasta la respuesta.

## Antes de programar

Responde en tu reporte:

```text
¿Qué responsabilidad tiene Controller?
¿Qué responsabilidad tiene Service?
¿Qué responsabilidad tiene Repository?
¿Qué objeto debería validar la entrada HTTP?
¿Dónde convertirías “usuario inexistente” en 404?
```

No busques las respuestas si crees recordarlas: escríbelas primero.

## Parte A — Construcción

Implementa la API con separación mínima entre:

```text
HTTP → Controller → Service → Repository
```

Puedes usar almacenamiento en memoria si quieres concentrarte primero en Spring MVC. JPA no es requisito para este baseline.

## Parte B — Debugging

Cuando la API funcione, provoca deliberadamente uno de estos errores y diagnostícalo:

1. hacer que un usuario inexistente termine en 500 en lugar de 404; o
2. quitar una dependencia del contexto para producir un fallo de arranque; o
3. romper una validación para que llegue información inválida al Service.

Registra:

```text
Síntoma:
Hipótesis:
Evidencia:
Root cause:
Corrección:
```

## Parte C — Explicación oral

Sin leer código, explica durante 3–5 minutos:

1. cómo entra la request;
2. cómo Spring encuentra el controller;
3. de dónde sale la instancia del service;
4. qué es un bean en este ejemplo;
5. qué diferencia hay entre Spring y Spring Boot en lo que acabas de usar;
6. por qué un 404 no debería ser un 500.

## Criterio de terminado

- endpoints funcionales;
- tests mínimos ejecutados;
- reporte de sesión completado;
- explicación oral realizada;
- nivel máximo de ayuda IA registrado.

## Importante

No necesitas construir una aplicación “bonita”. El objetivo es descubrir cuánto puedes explicar y resolver sin asistencia antes de personalizar las siguientes sesiones.