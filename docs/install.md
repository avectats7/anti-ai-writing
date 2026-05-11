# Install Guide

Three install paths, in rough order of how most people will use this skill.

---

## Path 1: Claude Code

Inside any Claude Code session:

```bash
/plugin marketplace add avectats7/anti-ai-writing
/plugin install anti-ai-writing
```

To verify:

```bash
/plugin list
```

You should see `anti-ai-writing` in the list. The bundled skill is auto-discovered from `skills/anti-ai-writing/SKILL.md`.

To update later:

```bash
/plugin marketplace update avectats7/anti-ai-writing
```

To remove:

```bash
/plugin uninstall anti-ai-writing
/plugin marketplace remove avectats7/anti-ai-writing
```

---

## Path 2: Claude Cowork

Download:

[`dist/anti-ai-writing.skill`](../dist/anti-ai-writing.skill)

Open the file. Cowork will detect the `.skill` format and install it.

---

## Path 3: Manual install

```bash
git clone https://github.com/avectats7/anti-ai-writing.git
mkdir -p ~/.claude/skills/
cp -r anti-ai-writing/skills/anti-ai-writing ~/.claude/skills/
```

Restart Claude. The skill should appear in your available skills list.

---

## How to confirm the skill is working

Paste this draft into Claude after install:

> In today's fast-paced world, our innovative platform empowers users to seamlessly navigate complex workflows and unlock the full potential of their data. Furthermore, it's worth noting that we leverage cutting-edge technology to deliver meaningful impact.

If the skill is loaded, Claude will return:
- A Diagnosis block listing 8+ banned words, 2 banned phrases, 1 formulaic transition.
- A Rewrite block with a clean version.
- A Changes block showing the biggest edits.
- A Notes block.

If you just get a generic edit without that structure, the skill is not loaded.

---

## Troubleshooting

### "Plugin not found" in Claude Code

Run the marketplace add command first. Claude Code needs to know about the marketplace before it can install the plugin.

### Skill does not trigger on edit requests

Two common causes:

1. The prompt is too short. Skills trigger on substantive requests. "Edit this" alone may not trigger. "Edit this draft to remove AI tells: [paste]" will.
2. Another editing skill is also installed and outranks this one. Run `/plugin list`.

### The rewrite stripped my voice

Open an issue with the original draft and the bad output. The skill is supposed to preserve voice; if it does not, that is a bug worth fixing.

### A "banned word" appeared in the rewrite anyway

File a bug. The self-edit pass should catch every word on the master list. If a word slips through, that is a bug.

---

## Where to go next

Try the skill on your last LinkedIn post. Try it on a cold email you are about to send. Try it on the first paragraph of your last blog draft.

For deeper study, read `references/examples.md` to see the skill working across formats. Read `references/banned-list.md` to internalise the patterns. Read `references/rewrites.md` to learn the fixes by hand.
