# Founder commands

Twelve slash commands for Claude Code that answer the questions a solo founder actually asks, and that read your own company when you connect one.

They are plain markdown files. There is nothing to build, no dependency to install, and no runtime. Each command works on its own with whatever you can give it in the terminal. Each one gets sharply better when a Castan workspace is connected, because it can then read your real email, calls, documents, customers and invoices, and cite the source of every claim it makes.

## Install

### 1. Copy the commands

```bash
git clone https://github.com/castan-ai/founder-commands.git
mkdir -p ~/.claude/commands
cp founder-commands/commands/*.md ~/.claude/commands/
```

`~/.claude/commands` makes them available in every project. Use `.claude/commands` inside a repository if you want them only there. The file name is the command name, so `promised.md` becomes `/promised`. If one of these names is already taken on your machine, rename the file and the new name is the command.

Restart Claude Code, type `/`, and the commands are in the list.

### 2. Add the company memory

This half is optional. Skip it and every command still runs. Add it and the same commands stop guessing about your company and start reading it.

Castan is a company memory. It joins your calls, holds what happened across email, Slack, calendar, GitHub, Stripe and the books, and answers questions with the source attached. It speaks MCP, so Claude Code can read it directly.

Get a key at [castan.ai](https://castan.ai), under Settings, in the API and MCP tab. Keys start with `ck_`. One key opens one workspace with one role: an owner key includes the money tools, a member key never sees finances. The free tier is enough to try this, and every tool the pack uses is read only, so nothing here can change your company data.

**Claude Code, one command:**

```bash
claude mcp add --transport http castan https://castan.ai/api/mcp \
  --header "Authorization: Bearer ck_your_key_here"
```

**Claude Code, checked into a project instead.** Put this in `.mcp.json` at the repository root:

```json
{
  "mcpServers": {
    "castan": {
      "type": "http",
      "url": "https://castan.ai/api/mcp",
      "headers": {
        "Authorization": "Bearer ${CASTAN_API_KEY}"
      }
    }
  }
}
```

Claude Code expands `${CASTAN_API_KEY}` from your environment, so the file stays safe to commit and the key stays in your shell profile. Write the key inline instead if you keep the file out of version control.

**Cursor.** Put this in `~/.cursor/mcp.json` for every project, or `.cursor/mcp.json` for one:

```json
{
  "mcpServers": {
    "castan": {
      "url": "https://castan.ai/api/mcp",
      "headers": {
        "Authorization": "Bearer ${env:CASTAN_API_KEY}"
      }
    }
  }
}
```

Cursor uses `${env:NAME}` for environment variables, and remote servers there take no `type` field.

### 3. Check it

In Claude Code, run `/mcp`. The `castan` server should be listed as connected. Then run `/week`. If the workspace is connected, the answer opens with the name of the workspace it read.

## The commands

Six of these ask your company what happened. Six help you decide what to build and what to charge. All twelve run without an account.

| Command | What it answers |
| --- | --- |
| `/promised` | What did we actually promise this customer, and which promises are still open. |
| `/owed` | Who owes us money, why each one has not paid, and the message to send today. |
| `/call-prep` | Who is on the next call, what happened last time, and the one thing to close. |
| `/week` | What changed in the company this week, separated from what was merely discussed. |
| `/blocked` | What is genuinely stuck, who it is stuck on, and the message that unblocks it. |
| `/at-risk` | Which customers have gone quiet against their own past rhythm, and who to let go. |
| `/idea-check` | Is this worth building. Ends in build, pivot or kill, with the evidence that would flip it. |
| `/customer` | Who exactly the customer is, narrowed until you can name three reachable people. |
| `/first-version` | What the first version is, and what is deliberately not in it. |
| `/pricing` | What to charge. One number with a reason, not a range. |
| `/interview` | Eight interview questions about what people already did, and how to grade the answers. |
| `/positioning` | One sentence about what you do that a customer would repeat, built from their words. |

## What connecting a workspace changes

Every command in this pack states, at the top of its answer, what it was able to read. That is the whole difference and it is visible at the moment of use.

Without a workspace, `/owed` writes you three good collection messages from the reasons people usually do not pay. With a workspace, it lists your unpaid invoices oldest first, reads the last real exchange with each of those customers, and writes the message in the terms of that exchange, with the passage it came from attached to each claim.

Without a workspace, `/idea-check` interrogates your idea properly and forces a decision. With a workspace, it first searches whether anyone has already asked you for this thing, in email, on calls, in documents, and quotes them.

Three rules hold across the pack, connected or not:

1. **Every fact carries its source.** When a claim comes from your company, the command names the passage and the kind of source it came from. When it does not, the command labels it as inference. The two never merge into one confident paragraph.
2. **Judgements end in a decision and a threshold.** Not a score out of ten. Build, pivot or kill, and the single observation that would change the answer.
3. **Questions are about the past.** No command asks whether someone would buy. They ask what that person already did, already paid for, and already abandoned. Every command ends with one action small enough to finish this week.

## License

MIT. See [LICENSE](LICENSE).
