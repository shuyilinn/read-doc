# read-doc

*[English](#read-doc) · [中文](#read-doc--中文)*

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

---

# read-doc — 中文

*[English](#read-doc) · [中文](#read-doc--中文)*

一个 Claude Code / Claude Agent 技能，**陪你**一节一节地读密集的技术材料——而不是甩给你一份总结。

## 用来干嘛

**目标对象：** 又长又堆术语的**技术文档和技术博客**——论文、spec、工程博客，凡是长句套从句、术语扎堆、第一遍读起来很痛苦的东西。

它**不做总结**。它把原文改写成你本来想读的那个样子。

## 它怎么工作

每一节都跑同一个循环：

1. **分段**：一次只处理一个自然小节（一个小标题，或 2–4 个紧密相关的段落）——绝不一口气倒完整篇。
2. **画图**：凡是能形象化的地方就用 ASCII 画图——数据布局、内存层次、管线流程、分层架构、并排对比。
3. **拆解**：用人话重写这一节，每出现一个术语/抽象概念就**立刻**给一个具体例子（人话定义 → "比如……" → 可选的术语原文）。
4. **一段段喂给你**：讲完这一节就**停下来等你**，再进下一节。
5. **每节末尾出 3 个苏格拉底小问题**：让你用自己的话把它复述/推理回来。你答完后它会判对错（对的确认、错的明确纠正），再继续。

它还会保持全篇连贯（"还记得前面那个 X 吗"），并且**仅在你要求时**才去翻本地仓库，给你看真实代码/实现长什么样。

## clone 之后怎么用

这是个人技能——一般你直接丢给 Copilot / Claude 让它来驱动就行。

### 方式 A — Claude Code（推荐）

clone 到你的 Claude 技能目录，这样在哪都能用：

```bash
git clone git@github.com:shuyilinn/read-doc.git ~/.claude/skills/read-doc
```

然后在任意 Claude Code 会话里：

```
/read-doc path/to/paper.pdf
```

或者直接指着文件用自然语言说——触发语包括 `带我读`、`读这个文档`、`改写成我能读的样子`，或者 "help me read this"。

### 方式 B — 把 prompt 丢给 Copilot / 别的助手

整个技能就是 [`SKILL.md`](SKILL.md) 里一段自包含的 prompt。如果你不在 Claude Code 里，把 `SKILL.md` 的正文当作 system/role prompt 粘给你的助手，再把文档给它就行。那套指令（分段 → 画图 → 拆解 → 一段段喂 → 3 个苏格拉底问题）对任何有能力的模型都适用。

```bash
git clone git@github.com:shuyilinn/read-doc.git
# 打开 read-doc/SKILL.md，把内容复制进你的助手，再把要读的文档丢进去
```

## 说明

- 语言跟随你（prompt 里默认中文，但任何语言都能用）。
- 它会直接纠正你的理解偏差，而不是含糊放过——这才是让一次精读真正"读进去"的关键。
