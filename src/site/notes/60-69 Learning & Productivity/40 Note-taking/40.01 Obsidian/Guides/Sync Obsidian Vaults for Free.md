---
{"created":"2023-05-13T01:00:00","modified":"2024-04-28T21:10:26","up":null,"tags":null,"completed":null,"title":"Sync Obsidian Vaults for Free","dg-publish":true,"permalink":"/60-69-learning-and-productivity/40-note-taking/40-01-obsidian/guides/sync-obsidian-vaults-for-free/","dgPassFrontmatter":true,"updated":"2024-04-28T21:10:26"}
---


up:: 
tags:: #how-to #sync #free-alternative #windows #android


# Sync Obsidian Vaults for Free

## Motive

The motive here is to find a solution that can sync my Obsidian Vaults across my devices, which can have different OS.

Although [Obsidian Sync](https://obsidian.md/sync) is the most convenient option, but the $10 monthly is hard to swallow, at least for me. Therefore, I pursued free alternatives.

## Methods and Tools

### 1. Git Version Control

- Advantages:
	- [[50-59 Technical Skills/Git Version Control\|Git Version Control]] provides the ability to track and manage the changes in all files included in the repo. 
	- I am comfortable with [[50-59 Technical Skills/Git Version Control#Git commands\|Git commands]]
- Steps required:
	1. [[50-59 Technical Skills/Git Version Control#Initialize a new repo\|Initialize a new repo]]
	2. Decide when a right amount of change is worth to [[50-59 Technical Skills/Git Version Control#Git Commit\|commit]] a file, or files.
	3. Give a proper commit message for future me to be grateful.
	4. [[50-59 Technical Skills/Git Version Control#Git Push\|Push]] the changes to the remote repo.
	5. [[50-59 Technical Skills/Git Version Control#Git Pull\|Pull]] the changes from the remote repo into other devices.
- Caveats:
	- Doing steps 2 to 5 so frequently, which high effort-vs-impact ratio.
	- Need to do the exact same steps for each device.
	- The urge that I need to push the changes as soon as possible to be readily available on other devices.
	- There is no direct installation for GIT. All is needed is to install the community plugin. But if you need more flexibility and security like encryption and SSH, there are multiple guides [here](https://renerocks.ai/blog/obsidian-encrypted-github-android/#why-not-use-boxcryptor--cryptomator-and-dropbox) and [here](https://www.reddit.com/r/ObsidianMD/comments/110om69/guide_obsidian_git_sync_on_app_opening_android/) to do so.

### 2. SyncThing

- Overview: 
	
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



# Syncthing

Syncthing is a **continuous file synchronization** program. It synchronizes files between two or more computers in real time, safely protected from prying eyes. Your data is your data alone, and you deserve to choose where it is stored, whether it is shared with some third party, and how it’s transmitted over the internet. ^syncthing-overivew

- **Documentation**: https://docs.syncthing.net/intro/getting-started.html
- **Open-Source**? Yes
- **Usability**:
	- It is relatively easy to get it up and running.
	- Linking devices are straightforward, especially using device ID QR code
	- Intuitive in selecting which folder to be synced to which devices
- **Pros**:
	- No central hub, so the data are not available anywhere except my own devices.
	- Flexible
	- Portable, no installation required.
	- Supports multiple flavors for [File Versioning](https://docs.syncthing.net/users/versioning.html)
		1. Backup file which gets deleted after specific duration.
		2. Have multiple versions for a file. The number of versions is configurable.
		3. A combination between 1 and 2.
	- E2E encrypted
	- [Ignore Files](https://docs.syncthing.net/users/ignoring.html)
- **Cons**:
	- Since the data are not stored in a central hub, it requires both devices, source and receiver, to be online at the same time to be able to synchronize.
		- To overcome this problem, you can set your own central hub if you want.
	- On Windows, it uses a local web page for control instead of an app. This requires to open the app manually and to have a browser open.
		- This [guide](https://docs.syncthing.net/users/autostart.html#autostart-windows-startup) has multiple workaround to solve the autostart problem. I used the below one:
			- Navigate to startup folder using `%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup` or `shell:startup` using RUN.
			- Create a new shortcut in the folder
			- Enter the path to `syncthing.exe` in “Type the location of the item:” followed by `--no-console --no-browser` (for example `C:\syncthing\syncthing.exe --no-console --no-browser`). 
				- If Windows Terminal is the default terminal, then the console will be launched despite the `--no-console` command, it was addressed in this [issue](https://github.com/syncthing/syncthing/issues/8046). To overcome this, add the path of the Windows Console Host at the beginning. So the final target should be `C:\Windows\System32\conhost.exe "C:\Program Files\syncthing-v1.23.4\syncthing.exe" --no-console --no-browser`
			- Syncthing will now automatically start the next time you log on to your user account in Windows. No console or browser window will pop-up, but you can still access the interface by opening [http://localhost:8384](http://localhost:8384) in a Web browser.
- **Other Concerns**:
	- Still monitoring its mobile battery consumption.
		- It is very heavy on mobile battery
	- Will be there any sync conflicts and how it will handle solving them?
		- It keeps both versions

</div></div>

- Steps required:
	- Choose the Vault folder on the web UI
	- Connect to my other devices and choose the location for the synced folder on each of the connected device
- Caveats:
	- The devices need to be online at the same time to be synced together.
	- There is no real file versioning. The files could be overridden without noticing. Especially that Obsidian auto-saves.

### 3. Cloud Storage

- Overview:
	- Cloud storage is always online and could be accessed from anywhere
	- Practically, it has infinite storage space.
- Services provide cloud storage
	- OneDrive
	- Google Drive
	- Amazon S3
	- Cloudflare R2

## Solution

So I decided to set up GIT as my version control as a backup and Cloud Storage for syncing
- Steps to set up GIT on main device:
	1. Make sure that GIT is installed in your system.
	2. Install [[60-69 Learning & Productivity/40 Note-taking/40.01 Obsidian/Plugins/Obsidian Git\|Obsidian GIT]] community plugin
	3. Create a new repo using Obsidian command palette (CTRL + P) and enter `Git: Initialize a new repo`
	4. To overcome the need to commit my changes and write a commit message, I use the auto backup feature in [[60-69 Learning & Productivity/40 Note-taking/40.01 Obsidian/Plugins/Obsidian Git\|Obsidian GIT]] community plugin.
- Steps to set up cloud storage for syncing, I am using Cloudflare R2 as my cloud storage:
	1. [[50-59 Technical Skills/50 Web Development/50.03 Cloud/Cloud Storage/Cloudflare R2#Create R2 Bucket\|Create an R2 Bucket]]
	2. [[50-59 Technical Skills/50 Web Development/50.03 Cloud/Cloud Storage/Cloudflare R2#Generate R2 API Token\|Generate an R2 API Token]] to get:
		1. Token value
		2. Access Key ID
		3. Secret Access Key
		4. Use jurisdiction-specific endpoints for S3 clients
	3. Install [[60-69 Learning & Productivity/40 Note-taking/40.01 Obsidian/Plugins/Remotely Save\|Remotely Save]] community plugin on each device and configure as below
		1. Set `A Remote Service` as `S3 or compatible`
		2. Set `Endpoint` as "*Use jurisdiction-specific endpoints for S3 clients*" value you got on step 2.4
		3. Set `Region` as `auto`
		4. Set `Access Key ID` as "*Access Key ID*" value you got on step 2.3
		5. Set `Secret Access Key` as "*Secret Access Key*" value you got on step 2.2
		6. Set `Bucket Name` as the name of the bucket you created in step 1
		7. Leave the rest of this section as default.
		8. Click on `Check` button at the end of this section to make sure that the configuration is correct.
	4. Start syncing by either:
		1. clicking on the button on Obsidian left bar, or using command palette `Remotely Save: start sync`.