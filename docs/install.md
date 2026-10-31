# Install Guide

There are three install paths. Most people use Path 1.

---

## Path 1: Claude Code

In a Claude Code session, run these commands:

```bash
/plugin marketplace add avectats7/anti-ai-writing
/plugin install anti-ai-writing
```

To make sure that the install worked, run this command:

```bash
/plugin list
```

The list must show `anti-ai-writing`. Claude Code finds the bundled skill in `skills/anti-ai-writing/SKILL.md` automatically.

To update the skill, run this command:

```bash
/plugin marketplace update avectats7/anti-ai-writing
```

To remove the skill, run these commands:

```bash
/plugin uninstall anti-ai-writing
/plugin marketplace remove avectats7/anti-ai-writing
```

---

## Path 2: Claude Cowork

1. Download [`dist/anti-ai-writing.skill`](../dist/anti-ai-writing.skill).
2. Open the file. Cowork finds the `.skill` format and installs the skill.

---

## Path 3: Manual install

```bash
git clone https://github.com/avectats7/anti-ai-writing.git
mkdir -p ~/.claude/skills/
cp -r anti-ai-writing/skills/anti-ai-writing ~/.claude/skills/
```

Restart Claude. The skill must appear in your list of available skills.

---

## How to make sure that the skill works

After the install, paste this draft into Claude:

> In today's fast-paced world, our innovative platform empowers users to seamlessly navigate complex workflows and unlock the full potential of their data. Furthermore, it's worth noting that we leverage cutting-edge technology to deliver meaningful impact.

If Claude loaded the skill, Claude returns these four blocks:
- A Diagnosis block. It lists 8 or more banned words, 2 banned phrases and 1 formulaic transition.
- A Rewrite block with a clean version.
- A Changes block with the largest edits.
- A Notes block.

If you get a general edit without that structure, Claude did not load the skill.

---

## Troubleshooting

### Claude Code shows "Plugin not found"

Run the `marketplace add` command first. Claude Code must know the marketplace before it can install the plugin.

### The skill does not start on edit requests

There are two usual causes:

1. **The prompt is too short.** Skills start on requests that have content. "Edit this" alone possibly does not start the skill. "Edit this draft to remove AI tells: [paste]" starts it.
2. **A different editing skill has a higher priority.** Run `/plugin list` to see the installed skills.

### The rewrite removed my voice

Open an issue. Include the original draft and the bad output. The skill must keep your voice. If it does not, that is a bug.

### A banned word is in the rewrite

Report a bug. The self-edit pass must find every word on the master list. If a word gets through, that is a bug.

---

## Next steps

Use the skill on your last LinkedIn post, on a cold email before you send it, or on the first paragraph of your last blog draft.

To learn more, read these files:
- `references/examples.md` shows the skill on different formats.
- `references/banned-list.md` shows all the patterns.
- `references/rewrites.md` shows how to make the fixes yourself.
