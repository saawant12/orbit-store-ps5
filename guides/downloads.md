# Find and download a game

Orbit includes 705 games with single-file options from Archive.org and Vikingfile. Each game appears once; open it to choose from its available sources and formats. The selection depends on which sources you enable.

## Browse and choose

**Discover opens first.** Explore the featured game and Latest releases. New on Orbit shows the latest additions to the catalogue, ordered by game release date. Move down to All games for the full collection. Its grid shows 96 games per page, ordered by the largest available download option first. Use Previous and Next to move between pages.

![Browser Discover All games grid](../assets/0.9.0/desktop-discover-grid.jpg)

Switch to **Browse** when you want search and filters. It defaults to **Release date (newest first)**. Games without a recorded date follow alphabetically. Search by game name or title ID, filter by source, format, region or download size, and change the sort order. **Reset filters** restores the default. Missing dates and other metadata can be added later through catalogue updates.

![Browse with filters and newest-first sorting](../assets/0.9.0/desktop-browse.jpg)

*Use filters to find options that fit your drive and preferred format. Sizes reflect the download option you choose.*

Save a game from its details page to find it under **Favourites** later; favourites are shared with your paired devices.

In the native TV app, use D-pad/left stick to move, Cross to select, Circle to go back and L1/R1 to switch tabs. Select filters with Cross; choose an option with the D-pad and Cross. The controls below apply to the browser version.

| Input | Action |
|---|---|
| D-pad or arrow keys | Move focus |
| Cross or Enter | Select the focused control |
| Circle or Escape | Go back or close a panel |
| Search: Down or Enter | Move into results |
| Search: Up | Return to the Browse tab |
| Search: Left or Right | Edit the text normally |
| Touch or mouse | Select a control |

## Pick a source, format and drive

On the game page, select the main download button to open **Download options**. This reviews your choices without starting a transfer. Open **Source** to choose a format and provider, **Download using** for direct or TorBox delivery, and **Save to** for storage attached to the PS5. The storage panel shows **Free now**, **Unfinished downloads**, and **After queue + this download**. Back returns to your previous selection.

![Download options with source, delivery method and destination](../assets/0.9.0/desktop-details.jpg)

*Different sources can offer different formats or sizes for the same game. Select the exact option you intend to download.*

For a direct option, select **Download to PS5**. Orbit checks the file and destination, then adds it to Downloads.

## Optional: download through TorBox

**Available in 0.8.0 and later.** TorBox is an optional delivery choice for supported links. Update both Orbit’s service ELF and native FFPKG to use it in the TV app. You need your own TorBox account; its plan, host availability, quotas and file-size limits apply. You can keep using the original provider without connecting TorBox.

1. In Orbit’s browser version, open **App settings → Debrid**. You can do this on the PS5 or a paired phone or computer.
2. Get your API key from [TorBox settings](https://torbox.app/settings), enter it in Orbit and choose **Connect TorBox**. Keep the key private.
3. Open a game in either Orbit app and use its main button to open **Download options**. Select **Source**, then **Download using → TorBox**, and choose your destination drive.
4. Select **Download via TorBox**. Follow preparation and transfer progress in Downloads, where the job is labelled **via TorBox**.

![Browser Debrid settings with a sample connected TorBox account and an empty API-key field](../assets/0.9.0/desktop-torbox-setup.jpg)

*Connect the account in the browser once. The native TV app and paired devices share that connection. If you are not connected, choose **Set up TorBox** under a game’s **Download using** options. In the TV app this opens the browser with your game, source and destination selected; connect in App settings, then return to the game.*

![Game details with TorBox selected and a PS5 destination drive](../assets/0.9.0/desktop-torbox-details.jpg)

An account connection does not guarantee support for every file. If an option is unavailable through TorBox, select the original provider explicitly. Orbit does not silently switch a TorBox job to another delivery method.

Pause and resume from Downloads as usual. Disconnecting TorBox pauses its unfinished jobs and keeps their partial files. Reconnect the same account to resume them. Disconnecting does not remove files from your remote TorBox account.

## Vikingfile: open the page on PS5 first

**Starting in the native TV app?** Open **Download options**, choose your source and drive, then select **Open browser version** for a browser-only option. The browser opens your selected game with the same source and destination. Check those choices, then follow the steps below. If the source or drive is no longer available, select an available one explicitly. This does not start the provider step automatically. After Orbit queues the download, you can return to the TV app to follow it.

**Requires Orbit 0.5.0 or later.** Older versions keep their Archive.org catalogue and do not receive unsupported Vikingfile options.

1. Select the Vikingfile option and destination drive in Orbit.
2. Select **Open download page on PS5**. This is the first step; it opens the provider page on the console.
3. Complete any verification yourself and select the provider’s **Download** button. Follow the file’s download controls if a redirect opens another Vikingfile page.
4. Return to Orbit Store and open **Downloads**. Orbit checks that the captured file matches the selected option before adding it to your queue.

![Vikingfile instructions inside Download options](../assets/0.9.0/desktop-viking.jpg)

*The Open download page on PS5 button starts the provider step. Download on Vikingfile comes next; then return to Orbit.*

You can start the session from a paired phone, but the provider page and verification still appear on the PS5. There is no need to paste a generated link. If the session expires or reports no matching file, return to Orbit and start that option again. Only one browser verification session can run at a time; **Cancel verification** stops the pending session without adding a download.

When a Vikingfile option offers **Download directly**, you can use that button to start it. Otherwise, follow the browser steps above.

<table>
  <tr><th>Choose an option on your phone</th><th>Start the PS5 browser step</th></tr>
  <tr>
    <td valign="top" width="50%"><img src="../assets/0.9.0/phone-details.jpg" width="280" alt="Phone game page with source and format options"></td>
    <td valign="top" width="50%"><img src="../assets/0.9.0/phone-viking.jpg" width="280" alt="Phone Vikingfile instructions and Open download page on PS5 button"></td>
  </tr>
</table>

*Interface previews use example storage and account data. Complete the Vikingfile download steps on your PS5.*

## Follow your queue

Use **Active**, **Finished**, **Failed**, and **Cancelled** to find a transfer. Move waiting items up or down, pause and resume, or cancel. Cancelled items have their own view; Finished contains successfully completed downloads.

![Native Downloads showing paused and queued sample transfers labelled via TorBox](../assets/0.9.0/native-downloads.png)

<p><a href="../assets/0.9.0/phone-downloads.jpg"><img src="../assets/0.9.0/phone-downloads.jpg" width="320" alt="Phone Downloads showing the same sample TorBox queue"></a></p>

*The TV app and paired phone show the same queue, illustrated here with sample paused and queued jobs.*

New supported large downloads use up to eight connections. Existing partials retain their original layout. Speed depends on the provider, network and drive. Pause, Resume and Cancel control the whole file.

After deleting a cancelled partial, you can start the download again from its game page. If you kept the partial, resume it from Downloads.

**Remove from history** and the history-clear buttons keep completed files. To remove a cancelled download and its partial file, use **Delete download** and confirm. If its drive is disconnected, reconnect it before deleting the file. If you already deleted the partial yourself, Orbit can clear the stale entry so you can start fresh.

Keep the PS5 awake. Closing the TV app or control browser leaves the download worker running; stopping Orbit interrupts it. Interrupted transfers return paused after restart. Orbit does not extract archives, directly install game packages, launch games or continue downloading in rest mode. For compatible drive files, see [Library](library.md).

## Get new games and corrected metadata

Orbit checks its catalogue on startup and every six hours. Use **App settings → Game catalogue → Refresh catalogue** for a manual check. You can browse the saved catalogue offline, and queued downloads keep the files you originally chose. New games and corrected release dates arrive without reinstalling Orbit.

[Getting started](getting-started.md) · [Troubleshooting](troubleshooting.md) · [Project home](../README.md)
