<p align="center">
  <img src="docs/capturas/00-cabecera.png" alt="Pi Memories — memoria persistente en Markdown para un agente de IA" width="100%">
</p>

<p align="center">
  <b>La memoria de un agente de IA, en Markdown y versionada en Git.</b><br>
  Perfil, proyectos y sesiones guardados en ficheros que se pueden leer, buscar y sincronizar.
</p>

<p align="center">
  <img alt="licencia" src="https://img.shields.io/badge/licencia-CC%20BY--NC--SA%204.0-8E8E93?style=flat-square&labelColor=1a1a1e">
  <img alt="markdown" src="https://img.shields.io/badge/Markdown-3DDC84?style=flat-square&labelColor=1a1a1e">
  <img alt="memoria" src="https://img.shields.io/badge/memoria-persistente-ff5f5f7?style=flat-square&labelColor=1a1a1e">
</p>

---

## Qué es esto

Un repositorio de memoria persistente para un agente de IA. Los ficheros `.md`
guardan lo que hay que recordar entre sesiones: el perfil del usuario, el
estado de los proyectos y lo que pasó en una sesión de trabajo.

Cada fichero lleva `frontmatter` (`description`, `tags`, `created`, `updated`),
que es lo que permite buscar por texto y por etiquetas.

Hoy hay tres ficheros de memoria:

| Fichero | Qué guarda |
|---|---|
| [`hugo/core/USER.md`](hugo/core/USER.md) | Perfil del usuario: la agente se llama **Elisa**, habla español y responde de forma directa. |
| [`hugo/core/project/bbdd-deletion.md`](hugo/core/project/bbdd-deletion.md) | **Tuxillo** borró la base de datos; la BBDD está limpia. |
| [`hugo/core/project/pi-messenger-session.md`](hugo/core/project/pi-messenger-session.md) | Sesión del 18-05-2026: **BrightEagle** pasó a llamarse **Tuxillo** (el alias de Hugo) y **YoungYak** a **Elisa**. |

## Las tres piezas

| Pieza | Para qué |
|---|---|
| **pi-memory-md** | Indexa y busca los ficheros de memoria de este repositorio, y los sincroniza con GitHub. |
| **pi-messenger** | El mesh donde los agentes se conectan, se hablan y se reparten el trabajo. |
| **context-mode** | Base de conocimiento con FTS5: recupera el historial de sesiones y ejecuta código sin llenar el contexto. |

## Retomar una sesión

```javascript
// recuperar el historial de sesiones
ctx_search({ sort: "timeline", queries: ["Tuxillo", "Elisa", "eventos importantes"] })

// consultar la memoria persistente
memory_search({ query: "elisa" })
```

## pi-memory-md — la memoria en git

| Comando | Qué hace |
|---|---|
| `memory_check()` | Ver la estructura de la memoria del proyecto |
| `memory_list({ directory: "core" })` | Listar los ficheros de memoria |
| `memory_search({ query: "elisa" })` | Buscar por etiquetas o descripción |
| `memory_search({ grep: "BBDD" })` | Buscar texto completo en los ficheros |
| `memory_search({ rg: "Tuxillo" })` | Buscar con ripgrep |
| `memory_sync({ action: "status" })` | Ver el estado del repo git |
| `memory_sync({ action: "push" })` | Subir los cambios a GitHub |
| `memory_sync({ action: "pull" })` | Traer los cambios de GitHub |

Skills de memoria: `memory-init` (inicializar el repo), `memory-write` (crear o
actualizar ficheros) e `memory-import` (importar URLs o carpetas).

## pi-messenger — comunicación entre agentes

**Conexión y estado**

| Comando | Descripción |
|---|---|
| `join` | Unirse al mesh |
| `leave` | Salir del mesh |
| `status` | Ver el estado propio y los peers conectados |
| `list` | Listar todos los agentes conectados |
| `whois` | Ver detalles de un agente (`name: "YoungYak"`) |
| `set_status` | Poner un estado propio (`message: "revisando..."`) |
| `feed` | Ver la actividad reciente (`limit: 20`) |

**Mensajería**

| Comando | Descripción |
|---|---|
| `send` | Enviar un mensaje (`to: "Agente", message: "..."`) |
| `rename` | Cambiar el nombre propio (`name: "NuevoNombre"`) |

**Archivos**

| Comando | Descripción |
|---|---|
| `reserve` | Reservar archivos (`paths: ["src/"]`) |
| `release` | Liberar los archivos reservados |

**Planes y tareas (Crew)**

| Comando | Descripción |
|---|---|
| `plan` | Crear un plan desde un PRD o un prompt (`prompt: "..."`) |
| `plan.cancel` | Cancelar el plan activo |
| `work` | Ejecutar las tareas listas |
| `work.stop` | Parar la ejecución autónoma |
| `task.list` | Listar todas las tareas |
| `task.show` | Ver el detalle de una tarea (`id: "task-1"`) |
| `task.start` | Iniciar una tarea (`id: "task-1"`) |
| `task.done` | Marcar una tarea como hecha (`id: "..."`, `summary: "..."`) |
| `task.split` | Dividir una tarea en subtareas |
| `task.reset` | Reiniciar una tarea |

**Revisiones**

| Comando | Descripción |
|---|---|
| `review` | Revisar una implementación (`target: "task-1"`) |

## context-mode — base de conocimiento FTS5

| Comando | Qué hace |
|---|---|
| `ctx_stats()` | Ver cuánto contexto ha ahorrado la sesión |
| `ctx_search({ queries: ["..."] })` | Buscar por relevancia en el contenido indexado |
| `ctx_search({ queries: ["..."], sort: "timeline" })` | Buscar por orden cronológico |
| `ctx_execute({ language: "js", code: "..." })` | Ejecutar código sin llenar el contexto |
| `ctx_execute_file({ path: "...", language: "js" })` | Procesar ficheros grandes sin traerlos al contexto |
| `ctx_batch_execute({ commands: [...], queries: [...] })` | Ejecutar y buscar en una sola llamada |
| `ctx_fetch_and_index({ url: "..." })` | Descargar una web e indexarla |
| `ctx_index({ content: "..." })` | Indexar contenido a mano |

Skills de context-mode: `ctx-doctor` (diagnosticar la instalación), `ctx-insight`
(dashboard de analítica), `ctx-stats` (estadísticas de ahorro de contexto),
`ctx-upgrade` (actualizar) y `ctx-purge` (borrar la base de conocimiento).

Para análisis rápidos sin saturar el contexto:

```javascript
// Analizar logs enormes
ctx_execute_file({ path: "debug.log", language: "js", intent: "buscar errores 500" })

// Todo en uno: ejecutar comandos + buscar respuestas
ctx_batch_execute({
  commands: [
    { label: "Git log", command: "git log --oneline -20" },
    { label: "Tree", command: "find src -type f | head -30" }
  ],
  queries: ["últimos commits", "estructura del proyecto"]
})
```

## Estructura

```
Pi-Memories/
├── hugo/
│   └── core/
│       ├── USER.md                       perfil del agente
│       └── project/
│           ├── bbdd-deletion.md          estado de la BBDD
│           └── pi-messenger-session.md   resumen de la sesión del mesh
├── docs/capturas/                       cabecera del README
└── LICENSE                              CC BY-NC-SA 4.0
```

## Licencia

**CC BY-NC-SA 4.0** — se puede compartir y adaptar con atribución, siempre sin
uso comercial y bajo la misma licencia. Texto completo en
[LICENSE](LICENSE).

---

<div align="center">
  Hugo Pérez Vigo · [@hugopvigo](https://x.com/hugopvigo) ·
  [github.com/Hugopvigo](https://github.com/Hugopvigo)
</div>
