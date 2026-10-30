# When something needs attention

Settings paths below use the default Store layout. In the browser’s other interfaces, use the [Settings page equivalents](appearance.md#find-settings-after-switching).

## Opening and updating Orbit

### I see two Orbit icons

That's normal if you use both PS5 versions. The icon in **Games** is the TV app from `PPSA99177.ffpkg`. The icon in **Media** is the browser version, added when `orbit_store.elf` runs. Both use the same downloads, favourites and service settings. Appearance is saved separately for each app or browser.

If the Media icon won't open, see the next section. If the Games icon won't open, see [The native TV app will not open or start Orbit](#the-native-tv-app-will-not-open-or-start-orbit).

### Orbit or its icon does not open

Start the Orbit payload through your manager, then reopen the Media-tab icon. The icon opens a running Orbit server and cannot start a stopped payload. If the icon was deleted, starting Orbit recreates it. Keep Orbit’s saved data when updating.

From another device, use `http://<ps5-ip>:34177/` on the same local network. Keep that port private to your LAN.

### The native TV app will not open or start Orbit

The Games-row app needs **kstuff and ShadowMountPlus**. Check that `PPSA99177.ffpkg` is in `/data/homebrew/` and let ShadowMountPlus register it. Keep only one FFPKG or folder installation.

If the app says Orbit is not running, start your ELF loader on **port 9021** and choose **Try again**, or launch `orbit_store.elf` through your payload manager. The app never stops another running payload to make room.

For missing artwork or crashes when opening a game page, use **native app 1.12.0** from Orbit 1.8.0, which includes service **1.8.0** and reduces artwork memory use. Check both running versions in **Diagnostics & about**. Stop any older running service before reopening the app; if you start the service separately through Payload Manager, update that copy too. Unavailable image hosts can still leave artwork missing. If a crash continues, include an existing diagnostic or crash log when reporting it.

If ShadowMount reports **TitleDir bridge unavailable**, its app-registration bridge is not ready. Close active games, restart the console when convenient, run your usual jailbreak and ShadowMount setup, then retry registration of the existing FFPKG. If it persists, include ShadowMount's version and the relevant registration errors from its debug log in your report.

If a TV app update still opens the previous version, compare the running and saved versions in **App settings → Updates & startup**. Orbit replaces the detected installation; a saved update does not replace an app that is still running. Close the app and reopen it. If ShadowMountPlus still holds the previous image, restart the console and jailbreak when convenient. Keep only one native installation. The TV app and service have separate versions.

### Automatic shutdown has not started

Check **App settings → Downloads → Automatic PS5 shutdown**, or **Settings → Downloads** in Zero. **Wait for** does not ignore other unfinished work. Paused or failed downloads, pending installation checks, active file operations or updates, and a busy or disconnected Zero computer can block shutdown. An installation failure cancels the schedule. Keep Zero open while it has work; reconnect it to report its current status. When all work is finished, the countdown lasts 60 seconds. See [automatic shutdown](shutdown.md).

### The selected drive is too small

Review free space and queued work in the download sheet. Archives may need room for the archive and extracted files together, and installation needs additional console storage. If Zero still has the computer files, use **Change drive** on that download to send them to another PS5 drive without downloading again. A completed copy on the old drive stays there. Direct PS5 downloads do not have this drive-change action. See [change the PS5 drive](orbit-zero.md#change-the-ps5-drive).

### An update says Orbit is already running

The replacement was saved for the next start. Open **App settings → Updates & startup** (or **Settings → Updates & startup**) and compare **Running** with **Saved for next start**. Use **Restart Orbit** with your ELF loader running on port 9021. If you use Payload Manager without that loader, follow the manual stop/start instructions and launch the saved or synced ELF through the manager. On older versions, choose **Stop Orbit to restart**, then launch the saved `/data/orbit-store/orbit_store.elf` or a synced manager copy. Pairing and the queue stay saved. A manually imported old ELF starts that older copy unless you replace it.

### Orbit shows BlackBox's icon, can't connect or is missing after BlackBox

BlackBox's builds up to v1.0.6 use Orbit's title ID, `ORBT00001`. If you installed one of them, Orbit's Media-tab icon may show BlackBox's logo, fail with "127.0.0.1 could not reach", or not appear at all. Removing BlackBox's payload alone doesn't fix this, because its app files stay on the console. These steps come from users who fixed it ([#42](https://github.com/saawant12/orbit-store-ps5/issues/42), [#39](https://github.com/saawant12/orbit-store-ps5/issues/39)).

You need FTP access to the PS5, for example `ftpsrv` from your payload manager and FileZilla on a computer (port 2121). Delete only the items listed here.

1. **Stop BlackBox from starting.** Remove `blackbox.elf` from your payload manager and turn off its auto-start.
2. **Delete the home-screen icons.** On the PS5, delete BlackBox's icon from the Games row and Orbit's icon from the Media tab. Orbit's icon comes back in step 5.
3. **Delete BlackBox's files over FTP:**
   - `/user/app/BLKB00001`
   - `PPSA01453` in `/data/homebrew/` (its TV app, a `.ffpkg` file or a folder)
   - `/user/download/PPSA01453`
   - `/data/shadowmount/icon-cache/PPSA01453*.png`
   - its payload-manager folder, such as `/data/pldmgr/payloads/BlackBox`
4. **Delete Orbit's icon folder, `/user/app/ORBT00001`.** Orbit rebuilds it the next time it starts. Keep `/data/orbit-store`: it holds your download queue and settings.
5. **Restart and start Orbit.** Restart the console, run your jailbreak, then start `orbit_store.elf`. Open Orbit from the Media tab, or open the TV app from the Games row, which needs kstuff and ShadowMountPlus.

If Orbit still shows BlackBox's icon, open a bug report with your firmware, your Orbit version and what you deleted.

## Finding and downloading games

### A game or image is missing

Check the enabled Sources and clear Browse’s filters. Then try **App settings → Game catalogue → Refresh catalogue**. Use the latest matching apps; PS4 support starts with service 1.1.0, native app 1.4.0 and Orbit Zero 1.1.0. Builds without PS4 support use a PS5-compatible catalogue. Select **Platform → All platforms** or **PS4**, and check the running service version as well as the installed app version.

Artwork comes from external URLs. Orbit tries an available fallback when the primary fails. Network/DNS restrictions or unavailable host images can still prevent artwork from loading. Some dates and other metadata remain missing; corrections arrive through catalogue updates. Undated games appear after dated games in release-date sorting.

### A download fails or is slow

- **Provider returned a page:** update Orbit, restart it and retry from Downloads. For browser-only Vikingfile options, repeat the provider step. Orbit still rejects an actual error or verification page returned instead of file data.
- **Provider throttling:** let the retry delay finish. Orbit honours the provider’s Retry-After response.
- **Drive disconnected:** reconnect the original destination. In 1.7.5, Orbit can recognise the same drive after a remount using its saved marker or the job’s own partial file. Keep those files and select **Resume**. If it still asks for the original drive, export diagnostics before changing the queue. Orbit does not silently switch to a different drive.
- **Not enough space:** free space on the chosen destination, considering unfinished downloads, then retry.
- **Source changed:** keep the partial until you decide whether to remove it and restart. Orbit will not append a different file to it.
- **Partial file deleted or empty:** choose **Retry**. In 1.5.0 and later, Orbit starts that download again from the beginning on the same drive.

Parallel connections can help only when supported by the host and file identity. Provider speed limits, network conditions and drive performance still apply.

### TorBox stops or cannot reach its download server

Use the matching [1.8.0 apps](https://github.com/saawant12/orbit-store-ps5/releases/tag/v1.8.0). TorBox uses at most eight connections per game and honours provider cooldowns. In Zero, if the download server refuses a connection before any data arrives, a retry waits at least five minutes. Keep the partial files and allow that wait to finish.

If the message says the original source no longer has the file, choose another download option. A fresh temporary link cannot restore a removed source. If failures continue, export a new diagnostic log and include the app version, source and the point at which it stopped. Do not share your TorBox key or temporary download URLs.

### Vikingfile does not enter Downloads

Use the current Orbit app and matching running service, and enable Vikingfile under **Sources & accounts**. [Sign in](vikingfile.md) in the interface handling the download. The PS5 browser and native app keep separate sessions. Select the desired option and drive; Orbit first tries the signed-in direct flow. If a provider page opens, complete verification and wait without pressing Download. Orbit captures the matching link and returns automatically. For computer downloads in Orbit Zero 1.4.0 or later, complete verification and wait without pressing Download in its provider window too. Verification happens on the PS5 even if you initiated it on your phone.

If the session times out, the provider page changes or the browser restarts, return to Orbit and try that option again. Cancel an existing session before starting another. A file that does not match the selected option is not queued. Provider links may become unavailable.

### AkiraBox does not enter Downloads

Use the latest matching Orbit Store or Orbit Zero apps. AkiraBox requires **1.2.0 or later**. Open the file page from Orbit, complete verification and wait a few seconds without pressing Download. Orbit captures the ready link; avoid advertisements and popup buttons. If the session expires, return to Orbit and open the provider step again. For a paused or failed job, use **Refresh download link**. In Zero, the PS5 can stay disconnected while you refresh a computer download’s link; reconnect it when you are ready to transfer.

### Archive.org reports HTTP 401, 403 or 404

Some files need an Archive.org account. Follow [Archive.org sign-in](downloads.md#archiveorg-sign-in) in the app handling the download, then retry. The PS5 service and Orbit Zero keep separate account sessions. If the source page says the item was removed or is unavailable, signing in will not restore it; choose another source. An HTTP code alone does not prove which case applies.

### Archive needs a password

Orbit automatically tries the [known source passwords](../README.md#automatic-archive-extraction). If the archive needs a different one, choose **Enter archive password**, enter the source’s password exactly, then **Retry extraction**. Keep the downloaded archive and enough free space for its extracted files. A corrupt or unsupported archive can still fail with the correct password.

### Internal storage or an M.2 SSD is missing

Update to the [latest matching Orbit apps](https://github.com/saawant12/orbit-store-ps5/releases/latest), restart the download service and reopen **Library → Files**. Drive information refreshes automatically. Native app users should update the TV app too. Replacing the FFPKG alone does not replace a service that is already running.

An available drive appears even if its `homebrew` folder has not been created yet. Orbit creates the folder when needed and checks actual write access when a download starts or resumes. If the destination cannot be written, the download stops and existing partial data is kept.

If the drive still does not appear, include your firmware, Orbit and ShadowMount versions and a fresh diagnostic report in your bug report.

## Orbit Zero transfers

### An Orbit Zero transfer is stuck after sleep or disconnection

Wake the computer and PS5, keep the original destination connected, and reconnect in **Console**. Start Orbit on the PS5 if its service stopped. Keep the computer partial file, then select **Resume** on the interrupted transfer. If the PS5’s IP address or pairing changed, follow [address and pairing recovery](orbit-zero.md#reconnect-after-an-address-change). Orbit checks the saved files before continuing; it does not start every paused transfer automatically.

If other games show **Waiting to transfer**, an earlier PS5 transfer may still hold their turn. In Downloads, choose the recovery action that matches what you want:

- **Resume** to continue that transfer.
- **Cancel and remove partials** to delete its unfinished files after confirmation and start fresh.
- **Stop transfer** to keep remaining files and free the queue. **A stopped transfer cannot resume afterward.**
- **Restart PS5 transfer**, when offered, to reuse the computer copy for a fresh PS5 transfer.
- **Remove from Downloads** to clear a stuck entry while keeping its files. If the PS5 is still blocked afterward, use **Recover downloads → Review PS5 transfer**.

For a transfer already created on the PS5, cancellation and stopping need a response from the original console. If it cannot confirm the operation, reconnect and retry. If Zero asks for a newer receiver, update both the desktop app and the PS5 service using [these steps](orbit-zero-installation.md#update-orbit-zero). The receiver is `orbit_store.elf`; installing only the desktop update does not replace a running PS5 service.

Keep both devices awake while transferring. See [transfer recovery and cleanup](orbit-zero.md#pause-reconnect-and-clean-up) for the differences between stopping, deleting partials and clearing completed computer copies.

### I removed a download but still have its computer cache

In Orbit Zero, open **Downloads → Recover downloads → Choose file** and choose the completed game file or older `.cache` file. Keep the name and folder Orbit used; a named file needs its completion record on this computer. Review the matching game and destination, add it back to the queue, then select **Resume**. See [cache recovery](orbit-zero.md#recover-a-completed-computer-download) for checks and limits.

## Library, installing and DLC

### A completed download is missing from Library

For downloads handled by Orbit Store, check **Downloads → Finished → Location** in the browser or native app. Open **Library → Files** to check that exact saved path on the selected drive. Extracted downloads may be a folder containing several files. The recorded path remains in history even if a file is later moved or deleted.

Orbit Zero download details also show the full PS5 destination path and the computer path while a cached copy remains. Check the selected PS5 drive's [homebrew folder](downloads.md#where-downloads-are-saved). For **Send to PS5**, wait for **Transfer to PS5** to complete too. If you used **Stream & install**, check the installation result instead; it does not leave a full package in the PS5 download folder.

If the file exists but does not appear in Library or on the home screen, check its format and the installation or mounting method supported by your console setup. A finished download is not automatically installed, and ShadowMount may not list every format. PKG and FPKG packages need installing first; see [below](#a-downloaded-pkg-or-fpkg-game-doesnt-appear). If the file is absent, include the app, game, source, format, destination and completion screen in your report; do not delete the queue or remaining files while investigating.

### A downloaded PKG or FPKG game doesn't appear

PKG and FPKG options are `.pkg` packages, for PS4 or PS5 games. Orbit saves them to the chosen drive's `homebrew` folder. In **1.5.0** and later, open the completed download’s **Downloaded files**, select the package and choose **Install on PS5**. With Zero, either finish transferring it to the PS5 first or use [Stream & install](stream-install.md) from the completed computer copy. Earlier versions need a compatible package installer. ShadowMountPlus does not mount `.pkg` files, so **Scan for games** is not a substitute for installation.

Check installation status separately from download completion. If **Check installation** appears after a restart or lost response, use it and check the PS5 home screen before trying again. Orbit retains the downloaded file if installation fails. See [installation help](install-games.md#if-installation-needs-attention).

Installation through Orbit does not change compatibility. PS5 FPKG games currently run only on firmware 11.60 or lower (October 2026); on 12.xx and 13.xx they may install but won't start. Copying a game package to the same folder as Orbit's native app does not register it the way the TV app is registered.

If the game also offers exFAT or FFPFSC, those are mounted by ShadowMountPlus without installing. See [which format to pick](downloads.md#which-format-to-pick).

If you report a problem, include the title ID (`CUSA` for PS4, `PPSA` for PS5), source, format, destination, app versions, any error code from the installer, and whether it fails during the computer download, PS5 transfer or package installation. Do not share temporary signed links. See [PS4 games on PS5](downloads.md#ps4-games-on-ps5).

### Add-ons are missing or do not work

Add-ons are available in **1.5.0**; older apps do not gain the page through a catalogue refresh. Use matching apps and the running PS5 service from the same release. If the page is empty, enable the relevant sources, clear its filters and refresh the catalogue. A page opened from a game’s details initially shows only that game’s extras.

If a downloaded DLC does not appear in the game, check that its package was installed, then compare the required base-game edition, title ID, region and version. A title-ID match alone does not confirm compatibility. Activation packages need their content already present in the game; bundles require selecting the individual packages to install. Orbit does not fetch missing game updates or install an entire bundle automatically. See [the DLC guide](add-ons.md).

## Interface and settings

### I cannot find a setting after changing interface

Crossbar, Cinema and Panorama use a **Settings** page in the browser and Orbit Zero. In Zero, Appearance, Language and Updates move there from Store’s top bar. The native app also calls its settings page **Settings** in these layouts, keeping the same sections inside. See the [settings map](appearance.md#find-settings-after-switching).

### My interface choice switches back or is not remembered

Select **Keep** before the 15-second confirmation countdown ends. **Switch back**, or not answering in time, restores the previous interface. To return to the default yourself, choose **Store** in Appearance and confirm it.

Each app or browser saves its own appearance. A phone, native app and desktop app can use different layouts. Browser site-data clearing, private browsing or opening a different IP/hostname may reset the choice. If it still resets after confirmation on normal launches, report the app version, chosen interface and steps. See [where your choice is saved](appearance.md#where-your-choice-is-saved).

For less movement, choose **Appearance → Motion → Reduced**. Cinema and Panorama also offer **Plain black** instead of background artwork behind menus or pages.

## Reporting a problem

### Share a diagnostic report

Open **App settings → Diagnostics & about → View diagnostics**, then **Copy diagnostic report**. If automatic copying is unavailable, Orbit shows selectable report text. Reports omit pairing codes, access tokens, download links, game names and paths. Nothing is sent automatically.

You can also save a report as a file. In the browser, choose **App settings → Diagnostics & about → Save diagnostic report**, then a PS5 drive. On the TV app, **App settings → Diagnostics & about** offers **View diagnostics** and **Save diagnostic report**. In Zero, choose **Settings → Diagnostics & about → Export log**. Zero includes the PS5 report when connected. These exports omit game titles, filenames, folders, links, passwords and tokens; attach the saved file yourself when reporting a problem.

![App settings with local diagnostics](../assets/0.9.0/desktop-diagnostics.jpg)

*You choose whether to copy and share a report. This interface preview uses example diagnostic data.*

When reporting a problem in [Issues](https://github.com/saawant12/orbit-store-ps5/issues), include the Orbit version, PS5 firmware, loader, the steps taken and the displayed error. For a display or navigation problem, include the interface (Store, Crossbar, Cinema or Panorama) and whether you used a controller, keyboard, mouse or touch. Remove any private details before posting. The reported etaHEN payload-toggle interaction remains under investigation.

## Files and account checks in 1.7.0

- **A Files action says storage is busy:** pause active downloads/transfers and wait for any current installation or storage operation to finish. Opening folders remains available.
- **A copied source changed:** keep the original and retry after the program changing it has stopped. Orbit did not publish the incomplete copy.
- **Circle exits a folder:** it should go to the parent, then all drives, then Library. Update all apps to the latest matching build if you still see the old behaviour.
- **Vikingfile says sign-in could not be confirmed:** use Check sign-in or open its account page. A network error or provider challenge is not proof you signed out. See [account setup](vikingfile.md).
- **Stream & install is missing:** finish the computer download/extraction, connect the paired PS5 and run the matching receiver. See [streaming installation](stream-install.md).

[Getting started](getting-started.md) · [Download guide](downloads.md) · [Library guide](library.md) · [Appearance guide](appearance.md) · [Project home](../README.md)
