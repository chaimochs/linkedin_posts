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
3. Upload images if needed — `mediaUrls` must be publicly accessible URLs. If images are local files, they cannot be passed directly; they must be hosted first or use Blotato's visual/source pipeline.
4. Call `blotato_create_post` with `platform: "linkedin"`. Omit `pageId` to post to personal profile; include it for a company page.

To schedule instead of posting immediately, pass `scheduledTime` (ISO 8601) or `useNextFreeSlot: true`.

## Permissions

Pre-approved tools (no confirmation needed):
- `mcp__blotato__blotato_list_accounts`
- `mcp__blotato__blotato_create_post`

## Relevant Skills

- `/blog` — use this skill to draft a new LinkedIn post for Byzwize.
