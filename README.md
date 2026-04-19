# Obsidian Note Analyzer

A lightweight AI-powered tool that scans your Obsidian vault and generates a knowledge gap report — helping you notice what your first brain can't.

## Why This Exists

The Zettelkasten method is powerful because it turns reading into thinking. But as your vault grows, patterns emerge that are invisible to you: you've been accumulating notes on the same concept without realizing it, all your sources on a topic lean the same way, or a note you wrote 8 months ago is now outdated.

This tool runs Claude Code against your vault and surfaces:
- **Emerging themes** across your Reference, Literature, and Permanent Notes
- **Source diversity gaps** — when your reading on a topic is one-sided or platform-narrow
- **Staleness flags** — notes that haven't been touched in 3+ months on fast-moving topics
- **Synthesis readiness** — when you've accumulated enough to write a Permanent Note (your own publishable thesis)

## How It Works

Claude Code reads your `.md` files directly from your local vault — nothing leaves your machine. It identifies themes autonomously (you don't define them), then analyzes each one. The report is written back into your vault as a dated `.md` file for you to review and delete once processed.

## Prerequisites

- [Obsidian](https://obsidian.md/) with a Zettelkasten vault structure
- [Claude Code](https://claude.ai/code) installed (`npm install -g @anthropic-ai/claude-code`)
- A Claude Pro subscription or Anthropic API account
- Node.js (install via `nvm`)

## Vault Structure

This tool assumes the following folder structure:

```
Your Vault/
├── 1. Permanent Notes/   ← your original publishable ideas
├── 2. Literature Notes/  ← your own commentary on external sources
└── 3. Reference Notes/   ← raw input with your comments (Kindle, Media, etc.)
```

If your structure is different, update the folder paths in `CLAUDE.md`.

## Setup

1. Clone this repo:
```bash
git clone https://github.com/YOUR_USERNAME/obsidian-note-analyzer.git
cd obsidian-note-analyzer
```

2. Open `CLAUDE.md` and replace the vault path with your own:
```
/Users/YOUR_USERNAME/path/to/your/vault
```

3. (Optional) Add an alias for one-command launch:
```bash
echo 'alias obsidian-note-analyzer="cd /path/to/obsidian-note-analyzer && claude"' >> ~/.zprofile
source ~/.zprofile
```

## Daily Usage

```bash
obsidian-note-analyzer
```

Then type:
```
run vault analysis
```

The report will appear in your vault root as `Vault Analysis YYYY-MM-DD.md`. Review it, act on what's useful, delete when done.

## Report Structure

Each theme section contains:
- **Most relevant notes** (max 3) with folder type and last modified date
- **Source diversity** — platforms represented + what's missing
- **Staleness** — age flag + directional update on what's changed
- **Synthesis readiness** — whether you have enough to write a Permanent Note, and a suggested thesis if so

Followed by a **Summary** with your top 3 actions for the week.

## Customization

- Change the staleness threshold (default: 3 months) in `CLAUDE.md`
- Add or remove folder paths to expand/narrow the scan
- Modify the report format in `CLAUDE.md` to match your preferences
