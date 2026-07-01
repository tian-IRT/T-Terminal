# T-Terminal

T-Terminal is an AI-assisted terminal management tool for Windows. This repository is the public release page for downloadable builds.

> Source code is not open at this time. Only official binary releases are published here.

## Download

Download the latest Windows build from the GitHub Releases page.

Current build:

- `T-Terminal-v1.8.0-windows-x64.exe`

## Features

- Local terminals: PowerShell, CMD, Bash, WSL
- SSH terminal sessions and connection management
- SFTP file browser, drag-and-drop upload, and local editor sync
- AI assistant with terminal context, chat mode, operation mode, and session history
- Docker helper panel
- SSH tunnel and host-proxy outbound access for isolated SSH hosts
- Server report generation and PDF export

## Integrity Check

Each release includes a `.sha256` file. On Windows PowerShell:

```powershell
Get-FileHash .\T-Terminal-v1.8.0-windows-x64.exe -Algorithm SHA256
```

Compare the output with `T-Terminal-v1.8.0-windows-x64.exe.sha256`.

## Notes

- Windows may show a SmartScreen warning for unsigned executables.
- API keys, SSH credentials, and terminal settings are stored locally by the app.
- Please only download builds from this official release page.

## License

T-Terminal is distributed as proprietary freeware. See `LICENSE`.
