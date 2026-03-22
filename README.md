# >_ osk revshell

**Generate reverse shell one-liners in 12+ languages from your terminal.**

Part of [OffSecKit](https://offseckit.com) | [Browser version](https://offseckit.com/tools/revshell) | [Unified CLI](https://github.com/offseckit/cli)

## Install

This tool is part of the OffSecKit CLI toolkit:

```bash
pip install offseckit
```

## Usage

```bash
# Generate a bash reverse shell
osk revshell -i 10.10.10.10 -p 4444

# Python reverse shell
osk revshell -i 10.10.10.10 -l python

# Base64 encoded for filter evasion
osk revshell -i 10.10.10.10 -l bash -e base64

# Show all PHP variants
osk revshell -i 10.10.10.10 -l php --all

# List all supported languages
osk revshell list
```

### Options

| Flag | Description | Default |
|------|-------------|---------|
| `-i, --ip` | Attacker IP address | (required) |
| `-p, --port` | Attacker port | `4444` |
| `-l, --lang` | Language | `bash` |
| `-v, --variant` | Specific variant | first available |
| `-e, --encoding` | `raw`, `base64`, `url`, `double-url` | `raw` |
| `--all` | Show all variants | — |
| `--no-listener` | Hide listener command | — |

### Supported Languages

| Language | Variants |
|----------|----------|
| **Bash** | `bash-i`, `bash-196`, `bash-udp`, `bash-readline`, `bash-5` |
| **Python** | `python3-short`, `python3-1`, `python3-2`, `python2` |
| **PowerShell** | `powershell-1` |
| **PHP** | `php-exec`, `php-shell-exec`, `php-popen` |
| **Ruby** | `ruby-1` |
| **Perl** | `perl-1` |
| **Netcat** | `nc-e`, `nc-c`, `nc-mkfifo`, `ncat` |
| **Socat** | `socat-1` |
| **Java** | `java-runtime` |
| **Lua** | `lua-1` |
| **Node.js** | `node-1`, `node-2` |
| **Groovy** | `groovy-1` |

## Related

- [OffSecKit CLI](https://github.com/offseckit/cli) — full toolkit (`pip install offseckit`)
- [Browser version](https://offseckit.com/tools/revshell) — use in your browser
- [Reverse Shell Cheat Sheet](https://offseckit.com/blog/reverse-shell-cheat-sheet) — full guide

## License

MIT
