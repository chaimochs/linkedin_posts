# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This directory stores LinkedIn posts for Byzwize LLC. Each post lives in its own date-named folder (`MMDDYYYY/`), containing the post text and any images.

**Source repository:** https://github.com/chaimochs/linkedin_posts.git (private repo, clone via HTTPS)

## Folder Structure

```
linkedin_posts/
  MMDDYYYY/           # one folder per post/publishing session
    text.md           # post body text
    image0.png        # images, 0-indexed
    image1.png
    ...
```

## Publishing to LinkedIn

Posts are published via the **Blotato MCP** (`mcp__blotato__*` tools).

Standard publishing flow:
1. Call `blotato_list_accounts` to get the LinkedIn `accountId`.
2. Read `text.md` for the post body.
3. Prepare image URLs — `mediaUrls` must be publicly accessible URLs. Options:
   - Host on GitHub: commit and push files to `chaimochs/linkedin_posts`, then use raw.githubusercontent.com URLs (e.g., `https://raw.githubusercontent.com/chaimochs/linkedin_posts/main/MMDDYYYY/image0.png`)
   - Use any other public hosting (CDN, cloud storage, etc.)
   - Use Blotato's visual/source pipeline to generate or process images
4. Call `blotato_create_post` with `platform: "linkedin"`. Omit `pageId` to post to personal profile; include it for a company page.

To schedule instead of posting immediately, pass `scheduledTime` (ISO 8601) or `useNextFreeSlot: true`.

## Publishing to Instagram

Posts are published via the **Blotato MCP** (`mcp__blotato__*` tools).

Standard publishing flow:
1. Call `blotato_list_accounts` to get the Instagram `accountId`.
2. Read `text.md` for the post caption (use the full text as-is, no editing).
3. Prepare image URLs for a carousel — pass all images as an array in `mediaUrls`. Images must be publicly accessible URLs (see LinkedIn instructions above for hosting options).
4. Call `blotato_create_post` with `platform: "instagram"`, `mediaUrls` array, and `mediaType: "reel"` or omit for standard carousel post.

To schedule instead of posting immediately, pass `scheduledTime` (ISO 8601) or `useNextFreeSlot: true`.

## Permissions

Pre-approved tools (no confirmation needed):
- `mcp__blotato__blotato_list_accounts`
- `mcp__blotato__blotato_create_post`

## Relevant Skills

- `/blog` — use this skill to draft a new LinkedIn post for Byzwize.
