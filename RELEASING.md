# Releasing

Run this checklist before tagging. Each step is a manual check that doesn't need a script.

1. **Frontmatter:** `name` is `ui-copy` (the install folder name), the description is at most 400 characters, third person, with a "Use when" and a "Not for" clause, and **contains no hard-coded counts** of tells, phrases or rules. The "Not for" clause still names general writing (essays, emails, documentation, articles, SEO, translation), so the skill doesn't trigger on those. `metadata.version` matches the tag.
2. **Size:** `SKILL.md` is at most 200 lines. Every file in `references/` is linked from `SKILL.md`. Every file over 100 lines starts with a table of contents.
3. **Rule parity:** the five detector tells summarised in `SKILL.md` section 5 exist in `references/placeholder-detector.md` with the same meaning, and the state table in section 4 (must say, must not) matches the per-state rules in `references/state-microcopy.md`. The banned openers in `references/ban-list.md` section 8 agree with the state table's "must not" column.
4. **Patterns, not phrases:** every row of `references/ban-list.md` gives a replacement **pattern** with slots, never a finished phrase. A finished phrase in that column is a failure, because it would become the next cliché.
5. **No invented facts in examples:** every number in an example (minutes, counts, steps) is a slot (`{minutes}`), comes from the worked cafe brief in `references/voice-brief.md` and `references/state-microcopy.md`, or sits in a table row that is plainly a pattern illustration. No example reads as a claim about a real product. Search `references/` for digits and check each.
6. **Pointers:** search the repository for `SKILL.md §`, `section` and any link to a file or heading that doesn't exist.
7. **Cross-skill:** any law number cited from `ux-laws` matches that skill's numbering in its current tag, and nothing here restates a law, a token or a style rule. This skill owns strings only.
8. **Evals:** run the four functional evals by hand (`evals/README.md`), including eval 4's preserved-copy case, and record the result in the release notes. Hand-check the twenty trigger queries, tuning set before held-out.
9. **Tag:** update the README status line and the changelog **first**, and commit them. Then run `git tag -a vX.Y.Z -m vX.Y.Z`, and check the tagged tree with `git show vX.Y.Z:README.md`.
