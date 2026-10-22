---
name: aicombase
description: Work on the user's WordPress sites through AICOMBase — create and edit pages and posts, Elementor pages, WooCommerce products, translations, menus and media, or fix what AICOMBase's site checks found. Use when the user asks for a change on one of their WordPress sites, or asks what is wrong with them.
---

# Working on WordPress sites through AICOMBase

AICOMBase connects the user's WordPress sites (each runs the free AICOM plugin). Its tools let you do real work on those sites within the access the user approved: the sites, the permissions and the mode they chose when they connected you. Everything you do is recorded, and the user can undo it.

## Before the first job

- If the AICOMBase tools aren't available or answer that sign-in is needed, tell the user to run `/mcp`, choose **aicombase** and sign in. AICOMBase then asks them which sites and permissions to allow. Nothing else is needed — no key to copy.
- Call `initialize` (your client does this) and follow the working rules AICOMBase returns in its instructions. They are tailored to the user's access and win over anything here.

## How to do a job

1. **Find the site.** Use `sites.list`. If the user didn't say which site, or several match, ask — never guess a site.
2. **Open one session per job.** `session.open` with the site, a short name after the job ("Create Contact page") and a one-line description of what you'll do and why. Without an open session every change is refused.
3. **See what the site offers.** `capabilities.list` shows the tools you may use there and their arguments (in Tool Assist mode, describe the job to `tools.suggest` instead; in MCPAssist mode, just say it to `mcpassist`).
4. **Do the work** with `tasks.create`, one action at a time, and check each result with `tasks.get`.
5. **Read back what you changed** — the page, the post, the price — and give the user the link (for drafts, the preview link).
6. **Close the session** with `session.close`: the outcome and a one-line summary of what you did.

## Good habits

- Create pages and posts as **drafts** unless the user said to publish.
- For the same change on several sites, do it site by site, each in its own session, and report which sites succeeded.
- A refusal (permission, policy, lock, key limit) is final. Don't retry it in a loop — tell the user what was refused and why; they can change the access in AICOMBase (Keys, or Policies → "Why can't my AI agent…?").
- If MCP Guard asks you to justify an action (`guard_challenge`), explain honestly with `guard.justify` and repeat the same call. If an action is `held_for_approval`, stop and tell the user it waits for their approval in AICOMBase.
- Never ask for WordPress passwords. AICOMBase never needs them.
- If the user wants something undone, point them to **Work** in AICOMBase: every job there has an Undo button (when a step kept no backup, Work says which one).

## Useful questions to answer with the tools

- "What did the site checks find on example.com?" — `findings.list`, then `findings.get` for one.
- "Is anything down?" — `incidents.list`.
- "What's new?" — `notifications.list`.
- "What did people ask you to do?" — `tasks.pending` lists tasks the user wrote in AICOMBase for you; `tasks.resolve` does one.
