---
{"title":"Obsidian URI","created":"2023-05-13T01:00","modified":"2023-09-10T00:21","dg-publish":true,"dg-path":"Obsidian/Guides/Obsidian URI.md","permalink":"/obsidian/guides/obsidian-uri/","dgPassFrontmatter":true,"updated":"2023-09-10T00:21"}
---

# Obsidian URI

status:: #status/identified 
up:: 
tags:: #obsidian #how-to #uri 

## Built in URI Commands

- Doc: https://help.obsidian.md/Advanced+topics/Using+Obsidian+URI
- General syntax: `obsidian://action?param1=value&param2=value`
- `action`s:
	- `open` :
		- Opens an Obsidian vault, and possibly open a file within that vault.
		- Syntax: `obsidian://open?vault=<vault name or ID>&file=<file name or vault relative path>&path=<absolute file system path to a file>`
	- `search`:
		- Opens the search pane for a vault, and optionally perform a search query.
		- Syntax: `obsidian://search?vault=<vault name>&query=<search query>`
	- `new`:
		- Creates a new note in the vault, optionally with some content.
	- `show-plugin`:
		- Browses community plugin in Obsidian:  `obsidian://show-plugin?id=<plugin-id>`

## Obsidian Advanced URI Community Plugin

- [Obsidian Advanced URI](https://github.com/Vinzent03/obsidian-advanced-uri) allows you to control many different features in Obsidian just by opening some URIs [commands](https://vinzent03.github.io/obsidian-advanced-uri/actions/commands). Because they are just text and don't require any mouse clicks or keyboard inputs, they are perfect to automate your Obsidian workflow.
- Example:
	- I use this command with [Automate](https://play.google.com/store/apps/details?id=com.llamalab.automate&hl=en&gl=US) Android app to [[40-49 Toolbox/40 Note-taking/40.01 Obsidian/Guides/Add Android Widget for Obsidian#Automate\|create a widget]] that creates a new note. `obsidian://advanced-uri?commandid=zk-prefixer`

## Get Command ID

- Using this [[40-49 Toolbox/40 Note-taking/40.01 Obsidian/Plugins/DataView#^5426a1\|DataView JS Query]]

## Get Plugin ID

- Get core plugins ID from [this blog post](https://publish.obsidian.md/hub/05+-+Concepts/Obsidian+Core+Plugins)
- Get community plugins ID by searching the plugin [here](https://obsidian.md/plugins).

