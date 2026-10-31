---
name: anti-ai-writing
description: Edits writing to remove AI tells, in English and Spanish. Layer 1 removes banned words ("delve," "unlock," "leverage," "robust," and 50+ others), banned phrases ("in today's fast-paced world," "it is worth noting that"), banned structures (em dashes, en dashes, compound-word hyphens, the default rule of three, bulleted bold-title lists, "Furthermore") and weak verbs ("utilize," "serves as a"). Layer 2 removes discourse tells that survive a surface edit, such as stated takeaways, atmospheric openers, manufactured closure, vague references, epilogues. Use it when the user says "make this sound human," "remove the AI tells," "humanise this," "proofread for AI," "this reads like an LLM," "make this less corporate," or shares a draft and wants it sharper and more human. Strict review mode audits a draft and returns a verdict and findings, not a rewrite. Use it for "strict review," "audit this," "score this," "does this pass," "review estricto," or any request for a judgement.
metadata:
  source: "Tats anti-AI writing ruleset (Era 1 / Era 2 / Era 3 banned word + phrase + structure list, full compound-hyphen rule, weak-verb substitution table). Discourse layer adapted from Russell et al. 2026, StoryScope (arXiv:2604.03136)."
  version: 2.2.0
---

# Anti-AI Writing

Your task is to remove every mark in a piece of writing that shows "an LLM wrote this." Then return a clean version. The clean version must say what the writer meant, in the voice of the writer, with no AI tells.

This skill is an editor, not a generator. The user already wrote the text. You make it sharper.

The goal is not different writing for its own sake. The default voice of modern AI has a known set of words, phrases and structures. When a reader sees them, the reader stops trusting the text. Suppose that your reader saw "in today's fast-paced world" and "unlock the potential" in three blog posts this week. Then the reader stops reading your fourth post. Remove the tells. Keep the content.

---

## Two layers

The skill edits at two levels. You must do both passes.

**Layer 1, the surface.** Words, phrases, punctuation and sentence structure. `references/banned-list.md` and `references/rewrites.md` give the rules for this layer. Most people mean this layer when they say "AI tells."

**Layer 2, the discourse.** What the piece explains, what it resolves, what it names, how it starts and ends, and whether it speaks to the reader. `references/discourse-tells.md` and `references/discourse-rewrites.md` give the rules for this layer.

Layer 2 is necessary because Layer 1 is not sufficient. Russell et al. (2026) measured 61,608 stories from one human source and five models. Discourse features alone separated human from AI writing at 93.2% macro-F1, with no access to word choice or punctuation. Then the researchers removed the surface artifacts from the AI stories and ran the test again. Detection went to 93.9%. A clean surface did not change the structure.

Thus a draft can obey every rule in `banned-list.md` and still read as machine writing. Layer 2 fixes that problem.

Layer 2 has three limits. These limits are mandatory:

- **Register.** Layer 2 does not apply to every register. Legal, compliance and Simplified Technical English documents need the habits that Layer 2 removes.
- **Length.** Layer 2 changes with the length of the text. A twelve-word message cannot have a subplot, so you cannot evaluate most of the layer on it.
- **Addition budget.** Layer 2 has a limit on additions, because an invented aside is worse than the tell that it replaced.

The research corpus for Layer 2 is fiction of approximately 5,000 words. When you explain an edit on an email, do not quote its percentages to the writer. Name the habit, not the statistic.

---

## Read These Before You Edit

If the edit is not trivial, read the reference files. They are short.

- `references/banned-list.md`: the full Era 1, Era 2 and Era 3 banned word list, the banned phrases, the banned structural patterns and the weak-verb substitution table. A master alphabetical list at the bottom helps you scan quickly.
- `references/rewrites.md`: how to fix each type of violation. Word-level replacements, phrase-level rewrites and structural rewrites for em dashes, the rule of three, bulleted bold titles and formulaic transitions.
- `references/discourse-tells.md`: Layer 2. Eight structural habits to cut, six human signals to restore, the Claude-specific fingerprint, the batch convergence rule, a ten-question scan checklist and the registers where Layer 2 does not apply.
- `references/discourse-rewrites.md`: how to fix each structural habit, with worked pairs in email, chat, LinkedIn, client report and landing page. It also gives register playbooks, sequence-level editing, and what to do when a Layer 2 fix makes the text less clear.
- `references/strict-review.md`: audit mode. The scorecard, the verdict table, what is not a violation and the output format for reviews.
- `references/examples.md`: 40 before-and-after pairs. Tweets, emails, marketing copy, blog intros and Slack messages, plus ten pairs that show only the discourse layer.

On your first run, skim all six files. After that, read them when you need them. If the draft is longer than a chat message, read the two discourse files.

---

## Two modes

**Default mode edits.** The user has a draft and wants you to fix it. Do the workflow below and return the rewrite.

**Strict review mode audits.** The user wants to know what is wrong and how bad it is. The user does not want a clean version. Triggers: "strict review," "audit this," "score this," "does this pass," "check this against the rules," "review estricto," "how bad is this," or any request for a judgement. Also use this mode when the user checks writing that is not their own, or their own writing from before the ruleset.

In strict review mode, read `references/strict-review.md` and follow it. Do not do the workflow below. These are the important differences:

- Do not give a rewrite unless the user asks for one after the review.
- Score findings by severity and density, not by raw count.
- Give a quote for every finding.
- Do not give praise or soften the findings.
- Put the verdict in the first line, not in the last line.
- In the last line, say what the draft loses if you apply every finding.

If you skip the file, this mode makes two mistakes:

- A Clean verdict scores the absence of tells. It does not score the presence of anything worth reading. Thus dead prose can get a good score.
- The report is an internal working document. "Fails" describes a draft against a ruleset. If someone sends the report to the writer, "Fails" seems to describe the writer.

The two modes use the same rules. The difference is that one mode fixes and the other mode judges.

---

## The Workflow

For every edit request, do these five steps in order. If you skip a step, the rewrite is worse.

### 1. Read all of the draft one time

Do not start to edit on the first read. Read for meaning and voice. Find these items:

- What the writer wants to say.
- The format (tweet, email, blog, ad, internal memo).
- The audience.
- The natural rhythm of the writer.

If the draft does not show the voice of the writer clearly, ask one question before you edit.

### 2. Scan against the banned list

Examine the draft in this sequence:

- Word-level scan: find every banned word from `references/banned-list.md`. Record each occurrence and its location.
- Phrase-level scan: find every banned phrase. Record each occurrence.
- Structure scan: find em dashes, en dashes, standalone hyphens, compound-word hyphens (for example, mark "go-to-market"), the default rule of three, bulleted lists with bold titles, formulaic transitions (Furthermore, Moreover, Additionally, Subsequently, In addition, As previously mentioned) and weak verb constructions (serves as a, acts as a, marks the, features as filler, utilize, facilitate).

Be strict. A banned word inside a long sentence is still a violation. A compound-word hyphen is still a violation.

### 2b. Scan the discourse layer

First, check the register. If the text is legal, compliance, procedural or technical documentation, skip this step. Say that you skipped it in the Notes block.

Then check the length band. The band sets which habits apply and how many additions you can make:

| Band | Applies | Additions |
|---|---|---|
| Under 40 words | No scaffolding, one concrete specific, no stated takeaway | 0 |
| 40 to 200 words | Habits 1, 5, 6, 7, 8 | 1 |
| 200 to 800 words | All eight habits | 2 |
| Over 800 words | All eight plus time jumps and thread structure | 3 |

Batch convergence applies at every band, including the shortest band, because it compares pieces. It does not examine the inside of one piece.

Then answer the ten-question checklist in `references/discourse-tells.md`:

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

If the answer to a question from 1 to 5 is yes, that is a habit to cut. If the answer to a question from 6 to 10 is no, that is a signal to restore. The budget and the register gates limit each restore:

- A named feeling belongs in personal and internal writing. It does not belong in client work.
- In one client-facing piece, do not put a stated doubt about your own recommendation together with an open item.

### 3. Make the rewrite

For each marked item, apply the rewrite from `references/rewrites.md`. Use these principles:

- Replace a banned word with its natural equivalent ("utilise" → "use", "leverage" → "use" or a stronger verb).
- Cut a banned phrase, or rewrite the sentence without it ("It is worth noting that" → cut entirely).
- Break the rule of three. Change the count: sometimes two, sometimes four, sometimes none.
- Replace an em dash with a period, a colon or a new sentence. Replace a compound-word hyphen with the unhyphenated form or an acronym ("go-to-market" → "GTM" or "go to market").
- Replace a weak verb construction with a direct verb ("X serves as a bridge between A and B" → "X bridges A and B").
- Cut filler. Cut sycophantic openers. Cut summary closers.

Then apply the Layer 2 fixes from `references/discourse-rewrites.md` for the items that the checklist marked. Apply only those fixes. If you apply all eight habits only because all eight exist, the checklist becomes a new register.

Three rules control this pass:

- **Subtraction before addition.** You fix six of the eight habits when you delete something.
- **The source test.** Every addition must come from something real: a line in the draft, a message in the thread, a number in the data, or a doubt that the writer stated. If you cannot point to the source, cut the addition and say so in Notes. This test replaces the old advice "never fake the mess."
- **The open-item contract.** In client-facing work, an open item must have an owner, a date and a statement of what it affects and does not affect. If one of the three is missing, cut the open item.

Keep the voice of the writer. Use the same sentence length, the same level of formality and the same punctuation habits (within the rules). If the writer uses short sentences, do not write long sentences. If the writer uses British English, do not write American English.

### 4. Read the rewrite aloud

If the rewrite sounds like a committee wrote it, the rewrite is wrong. If you stop on a sentence when you read it, fix that sentence.

The test: does the rewrite still sound like the writer, but sharper? If yes, give it to the user. If no, do the rewrite again.

### 5. Give the result with the diagnosis

Use the Output Format section below. Always show what was wrong, what you changed and why. The user learns the rule when the user sees it applied.

---

## Output Format

Always give your response in four blocks.

### Diagnosis
A bulleted list of each category of violation that you found in the draft. Give the count for each category. Examples:

- 3 banned words: "delve" (1), "unlock" (1), "leverage" (1)
- 2 banned phrases: "in today's fast-paced world," "drive meaningful impact"
- 4 em dashes
- 1 instance of the rule of three (where the three items were interchangeable)
- 2 weak verb constructions: "serves as," "utilize"

Then write a second short block for the discourse layer. Name only what you found:

- Stated takeaway in the final sentence
- Atmospheric opener: first paragraph sets mood, content starts in paragraph two
- No named specifics in three of four claims
- Epilogue: closing paragraph adds nothing
- No acknowledgement of the reader anywhere

If Layer 2 does not apply to the register of the draft, write one line that says so.

### Rewrite
The full rewritten draft, ready to use. Do not put annotations inside the rewrite.

### Changes
A short list (3 to 6 items) of your largest changes. For each item, quote the original phrase, then the rewrite, then give one line about why. Example:

- "Unlock the potential of your inbox" → "Get your inbox under control" (replaced banned phrase, used concrete verb)
- "In today's fast-paced world, staying connected is more important than ever" → cut entirely (vague opener, said nothing)
- "Our seamless solution helps you delve into deeper conversations" → "Our app makes the conversations matter" (replaced banned words, replaced metaphor with concrete claim)

For Layer 2 changes, describe the action. Do not quote a substitution:

- Cut the closing paragraph (epilogue; nothing was lost)
- Moved the ask to sentence one, deleted the scene-setting opener
- Replaced "industry benchmarks suggest" with the actual competitor bid range (verify the figures)
- Kept the unresolved tracking issue as a separate paragraph instead of folding it into the summary

### Notes
One short paragraph. If part of the original was ambiguous, name it. If a style decision in the rewrite is open to debate, name it. If the writer must know about a pattern that occurs again and again in the drafts, tell the writer.

---

## When the User Disagrees

If the user says "I liked the original word X" or "Why did you cut that line?", do these steps:

1. Tell the user which rule the original broke.
2. Give one alternative rewrite that is closer to the preference of the user and still obeys the rules.
3. If the user still wants the original words, accept them. The skill is a tool, not a tribunal.

If the user says "this is too dry, the original had personality":

- Personality and AI tells are different things. Read the original again. Find what made it feel alive (a specific image, a turn of phrase, a self-aware aside). Put that into the rewrite.

If the user says "rewrite it without changing X":

- Obey the constraint. Rewrite the text around X.

---

## Edge Cases

### Quoted material
If the draft contains a quote (in quotation marks, and attributed to a person or a source), keep the quote exactly. AI tells inside a real quote are part of the historical record. Record them in the Diagnosis, but do not change them.

### Technical writing
Some banned words have correct technical uses. Examples: "framework" for a named software framework, "key" for a cryptographic key, "navigate" for real navigation in a UI. Use your judgement. The rule bans these words as filler, not as precise technical terms.

### Registers where the discourse layer does not apply

Layer 2 assumes that the writer had a choice about structure. Some registers remove that choice. In these registers, the habits that Layer 2 removes are requirements:

- Simplified Technical English, procedures, safety and operating instructions
- Legal, compliance, GDPR, privacy, and contractual text
- Regulatory and tax correspondence
- Technical documentation and API references
- Client reporting under a mandated house template

For these registers, do Layer 1 only. Say so in the Notes block. In these registers, explicit statements, closure and single-track logic are the specification, not the tell.

Two smaller gates apply in the registers where Layer 2 runs:

- **Named feelings.** A feeling in plain words is a restore for personal essays, first-person posts, internal messages and founder updates. It is not a restore for client deliverables, proposals, reports or marketing copy. In those texts, the correct emotional register is usually none.
- **Doubt and open items.** In one client-facing piece, do not put a stated doubt about your own recommendation together with an open item. Each one alone reads as candour. Both together read as a lost account.

In every gated case, the matching cut still applies. For example, you still remove habit 4 from a client email, but you do not add signal 4. Replace the habit with the fact, not with a feeling.

### Code and code comments
Do not change code. Do not change variable names. Different conventions control code.

### Headlines and ad copy
This skill works well with the `copy-that-sells` skill, if it is installed. For ad copy, run this skill after copy-that-sells, not before. Copy-that-sells generates the copy. This skill polishes it.

### Spanish, Portuguese, and other non-English drafts
The banned word list shows English fingerprints. For a draft in a different language, ask the writer to confirm the language. Then rewrite with the equivalent of the AI-default register in that language. Latino Spanish AI tells include "navegar," "potenciar," "fomentar" and "robusto." Castilian Spanish has its own tells. Change your edits to match.

### Very short drafts (under 50 words)
Examples: headlines, tweets, button text. You can make the Diagnosis and Changes blocks one line each. The Rewrite block is still the most important block.

### Very long drafts (over 2,000 words)
Edit the draft in sections. Diagnose all of the draft. Rewrite one section at a time. Return the full rewrite with one Diagnosis block and one Changes block for all of the document.

---

## What This Skill Is Not For

- Writing new content from the start. Use a generator skill for that (`copy-that-sells`, the user's own writer skill, or Claude with the right prompt).
- Improving the content of an argument. This skill is a style editor, not a logic checker. A bad argument is still bad after you remove the AI tells.
- Removing correct uses of words that are on the banned list. See Edge Cases.

If a request is a generation request and not an edit request, send it to a generator skill. If a request is a logic check or a research check, send it to general Claude.

---

## Why This Skill Exists

Modern LLMs have a default voice. That voice is now so common that readers recognise it in one sentence. This recognition is bad for trust, bad for engagement and bad for the writer.

The fingerprints of the voice are not random. They come from optimisation pressure:

- Words that test as "professional" and "engaging" in human feedback.
- Structures that give balanced answers across many topics.
- Hedges that make a wrong answer feel less wrong.

None of these is bad alone. Together, they make a sound that says "a machine wrote this."

The fix is mechanical: a list of fingerprints, applied with discipline. That is what this skill does. It does not make a writer better. It stops a good writer from sounding like the machine that helped with the draft.
