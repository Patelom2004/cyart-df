
### 3.3 `dynamic_analysis_notes.md`

```markdown
# Dynamic Analysis – Sample: `evil.exe` (ANY.RUN sandbox)

## Environment: FlareVM (Windows 10 guest, isolated network)

### Observed Behavior
- **Process creation**: `evil.exe` spawned `cmd.exe /c powershell -EncodedCommand ...`
- **File system changes**: Created `C:\ProgramData\updater.exe` (copy of itself)
- **Registry modifications**:  
  `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run` → `updater`
- **Network connections** (Wireshark):
  - DNS query for `evil-cc.com`
  - HTTP POST to `http://evil-cc.com/beacon` with User-Agent "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
- **API calls** (ProcMon): `CreateFile`, `WriteFile`, `RegSetValue`, `InternetOpen`

### Extracted IOCs
- Domains: `evil-cc.com`, `update.trusted.org`
- IPs: `45.33.22.11`
- SHA-256: `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`

### MITRE ATT&CK Mapping
- T1059.003 – Command and Scripting Interpreter: PowerShell
- T1547.001 – Boot/Logon Autostart Execution: Registry Run Keys
- T1071.001 – Application Layer Protocol: Web Protocols
