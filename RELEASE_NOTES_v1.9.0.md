# T-Terminal v1.9.0

## Highlights

- AI streaming can recover after a mid-response disconnect and continue without discarding the visible answer.
- Stopping an AI task now cancels active MCP tool waits as well as model output.
- AI conversations and streaming state remain isolated when switching terminal tabs.
- SSH uploads support resumable temporary-file transfers, size verification, and atomic replacement.
- Drag-and-drop uploads no longer keep the complete file in memory.
- External editor saves use atomic remote replacement and reconnect after recoverable SSH failures.
- Built-in update checks download releases from GitHub, verify SHA256, replace the executable, and restart the app.
- Per-run AI tool-call limits are configurable and visible during execution.
- Persistent configuration and connection history now live under `%LOCALAPPDATA%\T-Terminal`, outside build and release directories. Legacy portable data is copied on first launch and retained as a fallback.

## Security

- Update installation is blocked when the downloaded executable does not match the published SHA256 file.
- Windows Authenticode signing is supported by the release pipeline when a signing certificate is configured.
- Builds published without a configured certificate remain explicitly documented as unsigned.

## Build

- Platform: Windows x64
- File: `T-Terminal-v1.9.0-windows-x64.exe`
