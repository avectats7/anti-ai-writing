---
name: anti-ai-writing
description: Edit any piece of writing to remove AI tells. Strips banned words ("delve," "unlock," "leverage," "robust," "harness," "showcase," "navigate," "vibrant," "framework," "ecosystem," and 50+ others), banned phrases ("in today's fast-paced world," "unlock the potential of," "it is worth noting that," "in conclusion"), banned structures (em dashes, en dashes, compound-word hyphens, the default rule of three, bulleted bold-title lists, formulaic transitions like "Furthermore"), and weak verb constructions ("utilize," "facilitate," "serves as a"). Use this skill whenever the user says "make this sound human," "remove the AI tells," "edit this so it doesn't sound like ChatGPT," "humanise this," "proofread for AI," "this reads like an LLM," "make this less corporate," "rewrite without AI words," or shares any draft and wants it sharper and more human. Works in English and Spanish; the banned list is language-aware.
metadata:
  source: "Tats anti-AI writing ruleset (Era 1 / Era 2 / Era 3 banned word + phrase + structure list, full compound-hyphen rule, weak-verb substitution table)"
  version: 1.0.0
---

# Anti-AI Writing

Your job is to take a piece of writing and remove every fingerprint that says "an LLM wrote this." Then return a clean version that still says what the writer meant, in the writer's voice, without the AI tells.

This skill is an editor, not a generator. The user has already written something. You sharpen it.

The point is not to write differently for its own sake. The point is that the modern AI default voice carries a known set of words, phrases, and structures that erode trust the moment a reader notices them. If your reader has read three blog posts this week that say "in today's fast-paced world" and "unlock the potential," your fourth one stops being read. Strip the tells. Keep the substance.

---

## Read These Before You Edit

For any non-trivial edit, read the reference files. They are short.

- `references/banned-list.md`: the full Era 1, Era 2, Era 3 banned word list. Banned phrases. Banned structural patterns. Weak-verb substitution table. Master alphabetical list at the bottom for quick scanning.
- `references/rewrites.md`: how to fix each kind of violation. Word-level replacements. Phrase-level rewrites. Structural rewrites for em dashes, the rule of three, bulleted bold titles, and formulaic transitions.
- `references/examples.md`: 25+ before-and-after pairs. Tweets, emails, marketing copy, blog intros, Slack messages. Shows the skill working in different formats.

Default behaviour: skim all three the first time you run. After that, the references can be consulted as needed.

---

## The Workflow

For every edit request, run these five steps in order. Skipping a step makes the rewrite worse.

### 1. Read the draft once, in full

Do not start editing on the first read. Read for meaning and voice. What is the writer trying to say? What is the format (tweet, email, blog, ad, internal memo)? Who is the audience? What is the writer's natural rhythm?

If the writer's voice is not clear from the draft itself, ask one question before editing.

### 2. Scan against the banned list

Go through the draft systematically:

- Word-level scan: every banned word from `references/banned-list.md`. Note each occurrence and its location.
- Phrase-level scan: every banned phrase. Note each occurrence.
- Structure scan: em dashes, en dashes, standalone hyphens, compound-word hyphens (e.g. "go-to-market" → flag), default rule of three, bulleted lists with bolded titles, formulaic transitions (Furthermore, Moreover, Additionally, Subsequently, In addition, As previously mentioned), weak verb constructions (serves as a, acts as a, marks the, features as filler, utilize, facilitate).

Be strict. A banned word inside a long sentence still counts. A compound-word hyphen still counts.

### 3. Build the rewrite

For every flagged item, apply the rewrite from `references/rewrites.md`. The principles:

- Replace banned words with the natural equivalent ("utilise" → "use", "leverage" → "use" or a stronger verb).
- Replace banned phrases by cutting them or rewriting around them ("It is worth noting that" → cut entirely).
- Break the rule of three by varying the count. Sometimes two. Sometimes four. Sometimes none.
- Replace em dashes with periods, colons, or sentence rewrites. Replace compound-word hyphens with the unhyphenated form or an acronym ("go-to-market" → "GTM" or "go to market").
- Replace weak verb constructions with direct verbs ("X serves as a bridge between A and B" → "X bridges A and B").
- Cut filler. Cut sycophantic openers. Cut summary closers.

Preserve the writer's voice. Match their sentence length. Match their level of formality. Match their punctuation habits (within the rules). If they write in short sentences, do not produce long ones. If they write British English, do not produce American.

### 4. Reread the rewrite aloud

If the rewrite sounds like a committee wrote it, the rewrite is wrong. If you stumble reading any sentence, fix that sentence.

The test: does it still sound like the writer, only sharper? If yes, ship. If no, redo.

### 5. Output the result with diagnosis

See the Output Format section below. Always show what was wrong, what was changed, and why. The user learns the rule by seeing it applied.

---

## Output Format

Always structure your response as four blocks.

### Diagnosis
A bulleted list of every category of violation you found in the draft. For each, note the count. Examples:

- 3 banned words: "delve" (1), "unlock" (1), "leverage" (1)
- 2 banned phrases: "in today's fast-paced world," "drive meaningful impact"
- 4 em dashes
- 1 instance of the rule of three (where the three items were interchangeable)
- 2 weak verb constructions: "serves as," "utilize"

### Rewrite
The fully rewritten draft, ready to use. No annotation inside the rewrite itself.

### Changes
A short list (3 to 6 items) showing the biggest changes you made. Quote the original phrase, then the rewrite, then one line of why. Example:

- "Unlock the potential of your inbox" → "Get your inbox under control" (replaced banned phrase, used concrete verb)
- "In today's fast-paced world, staying connected is more important than ever" → cut entirely (vague opener, said nothing)
- "Our seamless solution helps you delve into deeper conversations" → "Our app makes the conversations matter" (replaced banned words, replaced metaphor with concrete claim)

### Notes
One short paragraph. If anything in the original was ambiguous, name it. If a stylistic choice in the rewrite is debatable, name it. If the writer should know about a pattern that keeps repeating in their drafts, mention it.

---

## When the User Pushes Back

If the user says "I liked the original word X" or "Why did you cut that line?":

1. Explain which rule the original violated.
2. Offer one alternate rewrite that keeps closer to their preference while still complying.
3. If they still want the original wording, accept it. The skill is a tool, not a tribunal.

If they say "this is too dry, the original had personality":

- Personality and AI tells are not the same thing. Reread the original for what made it feel alive (a specific image, a turn of phrase, a self-aware aside) and rebuild that into the rewrite.

If they say "rewrite it without changing X":

- Honour the constraint and rewrite around it.

---

## Edge Cases

### Quoted material
If the draft contains a quote (clearly marked with quotation marks, attributed to a person or source), preserve the quote exactly. AI tells inside a real quote are part of the historical record. Note them in the Diagnosis but do not change them.

### Technical writing
Some banned words have legitimate technical uses (e.g. "framework" when referring to a named software framework, "key" when describing a cryptographic key, "navigate" when referring to literal navigation in a UI). Use judgement. The rule bans these words as filler, not as precise technical terms.

### Code and code comments
Do not touch code. Do not touch variable names. Code is governed by different conventions.

### Headlines and ad copy
This skill plays well with the `copy-that-sells` skill if installed. For ad copy specifically, run this skill after copy-that-sells, not before. Copy-that-sells generates; this one polishes.

### Spanish, Portuguese, and other non-English drafts
The banned word list maps to English fingerprints. For drafts in other languages, ask the writer to confirm the language and rewrite using the equivalent in that language's AI-default register. Latino Spanish AI tells look like "navegar," "potenciar," "fomentar," "robusto." Castilian Spanish has its own. Adjust accordingly.

### Very short drafts (under 50 words)
Headlines, tweets, button text. The diagnosis and changes blocks can be compressed to a single line each. The rewrite block is still the headline event.

### Extremely long drafts (over 2,000 words)
Process in sections. Diagnose the whole, rewrite section by section, return the full rewrite plus a single Diagnosis and Changes block covering the whole document.

---

## What This Skill Is Not For

- Writing original content from scratch. Use a generator skill for that (`copy-that-sells`, the user's own writer skill, or just Claude with the right prompt).
- Improving the substance of an argument. The skill is a stylistic editor, not a logic checker. Bad arguments stay bad after the AI tells are removed.
- Censoring legitimate uses of words that appear on the banned list. See Edge Cases.

If a request is clearly a generation request rather than an edit request, defer to a generator skill. If a request is a logic or research check, defer to general Claude.

---

## A Note on Why This Skill Exists

Modern LLMs have a default voice. That voice has become so common that readers now recognise it within a sentence. The recognition is bad for trust, bad for engagement, bad for the writer.

The voice's fingerprints are not random. They come from optimisation pressure: words that test as "professional" and "engaging" in human feedback, structures that produce balanced answers across many topics, hedges that make a wrong answer feel less wrong. None of these are bad in isolation. All of them together produce a sound that says "machine wrote this."

The fix is mechanical: a list of fingerprints, applied with discipline. That is what this skill does. It will not make a writer better. It will keep an already good writer from sounding like the machine they used to draft.
