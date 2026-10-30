# Install games without leaving Orbit

**Available in 1.5.0 and later.** Keep the Orbit app you use and its running PS5 service on the [same release](getting-started.md#which-files-to-download). The native FFPKG includes that service; Zero can upload its included copy. Refreshing the catalogue alone does not add installation controls.

## Install a downloaded game

1. Finish downloading or transferring the game to your PS5. Orbit extracts ZIP, RAR and 7z downloads first.
2. Open the completed entry in **Downloads** and choose **Downloaded files** or **Install on PS5**.
3. If it contains several packages, choose the one you want to install.
4. Select **Install on PS5** and follow its installation status.

The same controls are available in the browser, native PS5 app and Orbit Zero, in all four interfaces. Downloading and installation have separate progress: a finished download means the files are saved, not that the game is installed.

The PS5 uses its configured installation storage. Choosing a download drive does not choose the installation drive. Allow space for both copies during installation. Downloaded PKG/FPKG files stay on the drive by default.

In **1.6.0**, enable **App settings → Storage & cleanup → Installed packages** to delete a downloaded package after installation succeeds. This is off by default. If installation fails or the file changed after it was checked, Orbit keeps it. This setting does not delete Zero’s computer copy or extracted non-package files. Archive cleanup and Zero’s computer-cache cleanup have their own settings.

In **1.7.5**, Orbit also shows firmware requirements found in supported metadata after extraction, in Downloads and before installation. Unknown requirements are not confirmation of compatibility.

Installation needs a compatible PS5 setup. It does not change a game's firmware, licence or jailbreak requirements. Orbit does not launch games or uninstall them.

## Install from Files

In **1.7.0**, open **Library → Files**, select a package or a folder’s **…** menu, and choose **Install on PS5**. Compatible images and game folders use ShadowMount. See [Files](files.md).

## Install from Orbit Zero

You can download to **This computer** without a connected PS5. When ready, pair or reconnect your PS5 and choose **Send to PS5**. After the transfer finishes, open **Downloaded files** and choose **Install on PS5**.

In **1.7.0**, you can instead choose **Stream & install** for a completed computer package, avoiding the extra PS5 download copy. See [streaming installation](stream-install.md).

Installation runs on the paired PS5, not on your computer. Keep the console awake and its matching Orbit service running. The computer-to-PS5 transfer and installation controls use your local network; downloading new content still requires provider access on the computer.

## exFAT, FFPFSC and game folders

These use ShadowMount instead of the package installer. After a new download or transfer completes, Orbit **automatically requests a scan** when a compatible ShadowMount version is running with its local API enabled. It also handles compatible `.ffpkg` images this way; an `.ffpkg` image is different from an FPKG `.pkg` package.

You do not normally need to run a scan yourself. Orbit checks ShadowMount's inventory before showing the game as registered. A scan request alone is not confirmation that registration succeeded.

If ShadowMount was unavailable, start it, open the completed download's details and choose **Scan with ShadowMount** when offered. Orbit does not start ShadowMount or change its configuration. Older completed downloads are not all rescanned automatically when you update Orbit; use **Library → Scan for games** to look for existing compatible files.

### LZ4 game files

For an [LZ4 download](downloads.md#lz4-games), Orbit extracts the outer archive and keeps the game’s LZ4 assets intact. Use a compatible game loader for the resulting files. The LZ4 label does not turn those assets into an installable package or confirm support on your console.

## Add-ons and bundles

Find DLC on **Add-ons**, or use **Add-ons (count)** from a game’s details. See [the DLC guide](add-ons.md) for the content types and download choices.

Review the required base-game edition, title ID and known version requirements before installing DLC. A matching title ID alone does not confirm compatibility, and seeing the base game in Library does not mean its DLC is installed.

For a bundle, select and install each package you intend to use. Orbit does not install the whole bundle automatically, fetch missing game updates or choose the installation order. Activation packages require their content to already be present in the base game.

## If installation needs attention

- **The button is missing:** check the running ELF as well as the app version. For ordinary installation the file must have finished reaching the PS5; Zero’s **Stream & install** uses the completed computer copy. Images and game folders use ShadowMount, including the **Install on PS5** action in Files.
- **The original drive is unavailable:** reconnect the drive containing the downloaded file. Orbit keeps the download's original location rather than selecting a different copy.
- **The installer reports an error:** follow the message and check space, package compatibility and your jailbreak. The downloaded file is kept for another attempt.
- **Installation status is unconfirmed:** use **Check installation** when offered and check the PS5 home screen. Orbit does not automatically submit an uncertain installation again after a restart or lost response.
- **A scanned game is missing:** check ShadowMount's status and the saved file path. See the [Library guide](library.md).

For a report, include the Orbit app and service versions, game or add-on, format, destination and exact installation or scan error. Keep the files while investigating.
