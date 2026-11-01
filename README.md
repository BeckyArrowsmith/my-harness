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

## Why these

_TODO: fill in as I figure out how I want to write code._

## Install

Symlink each skill into the global skills folder, so every project sees them and a
`git pull` keeps them current:

```bash
for n in grill-with-docs grilling domain-modeling; do
  ln -s "$PWD/skills/$n" ~/.claude/skills/$n
done
```

Symlink the global rules too, so they apply in every project, not just this repo:

```bash
ln -sf "$PWD/global/CLAUDE.md" ~/.claude/CLAUDE.md
```
