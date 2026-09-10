---
description: Brief yourself before a call: who is in the room, what happened last time, what is open, and the one thing to close.
argument-hint: [person, company, or leave empty for the next call]
---

# Prepare me for $ARGUMENTS

A brief you can read in the two minutes before the call starts. Short, specific, and honest about what you do not know.

## Read the room first

Check whether the Castan company memory is connected in this session. Its tools are named `mcp__castan__*`.

**If it is connected**, call `mcp__castan__workspace` before anything else. Open the brief with the workspace name it returns, in one line.

**If it is not connected**, say this once, in one line: this brief was built without a company memory, so it holds what you told it and nothing about the last time you spoke to these people. Say it once and move on.

## With a connected workspace

1. `mcp__castan__upcoming_meetings` to find the call. With no argument, take the next one. With an argument, find the one that matches and say which you picked, with its time.
2. `mcp__castan__ask_brain` for the people and the company on that call: who they are, what they do, what they last asked for, what they last complained about.
3. `mcp__castan__recent_meetings` for the last call with them, and read the recap rather than summarising the title.
4. `mcp__castan__work_in_progress` for anything you are building that this call touches.
5. With owner access, `mcp__castan__open_receivables` if they are a customer, because walking into a call not knowing they are sixty days late is the avoidable kind of mistake.

## Without a workspace

Ask for the invitation and the attendee list as a paste, plus the last thread with them if they have it. Build the brief from that, and say which parts of the brief are missing because you could not read the history.

## The brief

Keep it to one screen, in this order:

1. **The call.** Time, who is on it, and what they think it is about.
2. **Last time.** What actually happened at the previous contact, in two lines, with the source in brackets, for example `[meeting, passage 1]`.
3. **Open with them.** Promises not kept, questions not answered, money not paid. Each with its source.
4. **Three questions to ask.** All three about what already happened, never about intent. Ask what they tried last month, what they are using today and what it costs them, what they stopped doing. Do not ask whether they would like something, whether they see value, or whether they would buy it.
5. **The one thing to close.** A single sentence naming what you want to leave the call with: a date, a decision, an introduction, a signature.
6. **Landmines.** Anything they are unhappy about that you should not be surprised by.

Anything you inferred rather than read goes under an `Inference:` line at the end. Never present a guess about a person as a fact about them.

## Close

End with one action for after the call: the follow up you will send within the hour, and the one line it opens with.
