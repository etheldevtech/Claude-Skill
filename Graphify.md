**Install Graphify**

### 1. Install uv (recommended)
```bash
# macOS
brew install uv

# Linux / macOS (official installer)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows
winget install astral-sh.uv
```

Then open a **new terminal** and check:
```bash
uv --version
```

### 2. Install Graphify
```bash
uv tool install graphifyy
```

Alternatives:
```bash
pipx install graphifyy
# or
pip install graphifyy
```

Verify:
```bash
graphify --version
```

If `graphify` is not found after `uv tool install`, run:
```bash
uv tool update-shell
```
Then open a new terminal.

### 3. Register the skill with your coding assistant
```bash
graphify install
```

This detects your assistant (Claude Code is the default).  
For a specific platform:
```bash
graphify install --platform claude      # Claude Code
graphify install --platform codex       # Codex (use $graphify)
graphify cursor install                 # Cursor
graphify vscode install                 # VS Code / Copilot Chat
# …and many others (20+ supported)
```

Optional project-scoped install:
```bash
graphify install --project
```

### 4. Use it
Open a repository in your assistant and run:
```
/graphify .
```

Output appears in `graphify-out/`:
- `graph.html` – interactive graph
- `GRAPH_REPORT.md` – architecture summary
- `graph.json` – machine-readable graph

Common commands:

| Command | What it does | Sample |
| --- | --- | --- |
| `/graphify .` | Build graph for current folder | `/graphify .` |
| `/graphify . --update` | Re-scan only changed files | `/graphify . --update` |
| `/graphify . --mode deep` | Deeper multi-pass extraction | `/graphify . --mode deep` |
| `graphify query "…"` | Ask a question about the graph | `graphify query "what connects auth to the database?"` |

### 5. Uninstall
```bash
uv tool uninstall graphifyy
# or
pipx uninstall graphifyy
# or
pip uninstall graphifyy
```