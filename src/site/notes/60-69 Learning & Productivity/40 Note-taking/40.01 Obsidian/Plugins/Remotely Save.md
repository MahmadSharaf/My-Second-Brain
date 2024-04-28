---
{"title":"Obsidian Plugin - Remotely Save","created":"2023-07-05T20:00:00","modified":"2023-12-04T15:49:00","tags":["obsidian","plugin"],"dg-publish":true,"permalink":"/60-69-learning-and-productivity/40-note-taking/40-01-obsidian/plugins/remotely-save/","dgPassFrontmatter":true,"updated":"2023-12-04T15:49:00"}
---


up:: [[60-69 Learning & Productivity/40 Note-taking/40.01 Obsidian/Plugins/+ Obsidian Plugins\|Obsidian Plugins]]
tags:: #obsidian #plugin #sync


# Obsidian Plugin - Remotely Save

- GitHub:: https://github.com/remotely-save/remotely-save
- Documentation:: https://github.com/remotely-save/remotely-save/tree/master/docs
- Obsidian URL:: https://obsidian.md/plugins?id=remotely-save
- Obsidian URI:: [obsidian://show-plugin?id=remotely-save](obsidian://show-plugin?id=remotely-save)
- Settings:: [obsidian://advanced-uri?settingid=remotely-save](obsidian://advanced-uri?settingid=remotely-save)

## Overview

This is yet another unofficial sync plugin for Obsidian.

### Features

- Supports:
    - Amazon S3 or S3-compatible (Like: Cloudflare R2)
    - Dropbox
    - OneDrive for personal
    - Webdav
    - [Here](https://github.com/remotely-save/remotely-save/blob/master/docs/services_connectable_or_not.md) shows more connectable (or not-connectable) services in details.
- **Obsidian Mobile supported.** Vaults can be synced across mobile and desktop devices, with the cloud service as the "broker".
- **[End-to-end encryption](https://github.com/remotely-save/remotely-save/blob/master/docs/encryption.md) supported.** Files would be encrypted using openssl format before being sent to the cloud **if** the user specifies a password.
- **Scheduled auto sync supported.** You can also manually trigger the sync using the sidebar ribbon, or using the command from the command palette (or even bind the hot key combination to the command then press the hot key combination).
- Import And Export Not-Oauth2 Plugin Settings By QR Code
- **[Minimal Intrusive](https://github.com/remotely-save/remotely-save/blob/master/docs/minimal_intrusive_design.md).**
- **Fully open source under [Apache-2.0 License](https://github.com/remotely-save/remotely-save/blob/master/LICENSE).**
- **[Sync Algorithm open](https://github.com/remotely-save/remotely-save/blob/master/docs/sync_algorithm_v2.md) for discussion.**

### Limitations

- **To support deletions sync, extra metadata will also be uploaded.** See [Minimal Intrusive](https://github.com/remotely-save/remotely-save/blob/master/docs/minimal_intrusive_design.md).
- **No Conflict resolution. No content-diff-and-patch algorithm.** All files and folders are compared using their local and remote "last modified time" and those with later "last modified time" wins.
- **Cloud services cost you money.** Always be aware of the costs and pricing. Specifically, all the operations, including but not limited to downloading, uploading, listing all files, calling any API, storage sizes, may or may not cost you money.
- **Some limitations from the browser environment.** More technical details are [in the doc](https://github.com/remotely-save/remotely-save/blob/master/docs/browser_env.md).
- **You should protect your `data.json` file.** The file contains sensitive information.
    - It's strongly advised **NOT** to share your `data.json` file to anyone.
    - It's usually **NOT** a good idea to check the file into version control. By default, the plugin tries to create a `.gitignore` file inside the plugin directory if it doesn't exist, for ignoring `data.json` in the `git` version control. If you know exactly what it means and want to remove the setting, please modify the `.gitignore` file or set it to be empty.

## Preferences

- I use R2 (S3-compatible service from Cloudflare) as my cloud service.
- AutoSync every on 1 minute.
- Sync 1 second after startup.

## Tricks

- It is possible to share the credentials across other devices using its QR feature found in the [settings](obsidian://advanced-uri?settingid=remotely-save).



