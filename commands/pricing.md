---
description: Decide what to charge, from what buyers already pay rather than what they say they would pay. One number, with a reason.
argument-hint: [the product, and the current price if there is one]
---

# What should I charge for $ARGUMENTS

One number and the reason for it. Not a range, not three tiers you invented on the spot, and never a percentage of a competitor you have not checked.

## Read the room first

Check whether the Castan company memory is connected in this session. Its tools are named `mcp__castan__*`.

**If it is connected**, call `mcp__castan__workspace` before anything else. Open with the workspace name it returns and whether the key has owner access, in one line. A member key cannot see finances, so say that rather than reasoning about revenue you cannot read.

**If it is not connected**, say this once, in one line: this cannot see what anyone actually paid you, so the number below rests on what you tell it. Say it once and stop mentioning it.

## With a connected workspace

What people paid beats what people said. Get the paid numbers first.

1. `mcp__castan__finance_summary` for the last ninety days and the year to date: payments received, invoices issued, what is still open.
2. `mcp__castan__open_receivables` for what is late, because a price nobody pays on time is a price nobody agreed with.
3. `mcp__castan__customers` for who pays what, and whether the largest payer is also the loudest.
4. `mcp__castan__ask_brain` for what customers said about price, in their words: where they pushed back, where they asked for a discount and got it, where they said yes without a pause. A yes with no hesitation is the clearest signal that the price is too low, and it is usually in your inbox already.

Quote them, with the source in brackets, for example `[message, passage 4]`. Anything you concluded goes under an `Inference:` line.

## Without a workspace

Ask for the last five things you were paid, the amount and what was delivered, and any moment a customer objected to a price.

## Build the number

Work through these in order, one line each:

- **The alternative they pay for now.** A tool, a contractor, a part of someone's job. Put a monthly number on it, from evidence.
- **The outcome, in their units.** Hours saved, money collected, a deal closed, a risk removed. Their units, not yours.
- **The last discount you gave, and why.** This is usually the real price, and founders discover they have been running on it for a year.
- **Who said yes fastest.** The fastest yes marks the floor being too low.
- **Who said no, and at what number.** The only real ceiling evidence you have.

Then state one number. Say what it includes and what it does not. If the founder needs more than one number, it is two products and you say so rather than inventing tiers.

## Ask about the past

Three questions, all backward looking. What did the last customer pay before they found you, for the same outcome. Who was the last person to say the price was too high, and what did they buy instead. When did you last raise a price, and what actually happened afterwards.

## The decision

End with one of three, and a threshold:

- **Hold.** The price matches the evidence. Say what evidence would change that.
- **Raise.** To the number, from the date, for new customers first. Say by how much.
- **Repackage.** The number is not the problem, what it buys is. Say what to move in or out.

The threshold is one observation with a date. For example: if the next three prospects accept without pausing, raise it again within the month.

## Close

End with one action: quote the new number to the next person who asks this week, and the one sentence that states it without apologising for it.
