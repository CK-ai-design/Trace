---
name: serve
description: Start a local HTTP server to preview index.html with accurate resource loading. Use when you need to test the page with absolute paths or verify network behavior (fonts, layout at different viewport sizes).
disable-model-invocation: true
---

Run a local HTTP server for the Trace landing page.

1. Check if Python is available: run `python --version` or `python3 --version`
2. If Python is available, start the server:
   ```
   python -m http.server 8080
   ```
   from the project directory (`C:\Project with Claude\Trace\Trace pushup  publish\`)
3. Tell the user to open http://localhost:8080 in their browser
4. If Python is not available, suggest: `npx serve .` (requires Node.js) or `npx http-server -p 8080`
5. Remind the user to press Ctrl+C in the terminal to stop the server when done
