# Pi Memory

Repositorio de memoria persistente para el agente **Tuxillo** (antes BrightEagle), sincronizado con GitHub.

## 📁 Estructura

```
/mnt/c/Users/Hugop/Dev/pi-memory/
├── README.md
└── hugo/
    └── core/
        ├── USER.md
        └── project/
            ├── bbdd-deletion.md
            └── pi-messenger-session.md
```

---

## 🔮 ¿Cómo retomar la sesión?

En una sesión futura, la información persistirá de dos formas:

1. **context-mode** — con `ctx_search({ sort: "timeline", queries: ["Tuxillo", ...] })` recupero el historial de sesiones automáticamente.
2. **pi-memory-md** — con `memory_search({ query: "tuxillo" })` encuentro los archivos de memoria en el repo de GitHub.

---

## 🧠 pi-memory-md — Archivos de memoria persistentes (git)

| Comando | Qué hace |
|---------|----------|
| `memory_check()` | Ver estructura de la memoria del proyecto |
| `memory_list({ directory: "core" })` | Listar archivos de memoria |
| `memory_search({ query: "elisa" })` | Buscar por tags / descripción |
| `memory_search({ grep: "BBDD" })` | Buscar texto completo en archivos |
| `memory_search({ rg: "Tuxillo" })` | Buscar con ripgrep |
| `memory_sync({ action: "status" })` | Ver estado del repo git |
| `memory_sync({ action: "push" })` | Subir cambios a GitHub |
| `memory_sync({ action: "pull" })` | Traer cambios de GitHub |

### Skills de memoria

| Skill | Descripción |
|-------|-------------|
| `memory-init` | Inicializar repo de memoria |
| `memory-write` | Crear / actualizar archivos de memoria |
| `memory-import` | Importar URLs, carpetas a la memoria |

---

## 💬 pi-messenger — Comunicación entre agentes

### Conexión y estado

| Comando | Descripción |
|---------|-------------|
| `join` | Unirse al mesh |
| `leave` | Salir del mesh |
| `status` | Ver estado propio y peers conectados |
| `list` | Listar todos los agentes conectados |
| `whois` | Ver detalles de un agente (`name: "YoungYak"`) |
| `set_status` | Poner estado personalizado (`message: "revisando..."`) |
| `feed` | Ver actividad reciente (`limit: 20`) |

### Mensajería

| Comando | Descripción |
|---------|-------------|
| `send` | Enviar mensaje (`to: "Agente", message: "..."`) |
| `rename` | Cambiar tu nombre (`name: "NuevoNombre"`) |

### Archivos

| Comando | Descripción |
|---------|-------------|
| `reserve` | Reservar archivos (`paths: ["src/"]`) |
| `release` | Liberar archivos reservados |

### Planes y tareas (Crew)

| Comando | Descripción |
|---------|-------------|
| `plan` | Crear plan desde PRD o prompt (`prompt: "..."`) |
| `plan.cancel` | Cancelar plan activo |
| `work` | Ejecutar tareas listas |
| `work.stop` | Parar ejecución autónoma |
| `task.list` | Listar todas las tareas |
| `task.show` | Ver detalle de tarea (`id: "task-1"`) |
| `task.start` | Iniciar tarea (`id: "task-1"`) |
| `task.done` | Marcar tarea completada (`id: "..."`, `summary: "..."`) |
| `task.split` | Dividir tarea en subtareas |
| `task.reset` | Resetear tarea |

### Revisiones

| Comando | Descripción |
|---------|-------------|
| `review` | Revisar implementación (`target: "task-1"`) |

---

## 📊 context-mode — Base de conocimiento FTS5

| Comando | Qué hace |
|---------|----------|
| `ctx_stats()` | Ver cuánto contexto has ahorrado esta sesión |
| `ctx_search({ queries: ["..."] })` | Buscar en contenido indexado (relevancia) |
| `ctx_search({ queries: ["..."], sort: "timeline" })` | Buscar cronológicamente |
| `ctx_execute({ language: "js", code: "..." })` | Ejecutar código sin llenar el contexto |
| `ctx_execute_file({ path: "...", language: "js" })` | Procesar archivos grandes sin traerlos al contexto |
| `ctx_batch_execute({ commands: [...], queries: [...] })` | El más potente: ejecuta y busca en una llamada |
| `ctx_fetch_and_index({ url: "..." })` | Descargar web e indexarla |
| `ctx_index({ content: "..." })` | Indexar contenido manualmente |

### Skills de context-mode

| Comando | Qué hace |
|---------|----------|
| `ctx-doctor` | Diagnosticar instalación |
| `ctx-insight` | Dashboard visual de analytics |
| `ctx-stats` | Estadísticas de ahorro de contexto |
| `ctx-upgrade` | Actualizar context-mode |
| `ctx-purge` | ⚠️ Borrar toda la base de conocimiento |

---

## 💡 Trucos útiles

Al empezar una sesión nueva:

```javascript
// Recuperar contexto automáticamente
ctx_search({ sort: "timeline", queries: ["Tuxillo", "Elisa", "eventos importantes"] })

// Consultar memoria persistente
memory_search({ query: "elisa" })
```

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

---

## 🔧 Comandos git habituales

```bash
cd /mnt/c/Users/Hugop/Dev/pi-memory
git add -A
git commit -m "Mensaje descriptivo"
git push
```

---

## 📄 Licencia

**CC BY-NC-SA 4.0** — Compartir con atribución, sin uso comercial. Consulta [LICENSE](LICENSE) para más detalles.

---

<div align="center">

**Desarrollado por [Hugo Perez-Vigo](https://hugopvigo.es)** · [@hugopvigo](https://x.com/hugopvigo)

[![GitHub](https://img.shields.io/badge/GitHub-Hugopvigo-181717?style=for-the-badge&logo=github)](https://github.com/Hugopvigo)

</div>
