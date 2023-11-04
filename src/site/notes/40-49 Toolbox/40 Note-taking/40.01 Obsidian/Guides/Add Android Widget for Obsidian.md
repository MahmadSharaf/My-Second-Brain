---
{"created":"2023-05-13T01:00","modified":"2023-09-10T00:22","title":"How to Add Android Widget for Obsidian","dg-publish":true,"permalink":"/40-49-toolbox/40-note-taking/40-01-obsidian/guides/add-android-widget-for-obsidian/","dgPassFrontmatter":true,"updated":"2023-09-10T00:22"}
---


# How to Add Android Widget for Obsidian

I literally followed this [blog](https://joschuasgarden.com/50+Slipbox/How+to+add+an+Obsidian+note+to+the+homescreen+on+Android). But since it is not available anymore, I used a cached version and copied it below

## Setup

* Download the [[40-49 Toolbox/40 Note-taking/40.01 Obsidian/+ Obsidian\|Obsidian]] mobile app.
* Install [[40-49 Toolbox/40 Note-taking/40.01 Obsidian/Plugins/Advanced URI\|Advanced URI]] community plugin 
* Download an automation app: [Automate](https://llamalab.com/automate/) (free) or [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm) (paid)

### In Obsidian

* Open the command palette in the Obsidian app (swipe down by default).
* Search for "Advanced URI" and select with file you want to copy a link to.
 
## Automation App

### Automate

* **Premade**:
	* Joschua created a simple flow to open the Daily note in Obsidian: [Open Daily Note in Obsidian](https://llamalab.com/automate/community/flows/39984).
	* By duplicating the flow and editing the "Data URI" field, you can open any link in [[40-49 Toolbox/40 Note-taking/40.01 Obsidian/Guides/Obsidian URI\|Obsidian URI]]. 
		* I created another flow to create a new Unique Note by adding this URI `obsidian://advanced-uri?commandid=zk-prefixer`
* **Manual instructions**. If you're wary of downloading a script from the internet, here are the basic instructions:
	1. Create a new flow in Automate
	2. Select `App start` as a block
	3. Select `md.obsidian` for "Package"
	4. Select `md.obsidian.MainActivity` for "Activity class"
	5. Select `View` for "Action"
	6. Paste your URL in the field "Data URI"
	7. Connect the block `Flow beginning` with the `Start App` block

### Tasker

* Open [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm&hl=en&gl=US). Through the `+` icon, create a new task and give it a name.
* Add an action with the `+` icon. Select "Browse URL".
* Paste the copied URI in the "URL" box.
* With the arrow back, go to the task overview and select an image by tapping the icon in the middle at the bottom.
* Save the task and exit Tasker.

## Homescreen

* Add a widget to the homescreen.
* *Automate*: Select "Flow shortcut" in the "Automate" section.
* *Tasker*: Select "Task Shortcut" in the "Tasker" section.
* There you go! By long-pressing, you can customize the name or icon.
* Now you can add shortcuts to anything!