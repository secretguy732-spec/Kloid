# Kloid Terminal

<p align="left">
  <img src="https://img.shields.io/badge/version-1.0.24-2ce673?style=flat-square&labelColor=141414" alt="Version" />
  <img src="https://img.shields.io/badge/architecture-single--file_HTML5-38bdf8?style=flat-square&labelColor=141414" alt="Architecture" />
  <img src="https://img.shields.io/badge/UI-minimalist_matte-e5e5e5?style=flat-square&labelColor=141414" alt="UI" />
  <img src="https://img.shields.io/badge/AI-Claude_Code_CLI-f59e0b?style=flat-square&labelColor=141414" alt="Claude Code CLI" />
</p>

**Kloid** is a minimalist, zero-bloat web terminal inspired by **Termux**—featuring a persistent Virtual File System (VFS), an authentic `pkg` / `apt` package manager, real UNIX pipes & redirections, fullscreen TUI editors, and an integrated **Claude Code (`claude`)** agentic CLI with custom `~/.claude/skills/` support.

---

## Features

- **Minimalist Matte Terminal UI**: Flat `#0d0d0d` viewport with a single 32px session bar, multi-tab shell sessions (`+`), and an authentic Termux bottom extra-keys bar (`ESC`, `TAB`, `CTRL`, `ALT`, arrows, and quick symbols).
- **Persistent Virtual File System (VFS)**: Full hierarchical directory structure (`/data/data/com.kloid/files/home`) persisted automatically in `localStorage`.
- **Termux-Style `pkg` / `apt` Manager**: Update repository indexes (`pkg update`), upgrade packages with interactive `[Y/n]` prompts (`pkg upgrade`), and install CLI tools (`pkg install <package>`).
- **Integrated Claude Code CLI (`claude`)**:
  - Interactive REPL (`claude`) and one-shot prompts (`claude -p "<prompt>"`).
  - Agentic VFS inspection (`Glob`, `Read`) and file generation/modification (`Write`, `Edit`) with terminal **unified diffs** (`+` / `-`).
  - Extensible **Skills System** stored as Markdown files in `~/.claude/skills/<name>/SKILL.md`.
- **UNIX Shell Engine**: Supports command chaining (`&&`, `;`), output piping (`|`), file redirection (`>`, `>>`), environment variables (`$HOME`, `$USER`), aliases, and smart `TAB` autocompletion.
- **Zero-Build Single-File Architecture**: Runs directly in any modern browser or deploys seamlessly to GitHub Pages without bundlers or external build steps.

---

## Quick Start

### Run Locally
Clone the repository and open `index.html` in any browser:

```bash
git clone https://github.com/<your-username>/kloid.git
cd kloid
open index.html # or serve with any static HTTP server
```

### Deploy to GitHub Pages
1. Push `index.html` and `README.md` to your GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch** (`main` / `root`).
4. Access your live terminal at `https://github.com/secretguy732-spec/Kloid/`.

---

## Command Reference

### Package Manager (`pkg` / `apt`)
```bash
pkg update                  # Fetch latest repository metadata
pkg upgrade                 # Upgrade outdated packages (claude-code, nano, etc.)
pkg list-all                # View all available packages in the repository
pkg list-installed          # List currently installed packages
pkg search <query>          # Search packages by name or description
pkg show <package>          # Display package version, size, and dependencies
pkg install <package>       # Install a new CLI package
pkg uninstall <package>     # Remove an installed package
```

### Available Packages
| Package | Binaries | Description |
| :--- | :--- | :--- |
| `claude-code` | `claude` | Agentic coding CLI with VFS tools, unified diffs, and `~/.claude/skills` |
| `nano` | `nano` | Fullscreen terminal text editor (`^O` WriteOut, `^X` Exit, `^K` Cut, `^U` Paste) |
| `nodejs` | `node`, `npm` | JavaScript runtime execution (`node file.js`, `node -e "..."`, `npm init`) |
| `python` | `python3`, `python` | Python 3 script execution (`python3 app.py`, `python3 -c "..."`) |
| `git` | `git` | Local version control (`init`, `status`, `add`, `commit`, `log`, `branch`, `diff`) |
| `curl` | `curl` | Real HTTP/HTTPS fetch client (`curl -s https://api.github.com`) |
| `jq` | `jq` | Command-line JSON processor & path extractor (`curl -s ... \| jq .field`) |
| `openssl` | `openssl` | Cryptography toolkit (`rand -hex 16`, `uuid`, `base64`, `dgst -sha256`) |
| `luau` | `luau` | Roblox Luau `--!strict` syntax/type checker & runner |
| `http-server` | `http-server` | Local static HTML preview server (`http-server index.html`) |
| `qrencode` | `qrencode` | Terminal ASCII QR code generator (`qrencode https://github.com`) |
| `htop` | `htop` | Interactive live process & system resource monitor |

---

## Claude Code CLI & Skills (`claude`)

Kloid includes a built-in `claude` CLI capable of reading your workspace, generating/editing files with unified diffs, and loading modular engineering skills from `~/.claude/skills/`.

### CLI Usage
```bash
# Start interactive Claude Code REPL
claude

# Run a single prompt directly from bash
claude "create a strict Roblox Luau player data handler"

# Configure model or custom API key (optional; works offline via local synthesizer too)
claude config set model gemini-3-flash-preview
claude config set apiKey YOUR_API_KEY
```

### Managing Skills (`~/.claude/skills/`)
```bash
claude skill list                                   # List installed & active skills
claude skill search                                 # Browse skills in the registry
claude skill install mcp-builder                    # Install a skill from the registry
claude skill create api-design "RESTful guidelines" # Scaffold a new SKILL.md
claude skill show roblox-luau                       # Inspect a skill's instructions
claude skill remove <name>                          # Delete a skill
```

### Interactive REPL Slash Commands
Inside `claude ❯`:
- `/skills` — List installed and active skills
- `/use <skill-name>` — Toggle a skill on or off in the current session
- `/create-skill <name> "<description>"` — Create and activate a new `SKILL.md`
- `/model [model-name]` — View or switch the active model
- `/clear` — Reset conversation history and terminal output
- `/exit` — Return to the `bash` prompt

---

## UNIX Core Utilities

```bash
ls -la | grep ".js"         # Pipe output between commands
echo "hello" > note.txt     # Overwrite file output
echo "world" >> note.txt    # Append to file output
tree ~                      # Visualize directory hierarchy
find . -name "*.luau"       # Search files by glob pattern
neofetch                    # Display system & package summary
```

---

## License

MIT License — free to use, modify, and self-host.
