# W01-D02 — React + TypeScript Baseline: estado, datos derivados y tipos

Fecha: **20 de agosto de 2026**
Tiempo objetivo completo: **75 min**
Nivel inicial de ayuda permitido: **0–2**

## Objetivo

Medir el estado real de fundamentos de React + TypeScript sin entrar todavía en Effects avanzados, concurrencia o optimización. Queremos observar si siguen automáticos: props, state, eventos, actualizaciones inmutables, datos derivados, tipos unión y razonamiento sobre render.

## Parte 1 — Warm-up (10 min)

Sin ejecutar primero, explica qué problemas ves en este código y qué comportamiento esperarías:

```tsx
const [users, setUsers] = useState<User[]>(initialUsers);

function deactivateFirst() {
  users[0].active = false;
  setUsers(users);
}
```

Responde antes de modificarlo:

1. ¿Se está mutando estado?
2. ¿Por qué `setUsers(users)` puede no producir el render esperado?
3. ¿Qué tendría que cambiar conceptualmente para hacer una actualización inmutable?
4. ¿Qué diferencia hay entre cambiar el array y cambiar un objeto contenido dentro del array?

## Parte 2 — Challenge principal (35 min)

Construye un componente `TicketQueue` a partir de estos tipos:

```tsx
type TicketStatus = "open" | "resolved";
type TicketPriority = "low" | "medium" | "high";

export type Ticket = {
  id: number;
  title: string;
  status: TicketStatus;
  priority: TicketPriority;
};

type TicketQueueProps = {
  initialTickets: Ticket[];
};
```

Implementa:

```tsx
export function TicketQueue({ initialTickets }: TicketQueueProps) {
  // tu implementación
}
```

### Requisitos

1. Mostrar todos los tickets inicialmente.
2. Tener un input controlado para buscar por `title`, ignorando mayúsculas/minúsculas.
3. Tener un filtro de estado: `all`, `open`, `resolved`.
4. Mostrar solo los tickets que cumplen búsqueda + estado.
5. Cada ticket `open` debe tener un botón **Resolve**.
6. Al resolver un ticket, cambiar únicamente ese ticket a `resolved` mediante una actualización inmutable.
7. No modificar `initialTickets`.
8. Mostrar un contador `visibles / total`.
9. No guardar la lista filtrada en state: debe ser información derivada del state/props existentes.
10. No usar `any`.
11. Usar `ticket.id` como `key`, no el índice del array.
12. No usar `useEffect` para resolver los requisitos anteriores.

No se especifica si debes usar `filter`, `map`, funciones auxiliares o expresiones inline. Esa decisión forma parte del ejercicio.

### Datos para probar manualmente

```tsx
const tickets: Ticket[] = [
  { id: 1, title: "Payment webhook fails", status: "open", priority: "high" },
  { id: 2, title: "Update customer address", status: "resolved", priority: "low" },
  { id: 3, title: "Router offline", status: "open", priority: "high" },
  { id: 4, title: "Invoice duplicated", status: "open", priority: "medium" },
  { id: 5, title: "Password reset", status: "resolved", priority: "medium" },
];
```

## Parte 3 — Casos y debugging (15 min)

Comprueba al menos:

- búsqueda vacía;
- búsqueda sin resultados;
- búsqueda case-insensitive (`router` debe encontrar `Router offline`);
- filtro `open`;
- filtro `resolved`;
- combinar búsqueda + filtro;
- resolver un ticket y comprobar que los demás objetos siguen sin cambios;
- comprobar que `initialTickets` no fue mutado;
- comprobar que el contador visible cambia correctamente.

Si ya tienes Vitest + React Testing Library configurados, automatiza al menos tres casos. Si no están configurados, no gastes el baseline instalando tooling: registra comprobaciones manuales y lo introduciremos después.

## Parte 4 — Explicación técnica (15 min)

Sin reescribir el componente, explica:

1. ¿Qué datos deben vivir en state y cuáles son derivados?
2. ¿Por qué no necesitamos un `useEffect` para mantener `filteredTickets`?
3. ¿Por qué una actualización de un ticket debe crear nuevas referencias en lugar de mutar el objeto existente?
4. ¿Qué te aporta `TicketStatus` frente a declarar `status: string`?
5. ¿Qué problema puede producir usar el índice del array como `key` si la lista cambia?
6. ¿Qué cambiaría si `initialTickets` llegara después desde una petición HTTP?

La pregunta 6 es solo de razonamiento; no implementes fetching todavía.

## Regla de ayuda

- Nivel 0: intento propio.
- Nivel 1: aclaración de requisitos.
- Nivel 2: pista conceptual.
- Nivel 3+: registrar el concepto para repetición.
- Si necesitas solución completa, nivel 5 y el challenge se repetirá en otra sesión con ayuda 0–1.

Antes de pedir código, escribe qué estado crees que necesita el componente y qué información puede calcularse durante render.

## Criterio de terminado

- componente compilando;
- requisitos principales funcionando;
- sin mutación intencional de props/state;
- sin `any`;
- explicación técnica realizada;
- `REPORT.md` completado;
- nivel máximo de ayuda IA registrado.

No buscamos arquitectura ni UI bonita. El baseline mide fundamentos de React + TypeScript y autonomía para traducir requisitos a estado, tipos y transformaciones de datos.