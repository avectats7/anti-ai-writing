# Discourse Tells: The Structural Layer

Layer 1 of this skill (`banned-list.md`) removes surface fingerprints: words, phrases, punctuation. Layer 2, this file, removes the fingerprints that survive a surface edit.

## Why this layer exists

Russell et al. (2026) built a corpus of 61,608 stories written to the same 10,272 prompts by one human author and five LLMs, then extracted 304 interpretable discourse features per story. Three results matter here.

1. Discourse features alone separate human from AI writing at 93.2% macro-F1, with no access to word choice, punctuation, or sentence rhythm.
2. When AI stories were rewritten to strip surface artifacts (cliché, purple prose, redundant exposition), detection stayed at 93.9%. Cleaning the surface did not move the structure.
3. A compact set of 30 features carries most of the signal, and they group into a small number of habits.

Point 2 is the reason for v2. A draft can pass the whole Layer 1 checklist and still be recognisable, because what gives it away is not the words. It is how the piece is built: what it explains, what it resolves, what it names, and who it talks to.

## Scope and honesty note

The study measured ~5,000-word fiction. This file extrapolates to emails, messages, posts, and marketing copy. The extrapolation is reasoned, not measured: the habits below are structural dispositions of the model, not genre conventions of the short story, and they show up in short-form drafts in a recognisable form. Treat the percentages as the source's findings on fiction and the short-form applications as this skill's inference.

Two rules follow from that gap.

**Every number in this file is a measurement on fiction.** Not on emails, not on Slack, not on landing pages. Where a percentage appears below, read it as "in ~5,000-word short stories, this is how far apart the human and the models sat." The short-form rule attached to it is this skill's reading of that gap, and it is falsifiable in a way the number is not.

**Never quote these numbers to a writer.** The Diagnosis block says "stated takeaway in the final sentence." It does not say "77% of AI stories do this." Citing a fiction statistic to justify an edit on a client email launders a finding into a claim it does not support, and the writer has no way to check it. Name the habit. Leave the corpus out of it.

Some of these rules are wrong for some registers. See "Where this layer does not apply" at the bottom. Read it before applying anything here to a legal, technical, or compliance document.

---

## Table of contents

- The ten dimensions, and which reach short form
- Applying by length: the triage table
- Eight habits to cut
- Six signals to restore, and the budget that limits them
- The Claude-specific fingerprint
- Batch convergence
- When v2 becomes the tell
- Quick scan checklist
- Where this layer does not apply
- Source

---

## The ten dimensions, and which reach short form

StoryScope measured 304 features across ten discourse dimensions. The eight habits below are the editing-facing slice of that space. This table is the whole space, so you can see what was measured, which direction the model leans, and which dimensions survive the jump from a 5,000-word story to an email. Style is absent on purpose: it is Layer 1's territory, governed by `banned-list.md`.

| Dimension | Which way AI leans | Reaches short form? |
|---|---|---|
| Plot / theme | Over-explains the theme, moralises, ties every thread to one point | Yes — habit 1, signal 5 |
| Events | Tighter causal chains, protagonist-driven and internally-resolved endings | Yes — habits 2, 3 |
| Agents (character) | Emotion shown through the body, not named; characters introduced by external description | Yes — habit 4, habit 5 |
| Setting | Opens on scene; setting mirrors the character's inner state | Yes — habit 5 |
| Situatedness | Vague allusions over named works; reverent to genre, avoids subversion | Yes — habit 6 |
| Perspective | Uniform voice; rarely breaks the fourth wall or addresses the reader | Yes — signal 1 |
| Temporal structure | Single-track and linear; few time jumps, front-loaded reveals | Partly — signal 2 (a delayed reveal rarely fits an email) |
| Revelation | Less withholding, less suspense, discloses early | Rarely — needs narrative length |
| Social networks | Simpler relational topology, fewer integrated subplots | Rarely — fiction-specific |
| Style | (surface: word choice, syntax, rhythm) | Layer 1, not here |

Six dimensions carry straight into short-form prose. Two carry partly. Two are effectively fiction-only. When a diagnosis reaches for a tell, it is almost always pulling from the top six rows.

---

## Applying by length: the triage table

The corpus is fiction averaging 4,753 words. A twelve-word chat message has no room for a subplot, a flashback, or a delayed revelation, so most of what follows is not evaluable there. Applying an unevaluable rule produces invention, which is worse than the tell.

Check the length band before anything else.

| Band | What applies | Additions allowed |
|---|---|---|
| Under 40 words (chat, DM, subject line, push, button) | Three checks only: no scaffolding (greeting, sign-off, paragraph architecture), one concrete specific, no stated takeaway | None |
| 40 to 200 words (most emails, Slack posts, short social) | Habits 1, 5, 6, 7, 8. Skip 2 and 3: there is no room for a second thread and no decision large enough to leave open | One |
| 200 to 800 words (client update, long post, blog intro, page copy) | All eight habits | Two |
| Over 800 words (report, essay, deck narrative, sequence copy) | All eight habits plus time jumps and genuine thread structure | Three |

One rule applies at every band, including under 40 words: batch convergence. It measures difference between pieces rather than structure inside one, so it works on a set of five-word messages exactly as well as on a set of essays. For most short-form writing it is the only rule with real purchase.

---

## Eight habits to cut

### 1. The stated takeaway

Finding: AI narrators explain the story's theme 77% of the time, humans 52%. AI scores higher on explicitness and moralising across the board (3.94 vs 3.28 on a 1 to 5 scale). The same reflex shows up in dialogue: AI dialogue serves philosophical debate 59% of the time versus 34%, characters arguing the theme aloud so the reader cannot miss it. The paper's word for the pattern is over-determination: the model spells the meaning out rather than trusting the reader to infer it.

In short form: the last sentence tells the reader what the previous paragraphs meant. "Which is really what good onboarding is about." "It was a reminder that the small details matter." "The lesson here is to test early." The dialogue version: a quote inserted only to state the lesson. "As my mentor always said, 'ship early and listen.'"

Rule: delete the sentence that explains the point. End on the last concrete thing. Cut any quote that exists only to voice the moral. If the point does not survive without the explanation, the concrete things are too weak, and that is the actual fix.

### 2. The single clean track

Finding: AI produces tighter causal chains (4.20 vs 3.92) and no subplots 79% of the time versus 57% for humans.

In short form: context, problem, solution, ask, in that order, every loose end tied. Real emails carry an unrelated aside, a half-answered question from last week, a thing the writer forgot until the third paragraph.

Rule: allow one thing that does not serve the main line. An aside, a leftover, an unresolved item. One. This is not permission to ramble.

### 3. The tidy resolution

Finding: AI resolves through the protagonist's own choices 69% of the time versus 46% for humans, and through internal understanding or acceptance 47% versus 27%.

In short form: the writer always ends in control. "So I've decided to move the launch to March." "I've realised the problem was scope all along." Human writers end with the thing still open, or resolved by something outside their control, or not resolved.

Rule: if the situation is genuinely unresolved, say so and stop. Do not manufacture closure. External causes are allowed to be the answer.

### 4. The body report

Finding: AI conveys emotion through physical sensation and bodily metaphor 81% of the time versus 38% for humans. Humans name the emotion outright 29% of the time versus 8% for AI.

In short form: "my stomach dropped when I opened the dashboard," "the room went quiet," "something tightened in my chest." Humans write "I was annoyed."

Rule: name the feeling in plain words. Cut the physical translation unless the physical thing actually happened and matters.

### 5. The atmospheric opener

Finding: AI grounds the opening in physical setting more clearly and uses setting as a mirror of inner state more heavily (4.07 vs 3.58). It introduces characters through external description 52% of the time versus 30%.

In short form: "It was 7am and the office was still dark." "Sitting here after three weeks of calls, I keep coming back to one thing." The scene exists to set a mood before the content arrives.

Rule: open on the content. The ask, the fact, the number, the disagreement. If a scene earns its place, it is because something happened in it.

### 6. The vague allusion

Finding: AI keeps references non-specific 72% of the time versus 50%. Humans name a real text, brand, place, or person at nearly double the rate (47% vs 24%) and mix explicit and implicit references far more evenly (37% vs 16%).

In short form: "industry research suggests," "a lot of teams are seeing this," "there's a well-known principle about." No names, no numbers, no dates, no sources.

Rule: every paragraph that makes a claim names something real. A company, a tool, a date, a figure, a person, a specific past conversation. If nothing can be named, the claim is not ready.

### 7. The front-loaded context

Finding: front-loading crucial context that other sources leave until later is a per-model fingerprint (DeepSeek), and over-explanation is general to AI.

In short form: paragraph one re-explains what the recipient already knows. "As you know, we've been running Google Ads for the Q3 campaign since June, with the goal of..." Recipients hate this and humans rarely do it.

Rule: assume shared history. Reference it, do not reconstruct it. "The Q3 numbers" is enough for someone who has been reading the Q3 numbers.

### 8. The epilogue

Finding: Claude specifically favours epilogues and quiet, careful endings, with the flattest event escalation of the five models and the most uniform narrative voice.

In short form: the message ends, then continues for one more paragraph of warm wrap-up. "Happy to jump on a call if any of this is unclear. Either way, great work this quarter." Everything at the same volume, no sentence louder than the rest.

Rule: cut the last paragraph and read again. If nothing is lost, it was the epilogue. And let one sentence be louder than the others.

---

## Six signals to restore, and the budget that limits them

These are things human writers do that models under-produce. Every one of them is an addition, and additions are where this layer does damage. A cut that goes too far leaves a flat draft. An addition that goes too far leaves a lie.

Three constraints govern all six. They are not advice.

**The addition budget.** Under 40 words: zero additions. Under 200: one. Under 800: two. Above 800: three. Count them. A draft carrying four is not more human, it is performing.

**The source test.** For every addition, point at where it came from: a line in the draft, a message in the thread, a number in the data, a doubt the writer actually expressed. If you cannot point at it, you invented it, and it comes out. This is the operational form of "never fake the mess." Advice does not survive a deadline; a test does.

**The register gate.** Signals 4 and 5 do not apply everywhere. Each says where below.

When the register bars a restore, that is not a reason to skip the matching cut. Habit 4 comes out of a client email even though signal 4 cannot go in. The fix is deletion, not substitution: report what happened and stop.

### 1. Direct address and asides

Finding: humans break the fourth wall 67% versus 39% and address the reader directly 28% versus 7%.

Restore: a parenthetical aside, a rhetorical turn to the reader, an acknowledgement that someone is reading. "(You already know how that went.)" "Skip this part if you were on the call."

### 2. Time jumps and shared history

Finding: humans score higher on chronological discontinuity (2.40 vs 2.12), anachrony, and nonlinear framing for delayed disclosure.

Restore: reach backward or forward without smoothing the transition. "Anyway. Back in June we tried the opposite and it failed for a different reason."

### 3. Named specifics

The counterpart to habit 6. Names, numbers, dates, prices, tools, places.

### 4. Plain emotion labels

The counterpart to habit 4. "I'm frustrated." "This one worries me." "I don't love it."

Register gate: personal essays, first-person social posts, internal team messages, founder updates, and anything the writer signs alone. Not client deliverables, proposals, reporting, or marketing copy. In paid work the correct emotional register is usually none, and a named feeling reads as a bid for sympathy from someone who is paying for a result.

In a gated register, habit 4 is still cut. "My stomach dropped when the numbers came in" becomes "the numbers came in at $71," not "the numbers worried me."

### 5. Admitted ambivalence

Finding: humans present morally ambivalent protagonists 59% of the time versus 38%, and integrate competing threads rather than aligning everything to one point (42% vs 21%).

Restore: state the case against your own recommendation, or admit the self-interested reason.

Two hard constraints, both learned from client work rather than from the corpus.

**Position.** The concession comes after the recommendation, in the same paragraph, never before it and never instead of it. "Do X. The case against is Y." Never "I'm not sure, but maybe X." The first is a professional showing their work. The second is a professional asking the client to decide for them.

**Exclusivity.** In any piece a client is paying for, choose one: an open item (habit 2) or a stated doubt about your own recommendation (this one). Not both. Each on its own reads as candour. Together they read as someone who has lost control of the account, and the reader is right to read it that way.

Register gate: applies where the writer owns the recommendation. Does not apply where the deliverable is the decision itself, such as a formal proposal, a scope document, or a legal position.

### 6. Variance in shape

Finding: human stories occupy a rarer, more dispersed region of the feature space (mean rarity percentile 0.71 vs 0.49). The five models cluster together; the human sits outside the cluster.

Restore: do not write every piece to the same template. See "Batch convergence" below.

---

## The Claude-specific fingerprint

The study attributed authorship six ways at 68.4% macro-F1 using discourse features alone, and Claude was the most distinctive of the five models. Its markers:

- Event intensity escalates less than in any other source. Nothing builds. Everything sits at one level. This is Claude's single strongest fingerprint feature.
- Low event-type diversity. The same kinds of things keep happening. Claude's second strongest feature.
- The most uniform narrative voice of the five. No register shifts.
- A reverent, continuist stance toward convention: honouring the expected form rather than bending it (62% of Claude stories versus 39% to 56% across other models).
- A preference for epilogues and quiet endings over abrupt ones. The paper's phrase: Claude favours the quiet ending over the "avalanche" ending.
- Avoids dream sequences and other temporal distortions. It stays literal and in-sequence.

If the draft came from Claude, check those first. In short form they read as: flat emphasis with nothing rising above the rest, a narrow range of moves repeated, one tone throughout, the expected structure executed cleanly, and one calm paragraph too many at the end.

For reference, the other fingerprints: GPT leans on social framing, gossip and rumour as mechanism, and distant retrospective framing. Gemini produces the tidiest endings, extended wrap-ups, and bleak settings. DeepSeek front-loads context. Kimi has almost no fingerprint and sits at the generic centre of the AI distribution.

---

## Batch convergence

Finding: the five models cluster tightly in discourse space while human writers scatter. Applied to a sequence, this means every email in a five-email flow will arrive with the same architecture: same opener type, same paragraph count, same resolution style, same closing move.

Rule: when editing more than one piece at a time, diagnose the set, not just each piece. If all five open the same way, change three of them. Vary length by a real margin, not by ten words. Let one piece be blunt and one be long.

This is the single highest-value rule in this file for anyone shipping sequences: nurture flows, participant comms, weekly client updates.

---

## When v2 becomes the tell

The corpus finding behind batch convergence cuts both ways. Five models writing to one brief cluster tightly. So does one editor applying one checklist to fifty drafts.

If every piece that leaves this skill opens with a metric, "opens with a metric" is the new "We're excited to share." The fingerprint moves; it does not disappear. Optimising against a known feature space is a treadmill, and the honest position is that this layer buys durability over the surface rules, not permanence.

Three defences.

**Rotate the opener.** Habit 5 says do not open on mood. It does not say open on a number. The menu: the number, the ask, the disagreement, the correction, the blunt fact, the question, the thing that broke. Across any set, use at least three of them.

**Apply what the diagnosis found, not the whole list.** The checklist is a scan, not a schedule. A draft that only trips habits 1 and 6 gets two fixes. Running all eight because all eight exist is how a ruleset becomes a register.

**Watch for these, which this layer produces:**

- Every piece opens with a metric.
- Every piece closes with a date-stamped ask.
- The concession paragraph appears in every recommendation, always one sentence, always in the same slot.
- Chat fragments imposed on a writer who does not write in fragments.
- The loose end that is always present and always exactly one paragraph.
- Uniform bluntness, applied where the relationship did not earn it.

Any of these appearing across a set means the editor has become the model.

---

## Quick scan checklist

Ten questions. Any yes in 1 to 5, or any no in 6 to 10, needs a fix.

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

Then three budget checks before shipping:

- Is the piece inside its addition budget for its length band?
- Can every addition be traced to something real in the draft, the thread, or the data?
- Does the piece carry both an open item and a stated doubt? If it is client-facing, cut one.

---

## Where this layer does not apply

Layer 2 is about voice under conditions of choice. Several registers remove that choice, and the habits above stop being tells and start being requirements.

- Simplified Technical English, procedures, safety and operating instructions. Explicitness, one idea per sentence, and single-track logic are the specification. Do not add asides, time jumps, or ambivalence.
- Legal, compliance, GDPR, privacy, and contractual text. Closure and completeness are the point. Loose ends are liabilities.
- Regulatory or tax correspondence. State the case, cite the reference, close it.
- Technical documentation and API references. Front-loaded context is a feature.
- Structured reporting where a house template is mandated by the client.

Layer 1, the surface rules, still applies to all of these. Layer 2 does not.

When a draft sits in one of these registers, say so in the Notes block and apply Layer 1 only.

---

## Source

The findings in this file come from:

Jenna Russell, Rishanth Rajendhran, Chau Minh Pham, Mohit Iyyer, and John Wieting. "StoryScope: Investigating idiosyncrasies in AI fiction." Preprint, University of Maryland and Google DeepMind, 2026. arXiv:2604.03136. Code and data: https://github.com/jenna-russell/storyscope

The five models studied: Claude Sonnet 4.6, GPT-5.4, Gemini 3 Flash, DeepSeek V3.2, and Kimi K2.5, each writing to the same 10,272 prompts as one human author. The per-model fingerprints above are specific to these versions and will drift as the models change.

They measured the difference. This file only translates it into edits. Any error in the translation is this skill's, not theirs.
