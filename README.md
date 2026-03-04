# 🔍 Digital Forensics Incident Response — Investigative Report

A university digital forensics assignment in which I conducted a full forensic investigation on two pieces of digital evidence: a hard disk image and a memory dump. The scenario involved a suspect believed to be planning a politically motivated attack. The goal was to uncover, document, and present all relevant digital evidence in a professional investigative report.

---

## 🧰 Tools Used

| Tool | Purpose |
|------|---------|
| **Autopsy 4.22.0** | Hard disk image analysis — file recovery, browser history, OS accounts, cloud directories |
| **Volatility Workbench v2.1** | Memory dump profiling — `pslist`, `pstree`, `psscan` |
| **Volatility Workbench v3.0** | Advanced memory analysis — `netscan`, `hashdump` |
| **MD5Decrypt / NTLM Decrypt** | Credential recovery from extracted password hashes |

---

## 🗂️ Evidence Examined

### Evidence 1 — Hard Disk Image
- **Format:** RAW (DD), 500GB SATA drive
- **Integrity verified via:** MD5 and SHA1 hashing
- **OS:** Windows 10 Education (Eastern Standard Time)

### Evidence 2 — Memory Dump
- **Size:** 17GB
- **Profile:** Windows 10 x64 (Build 16299)
- **Integrity verified via:** MD5 and SHA1 hashing

---

## 🔬 Methodology

1. **Integrity Verification** — Confirmed hash values for both evidence items before examination to ensure no tampering.
2. **Hard Disk Analysis (Autopsy)**
   - Reviewed OS accounts and last login timestamps
   - Examined browser history, web searches, bookmarks, and downloads
   - Inspected the Desktop, Recycle Bin, and cloud-synced directories (Dropbox, Google Drive, OneDrive, Box Sync)
   - Located and documented key files including planning documents, a manifesto, and an attack coordination PowerPoint
   - Identified AWS credentials (`rootkey.csv`) in the Downloads folder, confirming Amazon S3 usage
3. **Memory Analysis (Volatility)**
   - Used `pslist` and `pstree` to enumerate active processes and establish a timeline
   - Used `netscan` to identify active network connections, traced to Virginia via IPv6 geolocation
   - Used `hashdump` to extract NTLM password hashes, subsequently cracked to recover user credentials
4. **Timeline Construction** — Correlated file creation/modification timestamps, browser activity, and process execution times to build a chronological picture of the suspect's activity (March–April 2018).

---

## 📋 Key Findings

- **Manifesto** (`The Cloudy Manifesto.docx`) — A 7-page ideological document expressing the suspect's motivations
- **Attack Plan** (`Operation 2nd Hand Smoke.pptx`) — Detailed slides including target location, escape route, flight booking, and hotel reservation
- **Planning Notes** (`Planning.docx`) — Structured notes covering target selection criteria, weapons, supplies, and escape strategy
- **Browser History** — Searches related to purchasing illegal firearms, police response times, cash smuggling, and Indonesia
- **Cloud Backup Activity** — All key documents were synced across Dropbox, Google Drive, OneDrive, Box Sync, and Amazon S3
- **Credential Recovery** — NTLM hash for the primary user account successfully decrypted, confirming authenticated access during the investigation period
- **Network Evidence** — Active connections traced back to the suspect's known location in Virginia

---

## 📁 Repository Structure

```
digital-forensics-investigation/
├── README.md
├── report/
│   └── Investigative_Report.pdf
└── screenshots/
    └── (evidence screenshots from Autopsy and Volatility)
```

---

## 💡 Skills Demonstrated

- Digital evidence acquisition and integrity verification (MD5/SHA1)
- Disk forensics using Autopsy (file system traversal, browser artefacts, cloud storage analysis)
- Memory forensics using Volatility (process analysis, network forensics, credential extraction)
- Forensic timeline reconstruction
- Professional report writing following digital forensics best practices

---

## ⚠️ Disclaimer

This investigation was conducted as part of a university coursework assignment. All evidence, suspects, and scenarios described are entirely fictional and were provided by the module instructor for educational purposes only. No real individuals were investigated.

---

## 📚 References

- [Autopsy Digital Forensics](https://www.autopsy.com/about/)
- [Volatility Workbench — OSForensics](https://www.osforensics.com/tools/volatility-workbench.html)
- [Volatility Command Reference](https://github.com/volatilityfoundation/volatility/wiki/command-reference)
