# Get started with Orbit Store

Orbit runs on your PS5. Use the TV with your controller, or pair a phone or computer to manage the same catalogue and download queue. Files go to the PS5’s selected storage.

You need a PS5 environment that can run homebrew ELF payloads, an ELF loader or payload manager, internet access on the console for direct provider downloads, and enough writable storage. A phone or computer should be on the same local network. Library management additionally needs a compatible ShadowMount v1 local API.

**No internet on your PS5?** [Set up Orbit Zero](orbit-zero-offline-ps5.md) to start Orbit and download through your computer over the same local network.

**Using Orbit Zero on your computer?** The [desktop installation guide](orbit-zero-installation.md) covers Mac, Windows and Linux. Orbit Zero 1.1.0 includes PS4 browsing and the same 11 interface languages as Orbit Store. Update both the desktop app and the matching PS5 service; update the native FFPKG too if you use it.

## PS4 and PS5 games

The catalogue includes both platforms. For PS4 games, use **Orbit Store 1.1.0** with **native app 1.4.0**, or **Orbit Zero 1.1.0**. In Browse, choose **Platform → PS4**, **PS5** or **All platforms**. A PS4 and a PS5 edition of the same game have separate download choices.

Orbit itself runs on PS5. Downloading a PS4 PKG/FPKG saves a package to your selected drive; installing and launching it uses the compatible tools for your PS5 setup. See [PS4 games on PS5](downloads.md#ps4-games-on-ps5).

## Install the native TV app

The native app requires **kstuff and ShadowMountPlus**. For the app to start Orbit's download service itself, keep a compatible **ELF loader on port 9021** running. You can instead start `orbit_store.elf` through your payload manager before opening the app.

1. Get `PPSA99177.ffpkg` and `PPSA99177.ffpkg.sha256` from the [latest release](https://github.com/saawant12/orbit-store-ps5/releases/latest). In the folder containing both files, run `shasum -a 256 -c PPSA99177.ffpkg.sha256`.
2. If an older Orbit service is running, stop it from **App settings → Update / reinstall → Stop Orbit to restart** in the browser version. Installing an FFPKG does not replace a running service.
3. Copy the FFPKG to **`/data/homebrew/` on the PS5**. Allow ShadowMountPlus to register it, then open **Orbit Store** from the **Games row**.
4. Discover is the starting page. On first use, select **Choose sources**, enable the sources you want and acknowledge the notice. Saving opens Discover. Source choices are shared with the browser.
5. Choose a game, source, format and destination drive. Follow the [download guide](downloads.md) for direct and Vikingfile browser options.

Already using Orbit 0.6.0 or later? In the browser version, open **App settings → TV app → Install on this PS5**. Orbit downloads the official FFPKG, verifies it and saves it to `/data/homebrew/`.

## Use the browser version

1. Get `orbit_store.elf` and `orbit_store.elf.sha256` from the [latest release](https://github.com/saawant12/orbit-store-ps5/releases/latest). Run `shasum -a 256 -c orbit_store.elf.sha256` from their folder.
2. Load the ELF through your payload manager. Orbit saves its runtime and creates its browser shortcut in the PS5 **Media tab**.
3. Open **Orbit Store**, then **App settings → Sources**. Choose Archive.org, Vikingfile, or both, and acknowledge the notice. Only download material you have permission to obtain and use.

Both interfaces use the same service, catalogue, favourites and download queue. The TV app does not need a pairing code on the console. The native **App settings** page includes Download sources, Storage, Pair a device, Game catalogue and Updates. **More settings → Open browser version** provides auto-start, payload-manager setup and diagnostics.

To use optional TorBox downloads in 0.8.0, connect your account in the browser’s **App settings → Debrid**. Both apps can then use it for supported options. See [TorBox setup](downloads.md#optional-download-through-torbox).

A drive connected to your phone or computer is not a PS5 destination. Attach your external drive to the console; Orbit uses its `homebrew` folder when available.

![Choose download sources and acknowledge the notice](../assets/0.9.0/desktop-sources.jpg)

*Sources are your choice. Turning one off later hides its options and pauses unfinished downloads without deleting files. Interface previews use example storage data.*

## Choose your language

Orbit Store and Orbit Zero support **11 interface languages**: English, German, Spanish, French, Hungarian, Italian, Dutch, Polish, Brazilian Portuguese, Russian and Turkish.

- **Native TV app:** Orbit follows your PS5’s system language when it starts. Change the console language in **Settings → System → Language → Console Language**, then close and reopen Orbit. Unsupported languages use English.
- **Browser, phone or computer:** open **App settings → Language**. Choose a language, or **Automatic** to follow your browser’s preference. The interface reloads after you choose. This preference is saved for that browser; it does not change other paired devices or the PS5’s system language.
- **Orbit Zero desktop:** select the globe-shaped **Language** button in the top bar. Choose a language or **System language**. The choice is saved on that computer, and changing it keeps your downloads running.

![Browser App settings with the language selector open](../assets/0.9.0/desktop-language.jpg)

<img src="../assets/0.9.0/phone-language.jpg" width="300" alt="The Language setting near the top of App settings on a phone">

*Browser interface previews are from Orbit 0.9.0; Hungarian is also available in 1.0.5. Game names, descriptions and provider pages may keep their original language. Changing Orbit’s language does not change a downloaded game’s language.*

## Choose a default drive

Open **App settings → Storage** in the native app. Select an available drive, or **Choose automatically** to prefer external storage when available. Selecting another drive for a download makes that drive the default. An unavailable drive must be chosen again explicitly; Orbit does not silently redirect an active transfer.

## Optional Payload Manager feed

In Payload Manager, open **Settings → Manage Sources → Add Source** and enter:

```text
https://raw.githubusercontent.com/saawant12/orbit-store-ps5/main/payloads.json
```

Open the Orbit Store source, download **Orbit Store (Beta)**, then run `orbit_store.elf`.

## Keep a manager copy up to date

Open **App settings → Payload managers** and choose **Add Orbit**, or **Allow updates to this copy** if it is already listed. This opts that manager into receiving Orbit updates. **Stop syncing** leaves the existing copy and auto-start choices in place.

Auto-start is separate. Choose **Start automatically** if wanted and enable your manager’s global Autoload switch yourself. Orbit does not change that global switch. After a reboot, run your jailbreak and start Orbit manually or through your configured auto-start. The Media-tab shortcut needs the payload already running. The Games-row TV app can start it through a local ELF loader on port 9021.

## Update the download service

In the native app, open **App settings → Updates → Download service**. Check for updates, install the chosen release, then confirm **Restart download service**. The app stops only Orbit and starts its saved service through your ELF loader. If no loader is available, follow the on-screen instructions to start Orbit manually.

The following steps apply to the browser version. The download service and native TV app have separate version numbers; compare the versions shown in their update panels.

1. Open **App settings → Update / reinstall → Check for updates**.
2. Choose **Install update**, or **Reinstall release** for the current version. Orbit verifies the release checksum and saves the replacement.
3. Select **Stop Orbit to restart** and confirm. The queue is saved; other payloads are left running.
4. Run `/data/orbit-store/orbit_store.elf` or a manager copy you opted to keep in sync. Reopen Orbit and resume any paused downloads. With the ELF loader running, the TV app can also start the newer saved service.

**Running**, **Saved for next start**, and **Latest release** are separate. Uploading a new ELF while Orbit is running saves it for the next start; it does not change the active session. A manually imported copy outside sync must be replaced yourself. Keep the icon and saved data.

![App settings with separate controls for the download service and TV app](../assets/0.9.0/desktop-settings.jpg)

*App updates install features and fixes. Refresh catalogue updates game data without reinstalling the app.*

Very old beta.2 or earlier installations need a manual ELF replacement and Orbit restart first. Pause downloads and stop only an identifiable Orbit process; if you cannot identify it, restart the console when convenient and load the new ELF after the jailbreak.

## Update the TV app

In the native app, open **App settings → Updates → TV app**, check for updates and choose **Update TV app**. Confirm **Replace with this release** if the existing image was copied manually. After installation, close and reopen the app.

Alternatively, use the browser:

1. Close the TV app using **PS button → Close Application**.
2. In the browser version, open **App settings → TV app** and check for an update. Confirm replacement if you previously copied the FFPKG yourself. Orbit verifies the download before replacing it.
3. Reopen Orbit from the Games row. If ShadowMountPlus still opens the previous app, restart the console when convenient and run your jailbreak again.

You can also verify and replace `/data/homebrew/PPSA99177.ffpkg` manually. Keep only one installation: Orbit will not overwrite a folder installation at `/data/homebrew/PPSA99177/`. Update that folder yourself, or remove your old app copy before switching formats. Keep `/data/orbit-store/`; it holds your settings and queue.

The TV app carries a service copy, but replacing the app does not switch the service already running. Stop Orbit deliberately before starting its new copy. A newer saved service is preserved when opening an older TV app package.

## Pair your phone or computer

In the TV app, open **App settings → Pair a device** to see the console address and six-digit code. While Orbit is running, visit `http://<ps5-ip>:34177/` on the same network. Choose **Pair devices** and enter the six-digit code shown on the PS5. On the console, **Pair devices** keeps the code visible; **Show code on PS5** repeats its notification. Do not share the code publicly.

Your paired device controls the console’s queue. For Vikingfile browser verification, use the PS5 screen to complete the provider steps even when you start from your phone.

### Use a local hostname

Orbit Store 1.1.0 also accepts browser addresses whose hostname ends in `.home.arpa`, `.local` or `.localhost`, with the usual port `34177`. For example, if your home network already resolves `ps5.home.arpa` to your console, open `http://ps5.home.arpa:34177/`. Pairing works the same way as with the IP address.

Orbit does not create or advertise these names. Your router or local name service must resolve the hostname to the correct device. `.localhost` normally resolves to the device you are browsing on, so it is generally for local testing rather than a remote PS5. If a name does not resolve, use `http://<ps5-ip>:34177/`. Orbit Zero’s Console connection field still takes the PS5’s local IP address.

[Download guide](downloads.md) · [Library guide](library.md) · [Troubleshooting](troubleshooting.md) · [Project home](../README.md)
