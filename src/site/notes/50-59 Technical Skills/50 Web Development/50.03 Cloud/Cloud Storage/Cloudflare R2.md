---
{"created":"2024-04-28T20:49:07","modified":"2024-04-28T21:59:00","up":null,"tags":null,"completed":null,"dg-publish":true,"permalink":"/50-59-technical-skills/50-web-development/50-03-cloud/cloud-storage/cloudflare-r2/","dgPassFrontmatter":true,"updated":"2024-04-28T21:59:00"}
---

# Cloudflare R2


## Overview

High-performance storage for files and objects with zero egress charges.

Cloudflare R2 Storage allows developers to store large amounts of unstructured data without the costly egress bandwidth fees associated with typical cloud storage services.

You can use R2 for multiple scenarios, including but not limited to:

- Storage for cloud-native applications
- Cloud storage for web content
- Storage for podcast episodes
- Data lakes (analytics and big data)
- Cloud storage output for large batch processes, such as machine learning model artifacts or data sets

## R2 Pricing

- [Pricing · Cloudflare R2 docs](https://developers.cloudflare.com/r2/pricing/)

| |Free|Paid - Rates|
|---|---|---|
|Storage|10 GB / month|$0.015 / GB-month|
|Class A Operations|1 million requests / month|$4.50 / million requests|
|Class B Operations|10 million requests / month|$0.36 / million requests|

## Pros

- It has a generous free-tier
- Supports S3 API which is excellent for compatibility. Especially, S3 CLI commands.

## Guides

### Create R2 Bucket

1. Redirect to [Cloudflare](https://www.cloudflare.com/) and sign in
2. From the left sidebar click on `R2`
3. Click on `Create bucket` button
4. Enter a name for the bucket and then click `Create bucket` button.

### Generate R2 API Token

1. Redirect to [Cloudflare](https://www.cloudflare.com/) and sign in
2. From the left sidebar click on `R2`
3. On the right side column, click on `Manage R2 API Tokens` link.
4. Click on `Create API token` button to navigate to creation form. In the creation form
	1. Enter your token name
	2. Set permission according to your needs. Most common needs is to set `Object Read & Write` to allow two-way communication.
	3. Under Specify buckets, choose whether the API to access all buckets or specific ones. It is recommended to apply to specific buckets
	4. Click on `Create API Token` button.
5. In the API token creation summary, you will be displayed with:
	1. Token value
	2. Access Key ID
	3. Secret Access Key
	4. Use jurisdiction-specific endpoints for S3 clients
	- Be noted that "*Token value*", "*Access Key ID*", and "*Secret Access Key*" values are shown only on this screen, make sure to copy them before navigating from it.

### Set Your Bucket for Public Access

1. Redirect to [Cloudflare](https://www.cloudflare.com/) and sign in
2. From the left sidebar click on `R2`
3. Click on your bucket name under `Buckets`
4. In Bucket page, click on `Settings` tab.
5. In Settings page, under Public access, you will find a section called `R2.dev subdomain` that has `Allow Access` button; click on it.
6. Copy `Public R2.dev Bucket URL`