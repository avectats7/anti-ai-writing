# Strict Review: Audit Mode

Default mode edits. Strict review judges. The user hands over a draft and wants to know what is wrong with it and how badly, not a cleaned-up version.

Run this mode when the user says "strict review," "audit this," "score this," "review estricto," "how bad is this," "does this pass," "check this against the rules," or asks for a verdict rather than a rewrite. Also run it when the user is checking someone else's writing, or their own writing from before they had the ruleset.

## What changes in this mode

**No rewrite unless asked.** The output is a verdict and a finding list. If the user wants the fix afterwards, they will ask, and then you switch to default mode.

**Verdicts are binary.** A rule is met or it is not. "Mostly fine" is not a verdict. If you cannot decide, the item goes in Contested, not in Clean.

**Two kinds of ambiguity, two different rules.** Ambiguity about what the text does resolves by reading, and it counts against the draft: if you cannot tell whether that final sentence is a stated takeaway, it is one, because the reader could not tell either. Ambiguity about whether the move is legitimate in this register is judgement, and it goes to Contested without counting. Softening the first defeats the request. Ruling on the second without saying so manufactures certainty you do not have.

**Every finding carries evidence.** Quote the exact words, under fifteen words, and say which rule they break. A finding without a quote is an opinion and gets dropped.

**No praise, no cushioning.** No opening line about what works well, no "otherwise this is strong." If the user wants to know what works, they will ask for that separately. Mixing the two makes the report unusable as a checklist.

---

## The scorecard

Run in this order. Stop at step 0 if it applies.

### Step 0: register check

Is the draft legal, compliance, GDPR, procedural, Simplified Technical English, API documentation, or a client-mandated template? If yes, audit Layer 1 only, state the register at the top of the report, and skip steps 3 to 6. Explicitness and closure are the specification in these registers, not violations.

### Step 1: length band

Count the words. Record the band, because it sets what can be scored at all.

| Band | Layer 2 items in scope | Addition budget |
|---|---|---|
| Under 40 | Scaffolding, one specific, no stated takeaway | 0 |
| 40 to 200 | Habits 1, 5, 6, 7, 8 | 1 |
| 200 to 800 | All eight habits | 2 |
| Over 800 | All eight plus threads and time jumps | 3 |

Never score a rule that is out of band. A twelve-word message cannot fail the subplot rule. Marking it as a violation is a false positive and it teaches the writer to distrust the whole report.

### Step 2: Layer 1

Count every banned word, banned phrase, em dash, en dash, compound-word hyphen, formulaic transition, default rule of three, bulleted bold title, and weak verb construction. Give raw counts, not impressions.

### Step 3: Layer 2 habits

For each habit in scope, one line: met or violated, with the quote.

1. Stated takeaway
2. Single clean track
3. Tidy resolution
4. Body report
5. Atmospheric opener
6. Vague allusion
7. Front-loaded context
8. Epilogue and flatness

### Step 4: Layer 2 signals

Only the signals whose register gate is open. Naming a feeling does not count as missing in a client deliverable. A stated doubt does not count as missing in a proposal.

### Step 5: budget and contract checks

- Additions counted against the band's budget.
- Source test: can each addition be traced to something in the draft, the thread, or the data? An addition you cannot trace is a fabrication and it is an automatic fail.
- Open-item contract: does every loose end carry owner, date, and consequence?
- Exclusivity: does a client-facing piece carry both an open item and a stated doubt?

### Step 6: convergence

If the user supplied more than one piece, or you have edited pieces for them earlier in the session, compare across them. Same opener type, same paragraph count within one, same closing move, same register: each of these repeated across the set is a finding at the set level, reported separately from the per-piece findings.

Also check the set against the fingerprints this layer produces: metric openers, date-stamped closes, a concession paragraph in every recommendation, imposed chat fragments, the always-one-paragraph open item.

---

## Severity

Not every finding is worth the same, and an early version of this file scored a formula phrase and a fabricated statistic identically. Three tiers.

**Critical.** A claim, number, or attribution that is not true or not traceable. A fabricated addition. An open item in client-facing work without owner and date. These are not style problems and they do not trade off against anything.

**Structural.** A Layer 2 habit: stated takeaway, atmospheric opener, front-loaded context, epilogue, tidy resolution, single track, body report, vague allusion. Each one changes how the piece is built.

**Surface.** A Layer 1 item: a banned word, a formula phrase, an em dash, a compound hyphen, a weak verb. Each one is a five-second fix.

## Verdicts

Score by density, not by raw count, so that a 2,000-word report is not judged on the same scale as a tweet. Density is findings per 100 words.

| Verdict | Condition |
|---|---|
| Clean | No critical findings. Structural density below 0.3 and surface density below 0.5 |
| Passes with flags | No critical findings. Structural density below 0.8, surface density below 1.5 |
| Needs work | No critical findings, either density above its threshold |
| Fails | Any critical finding |

Worked example: a 380-word section with one surface finding and three structural findings scores 0.26 surface and 0.79 structural. Passes with flags. Under raw counting it read as a failure, which is the calibration error this table replaces.

A critical finding overrides everything, including a draft that is otherwise clean. A fabricated aside is worse than the tell it was meant to replace, so it cannot be offset elsewhere.

Report the verdict as the first line. Not the last.

## Volume triage

Above roughly 800 words, report the ten highest-severity findings in full and give raw counts for the rest by category. A list of sixty findings is not a work item, it is a wall, and the writer fixes none of them.

Critical findings are never truncated. Report all of them however many there are.

## What a Clean verdict does not mean

This mode scores the absence of tells. It does not score whether the writing is any good. Prose with nothing in it scores Clean, because there is nothing in it to flag, and a draft that says something risky will always score worse than one that says nothing.

So a Clean verdict means the draft carries no fingerprints. It does not mean ship it. When a draft scores Clean and is also inert, say so in one line under the verdict. That line is the only place in this mode where a judgement about quality belongs.

## The cost line

Every report ends with one sentence naming what the draft would lose if every finding were applied. Not a hedge, a real accounting: the rhythm that the em dash was carrying, the warmth the closing paragraph gave a cold email, the emphasis the rule of three was doing.

Without this line the mode is a flattening machine. The writer needs to know the price before they pay it, and sometimes the right call is to keep the finding and accept the tell.

---

## The report is internal

The verdict vocabulary is for the desk, not for the recipient. "Fails" describes a draft against a ruleset; forwarded to the person who wrote the draft, or to the client whose copy you audited, it describes them.

Two rules. Never write the report as though it will be sent to the author unless the user says it will be. And if the user says it will be, ask before writing, then drop the verdict line and lead with the findings, since a ranked list of specific fixes survives being read by its subject and a grade does not.

## Re-audits

When the user returns with a revised draft, audit it as a delta rather than from scratch.

Report: the previous verdict and the new one, which findings closed, which remain open with the original quote, and which are new. Findings introduced by the revision get flagged separately, because a fix that creates a fingerprint is the most common outcome of a second pass and the writer cannot see it without being told.

If nothing moved, say that in the first line rather than restating the original report.

## What does not count as a violation

False positives are the failure mode of this mode. None of the following are findings:

- A banned word used in its precise technical sense: a named software framework, a cryptographic key, literal UI navigation.
- AI tells inside quoted material attributed to a real person or source. Note them, do not count them.
- Any rule outside the draft's length band.
- Any register-gated signal whose gate is closed.
- A structure that is correct for the register: single-track logic in a procedure, closure in a legal position, explicitness in safety instructions.
- The writer's own habits. Long sentences, formality, a fondness for semicolons, British spelling. Style is not a tell.

When you believe something is a violation but the register might justify it, it goes in Contested with both readings stated. Contested items do not count toward the verdict.

---

## Output format

Five blocks, in this order.

**Verdict.** One line. The verdict, the word count, the band, and the register if it is a gated one.

**Layer 1.** Raw counts by category. Zero counts can be omitted.

**Layer 2.** One line per violated habit, each with a quote under fifteen words and the rule name. In-scope habits that are met get a single summary line, not eight lines of confirmation.

**Budget and contract.** Additions counted, source test result, open-item contract result, exclusivity result. One line each, only where relevant.

**Contested.** Items where the register might justify the finding, with both readings. Omit the block if empty.

If the user supplied a set, add a sixth block: **Convergence**, listing what repeats across the pieces.

---

## Auditing your own output

Before shipping a strict review, run step 3 on the review itself. Audit reports written by this skill have failed their own rules: opening on framing rather than the verdict, closing with a paragraph that explains what the findings meant, and arriving in the same shape every time.

The verdict goes first. The report ends on the cost line. No closing summary.

One limit worth stating rather than hiding. The auditor and the ruleset come from the same place: a model scoring text against criteria a model helped write, using a feature space derived from detecting models. That is not independent review, and the self-audit clause above does not make it independent. It catches the obvious failures and it will systematically miss whatever the ruleset itself is blind to.

Where a verdict matters, a person reads the draft. This mode narrows what they have to look at; it does not replace them. Say so if a user starts treating the verdict as the decision.
