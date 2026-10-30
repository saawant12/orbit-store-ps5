# Your Library and storage

**For Orbit 1.8.1.** Update the Orbit apps you use from the [same release](getting-started.md#which-files-to-download); the native FFPKG includes its matching service. Library is available in the native TV app, browser and Orbit Zero. They share the same PS5 inventory and file operations. Store, Crossbar, Cinema and Panorama present it in different layouts; changing [appearance](appearance.md) does not change which games are installed or mounted.

![Native TV app Library with installed and on-drive games](../assets/0.9.0/native-library.png)

Library shows installed games and sources available on your drives, using a compatible **ShadowMount v1 local API** on the same PS5. Orbit also fills gaps for installed PKG games that older ShadowMount versions omit. It works independently of your download-source choices. Orbit does not start ShadowMount or change its configuration.

![Library with installed and on-drive status](../assets/0.9.0/desktop-library.jpg)

*Status labels distinguish installed games from files on a drive. Interface previews use example Library and storage data.*

## Understand the labels

- **Installed:** reported as installed by the provider.
- **On drive:** the source file or folder is currently available.
- **Mounted:** the provider reports the source as mounted.
- **Source missing:** a reported source is not currently available on its drive.

These states can overlap. Search by title, title ID or path, and filter by status, location or format.

## PS4 packages and platform labels

Library uses the inventory reported by ShadowMount, while Browse uses Orbit’s download catalogue. Where a platform is known, PS4 and PS5 editions stay separate. Downloading a PS4 `.pkg` file does not make it an installed game or guarantee that ShadowMount can mount that format.

To locate a completed Orbit Store download, open **Downloads → Finished → Location** in the browser or native app. That saved path is separate from the ShadowMount inventory. Orbit Zero download details show the PS5 destination and the computer path while the cached copy remains; see [where downloads are saved](downloads.md#where-downloads-are-saved).

The **1.5.0** apps provide **Install on PS5** to completed PKG/FPKG downloads, including PS4 games. Earlier versions need a compatible package installer. Installation is separate from Library’s mount controls; see [installing downloaded games](install-games.md) and [PS4 games on PS5](downloads.md#ps4-games-on-ps5).

## DLC and installed games

The **Add-ons** page is a separate collection. Finding the base game in Library does not mark its DLC as installed or confirm that an add-on matches its edition or version. Check the add-on’s requirements and its own installation status in Downloads. See [the DLC guide](add-ons.md).

## Automatic Library updates

Library and drive information refresh automatically. Game sizes show **Measuring…** until known. When Files puts a compatible game into `homebrew`, or a drive is connected, Orbit requests a ShadowMount scan at most once a minute. **Looking for new games…** appears while the scan is pending. **Try again** appears when the provider is not responding. **Scan for games** remains a manual fallback and may register or mount games after confirmation.

In **1.5.0** and later, a newly completed exFAT, FFPFSC or game-folder download or transfer automatically requests a scan when a compatible ShadowMount version is running. Orbit checks registration separately. If ShadowMount was unavailable, start it and use **Scan with ShadowMount** in the download’s details when offered. Older completed downloads are not all rescanned automatically on upgrade.

If Library is unavailable, start a compatible ShadowMount version and enable its local API. Available actions depend on your ShadowMount version and the selected game file.

## Manage a source

Open a Library game to see its available actions. Mount or unmount a compatible source, or choose **Copy** or **Move** between supported drives. Unmount it first, select the destination and confirm. Downloads keep running while it copies, and Orbit keeps enough space for both.

Copy keeps the original. In **1.7.5**, **Move** copies the game, reads the destination back to verify it, and registers the new location with ShadowMount before removing the original. If copying, verification or registration fails, the original is kept. Keep both drives connected until the operation finishes.

Follow copying and verification progress in Library. Cancellation is available before the original is removed; it cannot undo an already completed move. A compatible ShadowMount version is required. Orbit Zero offers the same flow when connected to the matching PS5 service. These Library moves are separate from ordinary file operations under **Library → Files**.

Open **Library → Files** to check free space and manage files and folders. Select a folder to open it; Circle goes back one folder. See the [Files guide](files.md). Game sizes are measured automatically. Available actions depend on your ShadowMount version, drive format and free space. If an action is unavailable or fails, check the displayed message and see [Troubleshooting](troubleshooting.md).

Orbit does not launch games or uninstall them. Downloads and Library actions are separate; a completed download is a saved file, not a promise that it is installed or ready to launch.

![Phone Library with status and filtering controls](../assets/0.9.0/phone-library.jpg)

*Pair a phone to inspect the same console inventory without changing download-source settings.*

[Getting started](getting-started.md) · [Download guide](downloads.md) · [Troubleshooting](troubleshooting.md) · [Appearance guide](appearance.md) · [Project home](../README.md)
