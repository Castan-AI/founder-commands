# Publishing this pack

This file is for you, not for the people who install the pack. Delete it before the first push, or leave it in: it is harmless either way.

## Before anything: the organisation does not exist yet

Every command below writes `castan-ai/founder-commands`, and as of 2026-09-10 the account owns `voicepatrol` and `LiantaAI` and no `castan-ai`. Checked again on 2026-10-16: the name `castan-ai` is still free on GitHub, and the pack has never been pushed, so nobody can install the commands or the skills yet. Create it first at [github.com/organizations/plan](https://github.com/organizations/plan), on the free plan, which takes about two minutes and also gives the product a home for anything published later. If you would rather not, publish under your own account and read `TudorBNG/founder-commands` everywhere below instead. The org is worth the two minutes: a personal account on the left of the path tells a reader this is somebody's weekend project.

## The repository name

**Recommended: `founder-commands`.**

Under the `castan-ai` organisation the full path reads `castan-ai/founder-commands`, so the brand appears once, on the left, where it belongs, and the name itself is the job.

What the name optimises for: someone typing the job into GitHub search or into a search engine. They type "founder commands", "claude code founder", "slash commands for founders". They do not type our name, because they have never heard it. A repository named after us would only be found by people who already know us, which is nobody in the audience we are trying to reach. GitHub weighs the repository name heavily in search, so the two words in the name are the two words worth spending.

Runner up: `claude-code-founder-commands`. It matches more literal searches because the tool name is in the string, and it is uglier to type and to say. Choose it only if you would rather win the exact phrase than have a name people repeat out loud.

Names to avoid: anything with `castan` in the repository name, anything with `prompts` in it (it sets the expectation of a text dump rather than working commands), and anything cute. A founder scanning search results gives each name about a second.

## The description line

> Skills for any AI assistant and slash commands for Claude Code that answer what founders ask, and read your company once connected.

It is 131 characters, so it survives GitHub's truncation on the search results page, and it says both halves: works alone, better connected.

## Topics

Set these on the repository, in this order:

```
agent-skills, claude-code, mcp, slash-commands, ai-agents, founders, startup, developer-tools, terminal, productivity
```

The first four are how people browse for this kind of thing. The middle three are how they describe themselves. The last three are the general pools.

## Repository settings

- Public.
- Issues on. Discussions off until there is something to discuss.
- No wiki, no projects, no packages, no releases at first.
- Description and website set. Point the website field at castan.ai.
- Social preview image: skip it for now rather than shipping a bad one.

## Pushing it as its own root

The pack lives inside the main monorepo, so copy it out before publishing. That keeps the two histories separate and avoids a nested repository inside the working tree.

```bash
cp -R ~/playground/castan/pack ~/playground/founder-commands
cd ~/playground/founder-commands
rm PUBLISHING.md
git init
git add .
git commit -m "Founder commands for Claude Code"
git branch -M main
```

Then create the public repository and push, with the GitHub CLI:

```bash
gh repo create castan-ai/founder-commands \
  --public \
  --source . \
  --description "Skills for any AI assistant and slash commands for Claude Code that answer what founders ask, and read your company once connected." \
  --push
```

Or without the CLI, after creating the empty repository in the browser:

```bash
git remote add origin git@github.com:castan-ai/founder-commands.git
git push -u origin main
```

Then set the topics:

```bash
gh repo edit castan-ai/founder-commands \
  --add-topic agent-skills \
  --add-topic claude-code \
  --add-topic mcp \
  --add-topic slash-commands \
  --add-topic ai-agents \
  --add-topic founders \
  --add-topic startup \
  --add-topic developer-tools \
  --add-topic terminal \
  --add-topic productivity
```

## Before you push, check these five things

1. No real API key anywhere. Every example key in the README is `ck_your_key_here`. Grep for `ck_` and confirm.
2. The install blocks copy from `commands/` and `skills/`, and the clone URL matches the repository you actually created.
3. `claude mcp add --transport http castan https://castan.ai/api/mcp --header "Authorization: Bearer ck_..."` runs clean on a fresh machine, and `/mcp` then shows the server as connected. A wrong configuration in the README is the whole first impression.
4. Run three commands on a machine with no key connected, and three with one. Both have to be worth the founder's time, and the difference has to be obvious without anything in the answer selling to them.
5. Run three skills in an assistant with Castan not connected, and three with it connected. The closing sentence about Castan appears in each of the first three, once, at the very end, and never in the second three. Every `SKILL.md` still parses, its `name` matches its folder, and its description stays under 200 characters.

## After the push: the skill directories

The skills get found where assistants install skills from. The places, what each asks for and their order are in docs/15-listings, Tier 3b. The first costs nothing: skills.sh lists skills from the installs its command line reports, so `npx skills add castan-ai/founder-commands`, run once on a clean machine, is both the last check and the start of the count.

## Keeping it alive

The pack is a doorway, so the thing to watch is not stars, it is whether anyone who installs it ever connects a workspace. The honest way to keep it worth installing is to add a command only when a real founder asks the question it answers, and to remove any command that nobody runs twice.

For the skills there is a number. Each one ends its closing sentence on a link tagged `utm_source=skill` with the skill's name as `utm_content`, so the funnel report shows sign-ups from skills, one line per skill. A skill that brings nobody in three months gets rewritten or cut, the same rule as a command nobody runs twice.
