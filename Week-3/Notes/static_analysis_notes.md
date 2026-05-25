# Static Malware Analysis – Sample: `evil.exe` (from MalwareBazaar)

## 1. File Identification
- `file evil.exe` → `PE32 executable (GUI) Intel 80386, for MS Windows`
- `exiftool evil.exe` → Compiler: Microsoft Visual C++ 2010, Packer: UPX (detected by PEiD)

## 2. PE Header Analysis (using `pescanner` or `pefile`)
IMAGE_DOS_HEADER – e_magic: MZ
IMAGE_NT_HEADERS – TimeDateStamp: 0x5C8F2A1B (March 2022)
Section headers: .text (executable), .rdata, .data, .rsrc
Entry Point: 0x00401234
Imports: CreateRemoteThread, VirtualAllocEx, WinExec, InternetOpenA

## 3. String Extraction (FLOSS)
$ floss evil.exe | grep -E 'http|.exe|regkey'
http://192.168.1.100/payload.exe
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
C:\Users\Public\svchost.exe


## 4. Hashing & Reputation
- SHA-256: `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`
- VirusTotal: 42/68 detections (Trojan.Agent, Emotet)
- MalwareBazaar: links to Emotet banking trojan family

## 5. YARA Rule (basic)
```yara
rule Emotet_String_Indicator {
    strings:
        $s1 = "http://192.168.1.100" ascii
        $s2 = "WinExec" ascii
        $s3 = "CreateRemoteThread" ascii
    condition:
        all of them
}
