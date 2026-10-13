---
name: ui-copy
description: >-
  Specific, non-interchangeable UI copy: headlines, CTAs, labels, loading, empty and error states and other microcopy, checked with a specificity test, a ban list, a voice brief and a placeholder detector. Use when writing or reviewing UI strings, or when copy reads as placeholder or could belong to any product. Not for essays, emails, documentation, long-form articles, SEO writing or translation.
metadata:
  version: "1.0.0"
---

# UI Copy (v1.0)

Most generic UI is generic because of its words: a headline that fits any competitor, a button that says "Get started" with nothing to start, a card that still says "Your text here". This skill writes and reviews the strings on a screen. It owns no colours, tokens or laws: looks are `ui-styles`, structure and behaviour are `ux-laws`. This file is the routing layer; the phrase lists, patterns and the detector live in `references/`.

**Scope.** Strings only: headlines, subheads, buttons and links, labels, placeholders, helper text, alt text, the `<title>`, and the loading, empty, error, success and confirmation states. It never changes what a control does. If the only honest label implies a different behaviour, say so and leave the behaviour to the owner.

## 0. Before you write (mandatory)
1. **Read the brief.** You need the product, the audience and the one thing the product does differently. If any of the three is missing, ask for it once, then state your assumption and label every string that rests on it.
2. **Read or write the voice brief** ([voice-brief.md](references/voice-brief.md)): audience, register, three words the brand would never use, one sentence the brand would say. If none exists, write one from the brief, mark it **assumed**, and put it at the top of your answer so the owner can correct it.
3. **Preserve supplied copy.** A string the user wrote, pasted or marked as final goes into the deliverable unchanged. If it fails a rule here, write the proposal in a separate **Proposed changes** block: original, proposal, the rule it failed, one line of reason. Never apply it silently, and never mix proposals into the delivered strings.
4. **Never invent a fact.** A number, a feature, a customer, a price or a guarantee appears in a string only if the brief or the product supports it. When a rule below asks for one you don't have, write `[needs a fact: what]` in its place and list it under **Needs a fact**.

## 1. The specificity test
Take the headline and remove the brand name. Then ask: **could a competitor publish this unchanged?** If yes, it fails. "Analytics that work for you" fails. "See which signup step loses the most users, by Tuesday" passes, because it names what, for whom and the difference.

Rewrite until the headline names all three:
| Part | Question it answers | Fails when |
| :--- | :--- | :--- |
| **What** | What does the user get or do? | A category word stands in for the thing: "a solution", "a platform", "tools" |
| **For whom** | Who is this for, in their own words? | "Everyone", "teams", "businesses", or nobody at all |
| **The difference** | Why this and not the one next to it? | An adjective does the work: "powerful", "seamless", "modern", "beautiful" |

Stop after three rewrites. If the headline still fails, the brief lacks the difference. Say so and write `[needs a fact: the difference]` rather than inventing one. Run the same test on subheads and feature headings; the "for whom" part may be inherited from the hero.

## 2. The ban list
[ban-list.md](references/ban-list.md) groups the interchangeable phrases by where they appear (headlines, CTAs, feature blurbs, badges, trust lines, states) and gives each a **replacement pattern**, never a replacement phrase. A replacement phrase would become the next cliché. A banned phrase that stays must be justified in one line in the deliverable; a voice brief that quotes it as the brand's own sentence is a valid justification.

## 3. Headline and CTA rules
- **Verb plus object.** A button or link names the action and its object: "Order the flat white", "Export this report", "Invite your team". Never "Get started", "Learn more", "Submit", "Continue", "Click here" or "Go" without an object. If the object is on the button already by context (a card titled "Weekly report" with "Download"), say so in the rule column.
- **The label matches the result.** After the tap, the user sees what the button promised: the page heading, the created thing or the completed action. A button that says "Send" and opens a form is wrong.
- **One promise per headline.** "Faster checkout and better analytics and lower fees" is three headlines. Pick the one the brief ranks first; the others become section headings.
- **Numbers over adjectives**, when the brief supplies the number: "Set up in 4 minutes" beats "Quick setup". Without a number, cut the adjective instead of inventing one (section 0.4).
- **Headline length.** A hero headline fits on two lines at 375 px, which is about eight words in most display faces. A CTA label is two to four words.
- **Name the thing, not the category.** "Your invoices" not "Your documents", "the flat white" not "the item".
- **No question headlines that the reader answers with "no"**, and no headline that repeats the nav label or the `<title>` (section 5).

## 4. State microcopy
Every component that loads or submits data has these states (the suite builds them at stage 3), and each one has required parts. Each string is **under 12 words**. Patterns and examples are in [state-microcopy.md](references/state-microcopy.md).

| State | Must say | Must not | Example |
| :--- | :--- | :--- | :--- |
| **Loading** | What is loading | "Loading…" alone, "Please wait" | "Loading your October invoices" |
| **Empty** | Why it is empty and what to do next | "No data", "Nothing here" with no action | "No orders yet. Add a drink to start one." |
| **Error** | What happened and the way out | "Something went wrong", "Oops", blame | "Card declined. Try another card or pay at the counter." |
| **Success** | What happened and what is next | "Success!" alone | "Order sent to the counter. Ready in about 6 minutes." |
| **Confirmation** | What will happen and to what; the button repeats the verb | "Are you sure?", "OK", "Yes" | "Delete 3 photos? This can't be undone." with a "Delete 3 photos" button |

Counts in a state come from the data ("3 photos"), never from a guess. A string that needs the user to retry says when or how, not just "Try again".

## 5. The placeholder detector
Run [placeholder-detector.md](references/placeholder-detector.md) over **every string** before and after you write, including alt text, labels, badges and the `<title>`. It lists the tells with a check for each. The main ones:
1. **Lorem ipsum** and any other filler text, in any language.
2. **Template strings**: "Your text here", "Insert headline", "Feature 1", "Image description", `{{name}}`, `[Brand]`, "John Doe", `example.com`, 555 phone numbers.
3. **Repeated adjectives**: the same adjective twice on one screen, or any of the ban list's adjectives at all.
4. **A headline that equals the page title**, the nav label or the section's own name ("Features" above the features).
5. **Three-item lists with parallel vague nouns**: "Fast. Simple. Secure.", "Speed. Quality. Trust.", or three cards whose headings are abstract nouns with no object.

Report the sweep as a table: location, string, tell, fix. A sweep that finds nothing says "0 tells in N strings", with N counted.

## 6. Workflow
1. Do section 0. List the strings in scope with their locations, and mark which ones the user supplied.
2. **Sweep first.** Run the detector (section 5) and the ban list (section 2) over the list, and record the table. Reviewing without writing stops here with the table and the proposals.
3. **Write.** Headlines through the specificity test (section 1), buttons and links through section 3, states through section 4. Keep every string inside the voice brief: the three never-words don't appear, and each string could follow the brand's one sentence without a change of register.
4. **Deliver one string table**: location, before, after, rule applied. Supplied copy appears unchanged; its proposals go in the Proposed changes block, and missing facts in Needs a fact.
5. Run the checklist in section 7, then re-run the detector on your own output and report the count.
6. If the user asks how the copy looks or whether the screen is usable, that is `ui-styles` or `ux-laws`. Don't grade layout, contrast or hit areas here.

## 7. Pre-delivery checklist
- [ ] Voice brief written or read, marked assumed if written here, and placed at the top.
- [ ] Every headline and feature heading passes the specificity test with the brand name removed, or carries `[needs a fact]`.
- [ ] Every button and link is verb plus object, and its label matches what happens next.
- [ ] One promise per headline; numbers only where the brief supplies them.
- [ ] Every loading, empty, error, success and confirmation string has its required parts and is under 12 words.
- [ ] Detector run over every string, including alt text and the `<title>`, before and after writing, with both counts reported.
- [ ] No ban-list phrase remains without a one-line justification.
- [ ] None of the three never-words appear anywhere.
- [ ] Supplied copy delivered unchanged; proposals and missing facts in their own blocks.
- [ ] No string changes what a control does; any label that would is flagged for the owner.

## References
- [ban-list.md](references/ban-list.md): interchangeable phrases grouped by type, each with a replacement pattern.
- [voice-brief.md](references/voice-brief.md): the voice brief block and a filled example.
- [state-microcopy.md](references/state-microcopy.md): patterns and examples for loading, empty, error, success and confirmation states.
- [placeholder-detector.md](references/placeholder-detector.md): the tells, a check for each, and the sweep table.
