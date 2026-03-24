# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a single-file static cheatsheet for the [Gemini CLI](https://github.com/google-gemini/gemini-cli). Everything — HTML, CSS, and JS — lives in `index.html`. There is no build step, no package manager, and no dependencies.

To preview: open `index.html` directly in a browser.

## Architecture

`index.html` is structured in three sections:

1. **`<style>`** — all CSS using CSS custom properties (`--bg`, `--text`, `--cyan`, etc.) defined in `:root`. OS-specific visibility is controlled via body classes (`os-mac`, `os-linux`, `os-win`) applied by JS; elements use classes like `.blk-mac` / `.blk-linux` / `.blk-win` to show/hide per-OS content.

2. **`<body>`** — a sticky `<header>` with OS toggle buttons, then a `.grid` containing 10 `.card` elements (one per topic). Each card contains `.sub` subsections with `.row` entries (description + key/command). Inline code uses semantic span classes: `.sl` (slash command), `.cmd` (shell command), `.flag` (CLI flag), `.val` (value), `.path` (file path), `.key` (kbd shortcut).

3. **`<script>`** — ~15 lines that handle OS toggle: sets `document.body.className` to `os-mac/linux/win` based on `navigator.userAgent`, and wires up the toggle buttons.

## Content conventions

- Each card maps to one topic area; card order and titles are intentional.
- Per-OS code blocks use `blk-mac`, `blk-linux`, `blk-win` classes — always provide all three variants when adding OS-specific content.
- Version badge (`v1.x`) is in the header and should be updated when the CLI version changes.
