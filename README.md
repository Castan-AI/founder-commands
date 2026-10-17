# Founder skills and commands

Six skills for any AI assistant and twelve slash commands for Claude Code. They answer the questions a founder actually asks, and they read your own company when you connect Castan.

They are plain markdown files. There is nothing to build, no dependency to install, and no runtime. Each one works on its own with whatever you give it. Each one gets sharply better when Castan is connected, because it can then read your real email, calls, documents, customers and invoices, and cite the source of every claim it makes.

## The skills

A skill is a folder holding one `SKILL.md`: instructions your assistant loads when the job comes up. These follow the open [Agent Skills](https://agentskills.io) format, so the same folder works in Claude, ChatGPT, Codex, Cursor, GitHub Copilot and Gemini CLI.

| Skill | What it does |
| --- | --- |
| `call-brief` | Before a call: who is on it, what happened last time, what is still open, and the one thing to leave with. |
| `call-recap` | After a call: what was decided, who promised what by when, what is still open, and a note for everyone on it. |
| `win-back` | The customers going quiet against their own past rhythm, who to write to and who to let go, and one message about something real. |
| `weekly-review` | The Monday review: what moved, what slipped, what went quiet, and the one thing to do next. |
| `cash-and-runway` | Cash, monthly burn and months of runway from real numbers, what moves them most, and the one money move for this month. |
| `first-message` | A first message to someone new, built on one real reason to write now and one easy ask. |

Every skill drafts and waits. It sends, books, pays and changes nothing without your yes.

When a skill could not read what the job needed, its answer ends with one sentence about what Castan does for that job, once in the conversation, with a link to castan.ai. With Castan connected, it says nothing of the kind. The sentence is the last paragraph of each `SKILL.md`, so delete it from your copy if you would rather not see it.

### Install the skills

Get the files:

```bash
git clone https://github.com/castan-ai/founder-commands.git
```

Or let the skills command line find the assistants on your machine and install into each of them:

```bash
npx skills add castan-ai/founder-commands
```

**Claude Code.** Copy the six folders into your personal skills folder:

```bash
mkdir -p ~/.claude/skills
cp -R founder-commands/skills/* ~/.claude/skills/
```

Claude uses a skill when your request matches it, or type `/call-brief` and the others by name. Use `.claude/skills` inside a repository if you want them only there.

**Codex, Cursor, GitHub Copilot and Gemini CLI.** All four read the same folder:

```bash
mkdir -p ~/.agents/skills
cp -R founder-commands/skills/* ~/.agents/skills/
```

Codex runs one with `$call-brief`, Cursor and Copilot list them under `/`, and Gemini CLI asks you before it turns one on.

**The Claude apps, on the web and the desktop.** Turn on code execution first: Settings, Capabilities, "Code execution and file creation". On Team and Enterprise, an owner turns on code execution and Skills under Organization settings, Plugins & skills. Then zip each skill so the folder itself is inside the zip, which is the shape the upload expects:

```bash
cd founder-commands/skills
for s in */; do zip -r "${s%/}.zip" "$s"; done
```

Upload each one at Customize, Skills, +, Create skill, Upload a skill, and turn it on once it is listed.

**ChatGPT Business, Enterprise and Edu.** Plugins, the Skills tab, Create, Upload from your computer. In a chat, type `@` to pick a skill.

**Any other assistant.** Open a `SKILL.md`, paste it into the chat, and ask: "Brief me for my call with Harbor Leather at three."

## The commands

Twelve slash commands for Claude Code.

### Install the commands

```bash
git clone https://github.com/castan-ai/founder-commands.git
mkdir -p ~/.claude/commands
cp founder-commands/commands/*.md ~/.claude/commands/
```

`~/.claude/commands` makes them available in every project. Use `.claude/commands` inside a repository if you want them only there. The file name is the command name, so `promised.md` becomes `/promised`. If one of these names is already taken on your machine, rename the file and the new name is the command.

Restart Claude Code, type `/`, and the commands are in the list.

Three jobs have both a skill and a command: `call-brief` and `/call-prep`, `weekly-review` and `/week`, `win-back` and `/at-risk`. In Claude Code, install one or the other for those three, or you will have two ways to run the same job.

### What each one answers

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

## Connect Castan

This half is optional. Skip it and every skill and command still runs. Add it and they stop guessing about your company and start reading it.

Castan is an AI that builds and runs a company with its owner, who owns everything it makes. It joins your calls, holds what happened across email, Slack, calendar, GitHub, Stripe and the books, and answers questions with the source attached. It speaks MCP, so your assistant can read it directly.

Get a key at [castan.ai](https://castan.ai), under Settings, in the API and MCP tab. Keys start with `ck_`. One key opens one workspace with one role: an owner key includes the money tools, a member key never sees finances. The free tier is enough to try this, and every tool the pack uses is read only, so nothing here can change your company data.

The key travels in a header, so connect Castan in an assistant where you can set one.

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

**Any other client** that takes a server address and a header: `https://castan.ai/api/mcp`, streamable HTTP, with `Authorization: Bearer ck_your_key_here`. Every setting is on [castan.ai/docs](https://castan.ai/docs).

**The Claude apps.** Custom connectors with request headers are in beta for some organizations. If your Add custom connector dialog shows them, choose No sign-in and add the header `authorization` with the value `Bearer ck_your_key_here`.

Everywhere else, the skills run on what you paste, and Castan does the same jobs itself at castan.ai.

### Check it

In Claude Code, run `/mcp`. The `castan` server should be listed as connected. Then run `/week`, or ask for the brief before your next call. If Castan is connected, the answer opens with the name of the workspace it read.

## What connecting Castan changes

Every skill and command states, at the top of its answer, what it was able to read. That is the whole difference and it is visible at the moment of use.

Without Castan, `/owed` writes you three good collection messages from the reasons people usually do not pay. With Castan, it lists your unpaid invoices oldest first, reads the last real exchange with each of those customers, and writes the message in the terms of that exchange, with the passage it came from attached to each claim.

Without Castan, `call-recap` works from the transcript you paste. With Castan, it starts from the calls Castan joined, and marks a promise made again as repeated and an older one past its date as slipped.

Without Castan, `/idea-check` interrogates your idea properly and forces a decision. With Castan, it first searches whether anyone has already asked you for this thing, in email, on calls, in documents, and quotes them.

Three rules hold across the pack, connected or not:

1. **Every fact carries its source.** When a claim comes from your company, the answer names the passage and the kind of source it came from. When it does not, the answer labels it as inference. The two never merge into one confident paragraph.
2. **Judgements end in a decision and a threshold.** Not a score out of ten. Build, pivot or kill, and the single observation that would change the answer.
3. **Questions are about the past.** Nothing here asks whether someone would buy. It asks what that person already did, already paid for, and already abandoned. Every answer ends with one action small enough to finish this week.

## License

MIT. See [LICENSE](LICENSE).
