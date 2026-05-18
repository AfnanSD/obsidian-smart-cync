# Obsidian Sync Agent

## Project Overview

A lightweight automation pipeline that saves content from a Telegram bot into a local Obsidian knowledge hub.

The workflow is orchestrated using n8n, with Google Sheets acting as a temporary buffer before the content is appended to an Obsidian hub note through the Obsidian Local REST API plugin.

Supported content types include:
- Blogs
- Articles
- YouTube videos
- Books
- Movies
- Podcasts
- Miscellaneous links


---

## Problem It Solves

I wanted a frictionless system for capturing content I plan to consume later while keeping everything organized inside my Obsidian vault.

Instead of manually copying links and categorizing them, this pipeline:
- captures content directly from Telegram
- stores it safely in a buffer layer
- appends it automatically into a centralized Obsidian hub note

This creates a simple personal knowledge ingestion workflow with minimal manual effort.


---

## Architecture


---

## Tech stack

- [n8n](https://n8n.io)
- [Obsidian](https://obsidian.md/)
- [Obsidian Local Rest API Plugin](https://github.com/coddingtonbear/obsidian-local-rest-api)
- [Google Sheets API](https://developers.google.com/workspace/sheets/api/reference/rest)


---

## Why Google Sheets?

The workflow is intentionally split into two agents instead of directly connecting the cloud workflow to Obsidian.

Google Sheets acts as:
- a lightweight buffer and queue layer
- a temporary persistence layer between agents
- a security boundary between the public cloud workflow and the local Obsidian vault

This design prevents exposing the local Obsidian vault directly to the internet or public cloud services.

The cloud-side workflow only interacts with Google Sheets, while the local agent securely pulls and processes entries into Obsidian. This keeps the personal knowledge base isolated while still enabling automated synchronization.


---

## Future Improvements
- Automatic content categorization
- Duplicate detection
- Multi-note routing inside Obsidian