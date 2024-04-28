---
{"title":"Obsidian Plugin - Obsidian Git","created":"2023-07-05T20:54:28","modified":"2023-10-03T22:19:07","dg-publish":true,"permalink":"/60-69-learning-and-productivity/40-note-taking/40-01-obsidian/plugins/obsidian-git/","dgPassFrontmatter":true,"updated":"2023-10-03T22:19:07"}
---


up:: [[60-69 Learning & Productivity/40 Note-taking/40.01 Obsidian/Plugins/+ Obsidian Plugins\|Obsidian Plugins]]
tags:: #obsidian #plugin #git

# Obsidian Plugin - Obsidian Git

- GitHub:: https://github.com/denolehov/obsidian-git
- Documentation:: https://publish.obsidian.md/git-doc/Start+here
- Obsidian URL:: https://obsidian.md/plugins?id=obsidian-git
- Obsidian URI:: [obsidian://show-plugin?id=obsidian-git](obsidian://show-plugin?id=obsidian-git)
- Settings:: [obsidian://advanced-uri?settingid=obsidian-git](obsidian://advanced-uri?settingid=obsidian-git)

## Overview

Plugin that allows you to back up your Obsidian.md vault to a remote Git repository (e.g. private repo on GitHub).

### Features

- Automatic vault backup every X minutes
- Pull changes from remote repository on Obsidian startup
- Assign hotkeys for pulling/pushing changes to a remote repository
- Manage different repositories via Git submodules (after enabling this feature in settings)
- The Source Control View allows you to stage and commit individual files. It can be opened with the `Open Source Control View` command.
- The History View shows the commits and their changed files. So basically an integrated `git log`. It can be opened with the `Open History View` command.
- For viewing the history of a file, I strongly recommend you the Version History Diff plugin

## Usage

- I use it only on my main device. It handles Git repo, which I use as a backup for recovering any unintended deletion or note modifications.

## Preferences

- Backup: Commit and Push changes every 30 minutes after last file change
- Commit Message: `vault backup: {{date}}`
- Date format: `YYYY-MM-DD HH:mm:ss`
- Merge on conflict
- Pull before Commit
- Push on Commit

## Tricks



## Resources


