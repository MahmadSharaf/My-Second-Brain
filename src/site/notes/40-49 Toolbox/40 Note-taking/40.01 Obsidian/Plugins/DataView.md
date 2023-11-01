---
{"title":"Obsidian Plugin - DataView","created":"2023-07-04T20:00:00","modified":"2023-10-04T00:03:21","dg-publish":true,"dg-path":"Obsidian/Plugins/DataView.md","permalink":"/obsidian/plugins/data-view/","dgPassFrontmatter":true,"updated":"2023-10-04T00:03:21"}
---


up:: [[40-49 Toolbox/40 Note-taking/40.01 Obsidian/Plugins/+ Obsidian Plugins\|Obsidian Plugins]]
tags:: #obsidian #plugin #query

# Obsidian Plugin - DataView

- GitHub:: https://github.com/blacksmithgu/obsidian-dataview
- Documentation:: https://blacksmithgu.github.io/obsidian-dataview/
- Obsidian URL:: https://obsidian.md/plugins?id=dataview
- Obsidian URI:: [obsidian://show-plugin?id=dataview](obsidian://show-plugin?id=dataview)
- Settings:: [obsidian://advanced-uri?settingid=dataview](obsidian://advanced-uri?settingid=dataview)

## Overview

Treat your [Obsidian Vault](https://obsidian.md/) as a database which you can query from. Provides a JavaScript API and pipeline-based query language for filtering, sorting, and extracting data from Markdown pages. See the Examples section below for some quick examples, or the full [reference](https://blacksmithgu.github.io/obsidian-dataview/) for all the details.

## Usage


## Preferences

> [!important]
> I configured inline query prefix to be "==", instead of default "="

## Tricks

- Get file modified date: 2023-10-04T00:00:00.000+03:00
- Get file modified time: 2023-10-04T00:04:06.456+03:00
- [Get list of commands sorted by assigned hotkey](https://forum.obsidian.md/t/dataviewjs-snippet-showcase/17847/37):
	```js
	const getNestedObject = (nestedObj, pathArr) => {
	    return pathArr.reduce((obj, key) =>
	        (obj && obj[key] !== 'undefined') ? obj[key] : undefined, nestedObj);
	}
	
	function hilite(keys, how) {
	    // need to check if existing key combo is overridden by undefining it
	    if (keys && keys[1][0] !== undefined) {
	        return how + keys.flat(2).join('+').replace('Mod', 'Ctrl') + how;
	    } else {
	        return how + '–' + how;
	    }
	}
	
	function getHotkey(arr, highlight=true) {
	    let hi = highlight ? '**' : '';
	    let defkeys = arr.hotkeys ? [[getNestedObject(arr.hotkeys, [0, 'modifiers'])],
	    [getNestedObject(arr.hotkeys, [0, 'key'])]] : undefined;
	    let ck = app.hotkeyManager.customKeys[arr.id];
	    var hotkeys = ck ? [[getNestedObject(ck, [0, 'modifiers'])], [getNestedObject(ck, [0, 'key'])]] : undefined;
	    return hotkeys ? hilite(hotkeys, hi) : hilite(defkeys, '');
	}
	
	let cmds = dv.array(Object.entries(app.commands.commands))
	    .where(v => getHotkey(v[1]) != '–')
	    .sort(v => v[1].id, 'asc')
	    .sort(v => getHotkey(v[1], false), 'asc');
	
	dv.paragraph(cmds.length + " commands with assigned hotkeys; " +
	    "non-default hotkeys <strong>bolded</strong>.<br><br>");
	
	dv.table(["Command ID", "Name in current locale", "Hotkeys"],
	  cmds.map(v => [
	    v[1].id,
	    v[1].name,
	    getHotkey(v[1]),
	    ])
	  );
```{ #5426a1}

- [Get list of commands sorted by Command ID](https://forum.obsidian.md/t/dataviewjs-snippet-showcase/17847/37): 

	```js
	
	const getNestedObject = (nestedObj, pathArr) => {
	    return pathArr.reduce((obj, key) =>
	        (obj && obj[key] !== 'undefined') ? obj[key] : undefined, nestedObj);
	}
	
	function hilite(keys, how) {
	    // need to check if existing key combo is overridden by undefining it
	    if (keys && keys[1][0] !== undefined) {
	        return how + keys.flat(2).join('+').replace('Mod', 'Ctrl') + how;
	    } else {
	        return how + '–' + how;
	    }
	}
	
	function getHotkey(arr, highlight=true) {
	    let hi = highlight ? '**' : '';
	    let defkeys = arr.hotkeys ? [[getNestedObject(arr.hotkeys, [0, 'modifiers'])],
	    [getNestedObject(arr.hotkeys, [0, 'key'])]] : undefined;
	    let ck = app.hotkeyManager.customKeys[arr.id];
	    var hotkeys = ck ? [[getNestedObject(ck, [0, 'modifiers'])], [getNestedObject(ck, [0, 'key'])]] : undefined;
	    return hotkeys ? hilite(hotkeys, hi) : hilite(defkeys, '');
	}
	
	let cmds = dv.array(Object.entries(app.commands.commands))
	    .sort(v => v[1].id, 'asc');
	
	dv.paragraph(cmds.length + " commands currently enabled; " +
	    "non-default hotkeys <strong>bolded</strong>.<br><br>");
	
	dv.table(["Command ID", "Name in current locale", "Hotkeys"],
	  cmds.map(v => [
	    v[1].id,
	    v[1].name,
	    getHotkey(v[1]),
	    ])
	  );
```

- Fetch data from the current file only. Add "Where" data command as below

	```sql
	TABLE
	WHERE file.path = this.file.path
	```

- [Comma separate numbers](https://forum.obsidian.md/t/dataview-numbers-display-with-comma-separation/57287): It uses regex to add a comma after each 3 numbers. However, regex function requires the input argument to be string, so you need to convert the numbers to string.

```js
regexreplace(string(123456), "\B(?=(\d{3})+(?!\d))", ",")
```

- If you have a file that contains bullet points, and each bullet point has the same metadata, it is possible to display each list in a single row using the below trick. However, it is heavy in computation.

	```sql
	TABLE WITHOUT ID
		L.text as Title,
		nonnull(L.children["Amazon Link"])[0] AS "Amazon Link",
		nonnull(L.children.Author)[0] AS Author,
		nonnull(L.children.Published)[0] AS Published,
		nonnull(L.children.Rating)[0] AS Rating,
		nonnull(L.children.Ratings)[0] AS Ratings,
		nonnull(L.children.Pages)[0] AS Pages
	WHERE file.path = this.file.path
	FLATTEN file.lists AS L
	WHERE nonnull(L.children)
	SORT L.children.Ratings DESC, L.children.Rating DESC
	```

- [inline query to check how metadata is structured in your file](https://forum.obsidian.md/t/query-for-dates-that-are-actually-links-dataview/32628/2): 
	- `'$=dv.span(dv.current())'`

- Table of Contents
	```js
	// Set this to 1 if you want to include level 1 headers,
	// or set it to 2 if you want to ignore level 1 headers
	const startAtLevel = 2
	const content = await dv.io.load(dv.current().file.path)
	const toc = content.match(new RegExp(`^#{${startAtLevel},} \\S.*`, 'mg'))
	  .map(heading => {
	    const [_, level, text] = heading.match(/^(#+) (.+)$/)
	    const link = dv.current().file.path + '#' + text
	    return '\t'.repeat(level.length - startAtLevel) + `1. [[${link}|${text}]]`
	  })
	dv.header(2, 'Table of contents')
	dv.paragraph(toc.join('\n'))
	```
- MOC with some depth up to the headings inside the note
	```js
	// Retrieve pages with title "path/to/your/notes"
	let p = dv.pages('"path/to/your/notes"')
	          // Filter out the current page
	          .where(p => p.file.name != dv.current().file.name)
	          //sort pages by creation time
	          .sort(p => p.file.ctime)
	          //for each page
	          .forEach(p => {
	            // Display page name as header
	            dv.header(2, p.file.name);
	            //get metadata cache for the page
	            const cache = this.app.metadataCache.getCache(p.file.path);
	            // If cache exists
	            if (cache) { 
	              // Get the headings from the cache
	              const headings = cache.headings;
	              //if headings exist
	              if (headings) { 
	                //exclude the first heading
	                const filteredHeadings = headings.slice(1)
	                  // Filter headings based on level (up to level 4)
	                  .filter(h => h.level <= 4) 
	                  .map(h => {
	                    // Determine indentation based on heading level
	                    let indent = " ".repeat(h.level - 1);
	                   // let linkyHeading = "[[#" + h.heading + "]]";
	    //Correct linking code
	    let linkyHeading = "[[" + p.file.name + "#" + h.heading + "|" + h.heading + "]]";     
			   return indent + "- " + linkyHeading;
				  })
				  // Join the formatted headings with newlines
				  .join("\n");
				// Display the formatted headings as a div
				dv.el("div", filteredHeadings);
			  }
			}
		  });
	```
- MOC with natural sort and no headers
	```js
	// Get the folder path of the current file
	let parentFolderPath = dv.current().file.folder;
	// The level of the parent folder relative to the vault
	let parentFolderLevel = parentFolderPath.split("/").length;
	// Initialize a string that will hold the current file parent folder in a for loop
	let currentFileParentPath = "";
	// An array that holds the file parent folder or folders names excluding the parents folders of this note
	var folders = [];
	//  An array to hold all resulted texts.
	var text = [];
	// Initialize an integer to hold the depth of the current file compared to this note.
	var depth = 0;
	// Retrieve all notes under this file parent folder.
	dv.pages(`"${parentFolderPath}"`)
	  // Filter out the current page
	  .where((p) => p.file.name != dv.current().file.name)
	  //.where(p=> p["dg-publish"])
	  // Natural sort by files path
	  .sort(
	    (p) => p.file.path,
	    "asc",
	    function (a, b) {
	      return a.localeCompare(b, undefined, {
	        numeric: true,
	        sensitivity: "base",
	      });
	    }
	  )
	  // for each note
	  .forEach((p) => {
	    // Check if the note parent folder path is different from the stored parent folder path
	    if (currentFileParentPath != p.file.folder) {
	      // If different then update the current parent folder path in the variable
	      currentFileParentPath = p.file.folder;
	      // Get the level of the note parent folder compared to the vault
	      let currentFolderLevel = currentFileParentPath.split("/").length;
	      // Get the depth level differences between this note parent folder and the looped note parent folder
	      depth = currentFolderLevel - parentFolderLevel;
	      // Loop over each depth level
	      for (let i = 0; i < depth; i++) {
	        // Get the folder name of the iterated depth level
	        let folderName = p.file.folder.split("/")[i + parentFolderLevel];
	        // Check if folder name is not already stored in the Folder names
	        if (folderName != folders[i]) {
	          // If not stored, then it means this is the first time to pass by this folder.
	          // So store it in the FolderNames folder by its depth level
	          folders[i] = folderName;
	          // Create an entry for this parent folder as title
	          text.push("  ".repeat(i + 1) + "- **" + folderName + "**");
	        }
	      }
	    }
	    // If the note parent folder is already stored in the variable.
	    // It means that no need to create an entry for the parent folder.
	    // And now create an entry of the file name as a link
	    let fileNameLink = "[[" + p.file.name + "]]";
	    let indent = "  ".repeat(depth + 1);
	    text.push(indent + "- " + fileNameLink);
	  });
	// Join all text entries and render them as a Div
	dv.el("div", text.join("\n"));
	```

## Resources

- [Dataview plugin snippet showcase - Share & showcase - Obsidian Forum](https://forum.obsidian.md/t/dataview-plugin-snippet-showcase/13673?filter=summary)
- [DataviewJS Snippet Showcase - Share & showcase - Obsidian Forum](https://forum.obsidian.md/t/dataviewjs-snippet-showcase/17847)
- [reddit.com: search results - dataview](https://www.reddit.com/r/ObsidianMD/search/?q=dataview)
- [Why is Dataview so great? : r/ObsidianMD](https://www.reddit.com/r/ObsidianMD/comments/x0xwwp/why_is_dataview_so_great/)
- [Dataview Example Vault](https://s-blu.github.io/obsidian_dataview_example_vault/)
- [Plugin Tutorials - Obsidian TTRPG Tutorials](https://obsidianttrpgtutorials.com/Obsidian+TTRPG+Tutorials/Plugin+Tutorials/Plugin+Tutorials#Dataview+and+Other+Advanced+Plugins)
- [Basic Dataview Query Builder](https://s-blu.github.io/basic-dataview-query-builder/)
- 