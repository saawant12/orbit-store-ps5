# Install Orbit Zero

Download on your computer and transfer to your PS5 over your home network. Wi-Fi and Ethernet both work, including when one device uses Wi-Fi and the other uses a cable. The PS5 does not need internet access for computer downloads.

This guide accompanies **Orbit Zero 0.1.0-dev.1**, a test build. The Mac app is Developer ID signed but is not yet notarized. Windows and Linux packages are unsigned.

## Choose your download

| Computer | File |
| --- | --- |
| Mac with an Apple M-series chip | `Orbit-Zero-0.1.0-dev.1-mac-arm64.dmg` |
| Mac with an Intel processor | `Orbit-Zero-0.1.0-dev.1-mac-x64.dmg` |
| Windows on Intel or AMD | `Orbit-Zero-0.1.0-dev.1-win-x64.zip` |
| Windows on ARM, including Snapdragon | `Orbit-Zero-0.1.0-dev.1-win-arm64.zip` |
| Ubuntu or Debian on Intel or AMD | `Orbit-Zero-0.1.0-dev.1-linux-amd64.deb` |
| Ubuntu or Debian on ARM64 | `Orbit-Zero-0.1.0-dev.1-linux-arm64.deb` |

On a Mac, check **Apple menu → About This Mac**. On Windows, check **Settings → System → About → System type**. On Linux, run `uname -m`: `x86_64` needs AMD64/x64; `aarch64` needs ARM64. In a virtual machine, choose the build for the guest operating system. 32-bit x86 is not supported.

## macOS

1. Quit any open copy of Orbit Zero.
2. Open the matching `.dmg` and drag **Orbit Zero** into **Applications**. If updating, choose **Replace**.
3. Eject the disk image and open **Orbit Zero** from Applications. Keep using this installed copy rather than launching from the disk image.
4. If macOS says it cannot verify the app, first check that you received this build from Orbit's maintainer. Then open **System Settings → Privacy & Security → Open Anyway** and confirm **Open**. This test build has not been notarized; see [Apple's instructions](https://support.apple.com/en-us/102445).
5. When connecting, allow **Orbit Zero** to access your local network. If you previously denied it, enable Orbit Zero in **System Settings → Privacy & Security → Local Network**, reopen the app, and retry. This permission lets it reach your PS5; it is separate from internet access. [Apple's local-network guidance](https://developer.apple.com/documentation/technotes/tn3179-understanding-local-network-privacy).

Pairing or selecting **Reconnect** may open a Keychain prompt to protect or unlock your saved pairing. Approve the Orbit Zero request if you want to continue; enter your Mac login password only in the macOS prompt if requested. Opening the app just to browse does not unlock Keychain.

## Windows

1. Save the matching ZIP to a folder on the Windows computer, such as **Downloads**.
2. Right-click it and choose **Extract All**. Keep the complete extracted folder together.
3. Open **Orbit Zero.exe** from that folder. Do not launch it from inside the ZIP or copy only the EXE out of the folder.
4. If SmartScreen says **Windows protected your PC**, check that this is the Orbit build you intended to download. For a trusted copy, choose **More info → Run anyway**, if offered. This test build is unsigned. If your organisation or Smart App Control blocks it without that option, contact the maintainer or administrator rather than disabling protection. [Microsoft's SmartScreen guidance](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation).
5. If Windows asks to allow network access, allow **Orbit Zero** on your trusted **Private** home network. This lets the PS5 reach the computer's controls. Firewall approval may require an administrator; the app itself runs as your normal user. [Microsoft's firewall guidance](https://support.microsoft.com/en-us/windows/security/firewall/risks-of-allowing-apps-through-windows-firewall).

There is no installation wizard for the Windows ZIP, and **Run as administrator** is not required. You can create a shortcut to the extracted EXE. To update, quit Orbit Zero, extract the new ZIP into a new folder, and launch that copy. Your saved pairing and queue stay in your Windows user profile.

**Using a virtual machine?** Copy the ZIP onto the Windows filesystem before extracting it. If the shared folder says **Access denied**, transfer the ZIP using the VM's supported file-transfer method or download it inside Windows. Changing Orbit's permissions will not repair the VM's shared-folder connection.

## Ubuntu and Debian

Use the `.deb` installer. It adds Orbit Zero to your application menu and sets up the browser sandbox automatically.

1. Save the matching `.deb` in **Downloads** on the Linux computer, not inside a shared folder.
2. Open a terminal and run **one** of these, matching your processor:

   ```sh
   # Intel / AMD 64-bit
   sudo apt install "$HOME/Downloads/Orbit-Zero-0.1.0-dev.1-linux-amd64.deb"
   ```

   ```sh
   # ARM64
   sudo apt install "$HOME/Downloads/Orbit-Zero-0.1.0-dev.1-linux-arm64.deb"
   ```

3. Enter your Linux password if asked. The installer needs administrator access; characters do not appear while typing the password. Internet access may be needed to install dependencies.
4. Open **Orbit Zero** from your application menu. Do not run the app itself with `sudo`.

If you are updating, quit Orbit Zero and install the new `.deb` the same way. Your saved pairing and queue stay in your user profile. When pairing or reconnecting, Ubuntu may ask you to unlock your login keyring; that stores the pairing securely.

### Other Linux systems or the portable archive

The `linux-x64.tar.gz` and `linux-arm64.tar.gz` files contain the portable app. Distribution compatibility can vary; Ubuntu/Debian users should prefer the installer above.

Extract the **whole archive** onto the Linux filesystem in a path without spaces or parentheses, such as `~/orbit-zero`. From the folder containing the executable, run:

```sh
./orbit-zero
```

If it specifically reports that **chrome-sandbox** is not configured correctly, run these two commands from that same folder, then launch normally:

```sh
sudo chown root:root chrome-sandbox
sudo chmod 4755 chrome-sandbox
./orbit-zero
```

`chrome-sandbox` is the browser engine's security helper. The Ubuntu/Debian installer handles its setup for you. If sandbox or AppArmor errors persist on Ubuntu, use the `.deb` rather than turning sandboxing off. If an old portable copy reports `LaunchProcess: failed to execvp`, move the extracted folder to a path without spaces or use the installer.

## Connect your PS5

1. Keep the computer and PS5 on the same reachable home network. Avoid guest Wi-Fi or network isolation that prevents devices from reaching one another. Keep both devices awake during transfers.
2. On the PS5, start its jailbreak and **Payload Manager** or your usual ELF loader. Orbit Zero does not jailbreak the console.
3. Open **Console** in Orbit Zero and enter the PS5's local IP address.
4. If Orbit is not running, expand **Start Orbit on PS5** and choose the method you use:
   - **Payload Manager → Upload and start Orbit** for its web interface, normally on port **8084**.
   - **ELF loader → Send to ELF loader** for a raw loader, normally on port **9021**.

   Zero supplies the compatible Orbit payload automatically; you do not need to find an ELF yourself. Use **Advanced** only if you changed your loader's port or want to select a custom file. If the compatible Orbit service is already running, skip starting it again.
5. Select **Connect to Orbit**. Its normal service port is **34177**.
6. Select **Show code on PS5**, enter the six-digit code from the console notification, then select **Pair with PS5**. If you miss the notification, request it again after the countdown or open **Pair devices** in Orbit on the PS5.
7. Open a game, choose a source and destination, and start the download. **Downloads** shows the computer download and PS5 transfer separately.

Leave **Console → Download preference → Computer** selected to download through your computer, whether or not the PS5 has internet. Choose **Prefer PS5** to use direct console downloads when the PS5 can reach that source, with the computer as the fallback. This preference applies to new downloads.

After reopening the app, use **Console → Reconnect** for your saved console. For controls in the native PS5 app, install the matching Orbit Store FFPKG supplied with your Zero build, then enable **App settings → Orbit Zero**. Alternatively, open the computer address shown under **Console → How it works** in the PS5 browser.

## If the connection fails

- **Payload Manager opens, but port 9021 is unavailable:** select **Payload Manager**, not ELF loader. Its web interface and the raw ELF loader are different methods.
- **Could not reach Orbit on port 34177:** start Orbit using the steps above, check the PS5's current IP address, and check local-network/firewall permission on the computer.
- **Pairing code is missing:** select **Show code on PS5** and watch for the console notification.
- **No drives appear:** confirm the destination is connected and available to Orbit on the PS5, then refresh the Console view.
- **Transfer stopped after sleep:** wake both devices, reconnect the original console, and select **Resume**. Keep the original pairing to resume unfinished transfers.

For new downloads, leave enough computer space for the full file. Completed files stay in the computer cache until you choose **Remove computer cache**. Keep Orbit Zero open while downloading or transferring.
