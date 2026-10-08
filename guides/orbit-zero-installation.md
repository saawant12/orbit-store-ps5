# Install Orbit Zero

Download on your computer and transfer to your PS5 over your home network. Wi-Fi and Ethernet both work, including when one device uses Wi-Fi and the other uses a cable. The PS5 does not need internet access for computer downloads.

**PS5 has no internet?** Follow [Set up Orbit on a PS5 without internet](https://github.com/saawant12/orbit-store-ps5/blob/main/guides/orbit-zero-offline-ps5.md) for the full local upload, pairing and optional native-app installation steps.

This guide covers the original **Orbit Zero 1.0.0** downloads and the optional **1.0.1 speed-optimized builds**, both available on the same release page. Choose the files labelled `speed-optimized` if you want to try the download and transfer improvements. The Mac app is Developer ID signed but is not yet notarized. Windows and Linux packages are unsigned.

Get the files from the [Orbit Store 1.0.0 release](https://github.com/saawant12/orbit-store-ps5/releases/tag/v1.0.0).

## Optional speed-optimized builds

If downloads or transfers feel slow, try **Orbit Zero 1.0.1**, labelled `speed-optimized` in the same release's Assets. The original 1.0.0 builds remain available. These optional builds improve the download and local-transfer pipeline and reconnect to your saved PS5 when you reopen the app.

| Computer | Optional file |
| --- | --- |
| Mac with an Apple M-series chip | `Orbit-Zero-1.0.1-speed-optimized-mac-arm64.dmg` |
| Mac with an Intel processor | `Orbit-Zero-1.0.1-speed-optimized-mac-x64.dmg` |
| Windows on Intel or AMD | `Orbit-Zero-1.0.1-speed-optimized-win-x64.zip` |
| Windows on ARM | `Orbit-Zero-1.0.1-speed-optimized-win-arm64.zip` |
| Ubuntu or Debian on Intel or AMD | `Orbit-Zero-1.0.1-speed-optimized-linux-amd64.deb` |
| Ubuntu or Debian on ARM64 | `Orbit-Zero-1.0.1-speed-optimized-linux-arm64.deb` |

1. Pause active transfers and quit Orbit Zero. Install or extract the optional build using the steps for your operating system below. On Ubuntu or Debian, use the optional file's full name, for example `sudo apt install ./Orbit-Zero-1.0.1-speed-optimized-linux-arm64.deb` from its download folder.
2. If Orbit Store is already running on the PS5, select **App settings → Update / reinstall → Stop Orbit to restart** in its browser interface to stop the service.
3. In the new desktop app, open **Console → Start Orbit on PS5** and upload and start its included **1.0.1 receiver**. This step enables the transfer improvements; your PS5 does not need internet. Keep its Payload Manager or ELF loader running.
4. Reconnect if needed, then select **Resume** for paused transfers. Pairing, settings and queues stay saved. You can keep the native PS5 app from the 1.0.0 release.

Use `SHA256SUMS-speed-optimized.txt` to verify these optional downloads. The included receiver's matching source and licences are in `orbit-store-1.0.1-source-bundle.zip`. The standard update feeds continue to offer the original release.

The same first-launch permissions apply. With saved pairing, reopening this version can ask to unlock macOS Keychain or the Linux keyring after the PS5 responds; an offline console does not trigger that prompt.

## Choose your download

The table below lists the **original 1.0.0 builds**. For the optional builds, use the [speed-optimized filenames and update steps above](#optional-speed-optimized-builds). The installation method for each operating system is the same.

| Computer | File |
| --- | --- |
| Mac with an Apple M-series chip | `Orbit-Zero-1.0.0-mac-arm64.dmg` |
| Mac with an Intel processor | `Orbit-Zero-1.0.0-mac-x64.dmg` |
| Windows on Intel or AMD | `Orbit-Zero-1.0.0-win-x64.zip` |
| Windows on ARM, including Snapdragon | `Orbit-Zero-1.0.0-win-arm64.zip` |
| Ubuntu or Debian on Intel or AMD | `Orbit-Zero-1.0.0-linux-amd64.deb` |
| Ubuntu or Debian on ARM64 | `Orbit-Zero-1.0.0-linux-arm64.deb` |

On a Mac, check **Apple menu → About This Mac**. On Windows, check **Settings → System → About → System type**. On Linux, run `uname -m`: `x86_64` needs AMD64/x64; `aarch64` needs ARM64. In a virtual machine, choose the build for the guest operating system. 32-bit x86 is not supported.

## macOS

For the optional build, choose the `1.0.1-speed-optimized` DMG for your Mac's processor from the [download table](#optional-speed-optimized-builds). Follow these same installation steps, then start its included receiver on the PS5.

1. Quit any open copy of Orbit Zero.
2. Open the matching `.dmg` and drag **Orbit Zero** into **Applications**. If updating, choose **Replace**.
3. Eject the disk image and open **Orbit Zero** from Applications. Keep using this installed copy rather than launching from the disk image.
4. If macOS says it cannot verify the app, first check that you received this build from Orbit's maintainer. Then open **System Settings → Privacy & Security → Open Anyway** and confirm **Open**. The Mac app has not been notarized; see [Apple's instructions](https://support.apple.com/en-us/102445).
5. When connecting, allow **Orbit Zero** to access your local network. If you previously denied it, enable Orbit Zero in **System Settings → Privacy & Security → Local Network**, reopen the app, and retry. This permission lets it reach your PS5; it is separate from internet access. [Apple's local-network guidance](https://developer.apple.com/documentation/technotes/tn3179-understanding-local-network-privacy).

Pairing or selecting **Reconnect** may open a Keychain prompt to protect or unlock your saved pairing. The speed-optimized build also reconnects automatically on reopening and may request Keychain access after your saved PS5 responds. Approve the Orbit Zero request if you want to continue; enter your Mac login password only in the macOS prompt if requested.

## Windows

For the optional build, choose the `1.0.1-speed-optimized` ZIP for your processor from the [download table](#optional-speed-optimized-builds). Extract it into a new folder and launch that copy, then start its included receiver on the PS5.

1. Save the matching ZIP to a folder on the Windows computer, such as **Downloads**.
2. Right-click it and choose **Extract All**. Keep the complete extracted folder together.
3. Open **Orbit Zero.exe** from that folder. Do not launch it from inside the ZIP or copy only the EXE out of the folder.
4. If SmartScreen says **Windows protected your PC**, check that this is the Orbit build you intended to download. For a trusted copy, choose **More info → Run anyway**, if offered. The Windows app is unsigned. If your organisation or Smart App Control blocks it without that option, contact the maintainer or administrator rather than disabling protection. [Microsoft's SmartScreen guidance](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation).
5. If Windows asks to allow network access, allow **Orbit Zero** on your trusted **Private** home network. This lets the PS5 reach the computer's controls. Firewall approval may require an administrator; the app itself runs as your normal user. [Microsoft's firewall guidance](https://support.microsoft.com/en-us/windows/security/firewall/risks-of-allowing-apps-through-windows-firewall).

There is no installation wizard for the Windows ZIP, and **Run as administrator** is not required. You can create a shortcut to the extracted EXE. To update, quit Orbit Zero, extract the new ZIP into a new folder, and launch that copy. Your saved pairing and queue stay in your Windows user profile.

**Using a virtual machine?** Copy the ZIP onto the Windows filesystem before extracting it. If the shared folder says **Access denied**, transfer the ZIP using the VM's supported file-transfer method or download it inside Windows. Changing Orbit's permissions will not repair the VM's shared-folder connection.

## Ubuntu and Debian

Use the `.deb` installer. It adds Orbit Zero to your application menu and sets up the browser sandbox automatically.

1. Save the matching `.deb` in **Downloads** on the Linux computer, not inside a shared folder.
2. Open a terminal and run **one** of these, matching your processor:

   ```sh
   # Intel / AMD 64-bit
   sudo apt install "$HOME/Downloads/Orbit-Zero-1.0.0-linux-amd64.deb"
   ```

   ```sh
   # ARM64
   sudo apt install "$HOME/Downloads/Orbit-Zero-1.0.0-linux-arm64.deb"
   ```

3. Enter your Linux password if asked. The installer needs administrator access; characters do not appear while typing the password. Internet access may be needed to install dependencies.
4. Open **Orbit Zero** from your application menu. Do not run the app itself with `sudo`.

**Installing the speed-optimized build?** Use one of these commands instead, matching your processor:

```sh
# Intel / AMD 64-bit
sudo apt install "$HOME/Downloads/Orbit-Zero-1.0.1-speed-optimized-linux-amd64.deb"
```

```sh
# ARM64
sudo apt install "$HOME/Downloads/Orbit-Zero-1.0.1-speed-optimized-linux-arm64.deb"
```

Then follow the [receiver update steps](#optional-speed-optimized-builds) to enable the PS5 transfer improvements.

**Saved the installer somewhere else?** Open a terminal in that folder and include `./` before its filename, for example `sudo apt install ./Orbit-Zero-1.0.0-linux-arm64.deb`. Without `./` or a full path, apt searches its package repositories and reports **Unable to locate package**. If `uname -m` says `aarch64`, use the ARM64 installer; AMD64 is for Intel/AMD computers.

If you are updating, quit Orbit Zero and install the new `.deb` the same way. Your saved pairing and queue stay in your user profile. When pairing or reconnecting, Ubuntu may ask you to unlock your login keyring; that stores the pairing securely.

### Other Linux systems or the portable archive

The `linux-x64.tar.gz` and `linux-arm64.tar.gz` files contain the portable app. Distribution compatibility can vary; Ubuntu/Debian users should prefer the installer above.

Optional portable builds are named `Orbit-Zero-1.0.1-speed-optimized-linux-x64.tar.gz` and `Orbit-Zero-1.0.1-speed-optimized-linux-arm64.tar.gz`. Use the same extraction and launch steps below, then [start the included receiver](#optional-speed-optimized-builds).

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

Keep the computer and PS5 on the same reachable home network. Wi-Fi and Ethernet both work; no internet connection is needed on the PS5. Avoid guest Wi-Fi or network isolation that prevents devices from reaching one another. Keep both devices awake during transfers.

The full-screen examples below show the setup flow. Use your own PS5 address and pairing code; the connection and storage values shown are illustrative.

### Start Orbit on your PS5

1. On the PS5, start its jailbreak and **Payload Manager** or your usual ELF loader. Orbit Zero does not jailbreak the console.
2. Open **Console** in Orbit Zero and enter the PS5's local IP address. Leave **Orbit port** at **34177** unless you changed it.
3. **Start Orbit on PS5** opens automatically while disconnected. Choose the method you use:
   - **Payload Manager → Upload and start Orbit** for its web interface, normally on port **8084**.
   - **ELF loader → Send to ELF loader** for a raw loader, normally on port **9021**.

![Full-screen Orbit Zero Console with the PS5 address and Upload and start Orbit controls](https://raw.githubusercontent.com/saawant12/orbit-store-ps5/main/assets/orbit-zero-development/connect-start.jpg)

Zero supplies the compatible Orbit payload automatically; you do not need to find an ELF yourself. Use **Advanced** only if you changed your loader's port or want to select a custom file. Once the upload finishes, Zero waits for Orbit to start and connects automatically. If Orbit is already running, select **Connect to Orbit** instead of uploading it again.

### Manual fallback: download the ELF yourself

The separate `orbit_store.elf` release asset is the original **1.0.0** service. For the speed-optimized receiver, use the desktop app's normal **Start Orbit on PS5** flow above; it includes **1.0.1** and does not need a separate ELF download.

If you need to select the payload manually:

1. On your **computer**, open the official [Orbit Store GitHub Releases page](https://github.com/saawant12/orbit-store-ps5/releases/latest). Under **Assets**, download **`orbit_store.elf`** and its matching **`orbit_store.elf.sha256`** checksum. Use the compatible Orbit Store build supplied with your Orbit Zero release; Zero requires Orbit Store 1.0.0 or later.
2. Keep Payload Manager or your ELF loader running on the PS5. In Orbit Zero, open **Console**, enter the PS5's local IP address, and expand **Start Orbit on PS5**.
3. Choose **Payload Manager** or **ELF loader**, then expand **Advanced**. Check the loader port: normally **8084** for Payload Manager or **9021** for an ELF loader.
4. Select **Choose another ELF** and choose the downloaded **`orbit_store.elf`**.
5. Select **Send custom ELF**. Zero uploads and starts that file, then waits for Orbit to start and connects automatically. Complete the pairing steps below if asked.

The GitHub download happens on your computer; **the PS5 still does not need internet access**. If replacing an older Orbit service that is already running, first use its **App settings → Update / reinstall → Stop Orbit to restart**, then send the new file. Uploading alone does not replace a running session.

### Pair with your PS5

1. When **Pairing required** appears, select **Show code on PS5**.
2. Enter the six-digit code from the console notification, then select **Pair with PS5**. If you miss the notification, request it again after the countdown or open **Pair devices** in Orbit on the PS5.
3. Allow access to your computer's credential store if prompted, so Zero can save the pairing securely.

![Full-screen Orbit Zero pairing screen with Show code on PS5 and Pair with PS5 controls](https://raw.githubusercontent.com/saawant12/orbit-store-ps5/main/assets/orbit-zero-development/connect-pair.jpg)

If you have already paired this console, Zero restores that pairing when it connects. You do not need a new code unless the pairing has been removed or is no longer valid.

### Check your connection and storage

When the status changes to **Connected**, your available PS5 drives appear under **Storage**. Open a game, choose a source and destination, and start the download. **Downloads** shows the computer download and PS5 transfer separately.

![Full-screen Orbit Zero Console after pairing, showing Connected, download preference and available storage](https://raw.githubusercontent.com/saawant12/orbit-store-ps5/main/assets/orbit-zero-development/connect-ready.jpg)

Leave **Console → Download preference → Computer** selected to download through your computer, whether or not the PS5 has internet. Choose **Prefer PS5** to use direct console downloads when the PS5 can reach that source, with the computer as the fallback. This preference applies to new downloads.

The speed-optimized build reconnects to your saved PS5 when you reopen it. In the original 1.0.0 build, or if automatic reconnection fails, use **Console → Reconnect**. For controls in the native PS5 app, use the **PPSA99177.ffpkg** from the 1.0.0 release with either desktop build, then enable **App settings → Orbit Zero**. Alternatively, open the computer address shown under **Console → How it works** in the PS5 browser.

## If the connection fails

- **Payload Manager opens, but port 9021 is unavailable:** select **Payload Manager**, not ELF loader. Its web interface and the raw ELF loader are different methods.
- **Could not reach Orbit on port 34177:** start Orbit using the steps above, check the PS5's current IP address, and check local-network/firewall permission on the computer.
- **Pairing code is missing:** select **Show code on PS5** and watch for the console notification.
- **No drives appear:** confirm the destination is connected and available to Orbit on the PS5, then refresh the Console view.
- **Transfer stopped after sleep:** wake both devices, reconnect the original console, and select **Resume**. Keep the original pairing to resume unfinished transfers.

For new downloads, leave enough computer space for the full file. Completed files stay in the computer cache until you choose **Remove computer cache**. Keep Orbit Zero open while downloading or transferring.
