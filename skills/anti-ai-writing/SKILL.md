---
name: anti-ai-writing
description: Edits any piece of writing to remove AI tells. Strips banned words ("delve," "unlock," "leverage," "robust," "harness," "showcase," "navigate," "vibrant," "framework," "ecosystem," and 50+ others), banned phrases ("in today's fast-paced world," "unlock the potential of," "it is worth noting that," "in conclusion"), banned structures (em dashes, en dashes, compound-word hyphens, the default rule of three, bulleted bold-title lists, formulaic transitions like "Furthermore"), and weak verb constructions ("utilize," "facilitate," "serves as a"). Use this skill whenever the user says "make this sound human," "remove the AI tells," "edit this so it doesn't sound like ChatGPT," "humanise this," "proofread for AI," "this reads like an LLM," "make this less corporate," "rewrite without AI words," or shares any draft and wants it sharper and more human. Also strips discourse-level tells that survive a surface edit: stated takeaways, single-track structure, manufactured closure, emotion rendered as physical sensation, atmospheric openers, vague unnamed references, front-loaded context, and the closing epilogue paragraph. Also runs a strict review mode that audits a draft against both layers and returns a verdict and finding list instead of a rewrite, triggered by "strict review," "audit this," "score this," "does this pass," "review estricto," or any request for a judgement rather than an edit. Works in English and Spanish; the banned list is language-aware.
metadata:
  source: "Tats anti-AI writing ruleset (Era 1 / Era 2 / Era 3 banned word + phrase + structure list, full compound-hyphen rule, weak-verb substitution table). Discourse layer adapted from Russell et al. 2026, STORYSCOPE."
  version: 2.0.0
---

# Anti-AI Writing

Your job is to take a piece of writing and remove every fingerprint that says "an LLM wrote this." Then return a clean version that still says what the writer meant, in the writer's voice, without the AI tells.

This skill is an editor, not a generator. The user has already written something. You sharpen it.

The point is not to write differently for its own sake. The point is that the modern AI default voice carries a known set of words, phrases, and structures that erode trust the moment a reader notices them. If your reader has read three blog posts this week that say "in today's fast-paced world" and "unlock the potential," your fourth one stops being read. Strip the tells. Keep the substance.

---

## Two layers

The skill edits at two levels, and both passes are required.

**Layer 1, the surface.** Words, phrases, punctuation, sentence structure. Governed by `references/banned-list.md` and `references/rewrites.md`. This is what most people mean by AI tells.

**Layer 2, the discourse.** What the piece explains, what it resolves, what it names, how it opens and closes, and whether it talks to the reader. Governed by `references/discourse-tells.md` and `references/discourse-rewrites.md`.

Layer 2 exists because Layer 1 is not enough. Russell et al. (2026) measured 61,608 stories across one human source and five models and found that discourse features alone separate human from AI writing at 93.2% macro-F1, with zero access to word choice or punctuation. When they stripped the surface artifacts out of AI stories and ran the test again, detection went to 93.9%. Cleaning the surface did not move the structure.

So a draft can pass every rule in `banned-list.md` and still read as machine-written. Layer 2 is the fix for that.

Layer 2 is bounded in three ways, and the bounds are not optional. It does not apply to every register: legal, compliance, and Simplified Technical English documents need the habits it removes. It scales with length: a twelve-word message cannot carry a subplot, so most of the layer is unevaluable there. And it carries an addition budget, because an invented aside is worse than the tell it replaced.

The corpus behind Layer 2 is ~5,000-word fiction. Never quote its percentages to a writer when explaining an edit on an email. Name the habit, not the statistic.

---

## Read These Before You Edit

For any non-trivial edit, read the reference files. They are short.

- `references/banned-list.md`: the full Era 1, Era 2, Era 3 banned word list. Banned phrases. Banned structural patterns. Weak-verb substitution table. Master alphabetical list at the bottom for quick scanning.
- `references/rewrites.md`: how to fix each kind of violation. Word-level replacements. Phrase-level rewrites. Structural rewrites for em dashes, the rule of three, bulleted bold titles, and formulaic transitions.
- `references/discourse-tells.md`: Layer 2. Eight structural habits to cut, six human signals to restore, the Claude-specific fingerprint, the batch convergence rule, a ten-question scan checklist, and the registers where none of this applies.
- `references/discourse-rewrites.md`: how to fix each structural habit, with worked pairs in email, chat, LinkedIn, client report, and landing page. Register playbooks. Sequence-level editing. What to do when a Layer 2 fix costs clarity.
- `references/strict-review.md`: audit mode. The scorecard, the verdict table, what does not count as a violation, and the output format for reviews.
- `references/examples.md`: 40 before-and-after pairs. Tweets, emails, marketing copy, blog intros, Slack messages, plus ten pairs that isolate the discourse layer.

Default behaviour: skim all six the first time you run. After that, the references can be consulted as needed. For any draft longer than a chat message, read the two discourse files.

---

## Two modes

**Default mode edits.** The user has a draft and wants it fixed. Run the workflow below and return the rewrite.

**Strict review mode audits.** The user wants to know what is wrong and how badly, not a cleaned-up version. Triggers: "strict review," "audit this," "score this," "does this pass," "check this against the rules," "review estricto," "how bad is this," or any request phrased as a judgement. Also use it when the user is checking writing that is not theirs, or their own writing from before the ruleset.

In strict review mode, read `references/strict-review.md` and follow it instead of the workflow below. The differences that matter: no rewrite unless asked afterwards, findings scored by severity and density rather than raw count, every finding carries a quote, no praise and no cushioning, the verdict in the first line rather than the last, and a closing line naming what the draft would lose if every finding were applied.

Two things that mode gets wrong if you skip the file. A Clean verdict scores the absence of tells, not the presence of anything worth reading, so inert prose scores well. And the report is an internal working document: "Fails" describes a draft against a ruleset, but forwarded to the person who wrote it, it describes them.

Both modes share the same rules. What changes is whether you fix or judge.

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

### 2b. Scan the discourse layer

First check the register. Legal, compliance, procedural, or technical documentation: skip this step and say so in Notes.

Then check the length band, which sets what applies and how many additions are allowed:

| Band | Applies | Additions |
|---|---|---|
| Under 40 words | No scaffolding, one concrete specific, no stated takeaway | 0 |
| 40 to 200 words | Habits 1, 5, 6, 7, 8 | 1 |
| 200 to 800 words | All eight habits | 2 |
| Over 800 words | All eight plus time jumps and thread structure | 3 |

Batch convergence applies at every band, including the shortest, because it compares pieces rather than looking inside one.

Then run the ten-question checklist in `references/discourse-tells.md`:

1. Does the last sentence explain what the piece meant?
2. Does everything in it serve one clean line?
3. Does it end with the writer in control of an unresolved situation?
4. Is any emotion expressed as a physical sensation instead of named?
5. Does it open on mood, scene, or restated context instead of content?
6. Is there at least one real name, number, or date?
7. Is there at least one moment that acknowledges the reader?
8. Is there at least one thing left open, uncertain, or conceded?
9. Does it assume shared history rather than rebuilding it?
10. If part of a set: does it differ structurally from its neighbours?

Any yes in 1 to 5 is a habit to cut. Any no in 6 to 10 is a signal to restore, subject to the budget and the register gates: naming a feeling belongs in personal and internal writing, not client work, and a stated doubt about your own recommendation never appears in the same client-facing piece as an open item.

### 3. Build the rewrite

For every flagged item, apply the rewrite from `references/rewrites.md`. The principles:

- Replace banned words with the natural equivalent ("utilise" → "use", "leverage" → "use" or a stronger verb).
- Replace banned phrases by cutting them or rewriting around them ("It is worth noting that" → cut entirely).
- Break the rule of three by varying the count. Sometimes two. Sometimes four. Sometimes none.
- Replace em dashes with periods, colons, or sentence rewrites. Replace compound-word hyphens with the unhyphenated form or an acronym ("go-to-market" → "GTM" or "go to market").
- Replace weak verb constructions with direct verbs ("X serves as a bridge between A and B" → "X bridges A and B").
- Cut filler. Cut sycophantic openers. Cut summary closers.

Then apply the Layer 2 fixes from `references/discourse-rewrites.md` for whatever the checklist flagged, and only that. Running all eight habits because all eight exist is how a checklist turns into a register.

Three rules govern this pass.

- Subtraction before addition. Six of the eight habits are fixed by deleting something.
- The source test. Every addition must trace to something real: a line in the draft, a message in the thread, a figure in the data, a doubt the writer voiced. If you cannot point at it, cut it and say so in Notes. This replaces "never fake the mess," which is advice rather than a test.
- The open-item contract. A loose end kept in client-facing work carries an owner, a date, and a statement of what it does and does not affect. Missing any of the three, it gets cut rather than kept.

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

Then a second short block for the discourse layer, naming only what you found:

- Stated takeaway in the final sentence
- Atmospheric opener: first paragraph sets mood, content starts in paragraph two
- No named specifics in three of four claims
- Epilogue: closing paragraph adds nothing
- No acknowledgement of the reader anywhere

If the draft is in a register where Layer 2 does not apply, write one line saying so instead.

### Rewrite
The fully rewritten draft, ready to use. No annotation inside the rewrite itself.

### Changes
A short list (3 to 6 items) showing the biggest changes you made. Quote the original phrase, then the rewrite, then one line of why. Example:

- "Unlock the potential of your inbox" → "Get your inbox under control" (replaced banned phrase, used concrete verb)
- "In today's fast-paced world, staying connected is more important than ever" → cut entirely (vague opener, said nothing)
- "Our seamless solution helps you delve into deeper conversations" → "Our app makes the conversations matter" (replaced banned words, replaced metaphor with concrete claim)

For Layer 2 changes, describe the move rather than quoting a substitution:

- Cut the closing paragraph (epilogue; nothing was lost)
- Moved the ask to sentence one, deleted the scene-setting opener
- Replaced "industry benchmarks suggest" with the actual competitor bid range (verify the figures)
- Kept the unresolved tracking issue as a separate paragraph instead of folding it into the summary

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

### Registers where the discourse layer does not apply

Layer 2 assumes the writer had a choice about structure. Several registers remove that choice, and the habits it strips are requirements there:

- Simplified Technical English, procedures, safety and operating instructions
- Legal, compliance, GDPR, privacy, and contractual text
- Regulatory and tax correspondence
- Technical documentation and API references
- Client reporting under a mandated house template

For these, run Layer 1 only and say so in the Notes block. Explicitness, closure, and single-track logic are the specification, not the tell.

Two narrower gates apply inside registers where Layer 2 does run. Naming a feeling in plain words is a restore for personal essays, first-person posts, internal messages, and founder updates, not for client deliverables, proposals, reporting, or marketing copy, where the right emotional register is usually none. And a stated doubt about your own recommendation never shares a client-facing piece with an open item: either alone reads as candour, both together read as a lost account.

In every gated case the matching cut still runs. Habit 4 comes out of a client email even though signal 4 cannot go in, and the replacement is the fact, not a feeling.

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
