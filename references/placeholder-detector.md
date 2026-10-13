# Placeholder detector

A sweep that finds strings nobody wrote on purpose: filler left from a template, a slot never filled, or a phrase that only reads as copy because the words are in the right place. Run it over **every string** in scope before writing (to find what to replace) and after (to check your own output), and report both counts.

It is a list of tells with a check for each. It is not a style grade: a string can pass every check and still be dull, which the specificity test and the ban list handle. The detector is unsure in a few places; each entry says where.

## Contents
- [What counts as a string](#what-counts-as-a-string)
- [The tells](#the-tells)
- [The sweep table](#the-sweep-table)
- [Procedure](#procedure)
- [Checks](#checks)

## What counts as a string
Everything a user can read or a screen reader can announce on the surface in scope:

| Kind | Where to look | Often missed |
| :--- | :--- | :--- |
| Headings and body | `h1` to `h6`, `p`, list items, table cells | Section headings that only name the section ("Features") |
| Controls | Button and link text, `aria-label`, `title`, `value` on submit inputs | Icon-only buttons with no accessible name (report, don't write) |
| Form text | `label`, `placeholder`, helper and error text, `legend` | Placeholders used as the only label |
| Media | `alt`, figure captions, video titles | `alt="image"`, `alt="photo"`, an empty `alt` on a meaningful image |
| Document | `<title>`, `meta name="description"`, the Open Graph title | A `<title>` still reading "Document", "Untitled" or the framework's default |
| States | Loading, empty, error, success and confirmation strings | Error strings only visible in source |
| Badges and chips | Tags, status pills, counters | "New", "Beta", "Pro" with no description |

Count the strings before the sweep so the report can say "N strings".

## The tells
| # | Tell | Check | Sure? |
| :-: | :--- | :--- | :--- |
| 1 | **Lorem ipsum** and other filler: "lorem", "ipsum", "dolor sit amet", "consectetur"; the Greek, Cyrillic and Chinese fillers; "asdf", "test test", "xxx"; a paragraph of one word repeated | Case-insensitive search for the words; any paragraph where one word is over a third of the text | Sure |
| 2 | **Template strings**: "Your text here", "Insert headline", "Headline goes here", "Add a description", "Feature 1", "Feature 2", "Image description", "Caption", "Button", "Link", "Label", "Title", "Subtitle", "Description", "Lorem" as a name | Exact match, case-insensitive, on the whole string; a heading that is only one of these words | Sure |
| 3 | **Unfilled slots**: `{{name}}`, `{name}`, `%s`, `[Brand]`, `<brand>`, `[Company Name]`, `TODO`, `TBD`, `FIXME`, `XXX` | Search for `{{`, `{`, `[`, `<` followed by a word and the closing bracket, inside visible text, not in source | Sure in text; a `[` can be real copy ("[PDF]"), so read the match |
| 4 | **Sample people and contacts**: "John Doe", "Jane Doe", "John Smith", "Lorem Ipsum" as a person, "example.com", "email@example.com", "test@test.com", 555 phone numbers, "123 Main Street", "Anytown", "00000" postcodes | Exact matches plus a `555-` or `(555)` search | Sure |
| 5 | **Repeated adjectives**: the same adjective twice on one screen, or any adjective from [ban-list.md](ban-list.md) section 7 at all | List every adjective in the strings; any count of 2 or more is a hit; any match with the section 7 list is a hit | Mostly: a repeated adjective can be a deliberate refrain, so quote both occurrences and let the owner decide |
| 6 | **A heading that only names its slot**: a generic section word used as the heading ("Features", "Benefits", "Services", "About", "Overview", "Welcome"), a document default ("Home", "Untitled", "Page 1"), the brand name alone as the hero `h1`, or a heading that names the element ("Card", "Section"). A nav label, `<title>` and `h1` that all say "Order history" are **not** a hit: they describe the content and agree with each other, which is what a user wants | For each heading, ask whether a reader learns what the section contains from the heading alone. Compare with the list of generic words; compare the hero `h1` with the brand name after removing suffixes | Sure for the generic words and defaults; a short descriptive heading ("Pricing" over a price table) is a judgement call, so quote it and say what it would gain from an object |
| 7 | **Three-item lists with parallel vague nouns**: "Fast. Simple. Secure.", "Speed. Quality. Trust.", "Plan. Build. Grow.", three cards headed "Collaboration", "Security", "Analytics" | Any list or card row of exactly three items whose headings are each one or two words and contain no object or verb phrase; also three items whose headings share the same ending ("-tion", "-ity") | Mostly: a three-item list can be real ("Espresso. Filter. Cold brew."), so the check is "no object", not "three items" |
| 8 | **Alt text that names the format**: "image", "photo", "picture", "icon", "logo", "screenshot", "banner", a filename (`hero-final-v2.png`), or the heading next to it repeated | Exact match and a `.png`/`.jpg`/`.svg`/`.webp` search in `alt` | Sure |
| 9 | **Document defaults**: `<title>` "Document", "Untitled", "Home", "Index", "React App", "Vite App", "Next.js", "My App", "Welcome"; `meta description` empty or lorem | Exact match | Sure |
| 10 | **Counts and claims with round placeholders**: "10,000+", "1M+", "99.9%", "#1", "5 stars" with no source in the brief | Search for `+` after a round number, `%` after 99, and `#1`; check each against the brief | Mostly: the number can be true, so the hit is "no source", and the fix is the source or a cut |
| 11 | **Copy that describes the element instead of the content**: a card body that says "This is a card", a hero that says "Hero section", a button "Primary button", a link "Link text" | Exact match on element names used as copy | Sure |
| 12 | **Mismatched language or product**: a string in another language on a monolingual page, another product's name, a left-over "Acme" | Language check per string; search for names not in the brief | Mostly: an intentional foreign word (a dish name) is not a hit |

## The sweep table
```markdown
| # | Location | String | Tell | Fix |
| :-: | :--- | :--- | :--- | :--- |
| 1 | hero `h1` | "Welcome to Acme" | 6 (names the slot, not the content), ban list 1 | "See which signup step loses the most users" |
| 2 | features, card 2 body | "Your text here" | 2 | `[needs a fact: what card 2 is about]` |
| 3 | footer | "Trusted by 10,000+ teams" | 10 | Source from the brief, or cut |
| 4 | hero image | alt "hero-final-v2.png" | 8 | "Dashboard showing the signup funnel with step 3 highlighted" |

**Before:** 4 tells in 31 strings. **After:** 0 tells in 31 strings.
```

The Fix column holds the replacement when the rule and the brief give one, and `[needs a fact: what]` when they don't. Supplied copy that trips a tell goes in the **Proposed changes** block instead (SKILL.md section 0.3), with the tell number as the rule.

## Procedure
1. **Collect** every string per the table above into a list with its location (selector, component name or screen and position). Count them.
2. **Run tells 1 to 4, 8, 9 and 11** mechanically: they are string matches. On a live page or source, a search does it. On a screenshot, read every visible string and say the sweep covered visible text only.
3. **Run tells 5, 6, 7, 10 and 12** by reading: list adjectives, compare headings with their containers, read every three-item group, check every number against the brief.
4. **Write the table**, one row per hit. A string with two tells gets both numbers in one row.
5. **Fix**, then re-run steps 2 and 3 on your own output. Report "Before: N tells in M strings. After: N tells in M strings."
6. A sweep that can't reach part of the surface (a modal that needs a login, a state that needs a failed payment) lists what it couldn't reach, under **Not swept**, instead of claiming zero.

## Checks
- [ ] The string count covers every kind in the first table, including alt text, the `<title>` and the states.
- [ ] Every tell was run, and the ones marked "Mostly" quote the string so the owner can decide.
- [ ] Both counts are reported, and anything unreachable is listed under Not swept.
- [ ] Fixes never fill a slot with an invented fact.
