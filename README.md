
# 🔐 Networkwalks: Week 3 Project: Password Cracking Using John the Ripper and Networkwalks tools

![Networkwalks](https://img.shields.io/badge/Networkwalks-Cybersecurity%20Program-0A66C2?style=for-the-badge&logo=github&logoColor=white)
![Week 3](https://img.shields.io/badge/WEEK%203-PASSWORD%20CRACKING-8A2BE2?style=for-the-badge)
![John the Ripper](https://img.shields.io/badge/John%20the%20Ripper-Password%20Auditing-CC0000?style=for-the-badge)
![Johnny GUI](https://img.shields.io/badge/Johnny-GUI%20Interface-6A5ACD?style=for-the-badge)
![Windows](https://img.shields.io/badge/Microsoft%20Windows-Environment-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Hash Calculator](https://img.shields.io/badge/Networkwalks-Hash%20Calculator-FF8C00?style=for-the-badge)
![Password Calculator](https://img.shields.io/badge/Networkwalks-Password%20Calculator-228B22?style=for-the-badge)
![Password Security](https://img.shields.io/badge/Password%20Security-Auditing-DC143C?style=for-the-badge)
![Ethical Hacking](https://img.shields.io/badge/Ethical%20Hacking-Authorized%20Testing-6A5ACD?style=for-the-badge)

---

## 📌 Project Overview

This repository documents two related lab exercises completed during **Week 3** of the Networkwalks Cybersecurity & Ethical Hacking Internship. Both labs tackle the same challenge — recovering the password of an encrypted PDF file (`My Locked PDF1.pdf`) — using two different methodologies:

- **Module 1:** Offline password cracking using **John the Ripper (JTR)** and its GUI, **Johnny**.
- **Module 2:** Browser-based password cracking using the **Networkwalks Hash Calculator** and **Password Cracker** tools.

Together, these labs demonstrate how password-protected documents can be assessed for weak or predictable passwords, and why strong password hygiene is essential.

## 🎯 Objectives
- Understand how password protection on files (PDF, ZIP, Office documents) is implemented via hashing.
- Learn how to extract a crackable hash from a password-protected PDF file.
- Perform a dictionary attack to recover the original password using both a dedicated offline tool and lightweight online tools.
- Compare traditional desktop-based cracking tools with modern browser-based alternatives.
- Reinforce awareness of why weak passwords pose a serious security risk.

## 🛠️ Tools Used
| Tool | Purpose |
|---|---|
| [John the Ripper (JTR)](https://www.openwall.com/john/) | Core password cracking engine (dictionary attack) |
| [Johnny](https://openwall.info/wiki/john/johnny) | GUI front-end for John the Ripper |
| [Online Hash Crack – PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) | Extracts a pdf2john-compatible hash from a locked PDF |
| [Networkwalks Hash Calculator](https://networkwalks.com/hash-calculator/) | Browser-based tool to extract the `$pdf$...` hash from a locked PDF |
| [Networkwalks Password Cracker](https://networkwalks.com/password-cracker/) | Browser-based dictionary attack tool |
| Notepad | Used to store the extracted hash in `.txt` format for JTR/Johnny |
| WPS | Used to verify the recovered password by opening the PDF |

## 🧠 Skills Demonstrated
- Password hash extraction from protected PDF documents
- Dictionary-based password cracking (offline and online)
- Configuring and operating John the Ripper via a GUI (Johnny)
- Interpreting and handling hash formats (`$pdf$...`)
- Basic file/hash hygiene (formatting, saving, avoiding corrupted hash strings)
- Comparative analysis of offline vs. browser-based security tools
- Documentation of a structured penetration-testing workflow

## 🔍 Methodology
**Module 1 – John the Ripper / Johnny**
1. Downloaded and installed John the Ripper and Johnny on a Windows PC.
2. Uploaded the locked PDF to an online PDF Hash Extractor to generate a `$pdf$...` hash.
3. Copied the hash and saved it into a text file (`hash1.txt`), ensuring no extraneous characters were included.
4. Configured Johnny to point to the `john.exe` executable.
5. Opened the saved hash file in Johnny via **Open password file**.
6. Launched a dictionary attack using **Start new attack**.
7. Retrieved the cracked password and used it to unlock the PDF in Adobe Acrobat Reader.

**Module 2 – Networkwalks Hash Calculator & Password Cracker**
1. Downloaded the same locked PDF file from the lab page.
2. Uploaded it to the Networkwalks Hash Calculator, which parses the file locally in-browser and outputs a pdf2john/hashcat-compatible hash.
3. Copied the full `$pdf$...` hash value.
4. Pasted the hash into the Networkwalks Password Cracker.
5. Ran the built-in dictionary attack (100-word wordlist).
6. Retrieved the cracked password and verified it by unlocking the PDF.

Both methodologies converged on the same result, validating the hash extraction and confirming the password.

## 💻 Lab Environment
- **Operating System:** Windows (also compatible with Kali Linux, where JTR comes pre-installed)
- **Target File:** `My Locked PDF1.pdf` (password-protected PDF provided for the lab)
- **Network:** Local/offline for Module 1 (after hash extraction); browser-based for Module 2
- **Software:** John the Ripper (Jumbo build), Johnny GUI, Adobe Acrobat Reader DC, web browser

## 📚 Key Learning Outcomes
- Password protection on documents relies on a stored **hash**, not the plaintext password — cracking tools work by hashing guesses and comparing them to this value.
- A short, common, or predictable password (e.g. `password1`) can be cracked almost instantly with a small dictionary, even without a wordlist of millions of entries.
- The same cracking outcome can be reached through very different tool stacks — a mature offline utility (John the Ripper) or a lightweight browser-based tool — showing that strong tooling knowledge matters more than any single application.
- Hash extraction accuracy (e.g. not truncating or corrupting the `$pdf$...` string) is critical; a malformed hash will cause the cracking attempt to fail even with a correct password in the wordlist.

## 🛡️ Security Perspective
From a defensive standpoint, these labs highlight:
- **Why weak passwords are a critical vulnerability** — password-protected files are only as strong as the password chosen, regardless of the encryption algorithm behind them.
- **The importance of long, random, unique passwords** (ideally generated by a password manager) to resist dictionary and brute-force attacks.
- **The dual-use nature of security tools** — the same tools and techniques used here by security professionals to test weak passwords can be misused by attackers, underscoring the need for authorization and ethical boundaries in all penetration testing work.
- **Defense-in-depth**: sensitive documents should not rely on password protection alone; additional controls (access management, encryption at rest, secure sharing channels) reduce risk if a password is cracked.

## ⚠️ Challenges Faced
- **Malformed hash output:** When copying the hash from the online extractor, extra characters (e.g. a leading `b'`) were sometimes included, causing John/Johnny to fail to parse the hash correctly.
- **Locating the correct executable:** Johnny required manually browsing to the `john.exe` file inside the `run` folder of the John the Ripper Jumbo build, which was not immediately obvious for a first-time setup.
- **Tool configuration:** Ensuring Johnny was correctly linked to a valid John the Ripper executable before an attack could be started.

## ✅ How It Was Resolved
- Carefully re-copied and cleaned the hash value in Notepad, verifying it started exactly with `$pdf$` and contained no stray characters, before saving it as a `.txt` file.
- Used Windows File Explorer to navigate directly to the `run` subfolder of the extracted John the Ripper Jumbo package to locate `john.exe`, then set this path in Johnny's Settings tab.
- Confirmed successful configuration by checking that Johnny displayed the detected John the Ripper version before starting the attack, avoiding wasted attack attempts on a misconfigured setup.

## 🔐 Ethical Use
These exercises were carried out in a **controlled lab environment**, using a file specifically provided for training purposes as part of an authorized cybersecurity internship curriculum. The techniques demonstrated in this repository are intended **strictly for educational purposes and authorized security testing** on systems or files you own or have explicit permission to test.

Unauthorized password cracking or accessing protected files without consent is illegal and unethical. This repository is shared purely to document learning progress and technical skills developed during the internship.


👤 Author
Atemlefac Nkafu Bechem

Cybersecurity Engineer

LinkedIn: https://www.linkedin.com/in/atemlefac-nkafu-bechem-179987248

# 📌 Project Information
Program Name: Cybersecurity at Networkwalks | Week: 03 | Project: password cracking using john the ripper and netwalks tools | Repository: GitHub

## 🏫 Credit
Labs completed as part of the **Networkwalks Academy** Cybersecurity & Ethical Hacking training program.
🔗 [www.networkwalks.com](https://www.networkwalks.com)
