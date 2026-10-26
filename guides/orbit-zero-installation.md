# Install Orbit Zero

Download on your computer and transfer to your PS5 over your home network. Wi-Fi and Ethernet both work, including when one device uses Wi-Fi and the other uses a cable. The PS5 does not need internet access for computer downloads.

This guide covers **Orbit Zero 1.7.0**. Get the files from the [Orbit Store release](https://github.com/saawant12/orbit-store-ps5/releases/latest).

- **Installing for the first time?** Follow this guide in order: choose and verify your download, install it on your computer, then connect your PS5.
- **Already using Orbit Zero?** Go to [Update Orbit Zero](#update-orbit-zero).
- **PS5 has no internet?** Follow [Set up Orbit on a PS5 without internet](https://github.com/saawant12/orbit-store-ps5/blob/main/guides/orbit-zero-offline-ps5.md) for the full local upload, pairing and optional native-app installation steps.

## Choose your download

| Computer | File |
| --- | --- |
| Mac with an Apple M-series chip | `Orbit-Zero-1.7.0-mac-arm64.dmg` |
| Mac with an Intel processor | `Orbit-Zero-1.7.0-mac-x64.dmg` |
| Windows on Intel or AMD | `Orbit-Zero-1.7.0-win-x64.exe` (installer) or `Orbit-Zero-1.7.0-win-x64.zip` (portable) |
| Windows on ARM, including Snapdragon | `Orbit-Zero-1.7.0-win-arm64.exe` (installer) or `Orbit-Zero-1.7.0-win-arm64.zip` (portable) |
| Ubuntu or Debian on Intel or AMD | `Orbit-Zero-1.7.0-linux-amd64.deb` |
| Ubuntu or Debian on ARM64 | `Orbit-Zero-1.7.0-linux-arm64.deb` |

Not sure which one you need? On a Mac, check **Apple menu → About This Mac**. On Windows, check **Settings → System → About → System type**. On Linux, run `uname -m`: `x86_64` needs AMD64/x64; `aarch64` needs ARM64. In a virtual machine, choose the build for the guest operating system. 32-bit x86 is not supported.

The Mac app is Developer ID signed but is not yet notarized. Windows and Linux packages are unsigned. The installation steps below explain the security prompts this can cause.

## Verify your download

Download **`SHA256SUMS`** from the same release as your desktop package. It contains a SHA-256 checksum for each package. Compute the checksum of the file you downloaded using one of the commands below, replacing the filename if you chose a different build.

**macOS, in Terminal:**

```sh
shasum -a 256 "$HOME/Downloads/Orbit-Zero-1.7.0-mac-arm64.dmg"
```

**Windows, in PowerShell:**

```powershell
Get-FileHash "$env:USERPROFILE\Downloads\Orbit-Zero-1.7.0-win-x64.zip" -Algorithm SHA256
```

**Linux, in a terminal:**

```sh
sha256sum "$HOME/Downloads/Orbit-Zero-1.7.0-linux-amd64.deb"
```

Open `SHA256SUMS` in a text editor and find the line with the **exact same filename**. Its 64-character checksum must match your result; uppercase and lowercase letters are equivalent. If it differs, download the file again before installing. You only need the package for your computer, not every file listed in `SHA256SUMS`.

The PS5 ELF and FFPKG have their own `.sha256` files; see [verify the PS5 files](getting-started.md#verify-the-ps5-files) for those.

## Install on your computer

Follow the steps for your operating system. Each section also covers the permission and security prompts you may see the first time you open the app.

### macOS

1. Quit any open copy of Orbit Zero.
2. Open the matching `.dmg` and drag **Orbit Zero** into **Applications**. If updating, choose **Replace**.
3. Eject the disk image and open **Orbit Zero** from Applications. Keep using this installed copy rather than launching from the disk image.
4. If macOS says it cannot verify the app, first check that you received this build from Orbit's maintainer. Then open **System Settings → Privacy & Security → Open Anyway** and confirm **Open**. The Mac app has not been notarized; see [Apple's instructions](https://support.apple.com/en-us/102445).
5. When connecting, allow **Orbit Zero** to access your local network. If you previously denied it, enable Orbit Zero in **System Settings → Privacy & Security → Local Network**, reopen the app, and retry. This permission lets it reach your PS5; it is separate from internet access. [Apple's local-network guidance](https://developer.apple.com/documentation/technotes/tn3179-understanding-local-network-privacy).

**Keychain prompts.** Pairing or selecting **Reconnect** may open a Keychain prompt to protect or unlock your saved pairing. Approve the Orbit Zero request to continue, and enter your Mac login password only in the macOS prompt if asked. When you reopen the app, it checks your saved PS5 and may unlock Keychain to reconnect. You won't see a Keychain prompt while the console is offline.

### Windows

**Installer (normal installation)**

1. Download the `.exe` matching your processor.
2. Quit Orbit Zero, then run the installer. Check any Windows security prompt against the file you downloaded from the official release.
3. Open Orbit Zero from the Start menu.

**Portable ZIP**

The installer is optional. The ZIP has no installation wizard, and **Run as administrator** is not required.

1. Save the matching ZIP to a folder on the Windows computer, such as **Downloads**.
2. Right-click it and choose **Extract All**. Keep the complete extracted folder together.
3. Open **Orbit Zero.exe** from that folder. Do not launch it from inside the ZIP or copy only the EXE out of the folder. You can create a shortcut to the extracted EXE.

**Security and network prompts (installer or ZIP)**

- If SmartScreen says **Windows protected your PC**, check that this is the Orbit build you intended to download. For a trusted copy, choose **More info → Run anyway**, if offered. The Windows app is unsigned. If your organisation or Smart App Control blocks it without that option, contact the maintainer or administrator rather than disabling protection. [Microsoft's SmartScreen guidance](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation).
- If Windows asks to allow network access, allow **Orbit Zero** on your trusted **Private** home network. This lets the PS5 reach the computer's controls. Firewall approval may require an administrator; the app itself runs as your normal user. [Microsoft's firewall guidance](https://support.microsoft.com/en-us/windows/security/firewall/risks-of-allowing-apps-through-windows-firewall).

**Using a virtual machine?** Copy the ZIP onto the Windows filesystem before extracting it. If the shared folder says **Access denied**, transfer the ZIP using the VM's supported file-transfer method or download it inside Windows. Changing Orbit's permissions will not repair the VM's shared-folder connection.

### Ubuntu and Debian

Use the `.deb` installer. It adds Orbit Zero to your application menu and sets up the browser sandbox automatically.

1. Save the matching `.deb` in **Downloads** on the Linux computer, not inside a shared folder.
2. Open a terminal and run **one** of these, matching your processor:

   ```sh
   # Intel / AMD 64-bit
   sudo apt install "$HOME/Downloads/Orbit-Zero-1.7.0-linux-amd64.deb"
   ```

   ```sh
   # ARM64
   sudo apt install "$HOME/Downloads/Orbit-Zero-1.7.0-linux-arm64.deb"
   ```

3. Enter your Linux password if asked. The installer needs administrator access; characters do not appear while typing the password. Internet access may be needed to install dependencies.
4. Open **Orbit Zero** from your application menu. Do not run the app itself with `sudo`.

**Saved the installer somewhere else?** Open a terminal in that folder and include `./` before its filename, for example `sudo apt install ./Orbit-Zero-1.7.0-linux-arm64.deb`. Without `./` or a full path, apt searches its package repositories and reports **Unable to locate package**. If `uname -m` says `aarch64`, use the ARM64 installer; AMD64 is for Intel/AMD computers.

**Keyring prompts.** When pairing or reconnecting, Ubuntu may ask you to unlock your login keyring; that stores the pairing securely.

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

## Set up the app

### Choose your language

Select the globe-shaped **Language** button in Store’s top bar, or **Settings → Language** in Crossbar, Cinema or Panorama. Orbit Zero 1.7.0 supports English, German, Spanish, French, Hungarian, Italian, Dutch, Polish, Brazilian Portuguese, Russian and Turkish. Choose **System language** to follow your computer. This changes Orbit’s interface, not a downloaded game’s language.

### Choose your interface

Use the palette-shaped **Appearance** button in Store’s top bar to choose Store, Crossbar, Cinema or Panorama. After switching, select **Keep** within 15 seconds. In the other layouts, return to **Settings → Appearance** to change it again. See the [appearance guide](appearance.md) for previews and motion/background options. Your choice is saved separately from the PS5 app’s appearance.

## Download without connecting a PS5

You can start downloading straight away. Open a game, choose its download option and select **Save to → This computer**. No pairing or running PS5 service is needed. When the download finishes, use **Show in folder** to find it. Connect your PS5 later and choose **Send to PS5** in Downloads when you want to transfer the saved game. See [download now and send later](orbit-zero.md#download-now-and-send-to-your-ps5-later).

## Connect your PS5

Keep the computer and PS5 on the same home network. Wi-Fi and Ethernet both work; no internet connection is needed on the PS5. Avoid guest Wi-Fi or network isolation that prevents devices from reaching one another. Keep both devices awake during transfers.

The screenshots below show the setup flow. Use your own PS5 address and pairing code; the connection and storage values shown are examples.

### Start Orbit on your PS5

1. On the PS5, start its jailbreak and **Payload Manager** or your usual ELF loader. Orbit Zero does not jailbreak the console.
2. Open **Console** in Orbit Zero and enter the PS5's local IP address. Leave **Orbit port** at **34177** unless you changed it.
3. **Start Orbit on PS5** opens automatically while disconnected. Choose the method you use:
   - **Payload Manager → Upload and start Orbit** for its web interface, normally on port **8084**.
   - **ELF loader → Send to ELF loader** for an ELF loader, normally on port **9021**.

![Orbit Zero 1.5.0 Console with connection and Start Orbit on PS5 controls](../assets/1.5.0/zero-console.jpg)

Orbit Zero includes the matching Orbit payload, so you do not need to find an ELF yourself. Use **Advanced** only if you changed your loader's port or want to select a custom file. Once the upload finishes, Zero waits for Orbit to start and connects automatically. If Orbit is already running, select **Connect to Orbit** instead of uploading it again.

Prefer to download the ELF yourself? See [Manual fallback: download the ELF yourself](#manual-fallback-download-the-elf-yourself).

### Pair with your PS5

1. When **Pairing required** appears, select **Show code on PS5**.
2. Enter the six-digit code from the console notification, then select **Pair with PS5**. If you miss the notification, request it again after the countdown or open **Pair devices** in Orbit on the PS5.
3. Allow access to your computer's credential store if prompted, so Zero can save the pairing securely.

![Full-screen Orbit Zero pairing screen with Show code on PS5 and Pair with PS5 controls](https://raw.githubusercontent.com/saawant12/orbit-store-ps5/main/assets/orbit-zero-development/connect-pair.jpg)

If you have already paired this console, Zero restores that pairing when it connects. You do not need a new code unless the pairing has been removed or is no longer valid.

### Check your connection and storage

When the status changes to **Connected**, your available PS5 drives appear under **Storage**.

![Full-screen Orbit Zero Console after pairing, showing Connected, download preference and available storage](https://raw.githubusercontent.com/saawant12/orbit-store-ps5/main/assets/orbit-zero-development/connect-ready.jpg)

You're ready to download. In Browse, use **Platform** to choose PS4, PS5 or both. Open a game, choose a source and destination, and start the download. PS4 packages use the same transfer controls. **Downloads** shows the computer download and PS5 transfer separately.

In **1.5.0**, after the files reach the console, open **Downloads → Downloaded files** and choose **Install on PS5** for a PKG/FPKG. Use the matching desktop app and PS5 service. Compatible exFAT, FFPFSC and game folders automatically request a ShadowMount scan when it is running. See [installing downloaded games](install-games.md).

### Choose where downloads run

Leave **Console → Download preference → Computer** selected to download through your computer, whether or not the PS5 has internet. Choose **Prefer PS5** to use direct console downloads when the PS5 can reach that source, with the computer as the fallback. This preference applies to new downloads.

### Reconnect and control from the PS5

After reopening the app, Orbit Zero reconnects to your saved console automatically. If the PS5 is offline or credential access is declined, use **Console → Reconnect** when ready.

For controls in the native PS5 app, install the matching Orbit Store FFPKG from the same release, then enable **App settings → Orbit Zero**. Alternatively, open the computer address shown under **Console → How it works** in the PS5 browser.

## If the connection fails

- **Payload Manager opens, but port 9021 is unavailable:** select **Payload Manager**, not ELF loader. Its web interface and the ELF loader are different methods.
- **Could not reach Orbit on port 34177:** start Orbit using the steps above, check the PS5's current IP address, and check local-network/firewall permission on the computer.
- **Pairing code is missing:** select **Show code on PS5** and watch for the console notification.
- **No drives appear:** confirm the destination is connected and available to Orbit on the PS5, then refresh the Console view.
- **Transfer stopped after sleep:** wake both devices, reconnect the original console, and select **Resume**. Keep the partial files. If the console’s address or pairing changed, follow [address and pairing recovery](orbit-zero.md#reconnect-after-an-address-change). If it holds up the queue, compare [Resume, Cancel and remove partials, and Stop transfer](orbit-zero.md#pause-reconnect-and-clean-up); a transfer ended with **Stop transfer** cannot resume afterward.

For new downloads, leave enough computer space for the full file. Keep Orbit Zero open while downloading or transferring.

## Manual fallback: download the ELF yourself

Orbit Zero includes the matching payload, so this is optional. To download and select the ELF yourself:

1. On your **computer**, open the official [Orbit Store GitHub Releases page](https://github.com/saawant12/orbit-store-ps5/releases/latest). Under **Assets**, download **`orbit_store.elf`** and its matching **`orbit_store.elf.sha256`** checksum. Use the same release as your Orbit Zero build and [verify the checksum](getting-started.md#verify-the-ps5-files). The matching service is needed for current transfer, DLC and installation features.
2. Keep Payload Manager or your ELF loader running on the PS5. In Orbit Zero, open **Console**, enter the PS5's local IP address, and expand **Start Orbit on PS5**.
3. Choose **Payload Manager** or **ELF loader**, then expand **Advanced**. Check the loader port: normally **8084** for Payload Manager or **9021** for an ELF loader.
4. Select **Choose another ELF** and choose the downloaded **`orbit_store.elf`**.
5. Select **Send custom ELF**. Zero uploads and starts that file, then waits for Orbit to start and connects automatically. Complete the [pairing steps](#pair-with-your-ps5) if asked.

The GitHub download happens on your computer; **the PS5 still does not need internet access**. If replacing an older Orbit service that is already running, first use its **App settings → Update / reinstall → Stop Orbit to restart**, then send the new file. Uploading alone does not replace a running session.

## Download settings

![Orbit Zero 1.5.0 download settings with simultaneous download and recovery controls](../assets/1.5.0/zero-download-settings.jpg)

*Download settings in Orbit Zero 1.5.0.*

### Choose how many games download at once

In **Downloads → Download settings → Simultaneous computer downloads**, choose **1–8**. Crossbar, Cinema and Panorama also offer **Settings → Download settings**, with cache cleanup under **Settings → Computer cache**. The default is **1**. Files transfer to your PS5 one at a time while computer downloads continue. Lowering the limit lets current downloads finish before another starts. Keep enough space for each file's full computer copy.

### Choose the computer download folder

Open **Console → Computer download folder → Choose folder**, or open the settings icon beside the **Downloads** title and select **Choose folder**. The choice applies to downloads from every source. New downloads and downloads with no saved bytes use the selected folder; existing partial downloads stay in their original folder so they can resume. Keep that drive connected until its downloads and transfers are finished.

### Clear completed computer copies

In **Downloads → Download settings → Computer cache**, turn on **Automatically remove after transfer** to remove future computer copies after the PS5 confirms a successful transfer. This is off by default.

To clear copies already completed, select **Clear completed cache**, review the amount to remove, then confirm. You can also use **Remove computer cache** on one completed download. Files on your PS5, active or paused downloads, unrelated files in the folder and download history are kept. If cleanup fails because a drive is missing or a file is locked, reconnect or unlock it and retry.

For compressed downloads, **Delete archives after extracting** is a separate setting and is on by default. It removes the archive after successful extraction. The extracted computer files remain until you remove their cache or enable **Automatically remove after transfer**.

## Vikingfile, AkiraBox and archive downloads

### Vikingfile downloads

Select a Vikingfile option on the game's download page. Zero first uses your saved [Vikingfile sign-in](vikingfile.md) to request the file. A matching direct link starts the download without a window. If a provider window opens, complete any verification yourself, then **wait without pressing Download**. Orbit Zero captures the ready file link, checks it against your selection and closes the provider window. Follow the download in Downloads.

Unwanted popup windows are blocked. Use **Back**, **Reload** or **Return to download page** if you need to return to the file page.

### AkiraBox downloads

Select an AkiraBox option and open its provider window. Complete any verification yourself, then **wait without pressing the Download button**. Orbit Zero captures the ready file link, checks it and closes the provider window. You can follow the download in Downloads.

### Refresh an expired download link

If a paused or failed Vikingfile or AkiraBox download needs a new link, select **Refresh download link**. The PS5 can stay disconnected while you refresh the computer download’s link. The partial file is reused only if the new link identifies the same file. Reconnect the PS5 when you are ready to transfer.

### Compressed downloads

ZIP, RAR and 7z files extract on your computer before their contents transfer to the PS5. Keep space for the archive and extracted files. Known source passwords are tried automatically; use **Enter archive password → Retry extraction** if a different password is needed. This does not download the archive again. See [archive downloads and cleanup](downloads.md#zip-rar-and-7z-downloads).

## Update Orbit Zero

Updating has two parts: replace the desktop app, then start its matching service on your PS5. Your pairing and queue stay saved.

### Update checks in Orbit Zero

Select **Updates** in Store’s top navigation, or **Settings → Updates** in the other interfaces, to see your installed version or check manually. **Check for updates automatically** is on by default: Orbit Zero checks its official GitHub release on opening and every six hours, reusing a recent check when available. You can turn this off in the same window.

When **Update available** appears, select **Download update**. Zero selects the package for your operating system and processor, then checks its size and SHA-256 before offering **Open installer** (Mac/Linux) or **Open ZIP** (Windows). You can cancel an update download without affecting game transfers.

### Install the desktop update

Installation remains your choice. Finish or pause transfers and quit Orbit Zero before replacing it, using the installer or archive for your computer.

- **Mac:** drag the app from the DMG into Applications and choose **Replace**.
- **Windows:** run the new installer, or extract the new ZIP into a new folder and launch **Orbit Zero.exe** from that copy. Your saved pairing and queue stay in your Windows user profile.
- **Ubuntu/Debian:** install the new `.deb` the same way as above, or open it with your package installer. Your saved pairing and queue stay in your user profile. Other Linux distributions can use the portable archive on GitHub.

### Update the PS5 service

1. In Orbit Store on the PS5, stop the running service under **App settings → Update / reinstall → Stop Orbit to restart**.
2. Open the new desktop app and use **Console → Start Orbit on PS5** to upload and start its included 1.7.0 service. The PS5 does not need internet for this step.
3. Select **Resume** for any paused transfers.

Install the matching native FFPKG if you use Orbit Store from the PS5 Games row. It includes the same updated service. Uploading a new ELF or replacing the FFPKG does not replace a session that is already running, so stop the old service first.

<a id="optional-speed-optimized-builds"></a>

### Coming from the optional speed-optimized builds

The download and transfer improvements from the earlier optional builds are now included in the standard packages. Follow the update steps above; you no longer need a separate speed-optimized download.

## Connections per download

In **Download settings → Connections per download**, choose **1–64**, with eight as the default. More connections help only when the provider and network allow them. Orbit can retry with fewer connections when a host refuses. This is separate from the simultaneous-game setting.
