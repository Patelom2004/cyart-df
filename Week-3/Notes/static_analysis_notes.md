# Static Malware Analysis – Sample: `evil.exe` (from MalwareBazaar)

## 1. File Identification
- `file evil.exe` → `PE32 executable (GUI) Intel 80386, for MS Windows`
- `exiftool evil.exe` → Compiler: Microsoft Visual C++ 2010, Packer: UPX (detected by PEiD)

## 2. PE Header Analysis (using `pescanner` or `pefile`)
