---
title:       "Quick Projects To Make Your Computer More Productive"
subtitle:    ""
description: "A practical list of small project ideas you can build when you have free time, from workstation setup and learning trainers to backup scripts, deployment helpers, demo videos, recovery USBs, and desktop improvements. Each idea is meant to make future work faster, safer, or easier to resume."
date:        2026-06-26
author:      "Anthony Cavuoti"
image:       ""
tags:        ["productivity", "automation", "projects"]
categories:  ["Tech" ]
---

# Quick Projects To Make Your Computer More Productive

Sometimes you have just enough time to build something, but not enough time to start a giant app. That is the perfect time to make small projects that improve how you work every day.

The best quick projects do one of four things:

- remove a repeated manual step
- make your computer more reliable
- turn a skill you want to learn into a real practice loop
- protect your work from mistakes or bad security assumptions

Here are project ideas worth making when you have free time.

# 1. Neovim And Codex Developer Workstation Config

Make your editor and terminal behave exactly the way you expect.

This can be a small project around your Neovim config, dotfiles, clipboard behavior, shell aliases, Codex permission defaults, and local launcher scripts. The goal is not to endlessly tweak your setup. The goal is to remove friction you hit every day.

A good first version:

- make copy, paste, yank, and put consistent between your editor and system clipboard
- document the permissions your local AI or automation tools are allowed to use
- add a small restore script so a new machine can get the same setup
- keep a changelog of weird fixes so you do not solve the same problem twice

This kind of project feels small, but it compounds. Every future coding session gets a little smoother.

# 2. No-Sleep Workstation Reliability Setup

If you run long builds, downloads, agents, tests, or local servers, make a workstation profile that stays awake while plugged in.

The deliverable can be simple:

- prevent sleep while plugged in
- prevent automatic lock during long trusted sessions
- stop dimming during demos or monitoring
- add a restore command that brings normal power behavior back

This is not glamorous, but it prevents a lot of wasted time. A computer that sleeps in the middle of a long operation is not being helpful.

# 3. Open World FPS GDScript Trainer

Instead of learning a language from random examples, build a trainer around one of your actual projects. The version from my checklist was an Open World FPS GDScript Trainer.

For example, if you are learning GDScript for Godot, make a terminal program that opens lessons tied to your real game files. Each lesson can ask you to change a function, run checks, and explain what changed.

Useful pieces:

- lesson files mapped to real source files
- progress tracking
- text-based checks
- hints that point to the exact project code being practiced
- review mode for old lessons

This turns learning into maintenance. You are not only studying syntax. You are making your own codebase easier to understand.

# 4. Godot Open World FPS Prototype

A Godot Open World FPS prototype is a great productivity project if you treat it like a systems practice lab.

Build a small first-person prototype where you can test input, physics, entities, diagnostics, save files, generated worlds, and simple AI. The point is not to finish a commercial game. The point is to create a playground where programming ideas become visible.

Good small milestones:

- player movement
- jumping or collision
- pick-up items
- simple enemy behavior
- procedural chunks
- debug overlays
- save and load snapshots

Game projects make abstract programming ideas easier to see because every bug moves on screen.

# 5. Stoneforge AI Agent Handoff Workspace

If you use AI tools for coding, make a workspace for tasks, handoffs, reviews, and background work. My checklist version of this was the Stoneforge Orchestration Workspace, built around Codex agents, worker tasks, merge reviews, and background steward work.

The small version can be a folder with structured files:

- current task
- project rules
- known risks
- commands that are safe to run
- commands that need caution
- agent handoff notes
- review checklist

The larger version can coordinate multiple local agents, but even the small text-file version is useful. It keeps work from becoming a vague chat history that nobody can resume cleanly.

# 6. Stoneforge Game AI Behavior Framework

If you are already making game prototypes, split out a reusable behavior framework.

The Stoneforge Game AI Framework version could include:

- state machines
- movement decisions
- navigation helpers
- pressure or alert states
- spawn rules
- smoke tests for behavior

The productive part is that you stop rebuilding enemy logic from scratch in every project. You start with reusable patterns and tune them for the current game.

# 7. Coolify WebDAV Sync Server

Build a tiny private sync service for apps that support WebDAV.

The checklist version was a Coolify WebDAV Server for syncing tools like Super Productivity. The useful version should include:

- Docker Compose setup
- environment-driven username and password
- persistent data mount
- persistent config mount
- a readme with setup, backup, and restore steps
- smoke tests for upload, download, list, and delete

This project teaches deployment, secrets, storage, and basic service testing. It also gives you a real thing you can use for syncing productivity apps.

# 8. OpenClaw Coolify Deployment Gateway

Make a deployment project that exposes a small gateway and a control UI for one of your tools.

My version of this idea was the OpenClaw Coolify Deployment project. Keep the first version practical:

- Docker Compose files
- health checks
- origin allowlist
- websocket or API token bootstrap
- readme handoff instructions
- local smoke tests

This is a good project because it forces you to think beyond "it runs on my machine." You have to think about startup, health, configuration, security, and future maintenance.

# 9. Ventoy Dream USB Builder

Make a workspace that builds your ideal repair and install USB.

The Ventoy Dream USB Builder version can stage:

- Linux ISO files
- persistence files
- boot menu notes
- checksums
- a manual Windows 11 installer path
- scripts to rebuild the bundle

This is productive because it helps future you. When a machine breaks, you do not want to invent your recovery process under pressure.

# 10. Shopify Navigation Product Demo

Make a polished product demo for a very specific app idea.

One good version is a Shopify navigation builder demo made with Remotion and Next.js. Build a video or interactive page that explains:

- visual menu-tree editing
- categories and actions
- mobile behavior
- publish flow
- storefront preview
- the rules for child nodes and links

This is not just marketing. A demo project forces you to clarify what the product actually does. If you cannot explain the workflow clearly, the app probably needs more design work.

# 11. Singularity Fiverr Clone

Build a small services marketplace prototype without trying to clone every feature of a giant platform.

The checklist version was the Singularity Fiverr Clone. The useful version can include:

- service listings
- seller profiles
- order request flow
- status tracking
- simple review model
- admin moderation page

This is a good project because marketplaces expose real product questions fast. Who creates the listing? Who trusts who? What happens when a job changes scope? Even a rough prototype can teach a lot.

# 12. Automated GitHub Repository Script

Make a script that creates and prepares new repositories in a repeatable way.

This pairs well with deployment automation work like the Coolify projects. The script can:

- create a private repo
- add a standard readme
- add branch protection reminders
- add topics
- set a remote
- push the first commit
- print the next manual steps

This is especially useful if you often make small deployment, experiment, or template repos. It also teaches where automation should stop. Some repo settings are security-sensitive and should be explicit.

# 13. GitHub CLI One-Time Repository Backup Project

This idea came from a security conversation about GitHub CLI, `gh`, local tokens, `delete_repo`, protected branches, and protecting repositories from a compromised machine.

The project is not an automatic mirror. Automatic mirrors can copy bad states after a destructive push. The safer idea is a one-time backup operation that you run intentionally, verify, and then disconnect.

Build a tool that can:

- list all repositories you own or control
- clone each repo as a full mirror when you need full history
- optionally download zip archives when you only need a static snapshot
- write a manifest with repo name, date, default branch, and backup location
- store the backup on an external drive or separate account
- log out of GitHub CLI or revoke the token after the operation

Add a warning directly in the readme: test on throwaway repos first. A backup script is powerful, so it should be treated like a migration tool, not a casual helper.

The same project can include a checklist for hardening important repositories:

- avoid unnecessary delete permissions
- protect `main` or `master` from force pushes
- protect `main-backup` and `backup/drift-*` branches from deletion
- require pull requests where it matters
- keep admin credentials separate from daily development credentials
- use GitHub Rulesets or Branch Protection for server-side enforcement

The important lesson is that local settings are not enough. If someone controls your computer, they may control your local tools. The strongest protections live on the remote service and in offline backups.

# 14. Arch Linux Live Wallpaper Setup

This one sounds less serious, but it can still help.

Make a small Arch Linux desktop customization project that selects, crops, loops, and installs a calm live wallpaper. Keep it low contrast so it does not fight your windows. Add a script that can turn it off when you need maximum performance.

This is productive in a different way. A workspace you like using is easier to sit down at.

# A Good Rule For These Projects

Do not start with the giant version.

Start with the smallest useful artifact:

- a script
- a readme
- a template repo
- a local prototype
- a checklist
- a smoke test
- a demo video

Then stop when the project starts paying you back. The goal is not to collect half-finished side quests. The goal is to make your future work faster, safer, or easier to understand.
