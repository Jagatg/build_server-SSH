# Unlock Bootloader on Xiaomi Android Go (MediaTek) Devices

> [!NOTE] **Tested on:** Redmi A1 (`ice`)
>
> This guide should work on most **Xiaomi Android Go devices powered by
> MediaTek (MTK)**. However, it has not been tested on every model.

## Overview

Most Xiaomi devices require an official bootloader unlock request using
the Mi Unlock Tool.

However, Android Go-based Xiaomi MediaTek devices do not support the
standard unlock procedure. Instead, we can use **MTK Client** to unlock
the bootloader through **BootROM Mode**.

> [!WARNING] Although this method **normally does not wipe user
> data**, it is strongly recommended to **back up all important files**
> before proceeding.
>
> You are responsible for anything that happens to your device.


---


## Requirements

-   Linux (**Recommended**)
-   macOS or Windows
-   Python 3
-   MTK Client
-   USB cable
-   Xiaomi Android Go device with a MediaTek chipset


---


## Installing MTK Client

Follow the official installation guide:

https://github.com/bkerler/mtkclient/blob/main/README-INSTALL.md

Open a terminal:

``` bash
Ctrl + Alt + T
```

Navigate to your MTK Client directory.


---


## Step 1: Connect the Device in BootROM Mode

Run:

``` bash
sudo python3 mtk.py printgpt
```

Then:

1.  Power off the device completely.
2.  Press and hold **Volume Up + Volume Down**.
3.  While holding both buttons, connect the USB cable.
4.  Keep holding until MTK Client detects the device and executes the
    exploit.

If everything is successful, the GPT partition table will be printed.


---


## If You Get Stuck at `Sending emi data...`

> [!NOTE] This issue is more commonly seen on **EU firmware**. Devices
> running the **Indian firmware** usually do **not** encounter this
> problem.

When the process gets stuck at `Sending emi data...`, the device may
continuously loop in **BootROM mode**.

To fix this:

1.  Press and hold **Volume Up + Power** for about **30 seconds**. This
    should force the device to release **BootROM mode**.
2.  If that doesn't work, disconnect the battery, wait **5 seconds**,
    then reconnect it.
3.  If disconnecting the battery isn't possible, let the battery drain
    completely.

After that, download the Fastboot ROM from the link below. Extract the
`preloader*.bin` file and place it anywhere on your PC.

https://xmfirmwareupdater.com/miui/ice/stable/V13.0.17.0.SGMINXM/

Then run:

``` bash
sudo python3 mtk.py printgpt --preloader /path/to/preloader.bin
```

Replace `/path/to/preloader.bin` with the actual path to your extracted
`preloader*.bin` file.

Once the command completes successfully, continue with the next step.


---


## Step 2: Unlock the Bootloader

Run:

``` bash
sudo python3 mtk.py da seccfg unlock
```

Wait until the process finishes.

Then reboot the device:

``` bash
sudo python3 mtk.py reset
```


---


## Step 3: Boot into Fastboot Mode

1.  Disconnect the USB cable.
2.  Hold **Volume Down + Power** until the **Fastboot** screen appears.
3.  Reconnect the device to your computer.

Run:

``` bash
fastboot oem cdms
```

Then:

``` bash
fastboot reboot
```


---


## Verify the Bootloader Status

Once the device boots and the **Mi** logo appears, look at the
top-center of the screen.

If you see an **🔓 unlocked** icon, your bootloader has been
successfully unlocked.

🎉 **Congratulations!**


---


## Relocking the Bootloader

Flash the stock Fastboot ROM:

``` bash
./flash_all.sh
```

Reboot into Fastboot Mode and run:

``` bash
fastboot oem lock
```


---

## Credits

- **MTK Client** by bkerler
- Android modding community
- **Special thanks to [Ishu43642](https://github.com/Ishu43642) for the bootloader unlock method.**
