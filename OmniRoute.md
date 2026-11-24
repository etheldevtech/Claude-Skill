**Install OmniRoute on Ubuntu**

OmniRoute is a free, open-source local AI gateway. It gives you one endpoint (`http://localhost:20128/v1`) that routes requests across many providers (free tiers + paid) with automatic fallback. Works with Claude Code, Cursor, Codex, OpenCode, and any OpenAI-compatible tool.

### 1. Install Node.js (required)

```bash
sudo apt update
sudo apt install -y nodejs npm
```

Or the newer NodeSource version (recommended, Node 22+):

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt install -y nodejs

node --version
npm --version
```

### 2. Install OmniRoute

**Recommended (npm global):**

```bash
npm install -g omniroute
```

**Alternative – pnpm:**

```bash
pnpm add -g omniroute@latest --allow-build=better-sqlite3 --allow-build=@swc/core
```

**Alternative – Docker:**

```bash
docker run -d --name omniroute -p 20128:20128 --restart unless-stopped diegosouzapw/omniroute:latest
```

**From source:**

```bash
git clone https://github.com/diegosouzapw/OmniRoute.git
cd OmniRoute
npm install
npm run dev
```

### 3. Start OmniRoute

```bash
omniroute
```

- Dashboard opens at `http://localhost:20128`
- API base URL: `http://localhost:20128/v1`

Useful flags:

```bash
omniroute --no-open          # don’t open browser
omniroute --port 3000        # custom port
omniroute doctor             # health check
omniroute setup              # guided first-time setup
```

### 4. Connect a provider + create API key

1. Open the dashboard → **Providers**
2. Add at least one provider (API key or account login)
3. Go to **Endpoints / API Keys** → create a new key (save it – it won’t be shown again)

Test:

```bash
curl http://localhost:20128/v1/models -H "Authorization: Bearer YOUR_KEY"
```

### 5. Point your tools at OmniRoute

| Setting   | Value                          |
|-----------|--------------------------------|
| Base URL  | `http://localhost:20128/v1`    |
| API Key   | the key you just created       |
| Model     | `auto` (or any `provider/model`) |

**Claude Code (easiest way):**

```bash
omniroute setup-claude
omniroute launch                    # or
omniroute launch --profile <name>
```

Manual env for Claude Code:

```bash
export ANTHROPIC_BASE_URL=http://localhost:20128
export ANTHROPIC_AUTH_TOKEN=YOUR_KEY
# optional: ANTHROPIC_MODEL=auto
claude
```

**Other tools (one-command setup):**

```bash
omniroute setup-codex
omniroute setup-opencode
omniroute setup-cline
omniroute setup-cursor
# etc.
```

Generic launcher:

```bash
omniroute run claude
omniroute run codex
omniroute run opencode
```

### 6. Uninstall

```bash
npm uninstall -g omniroute
```

Docker:

```bash
docker stop omniroute && docker rm omniroute
```

### Useful commands

| Command                  | What it does                              |
|--------------------------|-------------------------------------------|
| `omniroute`              | Start the gateway                         |
| `omniroute setup`        | Guided onboarding                         |
| `omniroute doctor`       | Local health checks                       |
| `omniroute providers`    | List / test / manage providers            |
| `omniroute status`       | Offline status dashboard                  |
| `omniroute logs`         | Stream usage logs                         |
| `omniroute update`       | Check / apply updates                     |
| `omniroute setup-claude` | Write Claude Code profiles                |
| `omniroute launch`       | Launch Claude Code pointed at OmniRoute   |
| `omniroute --help`       | Full help                                 |

---