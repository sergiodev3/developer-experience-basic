# Developer Experience Basic — Ejercicios prácticos

Este repositorio contiene los **ejercicios aplicados** del [Bloque 0 — Taller de fundamentos del desarrollador](bloque-0-fundamentos.md). El documento del bloque explica la teoría; esta carpeta `ejercicios/` es donde el alumno pone las manos.

## Organización y nomenclatura

Cada ejercicio vive en su propia carpeta dentro de `ejercicios/`, con el mismo número de tema que usa `bloque-0-fundamentos.md`:

```
ejercicios/
├── 0.1-la-terminal/
│   ├── README.md              ← guía paso a paso + resultado esperado
│   └── resultado-esperado/    ← archivos demo de referencia (contenido genérico)
└── 0.2-git-github/
    ├── README.md
    └── resultado-esperado/
```

Regla de nombres: `<número de tema del bloque>-<slug-corto>`. Así, cuando se agreguen los ejercicios de 0.3 y 0.4, la carpeta siguiente será `0.3-modulos-js/` y `0.4-flujo-errores-json/`, en el mismo orden en que aparecen en el documento del bloque.

Dentro de cada ejercicio:

| Archivo/carpeta | Para qué sirve |
|---|---|
| `README.md` | Tutorial autocontenido: objetivo, pasos numerados, comandos, resultado esperado y checklist de entrega. |
| `resultado-esperado/` | Archivos **demo con contenido genérico** que muestran cómo debería verse el resultado final. No son para copiar y entregar tal cual — son la referencia que usa el docente para verificar. |

## Orden sugerido de trabajo

| # | Ejercicio | Carpeta | Duración | Estado |
|---|---|---|---|---|
| 0 | Primera clase (intro rápida: terminal + hola mundo JS + Git/GitHub) | [`ejercicios/0.0-primera-clase/`](ejercicios/0.0-primera-clase/README.md) | 2 hrs | ✅ Disponible |
| 1 | La terminal | [`ejercicios/0.1-la-terminal/`](ejercicios/0.1-la-terminal/README.md) | 3 hrs | ✅ Disponible |
| 2 | Git y GitHub | [`ejercicios/0.2-git-github/`](ejercicios/0.2-git-github/README.md) | 5 hrs | ✅ Disponible |
| 3 | Módulos en JavaScript (`import`/`export`) | `ejercicios/0.3-modulos-js/` | 3 hrs | ⏳ Pendiente |
| 4 | Flujo, errores y JSON | `ejercicios/0.4-flujo-errores-json/` | 3 hrs | ⏳ Pendiente |

`0.0` es opcional: una probadita condensada de 0.1 + el arranque de 0.2, pensada para una sola sesión con principiantes totales. Para profundizar de verdad, el camino recomendado sigue siendo el orden completo: 0.2 da por hecho que ya sabes moverte en la terminal (0.1), y 0.3/0.4 (cuando se agreguen) van a dar por hecho que ya sabes subir tu código a GitHub (0.2).

## Cómo usar esto 

1. Sigue los pasos de ese `README.md` en su propia computadora.
2. Compara su resultado contra `resultado-esperado/` y contra la sección "Resultado esperado" del `README.md`.
3. Entrega lo que pida la sección "Checklist de entrega" de cada ejercicio.

