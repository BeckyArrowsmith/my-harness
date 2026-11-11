# my-harness

My personal setup for working with coding agents. Started from
[mattpocock/skills](https://github.com/mattpocock/skills); I'm adapting it as I learn
what works for me. The skills are used under the MIT license, see
[THIRD-PARTY-LICENSES.md](./THIRD-PARTY-LICENSES.md).

## Skills

| Skill | What it's for | Status |
|---|---|---|
| `grill-with-docs` | Entry point: interview me about a plan, writing docs as we go | from Matt, unmodified |
| `grilling` | The interview technique itself | from Matt, unmodified |
| `domain-modeling` | Maintains GLOSSARY.md and ADRs | from Matt, unmodified |
| `handoff` | Compacts a conversation into a document for another agent to continue | from Matt, unmodified |
| `retro` | Suggests improvements to the agent's environment after a session | from Matt, unmodified |

## Why these

_TODO: fill in as I figure out how I want to write code._

## Install

Symlink each skill into the global skills folder, so every project sees them and a
`git pull` keeps them current:

```bash
for n in grill-with-docs grilling domain-modeling handoff retro; do
  ln -s "$PWD/skills/$n" ~/.claude/skills/$n
done
```

Symlink the global rules too, so they apply in every project, not just this repo:

```bash
ln -sf "$PWD/global/CLAUDE.md" ~/.claude/CLAUDE.md
```

### Cloud sessions

A cloud session starts on a fresh machine with only the project's repo, so it never sees
`~/.claude/CLAUDE.md` from my laptop. To give it the global rules, add this as the setup
script on my cloud environment (claude.ai, environment settings). It runs at the start of
every cloud session and does what the symlink above does locally:

```bash
#!/bin/bash
git clone --depth 1 https://github.com/BeckyArrowsmith/my-harness ~/my-harness
mkdir -p ~/.claude
ln -sf ~/my-harness/global/CLAUDE.md ~/.claude/CLAUDE.md
```

To check it worked, run `/context` in a cloud session and look for
`/root/.claude/CLAUDE.md` under Memory files.

The skills don't come along this way. Enable them on claude.ai instead, and cloud
sessions load them automatically.
