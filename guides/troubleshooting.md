# When something needs attention

## Orbit or its icon does not open

Start the Orbit payload through your manager, then reopen the Media-tab icon. The icon opens a running Orbit server and cannot start a stopped payload. If the icon was deleted, starting Orbit recreates it. Keep Orbit’s saved data when updating.

From another device, use `http://<ps5-ip>:34177/` on the same local network. Keep that port private to your LAN.

## The native TV app will not open or start Orbit

The Games-row app needs **kstuff and ShadowMountPlus**. Check that `PPSA99177.ffpkg` is in `/data/homebrew/` and let ShadowMountPlus register it. Keep only one FFPKG or folder installation.

If the app says Orbit is not running, start your ELF loader on **port 9021** and choose **Try again**, or launch `orbit_store.elf` through your payload manager. The app never stops another running payload to make room.

For missing artwork in the TV app, check the running service version in the browser's **App settings → Update / reinstall**. Use **0.6.0 or later**; older services cannot load artwork for the TV app. Stop Orbit and start the updated service. Installing the new FFPKG alone does not replace a service already running.

If ShadowMount reports **TitleDir bridge unavailable**, its app-registration bridge is not ready. Close active games, restart the console when convenient, run your usual jailbreak and ShadowMount setup, then retry registration of the existing FFPKG. If it persists, include ShadowMount's version and the relevant registration errors from its debug log in your report.

If a TV app update still opens the previous version, close the app first. Restart the console and jailbreak when convenient so ShadowMountPlus can remount the replacement. The TV app and service have separate versions.

## An update says Orbit is already running

The replacement was saved for the next start. Open **App settings → Update / reinstall**, compare **Running** and **Saved for next start**, choose **Stop Orbit to restart**, then launch the saved `/data/orbit-store/orbit_store.elf` or a synced manager copy. Pairing and the queue stay saved. A manually imported old ELF starts that older copy unless you replace it.

## Vikingfile does not enter Downloads

Use Orbit 0.5.0 or later and enable Vikingfile in Sources. Select the desired option and drive, press **Open download page on PS5**, complete any provider verification and press Download on the provider page, then return to Orbit. Verification happens on the PS5 even if you initiated it on your phone.

If the session times out, the provider page changes or the browser restarts, return to Orbit and try that option again. Cancel an existing session before starting another. A file that does not match the selected option is not queued. Provider links may become unavailable.

## Internal storage or an M.2 SSD is missing

If the drive disappeared after updating to 0.9.0, install **Orbit 1.0.0 or later**, restart the download service and refresh storage. Native app users should also update the TV app to **1.3.0 or later**, which includes the fixed service. Replacing the FFPKG alone does not replace a service that is already running.

An available drive appears even if its `homebrew` folder has not been created yet. Orbit creates the folder when needed and checks actual write access when a download starts or resumes. If the destination cannot be written, the download stops and existing partial data is kept.

If the drive still does not appear, include your firmware, Orbit and ShadowMount versions and a fresh diagnostic report in your bug report.

## A download fails or is slow

- **Provider returned a page:** update Orbit, restart it and retry from Downloads. For browser-only Vikingfile options, repeat the provider step. Orbit still rejects an actual error or verification page returned instead of file data.
- **Provider throttling:** let the retry delay finish. Orbit honours the provider’s Retry-After response.
- **Drive disconnected:** reconnect the original destination. Orbit does not silently switch to a different drive.
- **Not enough space:** free space on the chosen destination, considering unfinished downloads, then retry.
- **Source changed:** keep the partial until you decide whether to remove it and restart. Orbit will not append a different file to it.

Parallel connections can help only when supported by the host and file identity. Provider speed limits, network conditions and drive performance still apply.

## A game or image is missing

Check the enabled Sources and clear Browse’s filters. Then try **App settings → Game catalogue → Refresh catalogue**. For PS4 games, use the 1.1.0 service and matching native app 1.4.0, or Orbit Zero 1.1.0. Older supported apps use a PS5-compatible catalogue. Select **Platform → All platforms** or **PS4**, and check the running service version as well as the installed app version.

Artwork comes from external URLs. Orbit tries an available fallback when the primary fails. Network/DNS restrictions or unavailable host images can still prevent artwork from loading. Some dates and other metadata remain missing; corrections arrive through catalogue updates. Undated games appear after dated games in release-date sorting.

## A downloaded PS4 game is not installed

Check the download’s platform, title ID and file format, and wait for the transfer to finish on the PS5. PS4 catalogue options are `.pkg` files labelled PKG or FPKG. Orbit saves them to the chosen drive’s `homebrew` folder; it does not install or launch them. Use the package installer supported by your PS5 setup. Copying a game package to the same folder as Orbit’s native app does not mean it will be registered in the same way.

If you report a problem, include the `CUSA` title ID, source, format, destination, app versions and whether it fails during the computer download, PS5 transfer or package installation. Do not share temporary signed links. See [PS4 games on PS5](downloads.md#ps4-games-on-ps5).

## Share a diagnostic report

Open **App settings → Diagnostics → View diagnostics**, then **Copy diagnostic report**. If automatic copying is unavailable, Orbit shows selectable report text. Reports omit pairing codes, access tokens, download links, game names and paths. Nothing is sent automatically.

![App settings with local diagnostics](../assets/0.9.0/desktop-diagnostics.jpg)

*You choose whether to copy and share a report. This interface preview uses example diagnostic data.*

When reporting a problem in [Issues](https://github.com/saawant12/orbit-store-ps5/issues), include the Orbit version, PS5 firmware, loader, the steps taken and the displayed error. Remove any private details before posting. The reported etaHEN payload-toggle interaction remains under investigation.

[Getting started](getting-started.md) · [Download guide](downloads.md) · [Library guide](library.md) · [Project home](../README.md)
