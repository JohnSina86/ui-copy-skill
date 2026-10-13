# State microcopy

Patterns and examples for the five states every data-driven component carries: loading, empty, error, success and confirmation. Each state has required parts, and each string is **under 12 words**. The limit is editorial: it keeps a state to one message and leaves room for translation growth. Whether a string fits one line depends on the font and the width, so a line-fit claim needs a render, never the word count. The parts come from the data and the brief, never from a guess: a count is read from the response, a time from a measured or stated figure.

`ux-laws` grades the result (law 6 for feedback, law 10 for end and error states, law 18 for time expectations). This file only says what the words must contain.

## Contents
- [Shared rules](#shared-rules)
- [1. Loading](#1-loading)
- [2. Empty](#2-empty)
- [3. Error](#3-error)
- [4. Success](#4-success)
- [5. Confirmation](#5-confirmation)
- [Worked set: a cafe order flow](#worked-set-a-cafe-order-flow)
- [Checks](#checks)

## Shared rules
- **Name the thing.** "Your October invoices", not "data", "items", "content" or "results".
- **No exclamation marks, no apologies, no blame.** "Sorry!" and "You entered an invalid…" both go. State what happened.
- **The action is a verb plus object**, and the button under the state repeats it. A state with a next step and no control for it is a layout defect to flag, not a copy fix.
- **Counts and times are read, not written.** `{count}` and `{minutes}` are filled by the component. The string must also work for 1 and for 0, so write the plural rule next to it in the handoff.
- **Under 12 words**, counted with the slots filled with a typical value. Count every space-separated token: a digit is a word, a contraction is one word, punctuation is nothing. Write the count down; don't estimate it.
- **One state, one message.** A loading state doesn't also explain the feature; an error doesn't also upsell.
- **Promise only what the product does.** "Your basket is saved", "Retry when online" and "nothing was charged" are claims about the product, not about the words. Write them only when the brief or the code shows the basket persists, the retry can't duplicate the order (a server-side idempotency key or an order status the user can check), or the charge is reversed. Without that evidence, write `[needs a fact: what]` and keep the string to what is known.

## 1. Loading
**Must say:** what is loading. **Must not:** "Loading…" alone, "Please wait", "Just a moment", a spinner with no words.

| Pattern | Example | Words |
| :--- | :--- | :---: |
| `Loading <named thing>` | "Loading your October invoices" | 4 |
| `Loading <named thing> for <scope>` | "Loading orders for table 4" | 5 |
| `<Verb>ing <named thing>` for an action, not a fetch | "Sending the order to the counter" | 6 |
| `Still loading <thing>. <Reason or time>.` after the Doherty threshold | "Still loading the report. Large exports take about a minute." | 10 |

A skeleton that shows the shape of the content can replace the string on a list, but the accessible name of the region still says what is loading. A loading state that can fail needs its error string written at the same time.

## 2. Empty
**Must say:** why it is empty and what to do next. **Must not:** "No data", "Nothing here", "No results", an illustration with no action.

Three kinds of empty, each with its own pattern:

| Kind | Pattern | Example | Words |
| :--- | :--- | :--- | :---: |
| **First use**: nothing created yet | `No <things> yet. <Verb> <object> to <result>.` | "No orders yet. Add a drink to start one." | 9 |
| **Filtered**: things exist, the filter hides them | `No <things> match <the filter>. <Verb> <object>.` | "No orders match 'oat'. Clear the search or try 'oat milk'." | 11 |
| **Cleared**: the user emptied it | `<Things> cleared. <What happens next or where they went>.` | "Basket emptied. Your usual is one tap away." | 8 |

The next step is a real control that the user can reach from the empty state. If the brief says the thing can't be created here (an inbox, a report fed by another system), say where it comes from: "Reviews appear here after a customer leaves one."

## 3. Error
**Must say:** what happened and the way out. **Must not:** "Something went wrong", "Oops", "An error occurred", a bare code, blame, "Try again" with no when or how.

| Kind | Pattern | Example | Words |
| :--- | :--- | :--- | :---: |
| **Validation** (the field) | `<Field> needs <the valid shape>` | "Phone needs 10 digits, no spaces" | 6 |
| **Validation** (the form) | `<Count> field(s) need a change. <First one>.` | "2 fields need a change. Start with Email." | 8 |
| **Rejected** by a rule or a third party | `<What was rejected>. <Way out A> or <way out B>.` | "Card declined. Try another card or pay at the counter." | 10 |
| **Not sent** (the request never left, or the server refused it before accepting) | `<What didn't happen>. <What is kept, if the product keeps it>. <Way out>.` | "Order not sent. Your basket is saved. Retry when online." | 10 |
| **Outcome unknown** (the connection dropped after sending, a timeout, no response) | `Couldn't confirm <what>. <Where to check before acting again>.` | "Couldn't confirm your order. Check Orders before ordering again." | 9 |
| **Server or unknown** | `<What didn't happen>. <Way out with a time or a person>.` | "Couldn't load the menu. Ask at the counter." | 8 |
| **Permission** | `<What needs permission> to <why>. <Where to allow it>.` | "Camera needed to scan the code. Allow it in Settings." | 10 |
| **Not found** | `<Thing> isn't here. <Where it might be>.` | "That order isn't here. It may have been collected." | 9 |

**A dropped connection is not proof of failure.** The server may have accepted the order before the reply was lost. Write "not sent" only when the client knows the request never left or was refused; otherwise the outcome is unknown, and the string says so and points at the place where the user can see the real state (an orders list, a confirmation email, the counter). A Retry button on an unknown outcome needs product evidence that retrying can't create a duplicate; without it, the way out is the status page, not Retry.

The way out is a control: a Retry button, a link to the field, a phone number, a different payment method. The error names it; the layout provides it. An error that can't be fixed by the user says who will fix it and when, and gives the reference code **in a second line** for support, never as the message.

## 4. Success
**Must say:** what happened and what is next. **Must not:** "Success!", "Done!", "Great!", confetti with no information.

| Pattern | Example | Words |
| :--- | :--- | :---: |
| `<What happened>. <What is next>.` | "Order sent to the counter. Ready in about 6 minutes." | 10 |
| `<What happened>. <Where to find it>.` | "Invoice saved. It's in Drafts until you send it." | 9 |
| `<What happened to what>.` when nothing is next | "Address updated." | 2 |
| `<Count> <things> <verb>ed. <Undo or next>.` | "3 photos deleted. Undo" | 4 |

A success that the user must act on (confirm an email, download a file) names the action as its button. A success that replaces a form keeps the form's heading context so the user knows which thing succeeded.

## 5. Confirmation
**Must say:** what will happen, to what, and the consequence. The confirming button **repeats the verb and object**; the other button is "Keep <object>" or "Cancel". **Must not:** "Are you sure?", "OK", "Yes", "Confirm", a destructive action on the primary-coloured button without its object.

| Pattern | Example | Buttons | Words |
| :--- | :--- | :--- | :---: |
| `<Verb> <count> <things>? <Consequence>.` | "Delete 3 photos? This can't be undone." | "Delete 3 photos" / "Keep photos" | 7 |
| `<Verb> <named thing>? <What is lost>.` | "Cancel the order? The counter has already started it." | "Cancel the order" / "Keep the order" | 9 |
| `<Verb> <thing>? <What happens to dependants>.` | "Remove oat milk? 2 drinks on the menu use it." | "Remove oat milk" / "Keep it" | 10 |
| `Leave without saving? <What is lost>.` | "Leave without saving? Your 4 edits will be lost." | "Leave" / "Keep editing" | 9 |

Reversible actions don't need a confirmation; they need an undo in the success state (section 4). Ask for confirmation only when the consequence line has content.

## Worked set: a cafe order flow
One component, the order basket, with all five states written against the voice brief in [voice-brief.md](voice-brief.md):

| State | String | Button | Words |
| :--- | :--- | :--- | :---: |
| Loading | "Loading your basket" | | 3 |
| Empty (first use) | "Nothing in your basket yet. Add a drink to start one." | "See the menu" | 11 |
| Error (rejected) | "Card declined. Try another card or pay at the counter." | "Try another card" | 10 |
| Error (not sent: the app knows the request never left) | "Order not sent. Retry when you're back online." | "Retry" | 8 |
| Error (outcome unknown: sent, no reply) | "Couldn't confirm your order. Check Orders before ordering again." | "See Orders" | 9 |
| Success | "Order sent to the counter. Ready in about {minutes} minutes." | "See the order" | 10 |
| Confirmation | "Cancel the order? The counter has already started it." | "Cancel the order" / "Keep the order" | 9 |

The minutes come from the cafe's stated preparation time in the brief. If the brief has none, the success string is "Order sent to the counter." and `[needs a fact: preparation time]` goes in the handoff. The not-sent string says nothing about a saved basket, because the brief gives no evidence the basket persists; `[needs a fact: does the basket survive going offline]` goes in the handoff, and "Your basket is saved" is added only once it does. The unknown-outcome string points at Orders rather than offering Retry, because the brief gives no evidence a retry can't duplicate the order.

## Checks
- [ ] Every data-driven component has all five strings, or a line saying which states it can't reach and why.
- [ ] Every string has its required parts from the table for its state.
- [ ] Every string is under 12 words with typical values in the slots, and the plural rule is noted for every count.
- [ ] Every next step and way out is a control the layout provides; missing controls are flagged.
- [ ] No exclamation marks, apologies, blame, bare codes or banned openers ([ban-list.md](ban-list.md) section 8).
- [ ] Counts and times come from the data or the brief; none is invented.
- [ ] Every "not sent", "saved", "retry" or "not charged" claim has product evidence behind it, and an unknown outcome is written as unknown with a place to check.
- [ ] Word counts were counted, not estimated, and no line-fit claim was made without a render.
