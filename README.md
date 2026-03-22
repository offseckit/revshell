# revshell

Reverse shell generator CLI — generate one-liners in 12+ languages.

Part of [OffSecKit](https://offseckit.com) | [Browser version](https://offseckit.com/tools/revshell)

## Install

```bash
pip install offseckit-revshell
```

## Usage

```bash
# Basic — bash reverse shell
revshell -i 10.10.10.10 -p 4444

# Python reverse shell
revshell -i 10.10.10.10 -l python

# Specific variant
revshell -i 10.10.10.10 -l netcat -v nc-mkfifo

# Base64 encoded
revshell -i 10.10.10.10 -l bash -e base64

# URL encoded (for command injection)
revshell -i 10.10.10.10 -l python -e url

# Show all variants for a language
revshell -i 10.10.10.10 -l php --all

# List all languages and variants
revshell list
```

## Supported Languages

| Language | Variants |
|----------|----------|
| Bash | bash-i, bash-196, bash-udp, bash-readline, bash-5 |
| Python | python3-short, python3-1, python3-2, python2 |
| PowerShell | powershell-1 |
| PHP | php-exec, php-shell-exec, php-popen |
| Ruby | ruby-1 |
| Perl | perl-1 |
| Netcat | nc-e, nc-c, nc-mkfifo, ncat |
| Socat | socat-1 |
| Java | java-runtime |
| Lua | lua-1 |
| Node.js | node-1, node-2 |
| Groovy | groovy-1 |

## Encoding Options

- `raw` — No encoding (default)
- `base64` — Base64 encode the payload
- `url` — URL encode the payload
- `double-url` — Double URL encode (bypasses single-decode filters)

## License

MIT
