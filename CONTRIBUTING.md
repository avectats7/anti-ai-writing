# Contributing to Anti-AI Writing

Thank you for considering a contribution. The banned list is a moving target: AI models change, the default voice shifts, new tells appear. PRs help the skill stay current.

## What contributions are welcome

In rough order of impact:

1. **New banned words.** If you can show a word is now a recognisable AI tell (with three or more public examples, ideally from different models), open a PR to `references/banned-list.md`. State which era it belongs to.
2. **New banned phrases.** Same standard as words: three or more public examples.
3. **Spanish list additions.** The Spanish list is a starter map. Native Spanish speakers especially welcome. Both Latino Spanish and Castilian fingerprints are wanted.
4. **Other languages.** Portuguese, French, German, Italian, Japanese, Mandarin. Each language has its own AI-default register. A new section in `banned-list.md` per language is the right format.
5. **New examples for `references/examples.md`.** Before-and-after pairs. Real drafts (anonymised) are stronger than invented ones. The pair should illustrate at least one specific banned pattern.
6. **Rewrite patterns for `references/rewrites.md`.** If you find a recurring AI structure not yet listed, propose the diagnostic plus the fix.
7. **Bug reports.** If the skill misfires (over-triggers, under-triggers, returns a worse draft, strips voice), open an issue with the original draft and the bad output.

## What contributions are not welcome

- Words or phrases that are merely overused. The list targets AI fingerprints specifically, not bad writing in general. "Suddenly" is overused but not an AI tell. Skip it.
- Examples without a clear teaching point.
- Aesthetic complaints ("I just don't like the word X"). Use a personal style guide for that.
- Changes that would weaken the skill's English coverage to favour another language. Add, do not replace.

## House style

The reference files dogfood the skill's own rules. Contributions should too.

- No em dashes, en dashes, or standalone hyphens in prose. The character can appear as a subject of discussion ("the em dash is banned") or in a quoted "Original:" example, but not in your own running prose.
- No compound-word hyphens ("go-to-market" becomes "GTM" or "go to market").
- No banned words from the list. The file `references/banned-list.md` is the source of truth.
- Lead with the point. Vary sentence length. Read aloud.

## How to propose a change

1. Fork the repo.
2. Create a branch named after the change. Examples: `add-spanish-aprovechar`, `era-3-new-words-from-claude-sonnet-46`, `fix-rewrite-rule-of-three-edge-case`.
3. Make the edit.
4. Run the skill on your own change. If your change reads like AI, fix it.
5. Open a pull request. In the description, explain what you added and why. Cite public examples for new banned items.

## Maintainer

[@avectats7](https://github.com/avectats7). Issues and PRs reviewed on a best-effort basis.
