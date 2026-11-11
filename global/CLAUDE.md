# Global rules

Loaded in every project (symlinked to `~/.claude/CLAUDE.md`). Same bar as the rest of this repo: a rule is added only when something went wrong without it.

## Style

No em-dashes in prose I write: docs, READMEs, commit messages, code comments. Where a sentence reaches for one, rewrite it with a comma, colon, period, parentheses, or a conjunction, whichever the sentence actually wants. Never do a blind character substitution.

## Code

Keep complexity low for whoever reads the code next, me included. It shows up three ways; avoid all three.

- **Cognitive load**: keep what a reader has to hold in their head small. Prefer the plain, explicit version over the compact or clever one, even when it's longer.
- **Change amplification**: one change should mean editing one place. Don't add abstractions, layers, or options until the same knowledge would otherwise live in two places.
- **Unknown unknowns**: make it obvious what a change touches and what the code depends on. No hidden coupling or surprising side effects.

## Git

Make atomic commits. Each commit is a thin slice of real value or one complete outcome, with a message saying what that outcome is. Don't bundle unrelated changes, and don't split one outcome across commits.
