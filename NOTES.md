# Notes

A running log: what I tried, what went wrong, what I changed and why.

## 2026-11-01
- Started harness repo. Copied grill-with-docs, grilling, domain-modeling from Matt Pocock's skills repo.
- **Failure: the em-dash rule only applied inside this repo.** While designing flaggy, I
  went looking for my em-dash rule and found it lived in this repo's CLAUDE.md, which
  Claude only loads here. `~/.claude/CLAUDE.md` was empty. Fix: added `global/CLAUDE.md`,
  symlinked to `~/.claude/CLAUDE.md`, and moved the em-dash rule there in general form.
- **Failure: had to ask for atomic commits by hand.** In the flaggy session I had to tell
  Claude to make atomic commits, each a thin slice of value, because nothing in the harness
  said so. Fix: added the rule to `global/CLAUDE.md`.

## Decisions
- **Interview style: kept as-is.** `grilling` asks every ready question in one numbered
  batch, each with a recommended answer, rather than one question at a time. I prefer
  being able to say "yes" to a lot at once and spend effort only where I disagree.
- **Adopted Matt's "observed failure" bar** (from his SCOPE.md). Nothing gets added or
  changed unless it fixes something that went wrong in a real session. Keeps the harness
  small and every piece explainable. Written into CLAUDE.md.
- **No em-dashes** in repo prose, also taken from his CLAUDE.md. Purely a style choice.
