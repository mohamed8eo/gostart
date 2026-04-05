# GoStart

> Bootstrap Go projects in seconds. Search and install packages without leaving your terminal.

---

## The Problem

Every time you start a Go project, you do the same thing:

1. Create `cmd/`, `internal/`, `pkg/`, `config/` manually
2. Stop coding mid-flow to Google a package URL, copy it, run `go get`
3. Repeat forever

GoStart eliminates both.

---

## Install

```bash
go install github.com/mohamed8eo/gostart@latest
```

Or download a prebuilt binary (no Go required) from the [releases page](https://github.com/mohamed8eo/gostart/releases).

**Requirements:** Go 1.21+ · Git

---

## Usage

### Scaffold a new project (interactive TUI)

```bash
gostart init
```

### Scaffold with flags (no TUI)

```bash
gostart init my-api --framework Gin --database PostgreSQL --sql GORM
```

| Flag | Options |
|------|---------|
| `--framework` / `-f` | `Gin`, `Echo`, `Fiber`, `Chi`, `None` |
| `--database` / `-d` | `PostgreSQL`, `MySQL`, `SQLite`, `MongoDB`, `None` |
| `--sql` / `-s` | `GORM`, `sqlx`, `sqlc`, `pgx`, `None` |

### Generated structure

```
my-project/
├── cmd/
│   ├── api/
│   │   └── main.go          # API server entry point
│   └── worker/
│       └── main.go          # Background worker entry point
├── internal/
│   ├── auth/                # Authentication logic
│   ├── storage/             # Database/storage layer
│   └── transport/           # HTTP handlers/transports
├── pkg/
│   ├── logger/              # Shared logging utilities
│   └── crypto/              # Cryptographic helpers
├── api/
│   └── openapi.yaml         # API specification
├── config/
│   └── config.yaml          # Configuration files
├── scripts/
│   └── deploy.sh            # Deployment scripts
├── go.mod
└── README.md
```

---

### Search and install packages (interactive)

```bash
gostart add
```

- Type to search (e.g. `jwt`, `redis`, `argon2`)
- Browse results with star counts
- Select with a keystroke — installs via `go get` automatically

![gostart add demo](https://github.com/user-attachments/assets/335ed0c4-0bef-4f3a-9b9f-856b0f8cd706)

**Requires a GitHub token** (zero scopes needed — public search only):

1. Go to [github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. Note: `gostart-cli` · Expiration: your choice · **Scopes: none**
3. Generate and add to your shell:

```bash
# Fish
echo 'set -x GITHUB_TOKEN "your_token"' >> ~/.config/fish/config.fish

# Bash/Zsh
echo 'export GITHUB_TOKEN="your_token"' >> ~/.bashrc
```

---

## Features

- **Interactive TUI** — Bubble Tea powered wizard for project setup
- **Framework support** — Gin, Echo, Fiber, Chi, or stdlib
- **Database integration** — PostgreSQL, MySQL, SQLite, MongoDB
- **SQL drivers** — GORM, sqlx, sqlc, pgx
- **Package search** — find and install Go packages without a browser
- **Production-ready layout** — consistent structure across all your projects

---

## Contributing

```bash
git clone https://github.com/mohamed8eo/gostart.git
cd gostart
go mod download
go build .
```

PRs welcome. Areas to contribute:

- Docker / CI-CD template generation
- pkg.go.dev integration for package search (replace GitHub search)
- More framework support (Beego, Revel)
- Tests for TUI components

See [CONTRIBUTING.md](CONTRIBUTING.md) or open an issue.

---

## Built with

- [Cobra](https://github.com/spf13/cobra) — CLI framework
- [Bubble Tea](https://github.com/charmbracelet/bubbletea) — TUI framework
- [Bubbles](https://github.com/charmbracelet/bubbles) — TUI components
- [Lip Gloss](https://github.com/charmbracelet/lipgloss) — terminal styling

---

## License

[MIT](LICENSE)
