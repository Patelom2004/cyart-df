# Tool Cheatsheet

| Tool | Purpose | Basic Command / Workflow |
|------|---------|---------------------------|
| **FTK Imager** | Create forensic disk images | File → Create Disk Image → Select source → Select image type (E01, DD) → Add hashing (SHA-256) |
| **Autopsy** | Disk image analysis | Create new case → Add data source → Run modules (Timeline, Keyword Search, File Carving) |
| **Wireshark** | Packet capture / analysis | Capture → Select interface → Apply display filter (e.g., `http.request`) |
| **RegRipper** | Windows Registry extraction | `rip.exe -r SYSTEM -f system` → outputs CSV |
| **HashMyFiles** | Hash file(s) MD5/SHA-256 | Drag & drop file – copy hash for reputation lookup |
| **Velociraptor** | Endpoint forensics live queries | Deploy client → `VQL` query: `SELECT * FROM pslist()` |
