# Anti-AI Writing

> A Claude skill that edits any piece of writing to remove AI tells. Strips the words, phrases, and structures that mark a draft as machine-generated. Returns a clean rewrite that still sounds like the writer, only sharper.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) [![Claude Code](https://img.shields.io/badge/Claude-Code-orange)](https://claude.com/claude-code) [![Claude Cowork](https://img.shields.io/badge/Claude-Cowork-orange)](https://claude.com) [![Skills](https://img.shields.io/badge/skill-anti--ai-purple)](skills/anti-ai-writing/SKILL.md)

Your reader can spot AI writing within a sentence. "Delve," "unlock the potential of," em dashes, the rule of three, "in today's fast-paced world." Once the reader notices, you lose them. This skill is the fix. Paste a draft. Get back a version that does not read like a chatbot.

**Two install paths in one repo.** Claude Code users install it as a plugin. Claude Cowork users drop in the bundled `.skill` file. Same skill, same references, both audiences.

---

## What's inside

A single skill, `anti-ai-writing`, with one entry point and three reference files.

- `SKILL.md` (172 lines). The workflow. Read draft, scan against banned list, rewrite, reread aloud, output with diagnosis.
- `references/banned-list.md` (153 lines). The full Era 1 / Era 2 / Era 3 banned word list. Banned phrases. Banned structural patterns (em dashes, the default rule of three, bulleted bold titles, formulaic transitions, weak verbs). Spanish AI tells. Master alphabetical list at the bottom for quick scanning.
- `references/rewrites.md` (200 lines). How to fix each kind of violation. Word-level substitutions. Phrase-level rewrites. Em dash patterns. Rule of three fixes. Bulleted-bold-title fixes. Formulaic transition fixes. Weak verb fixes. What to do when the rule kills the rhythm.
- `references/examples.md` (200 lines). 30 before-and-after pairs across tweets, emails, LinkedIn posts, blog intros, marketing copy, About pages, internal communication, and Spanish examples. Calibration set for the skill.

The skill works in any language. The English banned list is the most complete. The Spanish list is a starter map; additions welcome via PR.

---

## Install

### For Claude Code users

Two commands in any Claude Code session.

```bash
/plugin marketplace add avectats7/anti-ai-writing
/plugin install anti-ai-writing
```

After install, the `anti-ai-writing` skill triggers on phrases like:
- "make this sound less like AI"
- "remove the AI tells"
- "humanise this draft"
- "this reads like ChatGPT"
- "rewrite without 'delve' and 'unlock'"
- "proofread for AI words"
- "edit this so it sounds human"

To uninstall:

```bash
/plugin uninstall anti-ai-writing
/plugin marketplace remove avectats7/anti-ai-writing
```

### For Claude Cowork users

Download the packaged skill:

[**Download anti-ai-writing.skill**](dist/anti-ai-writing.skill)

Open the file. Cowork will offer to install. Click install. Done.

### For manual install (any environment with Claude skill support)

```bash
git clone https://github.com/avectats7/anti-ai-writing.git
cp -r anti-ai-writing/skills/anti-ai-writing ~/.claude/skills/
```

---

## How it works

The skill follows a five-step workflow on every edit.

1. **Read once, in full.** No editing on the first pass. Get the meaning and the writer's voice.
2. **Scan against the banned list.** Word-level, phrase-level, structure-level. Every fingerprint noted.
3. **Build the rewrite.** Apply the patterns from `references/rewrites.md`. Preserve the writer's voice and sentence length.
4. **Reread aloud.** If it sounds like a committee wrote it, redo.
5. **Output with diagnosis.** Show what was wrong, what changed, why.

Every output includes four blocks: Diagnosis (what was found), Rewrite (the fix), Changes (the biggest 3-6 edits with rationale), Notes (anything debatable or ambiguous).

---

## A before-and-after to show what good looks like

**Before**

> In today's fast-paced world, our innovative platform empowers users to seamlessly navigate complex workflows and unlock the full potential of their data.

Diagnosis: 5 banned words ("innovative," "empowers," "seamlessly," "navigate," "unlock"), 2 banned phrases ("in today's fast-paced world," "full potential"), no concrete claim.

**After**

> Our software cuts the average workflow from 47 steps to 12, and turns your customer database into reports your team can actually read.

Same product. Different tradition. Specifics replace abstractions. The reader knows what is on offer.

---

## What this is and what it is not

### What it is

A stylistic editor. Job: take an existing draft and remove the fingerprints that mark it as AI-generated. Returns a clean rewrite plus a diagnosis.

A learning tool. The diagnosis block teaches the writer which patterns they keep falling into. Used regularly, the writer drafts cleaner over time.

A multilingual tool. English banned list is the most complete. Spanish is mapped. Other languages: ask the writer to confirm and apply the same principles.

### What it is not

A generator. The skill does not write from scratch. For original copy, use a generator skill (e.g. [`copy-that-sells`](https://github.com/avectats7/copy-that-sells)).

A truth checker. The skill is stylistic, not editorial. Bad arguments stay bad after the AI tells are removed.

A censor. Many banned words have legitimate technical uses ("framework" for a named software framework, "key" for a cryptographic key, "navigate" for literal UI navigation). The rule bans these as filler, not as precise terms. Edge cases are handled in the SKILL.md.

---

## Why this skill exists

The modern LLM voice has a default. The default has become so recognisable that readers spot it within a sentence. Once spotted, trust drops, engagement drops, the writer loses.

The fingerprints are not random. They come from optimisation pressure: words that test as "professional" in human feedback, structures that produce balanced answers across topics, hedges that make wrong answers feel less wrong. Individually fine. Collectively, a sound.

The fix is mechanical: a list of fingerprints, applied with discipline. That is what this skill does. It will not make a writer better. It will keep a good writer from sounding like the machine they used to draft.

---

## Frequently asked questions

### What is the Anti-AI Writing skill?

A Claude skill that takes a piece of writing and removes the words, phrases, and structures that mark it as machine-generated. It returns a clean rewrite plus a diagnosis of what was wrong. Works in any Claude product that supports skills (Claude Code, Claude Cowork, the Claude desktop and web apps with skill support).

### Who is it for?

Writers who use AI for first drafts. Marketers cleaning up agency or AI-drafted copy. Founders writing their own LinkedIn posts. Students. Anyone whose first draft comes out sounding like a press release written by a committee of bots.

### How does it differ from a Grammarly-style proofreader?

Grammarly checks grammar and spelling. This skill checks for AI-default register: banned vocabulary, formulaic phrases, structural fingerprints. The two are complementary. Run Grammarly for grammar, this skill for voice.

### Does it work in Spanish?

Yes. The English banned list is the most comprehensive. The Spanish list (in `references/banned-list.md`) is a starter map that catches the most common Spanish AI tells: "aprovechar," "potenciar," "fomentar," "panorama," "en el mundo actual," "cabe destacar." Latino Spanish and Castilian Spanish have different fingerprints; the skill asks if it is unclear which the writer is using.

### Will the rewrite still sound like me?

Yes if the skill is working correctly. The rewrite preserves your voice, sentence length, level of formality, and punctuation habits (within the rules). What it strips is the AI-default register, not your style. If a rewrite has flattened your voice, the SKILL.md has a section on what to do (`What to do when the rule kills the rhythm`).

### What about words like "framework" that have legitimate technical meanings?

Legitimate technical uses are kept. "Framework" when referring to Rails or React is fine. "Framework" as filler ("a framework for thinking about X") is not. The skill applies judgement.

### Can I use this commercially?

Yes. MIT license. Use it, modify it, ship it. Attribution is welcome but not required.

### Can I add new banned words or new examples?

Yes. See [CONTRIBUTING.md](CONTRIBUTING.md). The Spanish list especially welcomes additions.

### What if my draft has AI tells inside a quote from someone else?

The skill preserves quoted material verbatim. Banned words inside a real quote are part of the historical record. The skill notes them in the Diagnosis block but does not change them. See the Edge Cases section of SKILL.md.

### Does this work with the `copy-that-sells` skill?

They pair well. `copy-that-sells` generates new ad copy. This skill cleans up existing drafts. If you use both, run `copy-that-sells` first (to generate), then this one (to polish).

---

## Repo structure

```
anti-ai-writing/
├── .claude-plugin/
│   ├── plugin.json              Claude Code plugin manifest
│   └── marketplace.json         Single-plugin marketplace
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   ├── new_banned_word.md
│   │   └── new_example.md
│   └── PULL_REQUEST_TEMPLATE.md
├── skills/
│   └── anti-ai-writing/
│       ├── SKILL.md             Entry point. The workflow.
│       └── references/
│           ├── banned-list.md   Full Era 1/2/3 banned words, phrases, structures.
│           ├── rewrites.md      How to fix each violation.
│           └── examples.md      30 before-and-after pairs.
├── dist/
│   └── anti-ai-writing.skill    Cowork install bundle.
├── docs/
│   └── install.md               Detailed install guide.
├── README.md                    This file.
├── llms.txt                     LLM optimisation file.
├── LICENSE                      MIT.
├── CONTRIBUTING.md              How to contribute new banned items or examples.
├── CHANGELOG.md                 Version history.
└── .gitignore
```

---

## Sister skill

This skill plays well with [`copy-that-sells`](https://github.com/avectats7/copy-that-sells), a generator for marketing copy that earns attention. `copy-that-sells` writes. This skill polishes. Install both.

---

## Maintainer

Tato Polanco. Senior marketing operator. 10+ years in fintech, SaaS, and Web3. Six Telly Awards including one for copywriting. Based in Vigo, Spain.

GitHub: [@avectats7](https://github.com/avectats7)

---

## Keywords

For search and discovery: Claude skill, Claude Code skill, Claude Cowork skill, anti-AI writing tool, humanise AI text, AI text editor, AI tells remover, ChatGPT detector and rewriter, AI proofreader, AI writing cleanup, banned words list, AI fingerprints, sound human, write like a human, GPT writing fix, anti-ChatGPT writing skill, copywriting editor, marketing copy editor, Spanish AI writing fix.
