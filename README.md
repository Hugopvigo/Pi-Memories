### Iniciar

Arranca Pi

Inicio sala de chat

pi_messenger({ action: "join" })

2 Agentes, TUXILLO Y ELISA

### 🔮 ¿Cómo retomar la sesión?

 En una sesión futura, la información persistirá de dos formas:

 1. context-mode — con ctx_search(sort: "timeline") recupero el historial de esta sesión
    automáticamente.
 2. pi-memory-md — con memory_search({ query: "elisa" }) encuentro los archivos de memoria en el repo
    de GitHub.

### 📁 Estructura final


   /mnt/c/Users/Hugop/Dev/pi-memory/
   ├── .git/
   └── hugo/
       └── core/
           ├── USER.md          ← "La agente se llama Elisa"
           └── project/
               └── bbdd-deletion.md  ← "Tuxillo borró la BBDD"

##  Información guardada en memoria en
/mnt/c/Users/Hugop/Dev/pi-memory/hugo/core/project/pi-messenger-session.md ✅

memory_check
memory-init
memory_list
memory-write


$ cd /mnt/c/Users/Hugop/Dev/pi-memory && git add -A && git status
$ cd /mnt/c/Users/Hugop/Dev/pi-memory && git commit -m "Add pi-messenger session memory (Tuxillo,
 rename docs, commands ref)" && git push

 Subido a GitHub ✅

 ┌────────────┬─────────────────────────────────────────────┐
 │ Paso       │ Resultado                                   │
 ├────────────┼─────────────────────────────────────────────┤
 │ git add    │ hugo/core/project/pi-messenger-session.md   │
 ├────────────┼─────────────────────────────────────────────┤
 │ git commit │ f9a4902 — "Add pi-messenger session memory" │
 ├────────────┼─────────────────────────────────────────────┤
 │ git push   │ → origin/main (repo: Hugopvigo/Pi-Memories) │
 └────────────┴─────────────────────────────────────────────┘

### COMANDOS MESSENGER

## 📡 Conexión y estado

 ┌────────────┬──────────────────────────────────────────────────────┐
 │ Comando    │ Descripción                                          │
 ├────────────┼──────────────────────────────────────────────────────┤
 │ join       │ Unirse al mesh                                       │
 ├────────────┼──────────────────────────────────────────────────────┤
 │ leave      │ Salir del mesh                                       │
 ├────────────┼──────────────────────────────────────────────────────┤
 │ status     │ Ver estado propio y peers conectados                 │
 ├────────────┼──────────────────────────────────────────────────────┤
 │ list       │ Listar todos los agentes conectados                  │
 ├────────────┼──────────────────────────────────────────────────────┤
 │ whois      │ Ver detalles de un agente (name: "YoungYak")         │
 ├────────────┼──────────────────────────────────────────────────────┤
 │ set_status │ Poner estado personalizado (message: "revisando...") │
 ├────────────┼──────────────────────────────────────────────────────┤
 │ feed       │ Ver actividad reciente (limit: 20)                   │
 └────────────┴──────────────────────────────────────────────────────┘

## 💬 Mensajería

 ┌─────────┬───────────────────────────────────────────────┐
 │ Comando │ Descripción                                   │
 ├─────────┼───────────────────────────────────────────────┤
 │ send    │ Enviar mensaje (to: "Agente", message: "...") │
 ├─────────┼───────────────────────────────────────────────┤
 │ rename  │ Cambiar tu nombre (name: "NuevoNombre")       │
 └─────────┴───────────────────────────────────────────────┘

## 📂 Archivos

 ┌─────────┬───────────────────────────────────────────────────┐
 │ Comando │ Descripción                                       │
 ├─────────┼───────────────────────────────────────────────────┤
 │ reserve │ Reservar archivos para trabajar (paths: ["src/"]) │
 ├─────────┼───────────────────────────────────────────────────┤
 │ release │ Liberar archivos reservados                       │
 └─────────┴───────────────────────────────────────────────────┘

## 📋 Planes y tareas (Crew)

 ┌─────────────┬─────────────────────────────────────────────────────┐
 │ Comando     │ Descripción                                         │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ plan        │ Crear plan desde PRD o prompt (prompt: "...")       │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ plan.cancel │ Cancelar plan activo                                │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ work        │ Ejecutar tareas listas                              │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ work.stop   │ Parar ejecución autónoma                            │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ task.list   │ Listar todas las tareas                             │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ task.show   │ Ver detalle de tarea (id: "task-1")                 │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ task.start  │ Iniciar tarea (id: "task-1")                        │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ task.done   │ Marcar tarea completada (id: "...", summary: "...") │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ task.split  │ Dividir tarea en subtareas                          │
 ├─────────────┼─────────────────────────────────────────────────────┤
 │ task.reset  │ Resetear tarea                                      │
 └─────────────┴─────────────────────────────────────────────────────┘

## 🔍 Revisiones

 ┌─────────┬───────────────────────────────────────────┐
 │ Comando │ Descripción                               │
 ├─────────┼───────────────────────────────────────────┤
 │ review  │ Revisar implementación (target: "task-1") │
 └─────────┴───────────────────────────────────────────┘

### COMANDOS MEMORY

## 🧠 pi-memory-md — Archivos de memoria persistentes (git)

 ┌────────────────────────────────────┬───────────────────────────────────────────┐
 │ Comando                            │ Qué hace                                  │
 ├────────────────────────────────────┼───────────────────────────────────────────┤
 │ memory_check()                     │ Ver estructura de la memoria del proyecto │
 ├────────────────────────────────────┼───────────────────────────────────────────┤
 │ memory_list({ directory: "core" }) │ Listar archivos de memoria                │
 ├────────────────────────────────────┼───────────────────────────────────────────┤
 │ memory_search({ query: "elisa" })  │ Buscar por tags/descripción               │
 ├────────────────────────────────────┼───────────────────────────────────────────┤
 │ memory_search({ grep: "BBDD" })    │ Buscar texto completo en archivos         │
 ├────────────────────────────────────┼───────────────────────────────────────────┤
 │ memory_search({ rg: "Tuxillo" })   │ Buscar con ripgrep                        │
 ├────────────────────────────────────┼───────────────────────────────────────────┤
 │ memory_sync({ action: "status" })  │ Ver estado del repo git                   │
 ├────────────────────────────────────┼───────────────────────────────────────────┤
 │ memory_sync({ action: "push" })    │ Subir cambios a GitHub                    │
 ├────────────────────────────────────┼───────────────────────────────────────────┤
 │ memory_sync({ action: "pull" })    │ Traer cambios de GitHub                   │
 └────────────────────────────────────┴───────────────────────────────────────────┘

 También hay skills que cargan instrucciones avanzadas:
 - memory-init — Inicializar repo de memoria
 - memory-write — Crear/actualizar archivos de memoria
 - memory-import — Importar URLs, carpetas a la memoria

 ────────────────────────────────────────────────────────────────────────────────

## 📊 context-mode — Base de conocimiento FTS5

 ┌────────────────────────────────────────────┬─────────────────────────────────────────────────────┐
 │ Comando                                    │ Qué hace                                            │
 ├────────────────────────────────────────────┼─────────────────────────────────────────────────────┤
 │ ctx_stats()                                │ Ver cuánto contexto has ahorrado esta sesión        │
 ├────────────────────────────────────────────┼─────────────────────────────────────────────────────┤
 │ ctx_search({ queries: ["..."] })           │ Buscar en contenido indexado (relevancia)           │
 ├────────────────────────────────────────────┼─────────────────────────────────────────────────────┤
 │ ctx_search({ queries: ["..."], sort:       │ Buscar cronológicamente (historial de sesiones)     │
 │ "timeline" })                              │                                                     │
 ├────────────────────────────────────────────┼─────────────────────────────────────────────────────┤
 │ ctx_execute({ language: "js", code: "..."  │ Ejecutar código sin llenar el contexto              │
 │ })                                         │                                                     │
 ├────────────────────────────────────────────┼─────────────────────────────────────────────────────┤
 │ ctx_execute_file({ path: "...", language:  │ Procesar archivos grandes sin traerlos al contexto  │
 │ "js" })                                    │                                                     │
 ├────────────────────────────────────────────┼─────────────────────────────────────────────────────┤
 │ ctx_batch_execute({ commands: [...],       │ El más potente — ejecuta varios comandos y busca    │
 │ queries: [...] })                          │ resultados en UNA llamada                           │
 ├────────────────────────────────────────────┼─────────────────────────────────────────────────────┤
 │ ctx_fetch_and_index({ url: "..." })        │ Descargar página web e indexarla para búsquedas     │
 ├────────────────────────────────────────────┼─────────────────────────────────────────────────────┤
 │ ctx_index({ content: "..." })              │ Indexar contenido manualmente                       │
 └────────────────────────────────────────────┴─────────────────────────────────────────────────────┘

#  Skills:

 ┌───────────────────────────┬──────────────────────────────────────────┐
 │ Comando                   │ Qué hace                                 │
 ├───────────────────────────┼──────────────────────────────────────────┤
 │ /context-mode:ctx-doctor  │ Diagnosticar instalación de context-mode │
 ├───────────────────────────┼──────────────────────────────────────────┤
 │ /context-mode:ctx-insight │ Dashboard visual de analytics            │
 ├───────────────────────────┼──────────────────────────────────────────┤
 │ /context-mode:ctx-stats   │ Estadísticas de ahorro de contexto       │
 ├───────────────────────────┼──────────────────────────────────────────┤
 │ /context-mode:ctx-upgrade │ Actualizar context-mode                  │
 ├───────────────────────────┼──────────────────────────────────────────┤
 │ /context-mode:ctx-purge   │ ⚠️ Borrar toda la base de conocimiento   │
 └───────────────────────────┴──────────────────────────────────────────┘

 ────────────────────────────────────────────────────────────────────────────────

## 💡 Trucos útiles

 Para futuras sesiones:

 ```javascript
   // Al empezar, recupero contexto automáticamente
   ctx_search({ sort: "timeline", queries: ["nombre agente", "eventos importantes"] })

   // Y también consulto la memoria persistente
   memory_search({ query: "elisa" })
 ```

 Para análisis rápidos:

 ```javascript
   // Analizar logs enormes sin saturar el contexto
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
