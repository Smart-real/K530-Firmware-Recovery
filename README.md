# ⌨️ K530-Firmware-Recovery
### *Hardware-Level Restoration of corrupted MCU Firmware*

![Status](https://img.shields.io/badge/Status-Recovered-success.svg)
![Method](https://img.shields.io/badge/Method-DFU_Injection-orange.svg)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

## 🎯 The Situation
Standard software update tools failed after a corrupted firmware flash, leaving the K530 unbootable and unrecognized by the OS. Local technicians deemed the logic board "unfixable." This project documents the successful recovery using a **First-Principles** engineering approach.

## 🛠️ Execution Roadmap
- [x] **Analyze Hardware:** Identified the MCU and located the physical boot-pins.
- [x] **Datasheet Verification:** Confirmed the Hardware Bootloader Trigger sequence.
- [x] **DFU Injection:** Initiated recovery mode by shorting specific GPIO pins during power-cycle.
- [x] **Firmware Restoration:** Manually flashed the OEM binary via low-level USB-HID interface.
- [x] **Validation:** Restored 100% functionality of the key matrix and RGB controller.

---

## 🕵️‍♂️ Technical Breakdown

### **The "Unbricking" Logic**
When the application layer of a microcontroller (MCU) is corrupted, it cannot process USB commands. By reading the MCU datasheet, I identified a hardware "backdoor"—the **Bootloader Mode**. 

**Recovery Pin Mapping:**
| Component | Function | Action Taken |
| :--- | :--- | :--- |
| **Microcontroller** | System Brain | Identified via visual inspection of PCB |
| **Boot-Pins** | Hardware Trigger | Shorted to GND to bypass corrupted OS |
| **USB-HID** | Recovery Path | Forced PC to recognize device in DFU mode |


### **Results**
By forcing the hardware into its native bootloader state, I was able to bypass the "unresponsive" status and push a clean firmware image directly to the chip's memory, saving the hardware from a landfill.

---

## 📜 License
This project is licensed under the **MIT License**.

*Resurrected by **Aoun Raza***
