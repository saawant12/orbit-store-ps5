# Orbit Zero

Orbit Zero can save games on your computer without a connected PS5, then send them to the console later. You can also download and transfer to a connected PS5 over the local network. For uncompressed files, the two stages overlap: completed chunks can reach the console while the computer is still downloading. ZIP, RAR and 7z archives finish downloading and extract on the computer before their files transfer. Use the desktop app, a compatible native Orbit TV app, or the local browser controls to browse and manage the queue.

Download the desktop app and matching PS5 files from [Orbit Store releases](https://github.com/saawant12/orbit-store-ps5/releases/latest). PS4 browsing and desktop language selection require Orbit Zero 1.1.0 or later. For a console without internet, follow the [offline PS5 setup guide](orbit-zero-offline-ps5.md).

**Download and transfer improvements are included as standard.** Follow the [installation and update steps](orbit-zero-installation.md) to update the desktop app and PS5 service together.

The current screenshots show Orbit Zero 1.5.0, rendered locally with the current catalogue.

![Orbit Zero 1.5.0 Discover with NieR:Automata selected](../assets/1.5.0/zero-discover-nier-automata.jpg)

*Discover in Orbit Zero.*

## What you need

- A computer with internet access and enough free space for the download and any extracted files.

For transfers to PS5, you also need:

- Writable storage on the PS5.
- A PS5 with its jailbreak and Payload Manager or a compatible ELF loader already running, or the matching Orbit receiver already started. Zero does not jailbreak the console.
- Both devices on the same home network. Wi-Fi, Ethernet, or a mixture of both work. Use the PS5's local IPv4 address.
- Orbit Zero and its included Orbit Store 1.7.0 service. For native TV controls, install the matching FFPKG from the same release.

Downloads are available for **ARM64 and x64 on macOS, Windows and Linux**; 32-bit x86 is not supported. Mac builds use Developer ID signing but are not notarized; Windows and Linux packages are unsigned.

## Install Orbit Zero

Follow the [macOS, Windows and Linux installation guide](orbit-zero-installation.md). It covers the right download for your computer, installation, first-launch permissions and updating an existing copy.

## Language and interface

### Choose your language

The interface supports English, German, Spanish, French, Hungarian, Italian, Dutch, Polish, Brazilian Portuguese, Russian and Turkish. In Store, select the globe-shaped **Language** button in the top bar; in the other interfaces, open **Settings → Language**. Choose a language or leave **System language** selected.

### Choose your interface

Orbit Zero offers **Store**, **Crossbar**, **Cinema** and **Panorama**. In Store, select the palette-shaped **Appearance** button in the top bar; in the other interfaces, open **Settings → Appearance**. Confirm **Keep** within 15 seconds. Your selection is saved on this computer. See the [appearance guide](appearance.md) for screenshots, motion options and navigation.

In Crossbar, Cinema and Panorama, **Settings** also contains **Download settings**, **Computer cache**, **Updates** and **Language**. **Console** continues to hold the PS5 connection and download-route preference.

## Download now and send to your PS5 later

1. Open a game, choose its source and format, then select **Save to → This computer**. You do not need to pair a PS5 or start its Orbit service.
2. Start the download. For Vikingfile or AkiraBox, complete verification in the provider window and wait for Orbit to capture the ready link.
3. Follow progress in **Downloads**. Archives extract on the computer; **Show in folder** opens the saved location when ready.
4. When you want to transfer, connect and pair your PS5 using the steps below. Select **Send to PS5** on the completed download and choose its destination drive. The saved computer copy stays in place.

## Connect the computer and console

1. Start the PS5's jailbreak and Payload Manager or ELF loader. Open **Console** in Zero and enter the PS5's local IP address.
2. Expand **Start Orbit on PS5**. For Payload Manager's web interface, choose **Payload Manager → Upload and start Orbit**. This saves or replaces `orbit_store.elf` in the manager and leaves autoload settings unchanged. For a separate ELF loader, choose **ELF loader → Send to ELF loader**. Zero checks the official GitHub payload feed for a compatible receiver, verifies its checksum and caches it. The app also includes a verified compatible receiver for offline setup. If the matching receiver is already running, use **Connect to Orbit** instead. Do not start another Orbit service on the same port.
3. Zero connects automatically after uploading Orbit. Once connected, select **Show code on PS5**. Enter the six-digit code shown by the console and select **Pair with PS5**. You can request the notification again after the countdown, or open **Pair devices** in Orbit on the PS5 to keep its code visible.
4. Open a game and choose its source and PS5 destination in the download sheet. The destination is selected for each download; the Console overview shows current storage capacity. Game details also offers **Favourite**, **About this game** and **View download** when that game is already in the queue.

![Orbit Zero 1.5.0 Console before connecting a PS5](../assets/1.5.0/zero-console.jpg)

*Console before pairing. Your PS5 storage and transfer status appear after connecting.*

The normal Orbit service port is **34177**. Payload Manager's web interface defaults to **8084**, while the ELF loader defaults to **9021**. These use different protocols: changing the port alone does not switch between them. Choose the matching method, then use **Start Orbit on PS5 → Advanced** if its port is different. Manual ELF selection is there too; a custom ELF sent through Payload Manager is saved as `orbit_zero_custom.elf`.

On macOS, allow Orbit Zero to access the local network when prompted. If access was denied, enable it in **System Settings → Privacy & Security → Local Network**, then reconnect.

Pairing is saved using the computer's encrypted credential store. Zero reconnects to your saved PS5 when you reopen it; macOS or Linux may ask to unlock saved pairing after the console responds. If reconnection fails, select **Console → Reconnect**. Zero never receives your computer password, and refuses to save an unencrypted pairing if secure storage is unavailable. If the console’s address or pairing has changed, follow [reconnect after an address change](#reconnect-after-an-address-change) rather than unpairing and deleting your queue.

Choosing a game and its destination (step 4):

![Black Myth: Wukong in Orbit Zero 1.5.0 with Add-ons and download controls](../assets/1.5.0/zero-game-details.jpg)

*Game details in Orbit Zero.*

![Orbit Zero 1.5.0 source choices, This computer destination and automatic Vikingfile link capture](../assets/1.5.0/zero-download-options.jpg)

*Download options with **This computer** selected, without a connected PS5.*

## Browse PS4 and PS5 games

[Saved filters](saved-filters.md) in **1.7.0** let the PS5 apps and connected Zero share named searches, filters and sort orders.

In 1.6.0, Browse supports selecting several sources or formats, the same eight [game tags](downloads.md#game-tags) as the PS5 apps, and hiding games installed or saved on the connected PS5. These controls work in all four interfaces.

In the Store interface, **New on Orbit** appears first in Discover, followed by **Latest releases** and the All games grid. The other interfaces present these collections in their own layouts. In Browse, use **Platform** to choose PS4, PS5 or both. Platform editions stay separate, with their own images, release dates and download options.

The current catalogue includes 971 PS4 games, with raw PKG/FPKG files and single ZIP, RAR or 7z archives among their download options. Choose a source and **This computer** or a PS5 destination just as you would for a PS5 game. The computer-download route also works with the PS5’s internet access blocked. The **1.5.0** apps provide **Install on PS5** after the transfer finishes. Earlier versions need a compatible package installer. See [installing downloaded games](install-games.md) and [PS4 games on PS5](downloads.md#ps4-games-on-ps5).

## DLC and add-ons

Orbit 1.5.0 adds **Add-ons** next to Browse in all four interfaces. Search by DLC or base-game name, or open **Add-ons (count)** from a game’s details. Review the type, contents and base-game requirements before choosing a source.

Use **This computer** to save DLC without a connected PS5, then **Send to PS5** when ready. Once the files reach the console, choose **Install on PS5** for the individual packages you want. A bundle does not install everything automatically. See [the DLC guide](add-ons.md) for filters, activation packages and compatibility.

## Choose where downloads run

| Preference | New downloads |
| --- | --- |
| **Computer** (default) | Download through the computer. Uncompressed files transfer in completed chunks; archives extract before their files transfer. |
| **Prefer PS5** | Check whether the PS5 can reach the selected source, then use a direct PS5 download if it can. Otherwise, use the computer. |

Change this under **Console → Download preference**. It applies to new downloads; running downloads keep their original route. The PS5 needs internet access for direct PS5 downloads. For computer downloads, the computer handles provider access and artwork, so the PS5 only needs its local network connection.

Download options also show known firmware requirements using the last paired PS5's firmware while it is offline; unpairing clears that saved firmware. A matching firmware label does not guarantee game or DLC compatibility.

## Vikingfile, AkiraBox and archive downloads

**1.7.0** adds [Vikingfile account sign-in](vikingfile.md). Zero tries the signed-in session first and opens the provider page when verification is needed.

For Vikingfile, Zero opens a separate browser window on the computer. Complete any provider verification and wait without pressing Download. Zero captures and checks the ready file link, closes its provider window and adds the download to the queue. Provider logins stay in a separate persistent browser profile on the computer. Unwanted popups are blocked; **Back**, **Reload** and **Return to download page** let you get back to the file.

For **AkiraBox**, open the provider page, complete verification and wait without pressing Download. Zero captures the ready link and closes the provider window. Supported ZIP, RAR and 7z downloads extract on the computer before transfer; see [archive downloads](downloads.md#zip-rar-and-7z-downloads).

For an expired Vikingfile or AkiraBox link, select **Refresh download link**. Your PS5 can stay disconnected while Zero refreshes the computer download’s link. Zero checks that it still identifies the selected file before reusing partial data. Reconnect the PS5 when you are ready to transfer.

For compressed downloads, **Extract on computer** appears between the download and transfer stages. Keep enough computer space for the archive and its extracted files together. **Download settings → Delete archives after extracting** is on by default and removes the archive after successful extraction. The extracted files follow the separate [Computer cache](#pause-reconnect-and-clean-up) preference.

## Follow your downloads

In 1.6.0, completed computer downloads keep their real filenames instead of an internal `.cache` name. If a name already exists, Zero adds a number, such as `Game (2).pkg`. **Show in folder** opens the saved copy.

Choose **1–64 connections per download** in **Download settings**; eight is the default. The provider must support validated byte ranges. Orbit falls back to fewer connections when required. Actual speed depends on the provider, network and storage. **Downloads** shows **Download to computer** and **Transfer to PS5** separately; their rates and progress can differ. A direct PS5 download shows the rate reported by Orbit.

Orbit **1.5.0** adds estimated time remaining for each stage and direct PS5 downloads. It reads upcoming chunks while transferring to reduce gaps between writes. Speeds still depend on your network and drives.

![Orbit Zero 1.5.0 Downloads with an empty queue](../assets/1.5.0/zero-downloads.jpg)

*Downloads in Orbit Zero 1.5.0, before adding a game.*

## Download settings

![Orbit Zero 1.5.0 download settings with simultaneous download and recovery controls](../assets/1.5.0/zero-download-settings.jpg)

*Download settings in Orbit Zero 1.5.0.*

### Simultaneous downloads

Zero downloads one game to the computer at a time by default. Open **Downloads → Download settings → Simultaneous computer downloads** to choose **1–8**. Lowering the limit lets current downloads finish before another starts. Files transfer to the PS5 one at a time while computer downloads continue. Each file needs enough computer space for its full cached copy.

### Choose the computer download folder

In Console, select **Computer download folder → Choose folder**. In Downloads, open the settings icon beside the page title to find the same control. This applies to every source. New downloads use the folder you choose; existing partial files stay in their original location so they can resume.

### Download recovery settings

Open **Downloads → Download settings → Download recovery** to choose how often Orbit retries, how long it waits between attempts and when a slow download should reconnect. Set **Automatic retries** to **0** to turn retries off. These settings apply to computer downloads; direct PS5 downloads use the settings saved on the console. See [download recovery settings](downloads.md#download-recovery-settings).

### Accounts for computer downloads

Open **Downloads → Download settings**, or **Settings → Download settings** in Crossbar, Cinema or Panorama. **Archive.org** lets you sign in for account-required downloads; **TorBox** lets you connect your API key and choose TorBox on supported download options. Both connections are kept on the computer and are separate from the accounts configured on your PS5. See [Archive.org setup](downloads.md#archiveorg-sign-in) and [desktop TorBox](downloads.md#torbox-in-orbit-zero).

### Export a log for bug reports

For a bug report in 1.5.0, **Download settings → Export log** saves recent activity and the connected PS5's diagnostics. It excludes game titles, filenames, folders, links, passwords and tokens. Nothing is uploaded automatically.

## Pause, reconnect and clean up

Keep Orbit Zero open and prevent the computer from sleeping during transfers. Keep the PS5 awake to receive files. If the console disconnects after a transfer starts, the computer can continue downloading into its cache. Reconnect the original console and select **Resume**. Temporary computer-download connection failures retry automatically, with fewer connections on later attempts. Deliberately paused downloads and downloads paused after restarting Zero still need **Resume**. A file change, access restriction or disk error needs attention; it is not retried indefinitely.

**Waiting to transfer** means the computer copy is ready for its PS5 turn. If an earlier PS5 transfer is paused or needs attention, resume it, cancel and remove its partials, or choose **Stop transfer** to keep its files and release that turn. Other computer downloads can continue in the meantime.

| Choose | What happens |
| --- | --- |
| **Resume** | Continues the existing transfer after checking its partial files. Reconnect the original PS5 and destination with a verified pairing, and leave the computer copy in place. |
| **Cancel and remove partials** | Asks for confirmation, then removes that transfer’s partial files from the computer and PS5. Use this to discard unfinished work before starting fresh. |
| **Stop transfer** | Keeps remaining computer and PS5 files and frees the queue after the PS5 confirms the stop. **This transfer cannot be resumed afterward.** You can recover a completed computer cache or start again. |
| **Restart PS5 transfer** | When offered, starts a fresh transfer using the saved computer copy, without downloading it again. Existing PS5 files stay untouched; select **Resume** afterward. |
| **Remove from Downloads** | Stops that computer job and removes its queue entry, keeping files on both devices. If a PS5 transfer still blocks the queue, use **Recover downloads → Review PS5 transfer**. |

For an existing PS5 transfer, keep the matching Orbit service running and reconnect before cancelling or stopping. If the PS5 cannot confirm the operation, the job stays available for you to retry. Updating Orbit Zero alone does not update its receiver on the console; follow [Update Orbit Zero](orbit-zero-installation.md#update-orbit-zero) to update both.

**Computer cache.** The computer copy is kept by default. **Downloads → Download settings → Computer cache** offers **Automatically remove after transfer** for future successful transfers and **Clear completed cache** for copies already completed. You can still select **Remove computer cache** on an individual download. Cleanup preserves PS5 files, partial downloads and history. **Remove from Downloads** removes a queue entry while keeping its files; it is also available for stuck jobs.

**Unpairing.** To forget the console, use **Console → Connection settings → Unpair PS5**. Zero blocks unpairing while transfers to that PS5 are unfinished, including paused or interrupted transfers. Finish or cancel those first; unpairing keeps files and download history. If the console has lost its pairing, use [Pair again and keep downloads](#reconnect-after-an-address-change) instead, so Zero can check and resume the saved partial files.

## Install on PS5 and find your files

In **1.7.0**, **Library → Files** manages the PS5’s drives: browse folders, copy, move, rename, delete, unpack and install supported items. Selecting a folder opens it; Circle or Escape returns to its parent. See [Files](files.md). Completed computer packages also offer [Stream & install](stream-install.md), without a full intermediate package copy on the PS5. Ordinary **Send to PS5 → Install on PS5** remains available. Zero does not launch games.

New exFAT, FFPFSC and game-folder transfers automatically request a scan when the PS5 has a compatible ShadowMount version running. If ShadowMount was unavailable, start it and use **Scan with ShadowMount** in the completed download’s details when offered. See [installation and scan guidance](install-games.md).

Completed transfer details show **PS5 location**, plus **Computer location** while the cached copy remains. Files go to the selected PS5 drive's `homebrew` folder; archives may produce a file or an extracted folder. See [where downloads are saved](downloads.md#where-downloads-are-saved).

## Reconnect after an address change

Open **Console → Connection settings**, enter the PS5’s new local IP address and select **Connect to Orbit**. Zero checks the saved pairing before moving the existing queue to that address.

If the console no longer accepts the saved pairing, Zero offers **Pair again and keep downloads**. Confirm that it is the PS5 used for those downloads, request the on-screen code and enter it. This requires a new pairing code, not just a confirmation. Downloads remain paused until you select **Resume**. Zero compares the existing PS5 partial with the computer copy and continues from the verified position when possible. If resuming is not possible, **Recover downloads → Review PS5 transfer** offers **Delete PS5 partial and start again** after you explicitly confirm the deletion. Only that partial copy is deleted; your computer download is kept.

## Recover a completed computer download

Use this when a finished computer download still exists but its Downloads entry was removed. Choose the file under its saved game filename, or an older `.cache` file. Keep the name and folder that Orbit used; recovery of a named file relies on its completion record on this computer.

1. Connect the PS5 and open **Downloads → Recover downloads → Choose file**.
2. Choose the completed Orbit Zero file from its original download folder.
3. Review the matching **Game and download** and select the **PS5 destination**. For an older cache without a completion record, confirm completeness only if you know the original download finished; matching size alone does not prove that.
4. Select **Add to queue**. Orbit checks the file and restores the entry paused. Select **Resume** to transfer it without downloading it again.

This does not repair incomplete or corrupt downloads, or recreate a cache already deleted. An unmatched file is left unchanged.

If an unfinished transfer on the PS5 blocks the queue after its desktop entry was removed, open **Recover downloads → Review PS5 transfer**. Check the displayed file and choose **Stop transfer and keep files** if offered. This releases the blocked transfer while retaining its remaining files.

## Control it from the PS5

After pairing the computer, open **App settings → Orbit Zero → Enable Orbit Zero** in the matching TV app. It uses the computer's catalogue and artwork, and new downloads follow the preference saved on the computer. Vikingfile verification asks you to continue on the computer. Turning Zero mode off affects new downloads; existing computer transfers keep their route.

Alternatively, expand **Console → How it works** in the desktop app. Open one of the displayed computer addresses in the PS5 browser and enter the computer's pairing code. This browser pairing code is separate from the console code used to pair the desktop. Keep it private. The desktop's local browser service normally uses port **34179**.

## Desktop updates

Open **Updates** in Store’s top navigation, or **Settings → Updates** in Crossbar, Cinema or Panorama. Automatic checks are enabled by default. When an update is available, download the matching verified package and open it when ready to install. Orbit Zero does not replace itself or restart automatically. See [update steps](orbit-zero-installation.md#update-checks-in-orbit-zero).

Return to the [Orbit Store README](../README.md) for the current release, supported PS5 workflows and third-party content notice.
