# 🔓 PDF Hash Extraction & Dictionary Attack Lab

![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Ethical_Hacking-red?style=for-the-badge)
![Password Cracking](https://img.shields.io/badge/Password_Cracking-Dictionary_Attack-orange?style=for-the-badge)
![Networkwalks](https://img.shields.io/badge/Platform-Networkwalks_Academy-blue?style=for-the-badge)

## 📖 Overview
This repository documents a practical lab focused on password recovery and hash cracking techniques. The exercise demonstrates how attackers extract password hashes from protected files and use dictionary attacks to uncover plaintext passwords, highlighting the critical importance of strong password policies.

## 🛠️ Tools Used
*   **Networkwalks Hash Calculator**: A web-based tool used to extract crackable hashes from protected files (PDFs).
*   **Networkwalks Password Cracker**: A web-based simulation of a dictionary attack tool (similar to John the Ripper or Hashcat).

## 🚀 Step-by-Step Execution

### 1️⃣ Hash Extraction (Hash Calculator)
To crack a password, we first need the hash. Using the Hash Calculator:
*   Uploaded a password-protected PDF (`My Locked PDF1`).
*   The tool parsed the PDF locally and extracted the hash in a **`pdf2john / hashcat` compatible format**.
*   **Extracted Hash Details**: 
    *   Format: `$pdf$4*4*128...`
    *   Revision: R4
    *   Version: V4
    *   Key length: 128 bit

### 2️⃣ Dictionary Attack (Password Cracker)
With the hash in hand, I moved to the Password Cracker tool:
*   Pasted the extracted `$pdf$` hash into the input field.
*   Selected the **Built-in wordlist** (100 common passwords).
*   Initiated the crack. 
*   The tool hashed every word in the list and compared it to the target hash. It successfully cracked the PDF password, revealing it to be **`password1`** after trying 91 out of 100 words.

---

## 💡 Tricks & Tweaks (Password Cracking Pro-Tips)

*   **Understanding the Hash Format**: The `$pdf$` prefix tells you immediately what algorithm and format you are dealing with. Knowing this allows you to use standard tools like John the Ripper (using `pdf2john.py`) or Hashcat.
*   **Why Extract the Hash?**: You don't crack the PDF file itself; you extract the cryptographic hash and attack *that*. It's much faster and easier to process.
*   **The Power of Dictionary Attacks**: Dictionary attacks don't guess randomly; they use lists of previously leaked, common, or predictable passwords. As seen in the lab, `password1` was found almost instantly because it's an incredibly common variation.
*   **Local vs. Online Attacks**: Notice the tool specifies "Nothing is uploaded, the PDF is parsed locally." In real-world red teaming, you extract the hash locally and use massive GPU rigs (like a cracking server with multiple RTX 4090s) to crack the hash offline, bypassing account lockouts entirely.
*   **Beyond the Basics**: While a 100-word list failed to find complex passwords, real-world attackers use lists like `rockyou.txt` (14+ million passwords) combined with rules (e.g., appending numbers or symbols) to crack complex-looking passwords.

## 🛡️ Security Implications & Mitigation
This lab proved how easily weak passwords fall. `password1` took a fraction of a second to crack.
*   **Use Passphrases**: Length beats complexity. "CorrectHorseBatteryStaple" is stronger than "P@ssw0rd1".
*   **Enable MFA**: Even if a password is cracked, Multi-Factor Authentication can prevent unauthorized access.
*   **Password Managers**: Use a manager to generate and store long, random, unique passwords for every service.

## ⚠️ Disclaimer
*This lab was performed using authorized, web-based educational tools provided by Networkwalks Academy. Hash extraction and password cracking must only be performed on systems and files you own or have explicit permission to test.*
