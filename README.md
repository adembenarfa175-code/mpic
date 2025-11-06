# 💥 MPIC-250 x86 Project: Custom Designed 250-bit Processor

This repository holds the **Open Source Software (OSS)** components of the **MPIC-250 x86**, a revolutionary custom-designed processor based on the x86 architecture with an expansive 250-bit data path.

---

## ⚖️ Hybrid Licensing and Security Strategy

The MPIC project utilizes a stringent hybrid licensing model to combine community collaboration with absolute hardware security:

### 🔴 Closed Source (MPIC Closed Source Copyright)

This section contains the critical security core that enforces intellectual property laws and prevents tampering:

* **Code:** `src/core/core\_check.asm`
* **Function:** Serves as the first executed code (BIOS/UEFI replacement), responsible for enabling 250-bit mode and setting up the **Memory Management Unit (MMU)** for security.
* **Defense Mechanism:** Includes the **"Security Guardian"** and **"Catastrophic Alarm"** systems, which initiate **Self-Disable (Fuse-Burning)** upon detecting deliberate infringement.
* **The Law:** **Permanent prohibition** against opening, modifying, or reverse-engineering the closed source code. Violation results in immediate hardware self-destruction and legal consequences.

### 🟢 Open Source (MPIC MIT Open Source)

This repository focuses on community contributions and development for non-critical components:

| Component | Description |
| :--- | :--- |
| **bootloader.c** | The initial C-based bootloader code (loaded after passing the Core-Check). |
| **pcb\_design/** | The Physical design files (Printed Circuit Board and 3D mounting casing). |

---

## ⚙️ Integrated Security Features

The processor is designed to counteract firmware and hardware attacks through a rigorous **Triple Intent Check** logic:

1.  **MMU Protection:** Prevents unauthorized write access to the sensitive `FILECPUROOTUESR.RFC` configuration file.
2.  **Justice Layer:** Distinguishes between **Virus Infection** (Process is killed, but the user is spared) and **Deliberate Tampering** (initiates Self-Destruction).
3.  **Catastrophic Response:** Upon deliberate tampering, the system displays personal warning messages and an image of "guilt," followed by loud, obnoxious noise, a flashing red LED, and the final irreversible **fuse-burning** of the processor's boot path.

---

## 🔌 Hardware I/O Ports (Specifications)

The following I/O ports are allocated for critical security and operational functions:

| Port | Function | Assembly Register |
| :--- | :--- | :--- |
| **0x30** | Disk Controller (For loading guilt image) | `R\_DISK\_PORT` |
| **0x90** | Audio Alarm (Buzzer/Speaker) | `R\_AUDIO\_PORT` |
| **0x91** | Visual Alarm (Red LED) | `R\_LED\_PORT` |
| **0xDEAD** | Self-Destruct Unit (OTP Fuse Controller) | `R\_DESTROY\_PORT` |

