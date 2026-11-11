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

## 2026-11-11
- **Failure: cloud sessions never saw my global rules.** Designing flaggy in a cloud
  session, Claude missed rules from `global/CLAUDE.md`, because a cloud session only has
  the project's repo and not my `~/.claude`. I worked around it by copying the key rules
  into flaggy's own CLAUDE.md, which will drift. Fix: documented a cloud environment setup
  script in the README that clones this repo and links `global/CLAUDE.md` into place, the
  same way the local symlink does. Once it's confirmed working, flaggy's copy can go.
- **Failure: grill-with-docs settled decisions without writing docs.** During a
  grill-with-docs session on the CastVault project, Claude ran 4 rounds of grilling and
  settled design decisions without creating any docs. It only started writing SPEC.md after
  being asked to. The skill's name promises docs, but nothing in `SKILL.md` told Claude to
  write them as decisions were made.
  Fix: added a rule to `skills/grill-with-docs/SKILL.md` requiring docs to be written
  incrementally as decisions settle, not batched up after grilling.
- **Failure: no structured handoff between sessions.** After a long CastVault session
  (design + build of slice 1), context was large and the next slice needed a fresh session.
  SPEC.md and PROGRESS.md existed but nothing produced a handoff document scoped to what
  the next agent actually needs.
  Fix: pulled the `handoff` skill from mattpocock/skills as an unmodified baseline.
- **Failure: retro was ad hoc.** End of the CastVault session, reviewed what went wrong and
  which skills would have helped. The review surfaced real improvements (the grill-with-docs
  fix, handoff) but the process was unstructured and not repeatable.
  Fix: pulled the `retro` skill from mattpocock/skills as an unmodified baseline.
- **Exception to the bar: a code readability rule with no failure behind it.** Added a
  "Code" section to `global/CLAUDE.md` built on the book's three symptoms of complexity:
  cognitive load, change amplification, and unknown unknowns. Nothing
  had gone wrong yet. I added it anyway because it's the foundation for all the code I'll
  write with Claude, and waiting for the first failure means paying exactly the cognitive
  load the rule exists to prevent. Prompted by rereading *A Philosophy of Software Design*.

## Decisions
- **Interview style: kept as-is.** `grilling` asks every ready question in one numbered
  batch, each with a recommended answer, rather than one question at a time. I prefer
  being able to say "yes" to a lot at once and spend effort only where I disagree.
- **Adopted Matt's "observed failure" bar** (from his SCOPE.md). Nothing gets added or
  changed unless it fixes something that went wrong in a real session. Keeps the harness
  small and every piece explainable. Written into CLAUDE.md.
- **No em-dashes** in repo prose, also taken from his CLAUDE.md. Purely a style choice.
