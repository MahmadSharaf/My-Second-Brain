---
{"title":"Obsidian Plugin - Digital Garden","created":"2023-07-05T20:39","modified":"2023-09-07T21:11","tags":["obsidian","plugin"],"dg-publish":true,"dg-path":"Obsidian/Plugins/Digital Garden.md","permalink":"/obsidian/plugins/digital-garden/","dgPassFrontmatter":true,"updated":"2023-09-07T21:11"}
---

# Obsidian Plugin - Digital Garden

- GitHub:: https://github.com/oleeskild/obsidian-digital-garden
- Documentation:: https://dg-docs.ole.dev/
- Obsidian URL:: https://obsidian.md/plugins?id=digitalgarden
- Obsidian URI:: [obsidian://show-plugin?id=digitalgarden](obsidian://show-plugin?id=digitalgarden)
- Settings:: [obsidian://advanced-uri?settingid=digitalgarden](obsidian://advanced-uri?settingid=digitalgarden)

## Overview

**Publish your notes to the web, for free. In your own personal garden.**

The [Obsidian Digital Garden Plugin](https://github.com/oleeskild/obsidian-digital-garden) is a free and open source publishing tool for [Obsidian](https://obsidian.md).

Publish your notes directly from [Obsidian](https://obsidian.md/) to the internet. While [feature packed](https://dg-docs.ole.dev/features/), it is [highly configurable](https://dg-docs.ole.dev/getting-started/03-note-settings/) and [hackable](https://dg-docs.ole.dev/advanced/adding-custom-components/). Enable and disable features on a per-note basis. Use it as a full-fledged digital garden or as a [simple note sharing solution](https://dg-docs.ole.dev/example-pages/simple-page/).

👉 [Getting Started](https://dg-docs.ole.dev/getting-started/01-getting-started/)  
👉 [Features](https://dg-docs.ole.dev/features/)

### Features

- Basic Markdown Syntax
- Links to other notes
- Dataview queries (as code blocks, inline and dataviewjs)
- Backlinks
- Obsidian Themes
- Style settings
- Local graph
- File tree navigation
- Global search
- Callouts/Admonitions
- Embedded/Transcluded Excalidraw drawings
- Embedded/Transcluded Images
- Transcluded notes
- Code Blocks
- MathJax
- Highlighted text
- Footnotes
- Mermaid diagrams
- PlantUML diagrams

### Note Global Settings

Settings presented in the plugin settings are global and applied instantly. But it is possible to set specific settings for a note using front matter.

#### Show home Link

Frontmatter: `dg-home-link`

Determines whether to show a link back to the homepage or not.

#### Show Local Graph for Notes

Frontmatter: `dg-show-local-graph`

When turned on, notes will show its local graph in a sidebar on desktop and at the bottom of the page on mobile.

#### Show Backlinks for Notes

Frontmatter: `dg-show-backlinks`

When turned on, notes will show backlinks in a sidebar on desktop and at the bottom of the page on mobile.

#### Show a Table of Content for Notes

Frontmatter: `dg-show-toc`

When turned on, notes will show all headers as a table of content in a sidebar on the desktop. It will not be shown on mobile devices.

#### Show Inline Title

Frontmatter: `dg-show-inline-title`

When turned on, the title of the note will show on top of the page.

#### Show File Tree Sidebar

Frontmatter: `dg-show-file-tree`

When turned on, a file tree will be shown on your site.

#### Enable search

Frontmatter: `dg-enable-search`

When turned on, users will be able to search through the content of your site.

#### Enable Link Preview

Frontmatter: `dg-link-preview`

When turned on, hovering over links to notes in your garden shows a scrollable preview.

#### Show Tags

Frontmatter: `dg-show-tags`

When turned on, tags in your frontmatter will be displayed on each note. If search is enabled, clicking on a tag will bring up a search for all notes containing that tag.

#### Let All Frontmatter through

Frontmatter: `dg-pass-frontmatter`

Determines whether to let all frontmatter data through to the site template. Be aware that this could break your site if you have data in a format not recognized by the template engine, 11ty.

### Note Specific Settings

#### Title

Frontmatter: `title: "My Custom Title"`

Add a custom page title instead of the name of your note. This allows you to use characters that are not allowed to use in filenames. (Ex: ":", "/", "|")

#### Custom Links

Frontmatter: `dg-permalink: "mynote"`

Set a custom URL for the note, disregarding its file structure. 

The permalinks can be an arbitrary level of folders deep, such as: `dg-permalink: "category/2022/mynote/"`

#### File Path

Frontmatter: `dg-path: "Advanced/Features.md"`

Set a custom file structure for the note

#### Pinning Notes to File Tree

Frontmatter: `dg-pinned: true`

Pin the note at the top of the folder it is in.

#### Hide File from File Tree

Frontmatter: `dg-hide: true`

Hide a note from the file tree

#### Hide Note from Graph

Frontmatter: `dg-hide-in-graph: true`

Hide note from graph view.

#### Metatags

Setting metatags for a note can be done by adding a dg-metatags attribute like so:

```
dg-metatags:
 description: "some description"
 "og:image": "https://example.com/someimage.png"
```

Note that there is a single space before the "description" field, **not** a tab.

This feature can be used if you want custom titles and images when sharing links in social media. Using the example below will add a title and an image that will be used when sharing the link in social media.

```
dg-metatags:
 "og:title": "Title Appearing on Social Media Site"
 "og:image": "https://example.com/someimage.png"
```

Read more about the [Open Graph Protocol](https://ogp.me/)

#### Body Classes

Frontmatter: `dg-content-classes: cards`

Allows to customize each note with specific class.

It is possible to change the frontmatter key. For example, from `dg-content-classes` to `cssClasses`

#### Note Icons

Frontmatter: `dg-show-tags`

When turned on, tags in your frontmatter will be displayed on each note. If search is enabled, clicking on a tag will bring up a search for all notes containing that tag.

Each note can have an associated note icon. By default, this is set by the  
`dg-note-icon` property, but this can be changed in the [note icon settings](https://dg-docs.ole.dev/getting-started/04-appearance-settings/#note-icon-settings).  
By default, the plugin provides 4 options: `default`, `1`, `2`, and `3`.

The provided icons look like this:
default: ![](https://raw.githubusercontent.com/oleeskild/digitalgarden/3d0155d9923c36f3637f87bf45b7142c6162e608/src/site/img/default-note-icon.svg)
1: <img src="https://raw.githubusercontent.com/oleeskild/digitalgarden/3d0155d9923c36f3637f87bf45b7142c6162e608/src/site/img/tree-1.svg"  width="35" height="35">
2: <img src="https://raw.githubusercontent.com/oleeskild/digitalgarden/3d0155d9923c36f3637f87bf45b7142c6162e608/src/site/img/tree-2.svg"  width="35" height="35">
3: <img src="https://raw.githubusercontent.com/oleeskild/digitalgarden/3d0155d9923c36f3637f87bf45b7142c6162e608/src/site/img/tree-3.svg"  width="35" height="35">

##### Changing and Adding Icons

You can change and add your own icons the following way:

The ideal way to change the default icons is by adding the svgs in the img folder and setting the appropriate css vars in body in a [custom css file](https://dg-docs.ole.dev/advanced/adding-custom-components/#dynamic-css-scss):

```css
body {
  --note-icon-1: url(/img/your-custom.svg);
  --note-icon-2: url(/img/tree-2.svg);
  --note-icon-3: url(/img/tree-3.svg);
  --note-icon-fallback: url(/img/default-note-icon.svg);}
}
```

To add new icons, let's say, for 'stone', add a snippet like this (and add the relevant svg) in a [custom css file](https://dg-docs.ole.dev/advanced/adding-custom-components/#dynamic-css-scss):

```css
body.title-note-icon .cm-s-obsidian > header > h1[data-note-icon="stone"]::before,
body.filetree-note-icon .filename[data-note-icon="stone"]::before,
body.links-note-icon .internal-link[data-note-icon="stone"]::before,
body.backlinks-note-icon .backlink[data-note-icon="3"]::before {
  background-image: url(/img/stone.svg);
}
```
### Custom Filters

If you want any of your content to be modified before publishing the note, you can add a filter. For example, hide text that is inside a specific pattern.

It also supports Regex groups, meaning you can use $1, $2 etc. in the replacement string to insert the first and second regex group and so on.
## Usage



## Preferences



## Tricks



## Resources

- [Tips and Tricks](https://dg-docs.ole.dev/advanced/tips-and-tricks/)
