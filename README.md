# karpathy-llm-wiki

**Battle-tested LLM Wiki skill for Claude Code, Cursor & Codex**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/Astro-Han/karpathy-llm-wiki?style=social)](https://github.com/Astro-Han/karpathy-llm-wiki)
[![GitHub forks](https://img.shields.io/github/forks/Astro-Han/karpathy-llm-wiki?style=social)](https://github.com/Astro-Han/karpathy-llm-wiki)
[![Agent Skills](https://img.shields.io/badge/Agent_Skills-compatible-blue)](https://agentskills.io)
[![Install](https://img.shields.io/badge/Install-npx_add--skill-green)](https://github.com/Astro-Han/karpathy-llm-wiki#install)

<p align="center">
  <img src="assets/karpathy-tweet.png" alt="Karpathy's tweet about LLM Wiki" width="560">
</p>

## Battle-Tested Results

> **Key Takeaways**
> - ✅ Production-ready: 94 articles, 99 sources, daily use since April 2026
> - ✅ Works with Claude Code, Cursor, Codex CLI, OpenCode
> - ✅ Agent Skills standard (SKILL.md) compatible
> - ✅ Three operations: Ingest → compile sources into wiki, Query → search with citations, Lint → health checks

This skill powers a **production knowledge base** that's been in daily use since April 2026:

| Metric | Count | Growth |
|--------|-------|--------|
| Wiki articles | **94** | 48 → 94 (nearly doubled) |
| Source materials | **99** | From zero |
| Topic directories | **13** | 8 → 13 |
| Operation log entries | **87** | Every day |
| Recent 7 days activity | **87 entries** | Active maintenance |

Top topics: ai-coding-tools (29 articles), ai-research (24), product-design-frameworks (8).

See [examples/](examples/) for real articles, raw sources, and the operation log. See [SKILL.md](SKILL.md) for the full skill specification.

## Quick Install

```bash
npx add-skill Astro-Han/karpathy-llm-wiki
```

Works with Claude Code, Cursor, Codex, and other tools that support the [Agent Skills](https://agentskills.io) standard. See [docs/SPEC.md](docs/SPEC.md) for detailed architecture and design decisions.

## Quick Start

**1. Ingest your first source**

Give the skill a URL, a file, or paste text directly:

> "Ingest this article: https://example.com/attention-is-all-you-need"

The skill fetches the content into `raw/`, then compiles it into a wiki article under `wiki/`.

**2. Ask your wiki a question**

> "What do I know about attention mechanisms?"

The skill searches your wiki and answers with citations linking back to your articles.

**3. Keep it healthy**

> "Lint my wiki"

The skill checks for broken links, missing index entries, stale cross-references, and reports potential issues.

## How Your LLM Wiki Works

**What is this skill?**

This skill is a SKILL.md-compatible implementation of Karpathy's knowledge compilation pattern. It turns raw documents into a structured, interlinked wiki that compounds over time.

Inspired by [Karpathy's LLM Wiki idea](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) (published April 4, 2026, 2,100+ stars in 12 hours):

> "The LLM writes and maintains the wiki; the human reads and asks questions."

**What is the Agent Skills standard?**

Agent Skills is an open standard for defining reusable skills via `SKILL.md` files. It's supported by Claude Code, Cursor, Codex CLI, OpenCode, and other LLM coding tools. The standard enables skill discovery, installation via `npx add-skill`, and cross-tool compatibility.

**Architecture**

```
your-project/
├── raw/            ← Immutable source material (you or the LLM add, never modify)
│   └── topic/
│       └── 2026-04-03-source-article.md
├── wiki/           ← Compiled knowledge (LLM maintains)
│   ├── topic/
│   │   └── concept-name.md
│   ├── index.md    ← One-page table of contents
│   └── log.md      ← Append-only operation log
```

Three operations:

| Operation | What it does |
|-----------|-------------|
| **Ingest** | Fetch a source into `raw/`, compile into `wiki/`, update index and cross-references |
| **Query** | Search the wiki and answer with citations. Optionally archive answers as wiki pages |
| **Lint** | Auto-fix broken links and index gaps. Report contradictions, orphan pages, stale content |

The wiki compounds over time. Each new source enriches existing articles, adds cross-references, and flags conflicts.

## Tool Compatibility

This skill follows the [agentskills.io](https://agentskills.io) open standard. It works with any LLM coding tool that supports SKILL.md:

| Tool | Install method |
|------|---------------|
| Claude Code | `npx add-skill Astro-Han/karpathy-llm-wiki` |
| Cursor | `npx add-skill Astro-Han/karpathy-llm-wiki` (auto-converts) |
| Codex CLI | Copy to `.agents/skills/karpathy-llm-wiki/` |
| OpenCode | `npx add-skill Astro-Han/karpathy-llm-wiki` |
| Others | Copy `SKILL.md` + `references/` to your tool's skill directory |

**Alternative implementations**: See [lucasastorian/llmwiki](https://github.com/lucasastorian/llmwiki) (MCP-based web app) and [atomicmemory/llm-wiki-compiler](https://github.com/atomicmemory/llm-wiki-compiler) (CLI compiler) for other approaches to Karpathy's LLM Wiki pattern.

## Inspired By

This is an unofficial community implementation of the knowledge compilation workflow described in [Karpathy's idea file](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) (April 2026). The core value is a battle-tested set of compilation principles and workflow templates, not the code itself.

## FAQ

**What is an LLM Wiki?**

An LLM Wiki is a knowledge management system where a large language model automatically writes, maintains, and queries a structured wiki from your raw source materials. Unlike RAG which retrieves at query time, an LLM Wiki compiles knowledge once into interlinked pages that compound over time.

**Which tools are compatible?**

Claude Code, Cursor, Codex CLI, OpenCode, and any tool that supports the Agent Skills (SKILL.md) standard. Install with `npx add-skill Astro-Han/karpathy-llm-wiki`.

**How does this differ from RAG?**

RAG searches raw document chunks at each query, re-deriving relationships every time. LLM Wiki pre-compiles documents into structured pages with cross-references, entity pages, and an index. Each new source enriches existing articles instead of being searched independently. Knowledge compounds, not repeats.

**What sources can I ingest?**

URLs (web articles, papers, blog posts), local files (PDFs, markdown, text), or pasted text. The skill converts everything to markdown in `raw/` and compiles into `wiki/`.

**Is this production-ready?**

Yes. This skill powers a real knowledge base with 94 articles and 99 sources, maintained daily since April 2026. See [examples/](examples/) for actual wiki pages and operation logs.

**How do I start?**

```bash
npx add-skill Astro-Han/karpathy-llm-wiki
```

Then tell your LLM: "Ingest this article: [URL]"

## License

[MIT](LICENSE)