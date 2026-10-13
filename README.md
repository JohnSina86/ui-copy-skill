# UI Copy AI Skill (`ui-copy`)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skill: Agents](https://img.shields.io/badge/Skill-Claude%20Code%20%2F%20Antigravity-purple.svg)](SKILL.md)

An agent skill for the **words on a screen**: headlines, buttons, labels, and the loading, empty, error, success and confirmation states. It's designed for AI coding assistants (Claude Code, Google Antigravity, Cursor, Copilot), so the copy they write names the product instead of fitting any product.

Most generic UI is generic because of its words. A headline that any competitor could publish, a "Get started" button with nothing to start, a card that still says "Your text here". This skill catches those and makes the assistant reach for the brief instead.

> **Scope:** UI strings only. It owns no colours, tokens or layout rules; those are in [ui-styles](https://github.com/JohnSina86/ui-styles-skill). It grades no usability; that is [ux-laws](https://github.com/JohnSina86/ux-laws-skill). It is not for essays, emails, documentation, articles, SEO writing or translation.

## No developer? Start here
You don't need to know any technical words. Install the skill, then paste the text from your page or describe the screen and say what the product does and who it is for. For example: *"Here is the text on my cafe's ordering page. Regulars order ahead so the coffee is ready when they walk in. Make the words say that."*

The assistant will show you a short **voice brief** (who you're talking to, how you sound, three words you'd never use, one sentence you would say) so you can correct it, then a table of every line with before and after. A line you mark as final, or paste without asking for a change, is kept as you wrote it; if the skill thinks it could be better, it says so separately and leaves the choice to you. A line you ask it to rewrite is rewritten, with your original shown beside it.

## What's inside
- **The specificity test** ([`SKILL.md`](SKILL.md) section 1): remove the brand name; if the headline fits any competitor it fails, and it is rewritten until it names what, for whom and the difference. Three rewrites, then it asks for the missing fact rather than inventing one.
- **A ban list** ([`references/ban-list.md`](references/ban-list.md)): interchangeable phrases grouped by where they appear, each with a replacement **pattern**, never a replacement phrase.
- **A voice brief** ([`references/voice-brief.md`](references/voice-brief.md)): audience, register, three never-words, one sentence the brand would say, with a filled example.
- **Headline and CTA rules**: verb plus object, one promise per headline, numbers over adjectives when the brief has the number, and the label matches what happens next.
- **State microcopy** ([`references/state-microcopy.md`](references/state-microcopy.md)): what loading, empty, error, success and confirmation strings must say, each under 12 words, with a worked set.
- **A placeholder detector** ([`references/placeholder-detector.md`](references/placeholder-detector.md)): twelve tells (lorem, template strings, repeated adjectives, a headline equal to the page title, three-item lists of vague nouns, and more), with a check for each and a sweep table.
- **Honesty rules**: supplied copy is sorted into preserved copy (marked final or given without a change request, delivered unchanged with proposals in their own block) and copy authorised for rewriting (the user asked, rewritten with the original beside it), and no number, customer or guarantee appears unless the brief supports it.
- **Evals** in [`evals/`](evals/): four functional tasks and twenty trigger queries (half are near-miss negatives).

## Installation

Install a tagged release, so you get a reviewed version and not whatever the default branch holds later.

> **Current release: none yet. `v1.0.0` is pending.** The tag is created only after the checks in [`RELEASING.md`](RELEASING.md) pass, including a hand run of the evals with the results recorded in the changelog below. Until then the install lines below point at a tag that does not exist, and `main` holds the reviewed branch. Once tagged, confirm an install with `git -C <install dir> describe --tags`, which should print `v1.0.0`.

### Claude Code
User level, so the skill is available in every project:
```bash
mkdir -p ~/.claude/skills && git clone --branch v1.0.0 https://github.com/JohnSina86/ui-copy-skill.git ~/.claude/skills/ui-copy
```
```powershell
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null; git clone --branch v1.0.0 https://github.com/JohnSina86/ui-copy-skill.git "$HOME\.claude\skills\ui-copy"
```
For project level, run this from the project root:
```bash
mkdir -p .claude/skills && git clone --branch v1.0.0 https://github.com/JohnSina86/ui-copy-skill.git .claude/skills/ui-copy
```
```powershell
New-Item -ItemType Directory -Force ".claude\skills" | Out-Null; git clone --branch v1.0.0 https://github.com/JohnSina86/ui-copy-skill.git ".claude\skills\ui-copy"
```
The folder name must be `ui-copy`, which is the skill's `name`. Claude Code loads the skill on demand from its description, so you don't need to edit a system prompt.

### Google Antigravity
```bash
mkdir -p .agents/skills && git clone --branch v1.0.0 https://github.com/JohnSina86/ui-copy-skill.git .agents/skills/ui-copy          # project
mkdir -p ~/.gemini/config/skills && git clone --branch v1.0.0 https://github.com/JohnSina86/ui-copy-skill.git ~/.gemini/config/skills/ui-copy   # global
```

### Cursor, Copilot and other tools without native skills
Clone it as above, then reference it in your rules file:
```markdown
When writing or reviewing UI strings (headlines, buttons, labels, empty, loading and error states), follow .agents/skills/ui-copy/SKILL.md.
```

## Example prompts

- "Rewrite the hero headline and buttons; right now they could be any analytics tool."
- "Write the loading, empty and error states for the orders list in our cafe app."
- "Sweep this page for placeholder copy before we ship."
- "Our founder's headline is final. Write the subhead and button, and tell me separately if you'd change the headline."

## Companion skills

[ui-styles](https://github.com/JohnSina86/ui-styles-skill) handles how the screen looks and [ux-laws](https://github.com/JohnSina86/ux-laws-skill) how it behaves. [ui-ux-suite](https://github.com/JohnSina86/ui-ux-suite-skill) runs a whole job in order; adding this skill to its pipeline is planned for a later suite release.

## Layout
```
SKILL.md                            the routing file: specificity test, headline and CTA rules, state table, detector summary, workflow, checklist
references/ban-list.md              interchangeable phrases by type, each with a replacement pattern
references/voice-brief.md           the four-line voice brief and a filled example
references/state-microcopy.md       loading, empty, error, success and confirmation patterns with a worked set
references/placeholder-detector.md  twelve tells with a check each, the sweep table and the procedure
evals/                              4 functional evals and 20 trigger queries (data only)
RELEASING.md                        the release checklist
```

## Changelog

- **v1.0.0 (pending, not tagged)**: first version.
  - The specificity test, the ban list with replacement patterns, the voice brief block, headline and CTA rules, state microcopy under 12 words with required parts per state, and the placeholder detector with twelve tells.
  - Supplied copy is preserved and proposals go in their own block; no invented facts, with `[needs a fact]` in their place. An error after a dropped connection is written as an unknown outcome unless the client knows the request never left, and "saved", "retry" and "not charged" are promised only with product evidence.
  - **Functional evals, hand-run on 2026-10-13** in fresh subagent contexts that read only this skill (per-expectation results in the pull request). First round: eval 1 passed 4 of 6, then 5 of 6 after the preserved-copy rule was corrected; evals 2, 3 and 4 passed 6 of 6. Second round, after the second inspection's fixes (string classes, role-based rules, status versus resend, detector candidates, CTA destinations in the prompts): evals 2, 3 and 4 passed 6 of 6; eval 1 passed 5 of 6 twice. The first of those runs exposed that the skill's own passing headline example named no audience; the example was fixed and the final run's headline names all three parts. Its remaining fail is expectation 3 as then worded, which required the secondary link to be verb plus object although it scrolls to a section; the expectation was corrected to judge it as navigation, under which that run passes. The run was not repeated after that correction.
  - **Trigger evals, run twice on 2026-10-13** as bare queries to Sonnet subagents in an empty project folder, with the skill temporarily installed: round 1 (first description) loaded on 2 of 10 positives and 0 of 10 negatives; round 2 (current description) loaded on 3 of 10 positives and 0 of 10 negatives. The negatives hold. The positives mostly did not load because the subagents went straight to searching the empty folder and asked for input; the same queries in a real session with a real project are **unmeasured**. The held-out half was read before the description was edited, so this set is no longer blind; a release needs fresh held-out queries. The automated tester was not run. The trigger set was not re-run after the second inspection's fixes, because the description did not change.

## License

MIT License © 2026 [JohnSina86](https://github.com/JohnSina86). See [LICENSE](LICENSE).
