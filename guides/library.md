# Your Library and storage

Library is available in both the native TV app and browser version. Both read the same ShadowMount inventory and share storage operations.

![Native TV app Library with installed and on-drive games](../assets/0.9.0/native-library.png)

Library shows installed games and sources available on your drives, using the inventory from a compatible **ShadowMount v1 local API** on the same PS5. It works independently of your download-source choices. Orbit does not start ShadowMount or change its configuration.

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

Use the PS4 package installation method supported by your PS5 setup. Library actions appear only when the provider supports them. See [PS4 games on PS5](downloads.md#ps4-games-on-ps5) before choosing a download.

## Refresh or scan

**Refresh library** reads the current inventory. It does not scan, mount or install games. **Scan for games** asks ShadowMount to discover sources and may register or mount them after you confirm.

If Library is unavailable, start a compatible ShadowMount version and enable its local API. Available actions depend on your ShadowMount version and the selected game file.

## Manage a source

Open a Library game to see its available actions. Mount or unmount a compatible source, or choose **Copy** or **Move** between supported drives. Unmount it first, pause active/queued Orbit downloads, select the destination and confirm.

Copy keeps the original. Move asks the provider to remove the original after a successful transfer. Follow progress in Library and cancel while the provider reports that it is safe. A provider storage job can continue independently if Orbit closes.

Open **Storage** to check free space and measure game sizes. Available actions depend on your ShadowMount version, drive format and free space. If an action is unavailable or fails, check the displayed message and see [Troubleshooting](troubleshooting.md).

Orbit does not launch games or uninstall them. Downloads and Library actions are separate; a completed download is a saved file, not a promise that it is installed or ready to launch.

![Phone Library with status and filtering controls](../assets/0.9.0/phone-library.jpg)

*Pair a phone to inspect the same console inventory without changing download-source settings.*

[Getting started](getting-started.md) · [Download guide](downloads.md) · [Troubleshooting](troubleshooting.md) · [Project home](../README.md)
