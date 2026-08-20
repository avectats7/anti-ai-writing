# Changelog

All notable changes to the `anti-ai-writing` skill.

## [2.0.0]: 2026-08-20

### Added
- **Discourse layer.** The skill now edits on two layers. Layer 1 (sentence level) is the original banned word / phrase / structure pass. Layer 2 (discourse level) catches tells that survive a surface edit: stated takeaways, single-track structure, manufactured closure, emotion rendered as physical sensation, atmospheric openers, vague unnamed references, front-loaded context, and the closing epilogue paragraph.
- `references/discourse-tells.md`: catalogue of the eight discourse-level tells, each with what it is, why it reads as machine-written, and how to spot it. Adapted from Russell et al. 2026, StoryScope.
- `references/discourse-rewrites.md`: how to fix each discourse tell without flattening the writer's voice.
- **Strict review mode.** A judgement mode that audits a draft against both layers and returns a verdict plus a finding list instead of a rewrite. Triggers on "strict review," "audit this," "score this," "does this pass," "review estricto."
- `references/strict-review.md`: the scoring rubric and output format for strict review mode.

### Changed
- `SKILL.md`: rewritten around the two-layer model and strict review mode.
- `references/examples.md`: expanded with discourse-level before/after pairs.

## [1.0.0]: 2026-05-12

### Added
- Initial release. `SKILL.md` workflow (read, scan, rewrite, reread aloud, output with diagnosis).
- `references/banned-list.md`: full Era 1, Era 2, Era 3 banned word lists. Banned phrases (sycophantic openers, summary phrases, hedgers, vague openers, buzzword phrases, contrastive AI patterns). Banned structural patterns (bulleted bold titles, default rule of three, em dashes, en dashes, compound-word hyphens, formulaic transitions). Weak verb substitution table. Spanish AI tells map. Master alphabetical word list.
- `references/rewrites.md`: word-level substitutions, phrase-level rewrites, em dash position fixes, rule-of-three fixes, bulleted-bold-title fixes, formulaic transition fixes, weak verb rewrites, sentence-level rewrites, rhythm restoration strategies.
- `references/examples.md`: 30 before-and-after pairs across tweets, emails, LinkedIn posts, blog intros, marketing copy, About pages, internal communication, Spanish examples, and edge cases (technical writing, legal register, quoted material).
- `dist/anti-ai-writing.skill`: Cowork install bundle.
- Claude Code plugin manifest + single-plugin marketplace manifest.
