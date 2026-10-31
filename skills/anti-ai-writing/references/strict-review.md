# Strict Review: Audit Mode

Default mode edits. Strict review judges. The user gives you a draft and wants to know what is wrong with it and how bad it is. The user does not want a clean version.

Use this mode when the user says "strict review," "audit this," "score this," "review estricto," "how bad is this," "does this pass," "check this against the rules," or asks for a verdict and not a rewrite. Also use it when the user checks writing from a different person, or the user's own writing from before the ruleset.

## What changes in this mode

**No rewrite unless the user asks.** The output is a verdict and a list of findings. If the user wants the fix after the review, the user asks for it. Then you change to default mode.

**Verdicts are binary.** A draft obeys a rule or it does not. "Mostly fine" is not a verdict. If you cannot decide, put the item in Contested, not in Clean.

**Two types of ambiguity have two different rules:**

- **Ambiguity about what the text does.** You resolve it when you read the text, and it counts against the draft. For example, if you cannot tell if the final sentence is a stated takeaway, it is a stated takeaway, because the reader also cannot tell. If you make this rule softer, you defeat the request.
- **Ambiguity about whether the move is correct in this register.** This is a judgement. Put it in Contested, and do not count it. If you give a ruling on it and do not say so, you invent certainty that you do not have.

**Each finding has evidence.** Quote the exact words, in fewer than fifteen words, and say which rule they break. A finding without a quote is an opinion. Remove it.

**No praise and no softening.** Do not start with what works well. Do not write "otherwise this is strong." If the user wants to know what works, the user asks for that separately. If you mix praise and findings, the user cannot use the report as a checklist.

---

## The scorecard

Do the steps in this order. If step 0 applies, stop at step 0.

### Step 0: Check the register

If the draft is legal, compliance, GDPR, procedural, Simplified Technical English, API documentation or a template that the client mandates, do these actions:

1. Audit Layer 1 only.
2. State the register at the top of the report.
3. Skip steps 3 to 6.

In these registers, explicit statements and closure are the specification, not violations.

### Step 1: Find the length band

Count the words. Record the band, because the band sets what you can score.

| Band | Layer 2 items in scope | Addition budget |
|---|---|---|
| Under 40 | Scaffolding, one specific, no stated takeaway | 0 |
| 40 to 200 | Habits 1, 5, 6, 7, 8 | 1 |
| 200 to 800 | All eight habits | 2 |
| Over 800 | All eight plus threads and time jumps | 3 |

Do not score a rule that is outside the band. A twelve-word message cannot fail the subplot rule. If you mark it as a violation, that is a false positive. A false positive teaches the writer to distrust all of the report.

### Step 2: Score Layer 1

Count each banned word, banned phrase, em dash, en dash, compound-word hyphen, formulaic transition, default rule of three, bulleted bold title and weak verb construction. Give raw counts, not impressions.

### Step 3: Score the Layer 2 habits

For each habit in scope, write one line: met or violated, with the quote.

1. Stated takeaway
2. Single clean track
3. Tidy resolution
4. Body report
5. Atmospheric opener
6. Vague allusion
7. Front-loaded context
8. Epilogue and flatness

### Step 4: Score the Layer 2 signals

Score only the signals that have an open register gate. In a client deliverable, a missing named feeling is not a finding. In a proposal, a missing stated doubt is not a finding.

### Step 5: Check the budget and the contracts

- **Budget:** count the additions against the budget of the band.
- **Source test:** for each addition, find its source in the draft, the thread or the data. If you cannot find a source, the addition is a fabrication. A fabrication is an automatic fail.
- **Open-item contract:** make sure that each open item has an owner, a date and a consequence.
- **Exclusivity:** make sure that no client-facing piece has both an open item and a stated doubt.

### Step 6: Check convergence

Do this step if the user gave you more than one piece, or if you edited pieces for the user before in this session. Compare the pieces. Look for these repeated patterns across the set:

- The same opener type.
- The same paragraph count, with a difference of one or less.
- The same closing move.
- The same register.

Each repeated pattern is a finding at the set level. Report set-level findings separately from the findings for each piece.

Also check the set for the fingerprints that this layer itself makes: metric openers, closes with a date stamp, a concession paragraph in every recommendation, chat fragments that you added, and an open item that is always one paragraph.

---

## Severity

Findings do not all have the same value. An early version of this file gave the same score to a formula phrase and to a fabricated statistic. There are three tiers:

**Critical.** A claim, number or attribution that is not true or that you cannot trace. A fabricated addition. An open item in client-facing work without an owner and a date. These are not style problems. You cannot balance them against other items.

**Structural.** A Layer 2 habit: stated takeaway, atmospheric opener, front-loaded context, epilogue, tidy resolution, single track, body report, vague allusion. Each habit changes how the piece is built.

**Surface.** A Layer 1 item: a banned word, a formula phrase, an em dash, a compound hyphen, a weak verb. Each item takes five seconds to fix.

## Verdicts

Score by density, not by raw count. Then you do not judge a 2,000-word report on the same scale as a tweet. Density is the number of findings for each 100 words.

| Verdict | Condition |
|---|---|
| Clean | No critical findings. Structural density below 0.3 and surface density below 0.5 |
| Passes with flags | No critical findings. Structural density below 0.8, surface density below 1.5 |
| Needs work | No critical findings, either density above its threshold |
| Fails | Any critical finding |

Worked example: a 380-word section has one surface finding and three structural findings. Its surface density is 0.26 and its structural density is 0.79. The verdict is Passes with flags. With raw counts, the section looked like a failure. This table corrects that calibration error.

A critical finding is more important than all other results, also in a draft that is otherwise clean. A fabricated aside is worse than the tell that it replaced. Nothing else in the draft can balance it.

Put the verdict in the first line, not in the last line.

## Triage for long drafts

If the draft has more than approximately 800 words, report the ten findings with the highest severity in full. For the other findings, give raw counts by category. A list of sixty findings is not a work item. It is a wall, and the writer fixes none of the findings.

Do not cut critical findings. Report all of them, however many there are.

## What a Clean verdict does not mean

This mode scores the absence of tells. It does not score if the writing is good. Empty prose scores Clean, because it contains nothing to mark. A draft that says something risky always scores worse than a draft that says nothing.

Thus a Clean verdict means that the draft has no fingerprints. It does not mean that the draft is ready to send. If a draft scores Clean and is also empty, say so in one line under the verdict. That line is the only place in this mode for a judgement about quality.

## The cost line

End each report with one sentence. The sentence names what the draft loses if the writer applies every finding. Do not hedge. Give a real account, for example: the rhythm that the em dash carried, the warmth that the closing paragraph gave a cold email, or the emphasis that the rule of three gave.

Without this line, the mode only makes text flat. The writer must know the cost before the writer pays it. Sometimes the correct decision is to keep the finding and accept the tell.

---

## The report is internal

The verdict words are for internal use, not for the person who receives the text. "Fails" describes a draft against a ruleset. If someone sends the report to the writer of the draft, or to the client whose copy you audited, "Fails" seems to describe that person.

There are two rules:

1. Do not write the report for the author unless the user says that the author gets it.
2. If the user says that the author gets it, ask before you write. Then remove the verdict line and start with the findings. A ranked list of specific fixes is acceptable to the person who wrote the text. A grade is not.

## Re-audits

If the user returns with a revised draft, audit only the changes. Do not start again.

Report these items:

- The previous verdict and the new verdict.
- The findings that the revision closed.
- The findings that are still open, with the original quote.
- The new findings.

Mark the findings that the revision added in a separate list. A fix that adds a new fingerprint is the most common result of a second pass. The writer cannot see it unless you say so.

If nothing changed, say so in the first line. Do not repeat the original report.

## What is not a violation

False positives are the main failure of this mode. These items are not findings:

- A banned word with its precise technical meaning: a named software framework, a cryptographic key, real UI navigation.
- AI tells inside a quote from a real person or source. Record them, but do not count them.
- A rule outside the length band of the draft.
- A signal that has a closed register gate.
- A structure that is correct for the register: single-track logic in a procedure, closure in a legal position, explicit statements in safety instructions.
- The habits of the writer: long sentences, formality, many semicolons, British spelling. Style is not a tell.

If you think that an item is a violation but the register can justify it, put it in Contested. Give both readings. Contested items do not count toward the verdict.

---

## Output format

Give five blocks, in this order:

1. **Verdict.** One line. The verdict, the word count, the band, and the register if it has a gate.
2. **Layer 1.** Raw counts by category. You can leave out zero counts.
3. **Layer 2.** One line for each violated habit. Each line has a quote of fewer than fifteen words and the rule name. For the in-scope habits that the draft obeys, write one summary line, not eight lines.
4. **Budget and contract.** The number of additions, the source test result, the open-item contract result and the exclusivity result. One line each, only where relevant.
5. **Contested.** Items that the register can justify, with both readings. If there are no items, leave out this block.

If the user gave you a set, add a sixth block: **Convergence**. List what occurs again across the pieces.

---

## Audit your own output

Before you give a strict review to the user, do step 3 on the review itself. Audit reports from this skill failed their own rules in the past. They started with framing and not with the verdict. They ended with a paragraph that explained what the findings meant. They had the same shape every time.

Put the verdict first. End the report on the cost line. Do not add a summary at the end.

This mode has one limit that you must state, not hide. The auditor and the ruleset have the same origin. A model scores text against criteria that a model helped to write, with a feature space that comes from the detection of models. That is not an independent review, and the self-audit rule above does not make it independent. It finds the obvious failures. It always misses the problems that the ruleset itself cannot see.

If a verdict is important, a person must read the draft. This mode makes the area that the person must examine smaller. It does not replace the person. If a user starts to use the verdict as the decision, tell the user this.
