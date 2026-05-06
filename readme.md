<div align="center">

# ⬡ ASTROM
### Open-source Windows Antivirus

![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Version](https://img.shields.io/badge/Version-3.2.6-00e5ff?style=for-the-badge)

**Astrom is a fully functional, antivirus for Windows.**
Real detection. Real quarantine. Real protection. No subscriptions. No telemetry. Free forever.

---

</div>

## 🛡️ What is Astrom?

Astrom is a real antivirus — not a toy project. It scans files using multiple detection layers, monitors your filesystem in real time, isolates threats in quarantine, and runs silently from your system tray. Built entirely in Python and not open source.

---

## ⚡ Features

### 🔍 Detection Engine
- **SHA256 Hash Matching** — every file is checked against a database of known malware hashes. If it matches, it's flagged instantly with zero false positives.
- **Multi-Category Heuristic Scanning** — files are analyzed for suspicious behavior patterns across 6 categories:
  - 🔴 Process Injection (`CreateRemoteThread`, `VirtualAllocEx`, `WriteProcessMemory`)
  - 🔴 Privilege Escalation (`SeDebugPrivilege`, `net user /add`)
  - 🔴 Persistence (`CurrentVersion\Run`, `schtasks /create`)
  - 🔴 Obfuscation (`powershell -enc`, `invoke-expression`, base64)
  - 🔴 Network C2 (`WebClient`, `DownloadFile`, `curl http`)
  - 🔴 Self-Deletion (`cmd /c del`, `DeleteFileA`)
  - A file must match **2 or more categories** to be flagged — drastically reducing false positives.
- **Entropy Analysis** — detects packed and encrypted executables (common in ransomware and trojans) by measuring Shannon entropy. Files scoring above 7.2 bits/byte are flagged.

### 📁 Scan Modes
- **Quick Scan** — scans Downloads, Desktop, Documents, and Temp
- **Full Scan** — scans the entire C: drive
- **Custom Scan** — choose any folder

### 👁️ Real-Time Monitoring
- Watches specified folders live using filesystem hooks
- Any new or modified file is automatically scanned the moment it appears
- Configurable monitor paths in Settings

### 🔒 Quarantine System
- Threats are moved to a locked quarantine folder — completely safe from execution
- Original file paths are preserved so files can be **restored** if needed
- Permanent deletion option for confirmed threats

### ✅ Whitelist
- Right-click any flagged file → **Whitelist** to permanently ignore it by hash
- Whitelisted files are never flagged again, even across reboots
- Trusted directories (`C:\Windows\`, `C:\Program Files\`) are always skipped automatically

### 🖥️ Interface
- Sleek dark GUI dashboard with live stats
- System tray integration — minimizes to tray, runs silently in the background
- Full threat log with timestamps, file hashes, detection methods, and threat names
- One-click installer and uninstaller

---

## 📥 Installation

### Installer (recommended, no Python needed)
1. Go to [Releases](../../releases)
2. Download **`Astrom_Installer.exe`**
3. Run it and follow the setup wizard

> ⚠️ Windows may show a SmartScreen warning because Astrom isn't code-signed yet. Click **"More info" → "Run anyway"** to proceed. This is a known limitation of unsigned software.

## 🗺️ Roadmap

- [ ] Auto-update signature database from online feed
- [ ] VirusTotal API integration for cloud lookups
- [ ] Scheduled scans
- [ ] Running process scanner
- [ ] Registry change monitor
- [ ] YARA rule support
- [ ] Code signing certificate

---

## ⚠️ Disclaimer

Astrom is an non-opensource project for educational and personal use. It is not a replacement for a commercial antivirus solution.

## 📄 License

MIT — You may use but you may NOT modify, and distribute without explicit permission.

---

<div align="center">
Made by <a href="https://github.com/the-visual-coder">the-visual-coder</a>
</div>
