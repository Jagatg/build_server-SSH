# Unlock Bootloader on Xiaomi Android Go (MediaTek) Devices

> [!NOTE]
> **Tested on:** Redmi A1 (`ice`)
>
> This guide should work on most **Xiaomi Android Go devices powered by MediaTek (MTK)**. However, it has not been tested on every model.

## Overview

Most Xiaomi devices require an official bootloader unlock request using the Mi Unlock Tool.

However, Android Go-based Xiaomi MediaTek devices do not support the standard unlock procedure. Instead, we can use **MTK Client** to unlock the bootloader through **BootROM Mode**.

> [!WARNING]
> Although this method **normally does not wipe user data**, it is strongly recommended to **back up all important files** before proceeding.
>
> You are responsible for anything that happens to your device.

---

## Requirements

- Linux (**Recommended**)
- macOS or Windows
- Python 3
- MTK Client
- USB cable
- Xiaomi Android Go device with a MediaTek chipset
