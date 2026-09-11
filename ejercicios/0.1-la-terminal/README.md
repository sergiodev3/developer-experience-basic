# Ejercicio 0.1 — La terminal: el laberinto a ciegas

> Ejercicio práctico del tema [0.1 en `bloque-0-fundamentos.md`](../../bloque-0-fundamentos.md#01-la-terminal-hablarle-a-la-computadora-sin-mouse-3-hrs).

## Objetivo

Moverte con confianza por el sistema de archivos **usando solo la terminal**: crear carpetas anidadas, crear archivos, navegar con rutas relativas y regresar a un punto de partida, sin abrir nunca el explorador de archivos.

## Duración estimada

20–30 minutos.

## Requisitos previos

- Una terminal abierta: PowerShell (Windows), Git Bash o la terminal de Mac/Linux.
- Saber qué es el "prompt" y que te indica en qué carpeta estás parado (ver la sección "El prompt te dice dónde estás" del bloque 0.1).

## Regla del juego

**El explorador de archivos (Finder / Explorador de Windows) queda prohibido durante todo el ejercicio.** Si lo abres, aunque sea para confirmar algo, reinicia el ejercicio desde el paso 1.

## Comandos de referencia

| Quiero… | Windows (PowerShell) | Git Bash / Linux / Mac |
|---|---|---|
| Saber dónde estoy | `pwd` | `pwd` |
| Ver qué hay aquí | `ls` | `ls` |
| Entrar a una carpeta | `cd nombre` | `cd nombre` |
| Subir un nivel | `cd ..` | `cd ..` |
| Subir dos niveles | `cd ..\..` | `cd ../..` |
| Crear una carpeta | `mkdir nombre` | `mkdir nombre` |
| Crear carpetas anidadas de golpe | `mkdir a\b\c -Force` | `mkdir -p a/b/c` |
| Crear un archivo vacío | `ni archivo.txt` | `touch archivo.txt` |
| Ver el historial de comandos | flecha `↑` | flecha `↑` |

> 💡 Usa `Tab` para autocompletar nombres de carpetas y archivos — te va a ahorrar errores de dedo durante todo el ejercicio.

## Paso a paso

### 1. Ubícate en tu carpeta de usuario

Abre la terminal y confirma dónde estás parado.

**Resultado esperado:** el comando te imprime una ruta que termina en tu nombre de usuario (por ejemplo `C:\Users\ana` o `/home/ana`).

### 2. Crea la estructura del laberinto con un solo comando

Sin salir de tu carpeta de usuario, crea de una sola vez esta estructura:

```
laberinto/
├── nivel-1/
│   ├── nivel-2/
│   │   └── tesoro/
│   └── trampa/
└── salida/
```

**Pista:** el comando para crear carpetas anidadas de golpe está en la tabla de arriba. Necesitarás dos llamadas: una para la rama `nivel-1/nivel-2/tesoro`, otra para `nivel-1/trampa` y otra para `salida` (o combínalas si tu terminal lo permite).

**Resultado esperado:** al listar el contenido de `laberinto/`, ves las carpetas `nivel-1` y `salida`; al entrar a `nivel-1`, ves `nivel-2` y `trampa`; al entrar a `nivel-2`, ves `tesoro`.

### 3. Navega hasta `tesoro` y deja evidencia

Desde `laberinto`, entra paso a paso hasta llegar a `laberinto/nivel-1/nivel-2/tesoro` y, ya ahí, crea un archivo `encontrado.txt`.

**Resultado esperado:** `pwd` (o `ls` desde un nivel arriba) confirma que `encontrado.txt` vive exactamente dentro de `tesoro/`.

### 4. Desde `tesoro`, crea un archivo dentro de `salida` — sin rutas absolutas

Sigues parado en `tesoro`. Sin usar la ruta completa (nada de `C:\Users\...`), crea un archivo `mapa.txt` dentro de `salida/`.

**Pista:** necesitas subir varios niveles con `..` antes de poder bajar a `salida`. Cuenta cuántos niveles hay entre `tesoro` y `laberinto`.

**Resultado esperado:** `mapa.txt` aparece dentro de `laberinto/salida/`, y tu terminal nunca dejó de estar "parada" en `tesoro` hasta que ejecutaste ese comando (es decir, resolviste la ruta relativa, no te moviste primero).

### 5. Regresa a `laberinto` con un solo comando

Desde `tesoro`, vuelve a `laberinto` en una sola llamada a `cd`.

**Resultado esperado:** `pwd` muestra que estás parado directamente en `laberinto/`.

### 6. Documenta tu recorrido

Escribe, en el orden exacto en que los usaste, todos los comandos que te tomó completar los pasos 1 a 5.

## Resultado esperado (estructura final)

```
laberinto/
├── nivel-1/
│   ├── nivel-2/
│   │   └── tesoro/
│   │       └── encontrado.txt
│   └── trampa/
└── salida/
    └── mapa.txt
```

Compara tu resultado contra la carpeta [`resultado-esperado/`](resultado-esperado/) de este mismo ejercicio — tiene la misma estructura con archivos demo genéricos a manera de referencia.

## Checklist de entrega

- [ ] Nunca abrí el explorador de archivos.
- [ ] Creé la estructura completa de carpetas desde la terminal.
- [ ] `encontrado.txt` existe dentro de `tesoro/`.
- [ ] `mapa.txt` existe dentro de `salida/`, creado con una ruta **relativa** desde `tesoro`.
- [ ] Tengo la captura de pantalla de mi terminal completa (que se vea el historial de comandos).
- [ ] Tengo mi lista de comandos, en orden y comentada.

**Entregable:** una captura de pantalla de tu terminal donde se vea el historial completo del ejercicio, más tu lista de comandos comentada. No requiere subir nada a un repositorio — ese flujo lo practicas en el ejercicio [0.2 — Git y GitHub](../0.2-git-github/README.md).

## Reto extra

Borra la carpeta `laberinto` y repite el ejercicio completo, esta vez cronometrado. Menos de 90 segundos de inicio a fin es dominio real de los comandos.
