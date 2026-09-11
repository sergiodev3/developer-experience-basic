# Ejercicio 0.2 — Git y GitHub: de cero a tu primer Pull Request

> Ejercicio práctico del tema [0.2 en `bloque-0-fundamentos.md`](../../bloque-0-fundamentos.md#02-git-y-github-la-máquina-del-tiempo-de-tu-código-5-hrs).

## Objetivo

Crear un repositorio local, hacer commits descriptivos, protegerlo con `.gitignore`, subirlo a GitHub, y — en parejas — trabajar con ramas, abrir un Pull Request y resolver un conflicto real.

## Duración estimada

Parte A (individual): 45–60 min. Parte B (en parejas): 60–90 min.

## Requisitos previos

- Git instalado (`git --version` debe responder con un número de versión).
- Una cuenta de [GitHub](https://github.com).
- Haber configurado tu identidad una única vez en la máquina:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tucorreo@ejemplo.com"
```

> Usa el mismo correo de tu cuenta de GitHub — así tus commits quedan asociados a tu perfil.

---

## Parte A — Individual

### 1. Crea la carpeta del proyecto desde la terminal

```bash
mkdir git-practica
cd git-practica
```

**Resultado esperado:** estás parado dentro de `git-practica`, una carpeta vacía.

### 2. Inicializa el repositorio

```bash
git init
git branch -M main
```

**Resultado esperado:** `git status` responde `On branch main` y `No commits yet`.

### 3. Crea tu primer archivo y haz el primer commit

Crea un `README.md` con tu nombre (usa tu editor o la terminal), luego:

```bash
git status                      # revisa qué cambió — hazlo siempre antes de add
git add README.md
git commit -m "Agrega README inicial con mi nombre"
```

**Resultado esperado:** `git log --oneline` muestra 1 commit.

### 4. Haz 4 commits más, cada uno con un cambio pequeño

Ejemplos de cambios pequeños y con sentido (no los hagas todos de golpe, uno por commit):

- Agregar una sección "Sobre mí" al `README.md`.
- Crear `src/index.js` con una función genérica de ejemplo.
- Agregar un comentario o mejora a `src/index.js`.
- Crear `notas.md` con lo que aprendiste del bloque 0.1.

Para cada uno:

```bash
git status
git add <archivo>
git commit -m "<mensaje descriptivo en presente>"
```

**Resultado esperado:** `git log --oneline` muestra 5 commits en total, cada uno con un mensaje que explica *qué* cambió sin necesidad de abrir el código (ver la tabla de buenos/malos mensajes en `bloque-0-fundamentos.md`).

### 5. Agrega `.gitignore` y comprueba que funciona

Crea un archivo `.gitignore` con:

```gitignore
node_modules/
.env
```

Después crea un archivo `.env` con el contenido `SECRETO=123` y ejecuta:

```bash
git status
```

**Resultado esperado:** `.env` **no aparece** en la lista de archivos que Git detecta como nuevos — el `.gitignore` lo está ignorando. Si `.env` sí aparece, tu `.gitignore` no está bien escrito o ya habías agregado `.env` a Git antes de crearlo (revisa con `git rm --cached .env` en ese caso).

Haz commit del `.gitignore`:

```bash
git add .gitignore
git commit -m "Agrega .gitignore para proteger .env y node_modules"
```

### 6. Sube tu repositorio a GitHub

Sigue la sección **"Cómo subir tu ejercicio a un repo"** más abajo.

### 7. Captura tu historial

```bash
git log --oneline
```

**Resultado esperado:** una captura de pantalla con tus 5 (o más) commits, en orden, con mensajes descriptivos.

---

## Cómo subir tu ejercicio a un repo

Estos son los pasos generales para conectar cualquier carpeta local con GitHub — los vas a repetir en cada proyecto del curso.

### 1. Crea el repositorio vacío en GitHub

1. Entra a [github.com/new](https://github.com/new).
2. Ponle un nombre (por ejemplo `git-practica`).
3. **No marques** "Add a README file", ni `.gitignore`, ni licencia — el repo debe quedar completamente vacío. Si tu carpeta local ya tiene commits, un README generado por GitHub provoca un conflicto innecesario al primer `push`.
4. Copia la URL que te da GitHub (termina en `.git`).

### 2. Conecta tu carpeta local con ese repositorio

```bash
git remote add origin https://github.com/<tu-usuario>/git-practica.git
git push -u origin main
```

`-u` (upstream) solo se necesita la primera vez: le dice a Git que, de aquí en adelante, `main` local siempre se sincroniza con `main` de `origin`.

**Resultado esperado:** al recargar la página del repositorio en GitHub, ves tus archivos y tu historial de commits.

### 3. De ahí en adelante, cada cambio nuevo

```bash
git status
git add .
git commit -m "Mensaje descriptivo"
git push
```

### 4. Para traer cambios que subiste desde otra máquina, o que subió alguien más

```bash
git pull
```

### Problemas comunes al conectar con GitHub

| Mensaje de error | Qué significa | Cómo resolverlo |
|---|---|---|
| `remote origin already exists` | Ya habías corrido `git remote add origin` antes | Usa `git remote set-url origin <url>` en vez de `add` |
| `Updates were rejected because the remote contains work that you do not have locally` | El repo remoto tiene commits que tu copia local no tiene (por ejemplo, el README que generó GitHub) | `git pull --rebase origin main` y luego `git push` |
| Te pide usuario y contraseña y la contraseña "no funciona" | GitHub ya no acepta tu contraseña de cuenta para `git push` | Usa un [Personal Access Token](https://github.com/settings/tokens) en vez de tu contraseña, o autentica con GitHub CLI (`gh auth login`) |

---

## Parte B — En parejas

### 1. Preparación

- Persona A crea un repositorio nuevo en GitHub (puede ser el mismo `git-practica` u otro) y agrega a Persona B como colaborador: **Settings → Collaborators → Add people**.
- Ambas personas hacen `git clone` de ese repositorio:

```bash
git clone https://github.com/<usuario-A>/<repo>.git
cd <repo>
```

### 2. Cada quien crea su propia rama

Persona A:
```bash
git switch -c feature/nombre-a
```

Persona B:
```bash
git switch -c feature/nombre-b
```

**Resultado esperado:** `git branch` muestra que cada quien está parado en su propia rama, no en `main`.

### 3. Provoquen un conflicto a propósito

Ambas personas editan **la misma línea** del `README.md` (por ejemplo, la línea de la sección "Sobre mí") con contenido distinto, y hacen commit en su propia rama:

```bash
git add README.md
git commit -m "Actualiza sección Sobre mí"
git push -u origin feature/nombre-a    # (o feature/nombre-b)
```

### 4. El primero abre Pull Request y hace merge

En GitHub: **Pull requests → New pull request** → base `main` ← compare `feature/nombre-a` → **Create pull request** → **Merge pull request**.

**Resultado esperado:** `main` en GitHub ahora tiene los cambios de la Persona A.

### 5. El segundo abre su Pull Request: aparece el conflicto

Cuando Persona B abre su PR contra `main`, GitHub va a marcar **"This branch has conflicts that must be resolved"**.

### 6. Resuélvanlo juntos

Localmente, sobre la rama de Persona B:

```bash
git switch feature/nombre-b
git pull origin main
```

Git va a marcar el archivo en conflicto así:

```
<<<<<<< HEAD
(el contenido de la rama de Persona B)
=======
(el contenido que ya está en main, de Persona A)
>>>>>>> main
```

Entre las dos personas: decidan qué línea final es la correcta (puede ser una, la otra, o una combinación de ambas), borren las marcas `<<<<<<<`, `=======` y `>>>>>>>`, guarden el archivo, y:

```bash
git add README.md
git commit -m "Resuelve conflicto en sección Sobre mí"
git push
```

Terminen el merge del Pull Request en GitHub, y agreguen un comentario en el PR explicando qué decidieron y por qué.

## Resultado esperado

- Un repositorio en GitHub con al menos 5 commits individuales (Parte A) con mensajes descriptivos.
- Un `.gitignore` que demuestra proteger `.env` desde antes de que exista el archivo.
- Dos ramas (`feature/nombre-a`, `feature/nombre-b`) que pasaron por Pull Request.
- Un conflicto real, resuelto y documentado en los comentarios del PR.

Revisa [`resultado-esperado/`](resultado-esperado/) de este ejercicio — tiene ejemplos genéricos de cómo debería verse el `README.md`, el `.gitignore` y el historial de commits al terminar la Parte A.

## Checklist de entrega

**Parte A**
- [ ] Repositorio en GitHub con 5+ commits, cada uno con mensaje descriptivo.
- [ ] `.gitignore` protegiendo `.env` desde su propio commit.
- [ ] Captura de `git log --oneline` con los 5 commits.

**Parte B**
- [ ] URL del repositorio compartido.
- [ ] Captura del Pull Request con comentarios.
- [ ] Captura del conflicto resuelto.
- [ ] Un párrafo por cada persona: *"¿qué pasó y cómo lo resolvimos?"*
