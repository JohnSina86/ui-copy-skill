# Ban list

Interchangeable phrases, grouped by where they turn up. Each entry gives a **replacement pattern**, never a replacement phrase: a phrase would become the next cliché, a pattern makes you reach for the brief. The pattern's slots (`<what>`, `<for whom>`, `<number>`, `<object>`) are filled from the brief or the product, never invented (SKILL.md section 0.4).

A phrase on this list can stay in the deliverable only with a one-line justification. The voice brief quoting it as the brand's own sentence is a valid one. "It sounds fine" is not.

## Contents
- [How to read an entry](#how-to-read-an-entry)
- [1. Hero headlines](#1-hero-headlines)
- [2. Subheads and taglines](#2-subheads-and-taglines)
- [3. Buttons and links](#3-buttons-and-links)
- [4. Feature headings and blurbs](#4-feature-headings-and-blurbs)
- [5. Badges and labels](#5-badges-and-labels)
- [6. Trust and social-proof lines](#6-trust-and-social-proof-lines)
- [7. Adjectives that do the work](#7-adjectives-that-do-the-work)
- [8. State and error strings](#8-state-and-error-strings)
- [9. Onboarding and welcome](#9-onboarding-and-welcome)
- [10. Pricing](#10-pricing)
- [Checks](#checks)

## How to read an entry
| Column | Meaning |
| :--- | :--- |
| **Phrase** | The string or the shape of string that fails. Case and punctuation don't matter. A phrase in angle brackets is a pattern, so "Welcome to `<brand>`" bans every brand. |
| **Why it fails** | Which part of the specificity test it skips, or which rule in SKILL.md it breaks. |
| **Replacement pattern** | The shape of the string that passes. Fill the slots from the brief. |

## 1. Hero headlines
| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "`<Category>` made simple" / "made easy" / "simplified" / "reimagined" | No what, no for whom; "simple" is an adjective doing the work | `<Verb> <the concrete thing> <for whom or by when>` |
| "The `<category>` platform for modern teams" | "Platform", "modern" and "teams" are all category words | `<What the user gets> for <the named audience>` |
| "Welcome to `<brand>`" | Says nothing the logo doesn't | Delete, or `<What the user can do here>` |
| "Everything you need to `<verb>`" | No difference; every competitor also has everything | `<The one thing> <the audience> can't get elsewhere` |
| "All-in-one `<category>`" / "one place for" | A feature count disguised as a difference | `<Named thing A> and <named thing B> in one <object>` with the names from the brief |
| "Work smarter, not harder" / "Do more with less" / "Take control of" | Could head any product since 1990 | `<Verb> <object> in <number from the brief>` |
| "Your `<category>`, elevated / supercharged / unleashed / on autopilot" | Adjective-verb doing the work | `<What changes> for <whom>` |
| "Build / create / design / ship anything" | "Anything" names nothing | `<Verb> <the specific thing the audience builds>` |
| "The future of `<category>`" / "next-generation" | A claim about time, not about the product | `<What it does that the current ones don't>` |
| "`<Brand>`: `<adjective>` `<category>`" ("Acme: Smarter Analytics") | Fails the test the moment the brand is removed | `<What> <for whom> <difference>` as a sentence |

## 2. Subheads and taglines
| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "Trusted by thousands / teams worldwide" | Unverifiable; see section 6 | `<Number> <named kind of customer>` only if the brief gives the number |
| "Seamlessly integrate with your workflow" | "Seamlessly", "integrate", "workflow": three category words | `Works with <named tool>, <named tool> and <named tool>` |
| "Powerful features. Simple interface." | Two adjectives, no object | `<The named feature> without <the named cost it avoids>` |
| "Designed for you" / "built with you in mind" | For whom is "you", so for nobody | `For <the named audience> who <the named situation>` |
| "Unlock your potential / the power of" | Metaphor instead of a claim | `<What the user can now do>` |
| "Fast. Simple. Secure." and any three-adjective triplet | Three slots filled with vague nouns or adjectives (placeholder tell 5) | Three parallel `<verb> <object>` phrases, or one sentence |

## 3. Buttons and links
| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "Get started" / "Start now" / "Begin" | No object: start what? | `Start <the named thing>` or `<Verb> <the first real step>` ("Create your first invoice") |
| "Learn more" / "Read more" / "Discover" / "Explore" | No object; also an accessibility gap when several share a page | `See <the named thing>` ("See the pricing table", "Read the refund policy") |
| "Submit" | Names the mechanism, not the result | `<The verb the user means> <object>` ("Send the application", "Save your address") |
| "Continue" / "Next" / "Proceed" | No object; acceptable only inside a numbered flow whose heading supplies it, and say so | `Go to <named next step>` ("Choose a delivery time") |
| "Click here" / "Tap here" / "Go" | Names the gesture | `<Verb> <object>` |
| "Sign up" (as a hero CTA) | Object is the account, not the benefit | `<Verb> <the first thing the account gives>` ("Start the 14-day trial" only if the brief says 14) |
| "Try it free" / "Try for free" | "It" names nothing | `Try <the named product or plan> free` with the terms from the brief |
| "Request a demo" / "Contact sales" | Fine as a secondary action; fails as the primary one because the object is a meeting, not the product | `See <the named thing> live` or keep, labelled secondary |
| "OK" / "Yes" / "Confirm" on a confirmation | Doesn't say what is confirmed (SKILL.md section 4) | Repeat the verb and object: "Delete 3 photos", "Cancel the order" |
| "Download" / "Export" / "Share" alone, outside a titled card | No object | `<Verb> <object>` ("Download the invoice PDF") |

## 4. Feature headings and blurbs
| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "Real-time collaboration" / "Powerful analytics" / "Smart automation" / "Advanced security" | Adjective plus category noun; every competitor's grid has the same four | `<What the user sees or does>` as a short verb phrase ("Two people edit one quote at once") |
| "Seamless integration" | See section 2 | `Connects to <named tool>` |
| "Lightning fast" / "Blazing fast" | Adjective; no number | `<Action> in <number from the brief>` or cut |
| "Enterprise-grade" / "military-grade" / "bank-level" | Borrowed authority with no fact | `<The named measure>` ("Encrypted at rest with AES-256") only if true |
| "Intuitive interface" / "User-friendly" / "Easy to use" | A claim the UI must prove, not state | Cut; show the step count instead if the brief has one |
| "Scalable" / "flexible" / "customisable" / "robust" | Abstract qualities with no object | `<What can be changed>` ("Rename any column") |
| "And much more" / "and more" | Names nothing; signals the list ran out of facts | Cut, or name the next real item |
| "`<Feature>` for everyone" | For whom is everyone | `<Feature> for <the named audience>` |

## 5. Badges and labels
| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "New" alone, for longer than a release cycle | Says nothing once it has been there a month | `New: <what>` with a removal date in the handoff |
| "Popular" / "Recommended" / "Best value" with no basis | Unverifiable; `ux-laws` law 1 allows a recommended default, but it needs a reason | `<Reason it is recommended>` ("Most cafes choose this") only with the fact |
| "Pro" / "Premium" / "Plus" as the only description | Tier names are not descriptions | Tier name **plus** `<what it adds>` |
| "AI-powered" / "Powered by AI" | Names a mechanism the user didn't ask about | `<What the user gets>` ("Drafts the reply for you") |
| "Beta" with no consequence | Doesn't say what might break | `Beta: <what may change or fail>` |

## 6. Trust and social-proof lines
| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "Trusted by 10,000+ companies" with no source | Unverifiable; a number is not a fact until the brief supplies it | `<Exact number> <named kind of customer>` with the source in the handoff, or cut |
| "Loved by users" / "Customers love us" | No one, no evidence | A quoted sentence from a named customer, with permission, or cut |
| "As seen in" plus unnamed logos | A logo row with no named outlet is a claim with no source | Named outlets with the article linked, or cut |
| "Award-winning" | Which award? | `<Award name>, <year>` or cut |
| "Rated 5 stars" | Where, by how many? | `<Rating> on <platform> from <number> reviews` or cut |
| "Join thousands of happy customers" | Three vague claims in one line | `<Number> <named customers> <did the named thing>` |

## 7. Adjectives that do the work
Any of these on a screen is a detector hit (placeholder tell 3), because each stands in for a fact the writer didn't have. Replace with the fact, or cut.

| Adjective | What it is hiding | Replacement pattern |
| :--- | :--- | :--- |
| powerful, robust, advanced | A capability with no name | `<The capability>` |
| seamless, smooth, frictionless, effortless | A step count or a time | `<Number> steps` / `in <time>` |
| simple, easy, intuitive, user-friendly | The same | The same |
| beautiful, stunning, elegant, sleek, modern, clean | The design itself, which the user can see | Cut |
| innovative, cutting-edge, next-generation, revolutionary | A difference with no name | `<The difference>` |
| fast, lightning-fast, blazing, instant | A measured time | `<Time from the brief>` |
| smart, intelligent | What is decided automatically | `<What it decides for you>` |
| secure, safe, reliable | A measure or a guarantee | `<The measure>` or cut |
| best, leading, world-class, premium | A ranking with no source | `<Ranking> by <source>` or cut |
| unique, perfect, ultimate, amazing, incredible | Nothing; pure filler | Cut |

## 8. State and error strings
The full patterns are in [state-microcopy.md](state-microcopy.md). The banned openers:

| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "Loading…" / "Please wait" / "Just a moment" | Doesn't say what is loading | `Loading <the named thing>` |
| "No data" / "Nothing here" / "No results" alone | No reason, no next step | `No <named thing> yet. <Verb> <object> to <result>.` |
| "Something went wrong" / "An error occurred" / "Oops!" / "Uh oh" | No what, no way out | `<What happened>. <The way out>.` |
| "Error 500" / "Error: undefined" / any code alone | A code is for the log, not the user | `<What happened in the user's terms>. <Way out>.` with the code in a details line if support needs it |
| "Invalid input" / "Invalid email" | Doesn't say what valid looks like | `<Field> needs <the valid shape>` ("Email needs an @ and a domain") |
| "Are you sure?" | Doesn't say sure of what | `<Verb> <object>? <Consequence>.` |
| "Success!" / "Done!" / "Great!" alone | Doesn't say what succeeded | `<What happened>. <What is next>.` |
| "Try again" / "Please try again later" alone | No when, no how | `<Way out>` ("Check the connection, then tap Retry", "Back in about 10 minutes") |
| "You entered an invalid…" / "You forgot to…" | Blames the user | `<Field> needs <shape>` with no subject |

## 9. Onboarding and welcome
| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "Welcome aboard!" / "You're all set!" | Says nothing about what to do | `<The first real action>` as a verb phrase |
| "Let's get you started" / "Let's set things up" | No object, and the "let's" voice belongs to very few brands | `Step 1 of <n>: <verb> <object>` |
| "Tell us about yourself" | Asks for everything, names nothing | `<The one thing the form needs and why>` |
| "You're almost there!" | No count, no step name | `Step <n> of <m>: <what is left>` |
| "Skip for now" alone | Doesn't say what is skipped or the consequence | `Skip <the named thing>` plus the consequence in helper text |

## 10. Pricing
| Phrase | Why it fails | Replacement pattern |
| :--- | :--- | :--- |
| "Simple, transparent pricing" | Two adjectives; the table proves or disproves it | `Plans for <audience>` or `<What the price buys> from <price>`; a plain "Pricing" is acceptable when the nav and `<title>` say the same |
| "Plans for every team / everyone" | For whom is everyone | `Plans for <audience A> and <audience B>` |
| "Contact us for pricing" on a self-serve page | Hides the price | The price, or `From <price> for <named thing>` if the brief allows |
| "Most popular" with no basis | See section 5 | The reason, or cut |
| "No credit card required" | Fine when true; a ban only when the flow then asks for one (label matches result) | Keep only if the signup flow is verified not to ask |
| "Cancel anytime" | Fine when true; ban when the terms say otherwise | Keep only with the terms checked |

## Checks
- [ ] Every string in scope was compared against sections 1 to 10, including badges, alt text and the `<title>`.
- [ ] Every adjective in section 7 is gone, or replaced by the fact it was hiding.
- [ ] Every banned phrase that stays has a one-line justification in the deliverable.
- [ ] No replacement slot was filled with an invented number, customer, award or guarantee; unfilled slots read `[needs a fact: what]`.
