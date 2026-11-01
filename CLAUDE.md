# my-harness

Rules for working in this repo. Add a rule only when something went wrong without it.

## Style

No em-dashes anywhere in this repo's prose (`SKILL.md` files, README, NOTES, ADRs, commit messages, code comments). Where a sentence reaches for one, rewrite it with a comma, colon, period, parentheses, or a conjunction, whichever the sentence actually wants. Never do a blind character substitution.

## What gets added

A skill or rule is added or changed only if it clears this bar: it addresses something that went wrong in a real session (what I ran, what happened, what I expected). Hypothetical improvements do not qualify. Log the failure in `NOTES.md` in the same commit as the change.

Skills copied from mattpocock/skills start as an unmodified baseline commit, so `git diff` shows exactly what I changed.
