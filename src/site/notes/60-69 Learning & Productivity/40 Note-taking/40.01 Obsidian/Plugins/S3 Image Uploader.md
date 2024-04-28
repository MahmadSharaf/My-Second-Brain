---
{"created":"2024-01-01T15:05:16","modified":"2024-04-28T21:32:11","up":null,"tags":null,"completed":null,"installed":false,"dg-publish":true,"permalink":"/60-69-learning-and-productivity/40-note-taking/40-01-obsidian/plugins/s3-image-uploader/","dgPassFrontmatter":true,"updated":"2024-04-28T21:32:11"}
---



up:: [[60-69 Learning & Productivity/40 Note-taking/40.01 Obsidian/Plugins/+ Obsidian Plugins\|Obsidian Plugins]]
tags:: #obsidian #plugin 

# Obsidian Plugin - S3 Image Uploader

- GitHub:: https://github.com/jvsteiner/s3-image-uploader
- Documentation:: No docs found
- Obsidian URL:: https://obsidian.md/plugins?id=s3-image-uploader
- Obsidian URI:: [obsidian://show-plugin?id=s3-image-uploader](obsidian://show-plugin?id=s3-image-uploader)
- Settings:: [obsidian://advanced-uri?settingid=s3-image-uploader](obsidian://advanced-uri?settingid=s3-image-uploader)
- Mobile-compatible:: true

## Overview

- It is a solution for uploading media files like images, videos, audios, and PDF, to a S3-Compatible cloud storage.
- It supports upload on:
	- drag and drop
	- copy and paste
- It supports the option to copying the files to a local folder instead of uploading

If you do not want this behavior in all notes, you can customize it on a per note basis.

1. You can add an `uploadOnDrag` YAML frontmatter tag to the note, as seen below.
2. You can also set the `localUpload` option to `true`, which will copy the images to a folder in your local file system, instead of uploading them to the cloud, overriding the global setting.
3. You can also set note specific folder where the images will be uploaded to, by adding the `localUploadFolder` option to the YAML frontmatter. This overrides the global setting.

These settings override the global settings. The `uploadOnDrag` tag affects both S3 and local uploads. The other two options only affect local uploads.

```YAML
---
uploadOnDrag: true
localUpload: true
localUploadFolder: "my-folder"
---
```

## Installation

You have to set up your own s3 bucket, or s3-compatible service like [[50-59 Technical Skills/50 Web Development/50.03 Cloud/Cloud Storage/Cloudflare R2\|Cloudflare R2]], and configure it as below:

1. [[50-59 Technical Skills/50 Web Development/50.03 Cloud/Cloud Storage/Cloudflare R2#Create R2 Bucket\|Create an R2 Bucket]]
2. [[50-59 Technical Skills/50 Web Development/50.03 Cloud/Cloud Storage/Cloudflare R2#Generate R2 API Token\|Generate an R2 API Token]] to get:
	1. Token value
	2. Access Key ID
	3. Secret Access Key
	4. Use jurisdiction-specific endpoints for S3 clients
3. [[50-59 Technical Skills/50 Web Development/50.03 Cloud/Cloud Storage/Cloudflare R2#Set your bucket for public access\|Set your bucket for public access]] and get `Public R2.dev Bucket URL`
4. Configure as below
	1. Set `AWS Access Key ID` as "*Access Key ID*" value you got on step 2.3
	2. Set `AWS Secret Key` as "*Secret Access Key*" value you got on step 2.2
	3. Set `Region` as `auto`
	4. Set `S3 Bucket` as the name of the bucket you created in step 1
	5. `Bucket folder`: the folder in your bucket where you want to store the images (optional, and will be created on the fly if it does not exist.)
	6. Enable flag `Use custom endpoint`
	7. Set `Custom S3 Endpoint` as "*Use jurisdiction-specific endpoints for S3 clients*" value you got on step 2.4
	8. Enable flag `Use custom image URL`
	9. Set `Custom image URL` as "Public R2.dev Bucket URL" value you got on step 3
	10. **NECESSARY STEP**: Restart Obsidian

## Preferences

I am using Cloudflare R2 Cloud Storage, since it has a generous free-tier, and I am already hosting my website.

## Tricks

- It requires restarting Obsidian to update the settings.
- The region for R2 is `wnam`

## Resources


