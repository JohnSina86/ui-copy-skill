# Voice brief

Four lines that every string on the screen must fit. It is the smallest document that stops two writers, or one writer on two days, from producing two voices. Write it before the first string, and put it at the top of the deliverable.

If the user or the project already has a voice or tone guide, extract these four lines from it and cite the source. If nothing exists, write the block from the brief's product and audience, mark it **assumed**, and ask the owner to correct it. One assumed brief is better than none, because every string can then be checked against something.

## The block
```markdown
**Voice brief** (source: <guide name> | assumed from the brief)
- **Audience:** <who reads the screen, in their own words, and the situation they are in>
- **Register:** <how the brand talks to them: one phrase, plus sentence length and casing rules>
- **Never:** <three words the brand would never use>
- **Would say:** <one sentence the brand would actually say, from the product or written here>
```

### Audience
Name the reader and the moment, not a segment. "Small-cafe owners taking orders during the morning rush" is an audience. "SMB food and beverage" is a segment, and no string can be checked against it. If the brief names two audiences, pick the one the screen serves and note the other.

### Register
One phrase that a stranger could apply: "plain and quick, like a good barista", "precise and unhurried, like a bank statement", "dry, short, no exclamation marks". Add the mechanical rules that follow from it: sentence case or title case for headings, contractions or none, whether numerals are written as digits, how the product is referred to (by name, as "we", or never in first person).

### Never
Three words the brand would never use. Choose words that are **tempting** for this product, not words that are obviously wrong. A bank's never-words might be "easy", "instant" and "magic", because those are exactly what a bank's copywriter reaches for. A toy brand's might be "solution", "leverage" and "optimise". A never-word in any string you wrote is a checklist failure (SKILL.md section 7), including in alt text and button labels. The brief's own Never line, quoted originals, before-values and preserved supplied copy are exempt; a never-word in preserved copy is reported as a proposal for the owner.

### Would say
One sentence in the brand's own voice. If the product already has one (a line from the current site, an email, a support reply the owner is proud of), quote it. If not, write one about the product's actual difference. The test for every other string is: could it follow this sentence without a change of register?

## Filled example
For a mobile ordering flow for a single independent cafe (the brief: regulars want to skip the queue; the cafe's difference is that drinks are made in order of arrival, so an app order is ready when you walk in).

```markdown
**Voice brief** (assumed from the brief)
- **Audience:** regulars on their way to work, ordering on a phone with one thumb, who already know what they want
- **Register:** quick and plain, like the person behind the counter; sentence case; contractions; digits for every number; the cafe speaks as "we"
- **Never:** seamless, journey, experience
- **Would say:** Order now and it's on the counter when you get here.
```

Strings checked against it:

| String | Fits? | Why |
| :--- | :---: | :--- |
| "Order now and skip the queue" | Yes | Plain, a verb and an object, could follow the "would say" sentence |
| "Begin your seamless ordering journey" | No | Two never-words, no object, and a register the counter would never use |
| "Loading your usual" | Yes | Names what is loading, and "your usual" is the regulars' own word |
| "We're experiencing high demand. Please wait." | No | "Experiencing" is the banned word in verb form, "please wait" says nothing, and the register is a call centre's |
| "Busy right now: ready in about 9 minutes" | Yes | Says what happened and when, with a digit |

## Checks
- [ ] The block is at the top of the deliverable, with its source or **assumed**.
- [ ] The audience names a reader and a moment, not a segment.
- [ ] The register has at least one mechanical rule (casing, contractions, numerals, first person).
- [ ] The three never-words are tempting for this product, and none appears in any string.
- [ ] The "would say" sentence is quoted from the product where one exists.
