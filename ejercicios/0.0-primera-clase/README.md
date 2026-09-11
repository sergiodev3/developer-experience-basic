# Clase 1 — Terminal, primer "hola mundo" en JS y tu primer repositorio en GitHub

> Guía condensada para una sesión única de 2 horas. Cubre una probadita de [`0.1-la-terminal`](../0.1-la-terminal/README.md) y el arranque de [`0.2-git-github`](../0.2-git-github/README.md) (Parte A), pensada para alumnos que **nunca** abrieron una terminal.

## Objetivo

Que cada alumno salga de la clase habiendo: navegado la terminal sin el explorador de archivos, ejecutado JavaScript desde PowerShell (REPL y archivo), y subido un repositorio propio y **público** a su cuenta de GitHub.

## Duración estimada

2 horas (120 min), en un solo bloque con los alumnos en VSCode desde el inicio.

## Requisitos previos

- Node instalado (`node --version` debe responder con un número) — ya viene instalado en las máquinas del laboratorio.
- Git instalado (`git --version` debe responder con un número).
- Cuenta de [GitHub](https://github.com) creada de antemano (pídelo como tarea previa si puedes).
- VSCode abierto con una carpeta de trabajo cualquiera y su terminal integrada en PowerShell.

---

## 📋 Plan de la sesión (para el docente)

| Bloque | Tiempo | Qué haces tú | Qué hacen ellos |
|---|---|---|---|
| 0. Bienvenida y setup | 10 min | Verificas `node --version` y `git --version` en pantalla; abres VSCode y la terminal integrada (`` Ctrl+ñ `` o menú *Terminal → New Terminal*) | Verifican lo mismo en su máquina |
| 1. La terminal | 25 min | Demuestras cada comando antes de que lo repitan | Mini-ejercicio de navegación (abajo) |
| 2. Hola mundo en JS | 20 min | Demuestras REPL y luego archivo | Repiten y ejecutan su propio `hola-mundo.js` |
| — Descanso — | 5 min | | |
| 3. Git y GitHub | 55 min | Sigues `0.2-git-github/README.md` Parte A en pantalla, marcando qué recortar | Replican cada comando, crean su repo público |
| 4. Cierre y checklist | 5 min | Revisas 2-3 repos al azar proyectados | Comparten la URL de su repo |

> 👩‍🏫 **Nota docente:** no dejes que nadie se quede atrás en el Bloque 1 — si alguien no entiende `cd`/`..` ahí, se pierde todo lo que sigue. Vale la pena tardar 5 minutos extra aquí y recortarlos de la Parte B de Git (que hoy no se hace de todos modos).

---

## Bloque 1 — La terminal (25 min)

### El prompt te dice dónde estás

Antes de escribir nada, mira tu terminal: el texto antes del cursor es tu ubicación actual.

```
PS C:\Users\ana\proyectos>
```

Todo comando que escribas se ejecuta **desde ahí**.

### Comandos de hoy

| Quiero… | Comando en PowerShell |
|---|---|
| Saber dónde estoy | `pwd` |
| Ver qué hay en esta carpeta | `ls` |
| Entrar a una carpeta | `cd nombre` |
| Subir un nivel | `cd ..` |
| Crear una carpeta | `mkdir nombre` |
| Crear carpetas anidadas de golpe | `mkdir a\b\c -Force` |
| Crear un archivo vacío | `ni archivo.txt` |
| Crear un archivo **con contenido** | `"texto" > archivo.txt` |
| Agregar contenido sin borrar lo anterior | `"más texto" >> archivo.txt` |
| Leer el contenido de un archivo | `Get-Content archivo.txt` (o `cat archivo.txt`) |
| Repetir el comando anterior | flecha `↑` |
| Autocompletar un nombre | `Tab` |

> 👩‍🏫 **Nota docente:** `>` sobreescribe todo el archivo; `>>` agrega al final. Es el error más común — alguien va a perder su contenido con `>` por accidente. Apunta a que lo vean en vivo.

### Mini-ejercicio: la carpeta de práctica

**Regla: el explorador de archivos queda prohibido durante este bloque.**

1. Desde tu carpeta de usuario, crea de un solo comando esta estructura:

```
practica-clase1/
└── notas/
    └── borrador/
```

2. Entra hasta `borrador` y crea un archivo `idea.txt` con el contenido `"Mi primera idea"` usando `>`.
3. Agrega una segunda línea a `idea.txt` con `>>` sin borrar la primera.
4. Lee el archivo completo con `Get-Content` para confirmar que quedaron las dos líneas.
5. Regresa a `practica-clase1` con un solo comando (cuenta cuántos `..` necesitas).

**Resultado esperado:** `pwd` te confirma que estás de vuelta en `practica-clase1`, y `Get-Content notas\borrador\idea.txt` muestra las dos líneas en orden.

> 👩‍🏫 **Nota docente:** si sobra tiempo o alguien termina rápido, mándalo a intentar el laberinto completo (3 niveles + cronómetro) de [`0.1-la-terminal`](../0.1-la-terminal/README.md) como reto extra.

---

## Bloque 2 — Tu primer "hola mundo" en JavaScript (20 min)

### Paso 1: el REPL de Node (modo interactivo)

Desde la terminal de VSCode, en cualquier carpeta:

```powershell
node
```

Tu prompt cambia a `>` — ya estás **dentro** de Node, no de PowerShell. Prueba, línea por línea:

```js
console.log("Hola, mundo!")
2 + 2
"Hola" + ", " + "mundo!"
```

Cada línea se ejecuta al instante y ves el resultado. Para salir y volver a PowerShell:

```js
.exit
```

> 👩‍🏫 **Nota docente:** aclara que el REPL es para **probar cosas rápido**, no para guardar trabajo — al cerrarlo, todo se pierde. Por eso el siguiente paso es guardar el código en un archivo.

### Paso 2: guarda tu código en un archivo

De vuelta en PowerShell (ya saliste del REPL con `.exit`), crea un archivo `hola-mundo.js` desde VSCode (o con `ni hola-mundo.js`) y escribe dentro:

```js
console.log("Hola, mundo!");
```

Guarda el archivo y ejecútalo **sin entrar al REPL**, directo desde PowerShell:

```powershell
node hola-mundo.js
```

**Resultado esperado:** la terminal imprime `Hola, mundo!` y regresa al prompt de PowerShell — a diferencia del REPL, el archivo corre de principio a fin y termina solo.

### Paso 3: una versión con función (la usarás en el Bloque 3)

Reemplaza el contenido de `hola-mundo.js` por:

```js
function saludar(nombre) {
  return `Hola, ${nombre}!`;
}

console.log(saludar("mundo"));
```

Ejecuta de nuevo `node hola-mundo.js` — mismo resultado, pero ahora es una función reutilizable. Guarda este archivo: lo vas a subir a GitHub en el bloque siguiente.

---

## Bloque 3 — Git y GitHub: sube tu primer repositorio (55 min)

Vas a seguir la **Parte A** del ejercicio [`0.2-git-github/README.md`](../0.2-git-github/README.md), con estos recortes para que quepa en el tiempo de hoy:

| En vez de… | Haz esto hoy |
|---|---|
| 5 commits (pasos 3 y 4 del ejercicio completo) | **3 commits**: README con tu nombre → `hola-mundo.js` (el del Bloque 2) → `.gitignore` |
| Crear `src/index.js` con una función genérica | Usa tu **propio** `hola-mundo.js` del Bloque 2 — cópialo o muévelo a la raíz del nuevo proyecto |
| Parte B (ramas, Pull Request, conflictos) | **No se hace hoy** — queda para la próxima sesión |

Pasos exactos a seguir (abre `0.2-git-github/README.md` en pantalla y ve sección por sección):

1. **Sección "Requisitos previos"** → configura tu identidad de Git (una sola vez por máquina).
2. **Parte A, pasos 1 y 2** → crea la carpeta `git-practica`, entra, `git init`.
3. **Parte A, paso 3** → crea tu `README.md` con tu nombre, primer commit.
4. Copia tu `hola-mundo.js` del Bloque 2 dentro de esta carpeta y haz un commit (`"Agrega hola-mundo.js"`).
5. **Parte A, paso 5** → agrega `.gitignore`, crea un `.env` de prueba y confirma con `git status` que Git lo ignora, luego haz commit del `.gitignore`.
6. **Sección "Cómo subir tu ejercicio a un repo"** → crea el repositorio vacío en GitHub.

> ⚠️ **Al crear el repositorio en github.com/new, verifica que quede marcado como `Public`** (es la opción por defecto, pero confírmalo con cada alumno) — el objetivo de hoy es que el link sea compartible con cualquiera, no solo con colaboradores agregados a mano.

7. Conecta y sube: `git remote add origin ...` y `git push -u origin main`.
8. **Parte A, paso 7** → `git log --oneline` y captura de pantalla con tus 3 commits.

> 👩‍🏫 **Nota docente:** el error más común aquí es el mensaje `Updates were rejected...` cuando alguien marcó "Add a README file" al crear el repo en GitHub. La tabla "Problemas comunes al conectar con GitHub" de `0.2-git-github/README.md` tiene la solución (`git pull --rebase origin main`).

---

## Resultado esperado

Al final de la clase, cada alumno tiene:

- Una carpeta `git-practica` con 3 commits descriptivos (`git log --oneline` lo confirma).
- Un archivo `hola-mundo.js` que corrieron con éxito con `node hola-mundo.js`.
- Un `.gitignore` que demuestra ignorar `.env`.
- Un repositorio **público** en su cuenta de GitHub con ese historial.

Revisa [`resultado-esperado/`](resultado-esperado/) de este ejercicio para ver ejemplos genéricos de cómo debería verse cada archivo.

## Checklist de entrega

- [ ] Ejecuté comandos de navegación en la terminal sin abrir el explorador de archivos.
- [ ] Corrí JavaScript en el REPL de Node (`node`, `.exit`).
- [ ] Creé `hola-mundo.js` y lo ejecuté con `node hola-mundo.js` desde PowerShell.
- [ ] Tengo un repositorio en GitHub, **público**, con al menos 3 commits.
- [ ] Mi `.gitignore` protege `.env` desde su propio commit.
- [ ] Comparto la URL de mi repositorio.

## Qué sigue

- El laberinto completo (con reto de cronómetro) en [`0.1-la-terminal`](../0.1-la-terminal/README.md), si quieres más práctica de terminal.
- La **Parte B** de [`0.2-git-github`](../0.2-git-github/README.md) — trabajar en parejas con ramas, Pull Requests y resolver un conflicto real — en la próxima sesión.
