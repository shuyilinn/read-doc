# read-doc

A Claude Code / Claude Agent skill that reads dense technical material **with you**, one section at a time — instead of dumping a summary on you.

## What it's for

**Target:** long, jargon-heavy **technical documents and technical blog posts** — papers, specs, engineering blogs, anything where the long sentences and stacked terminology make the first read painful.

It does **not** summarize. It rewrites the source into the version you actually wanted to read.

## How it works

For each section, the skill runs the same loop:

1. **Splits** the document into one natural section at a time (a heading, or 2–4 tightly-related paragraphs) — never the whole thing at once.
2. **Draws a diagram** (ASCII) wherever the idea is visual: data layouts, memory hierarchies, pipelines, layered architectures, side-by-side comparisons.
3. **Unpacks it** — rewrites the section in plain language, and gives a concrete example the moment any term or abstraction shows up (plain-words definition → "for example…" → optional original term).
4. **Feeds it to you piece by piece** — finishes the section, then **stops and waits** for you before moving on.
5. **Ends each section with 3 short Socratic questions** so you reason it back in your own words. It checks your answers (confirms what's right, corrects what's wrong) before continuing.

It also keeps the thread coherent across sections ("remember that X from earlier?") and, **on request only**, will dig into a local repo to show what the real code/implementation looks like.

## How to use it after cloning

This is a personal skill — normally you just hand it to Copilot / Claude and let it drive.

### Option A — Claude Code (recommended)

Clone into your Claude skills directory so it's available everywhere:

```bash
git clone git@github.com:shuyilinn/read-doc.git ~/.claude/skills/read-doc
```

Then in any Claude Code session:

```
/read-doc path/to/paper.pdf
```

or just point at a file and ask in natural language — trigger phrases include `带我读`, `读这个文档`, `改写成我能读的样子`, or "help me read this".

### Option B — hand the prompt to Copilot / another assistant

The whole skill is a single self-contained prompt in [`SKILL.md`](SKILL.md). If you're not in Claude Code, just paste the body of `SKILL.md` to your assistant as a system/role prompt, then give it the document. The instructions (split → diagram → unpack → feed section-by-section → 3 Socratic questions) work with any capable model.

```bash
git clone git@github.com:shuyilinn/read-doc.git
# open read-doc/SKILL.md, copy its contents into your assistant, then drop in your doc
```

## Notes

- Language follows yours (defaults to Chinese in the prompt, but works in any language).
- It corrects misunderstandings directly rather than letting them slide — that's the part that makes a read actually stick.
