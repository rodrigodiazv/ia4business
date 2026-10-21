<!-- graphify-rules-start (managed by `graphify init`) -->
## Use Graphify before grep

This repository is indexed by Graphify: a code graph over its call, dependency, and test structure, exposed through a connected Graphify MCP server. Before reaching for grep or reading files, use the Graphify tools your MCP client lists (their exact names and descriptions are in the server's tool list) for what the graph knows and a text search does not:

- find where a symbol, function, or class is defined (instead of grepping for it)
- understand how something works, or where a behavior is handled
- find who calls a function, or what it calls
- see what a change affects (its blast radius) and which tests cover it
- map a file's dependencies and dependents

Fall back to grep or file reads only for what the graph does not model: literal string or comment matches, non-indexed files, or reading a file you have already located. If no Graphify tools are listed, check the MCP server connection.
<!-- graphify-rules-end -->

<!-- ahorro-start -->
## Protocolo de ahorro (siempre activo)

Claude no puede ver cuánto saldo queda, así que este protocolo se aplica en todas las sesiones, no solo al final:

1. **Modelo justo para cada tarea:** las tareas mecánicas (búsquedas amplias, resúmenes, traducciones, comprobaciones) se delegan a subagentes con `model: "haiku"` o `"sonnet"`. El modelo principal solo decide y toca código delicado.
2. **Contexto mínimo:** Graphify antes que grep; leer solo las líneas necesarias; nada de reescribir archivos enteros ni repetir lecturas.
3. **Una sola pasada:** agrupar los cambios, probar una vez y abrir un único PR.
4. **Respuestas cortas:** sin repetir lo ya dicho ni pegar salidas largas.
5. **`handoff.md` al día al terminar cada tarea** (objetivo, estado, cambios, intentos fallidos, próximos pasos), para que otro modelo u otra IA continúe si se acaba el saldo.
6. **Avisar antes de una tarea larga** y proponer `/model` (Sonnet o Haiku) para que el usuario cambie de modelo si quiere ahorrar.
7. **Si se agota el saldo:** el usuario abre otra IA (ChatGPT, Gemini, Copilot) con el repo y le dice "Lee handoff.md y continúa desde los próximos pasos". Detalle en el skill `motor-fallback`.
<!-- ahorro-end -->
