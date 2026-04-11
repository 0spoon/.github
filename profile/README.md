<p align="center">
  <img src="./assets/0spoon-full.webp" alt="0spoon" width="800">
</p>

<p align="center">
  <a href="#license"><img src="https://img.shields.io/badge/license-MIT-green.svg?style=flat-square" alt="License: MIT"></a>
  <img src="https://img.shields.io/badge/local--first-yes-brightgreen.svg?style=flat-square" alt="Local-first">
  <img src="https://img.shields.io/badge/filesystem--native-yes-brightgreen.svg?style=flat-square" alt="Filesystem-native">
</p>

# 0spoon

> _"Do not try to bend the spoon. That's impossible. Instead, only try to realize the truth... there is no spoon."_

Open-source tools for working with AI coding agents — **without pretending the agent is in charge.**

The agent doesn't know your project. It doesn't remember yesterday. It commits to the wrong branch, forgets why it made a decision, and starts every conversation from zero. The fix isn't a smarter model. The fix is infrastructure: durable memory, enforced guardrails, and artifacts you can read without the agent in the loop.

0spoon builds that infrastructure. Local-first. Filesystem-native. Single-user. Markdown on disk, git worktrees on disk, nothing hiding in a vendor's database.

---

## Projects

### [Seam](https://github.com/0spoon/seam) — _where ideas connect_

![Last commit](https://img.shields.io/github/last-commit/0spoon/seam?style=flat-square)
![Top language](https://img.shields.io/github/languages/top/0spoon/seam?style=flat-square)
![Open issues](https://img.shields.io/github/issues/0spoon/seam?style=flat-square)
![License](https://img.shields.io/github/license/0spoon/seam?style=flat-square)

A local-first personal knowledge system that doubles as **persistent memory for your agents.** Notes are plain `.md` files with YAML frontmatter. An MCP server exposes 40+ tools so Claude Code, Cursor, Windsurf — anything MCP-compatible — can search your notes, create new ones, track tasks, traverse a knowledge graph, and collaborate through shared research labs. What one agent learns, the next one knows, because they're working in the same files you are.

Go backend (REST + WebSocket), React web UI, Bubble Tea TUI. SQLite with FTS5, ChromaDB for vectors, Ollama for local LLM by default. OpenAI and Anthropic are one config line away if you want them.

**Not a memory layer.** A workspace: notes, projects, tasks, wikilinks, semantic search, daily briefings, and an autonomous librarian that organizes untouched notes for you.

### [projd](https://github.com/0spoon/projd) — _a harness for long-running and parallel agents_

![Last commit](https://img.shields.io/github/last-commit/0spoon/projd?style=flat-square)
![Top language](https://img.shields.io/github/languages/top/0spoon/projd?style=flat-square)
![Open issues](https://img.shields.io/github/issues/0spoon/projd?style=flat-square)
![License](https://img.shields.io/github/license/0spoon/projd?style=flat-square)

Claude Code works great in a single sitting. Long sessions and parallel agents fall apart: lost context, wrong branches, half-finished code, agents stepping on each other. projd adds the missing pieces — session continuity via `.projd/HANDOFF.md`, git policy enforced by PreToolUse hooks before commands execute, a feature lifecycle with dependency tracking, smoke-test gates, and branch-per-feature worktree isolation.

You describe what you want. projd decomposes it into features with acceptance criteria, dispatches up to 20 agents in dependency-aware waves, and hands you PRs. You review. Or don't — vibes mode closes the loop with an automated reviewer that fixes what it can and merges what passes.

**A project template, not a platform.** It lives inside your repo alongside your code. Nothing global to install, no daemon, no desktop app.

---

## Why these two together

projd is **how** agents do the work. Seam is **where** they remember it. The pairing is the point:

- An agent dispatched by projd calls `session_start` against Seam, gets a briefing of prior decisions and relevant notes, implements the feature, and writes findings back before closing the session. The next agent — or you, next week — picks up with context intact.
- Seam's research lab lets parallel projd agents on the same problem share trials, decisions, and dead ends, instead of each one rediscovering them in isolation.
- Your notes in Seam and your code in your projd-managed repo are both plain files on disk. You can grep them, diff them, back them up with git, sync them with Syncthing, and switch tools next year without an export script.

You can use either one alone. They just happen to fit.

---

## Principles

**Local-first, always.** Your files on your disk. Cloud AI is opt-in, one config line, never required.

**Filesystem-native.** Markdown for knowledge. Git worktrees for parallel work. No proprietary bundles, no export steps, no lock-in. If the project disappears tomorrow, your data is still yours and still readable.

**Opinionated, single-user.** These are tools built by someone who uses them every day, not platforms chasing every audience. The common paths are paved. The sharp edges are real — but they're documented.

**Durable artifacts over ephemeral state.** A `HANDOFF.md` you can open in vim survives a dead laptop. A conversation history in an app's memory does not.

**The agent is a tool, not a teammate.** You stay the protagonist. The infrastructure exists so the model does more useful work — not so you do less thinking.

---

## License

Everything here is MIT unless a repo says otherwise. Contributions welcome; see each project's `CONTRIBUTING.md`.
