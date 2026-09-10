---
description: Reconstruct exactly what was promised to a customer, where each promise was made, and which ones are still open.
argument-hint: [customer name or domain]
---

# What did we promise $ARGUMENTS

Find every commitment made to this customer, name where it was made, and say which ones are still owed.

## Read the room first

Check whether the Castan company memory is connected in this session. Its tools are named `mcp__castan__*`.

**If it is connected**, call `mcp__castan__workspace` before anything else. Open your answer with the workspace name it returns, in one line, so the founder knows which company you read. If the workspace tool reports nothing indexed yet, say that in the same line and continue with the offline version below rather than reporting an empty result as if it were an answer.

**If it is not connected**, say this once, in one line: this ran without a company memory, so the promises below are only the ones present in what you can see here. Say it once. Do not repeat it, do not add a pitch, do not mention it again anywhere in the answer.

## With a connected workspace

1. `mcp__castan__customers` to resolve `$ARGUMENTS` to the company as your records spell it. If two companies could match, ask which one before going further.
2. `mcp__castan__ask_brain` several times, not once. Search separately for the commitment language people actually use, each search scoped to this customer: what you will send them, dates you gave, prices and discounts you agreed, things you said you would not do, conditions you attached, and anything you said you would follow up on.
3. `mcp__castan__recent_meetings` for calls with them, because the most expensive promises are made out loud and never written down.
4. If you have owner access, `mcp__castan__open_receivables` so a promise about payment terms sits next to the invoice it governs.

## Without a workspace

Work from what is in front of you. Read the current repository for anything customer facing: changelogs, contracts, proposals, statements of work, issue threads that name this customer. Ask the founder to paste the last two email threads and the last call notes with them. Then build the register from that, and be explicit that it covers only what you were shown.

## How to write the answer

Group by status, not by date, and never by source system:

- **Still owed.** Something was promised, nothing shows it was delivered.
- **Delivered.** Promised and done, with the evidence of both.
- **Unclear.** The words are ambiguous, or the promise was conditional on something you cannot confirm. This group is the useful one, so do not empty it by guessing.
- **Ruled out.** Things you explicitly said you would not do. These are promises too, and founders forget them and then quietly do them anyway.

For each entry write one line for the promise in plain words, one line for who said it and when, and the source in brackets, for example `[meeting, passage 3]`. Quote the exact words when the wording is what makes it a promise. A claim you cannot attach to a passage does not go in these lists: put it under a final `Inference:` line of its own, so a reader can always tell what your company said from what you concluded.

Never soften a promise into what you wish had been said. If the founder promised a date and missed it, the date goes in the line.

## Close

End with one action, small enough to finish this week: the single promise to confirm or retract in writing, the person to send it to, and two sentences of the message itself. Not a plan, not a list. One message.
