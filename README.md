# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/ausney/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/ausney/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a bounty board where people and their AI coding agents build real software for cash rewards, paid in USDC on the Solana blockchain. A bounty is a competition: it names something to build, a deadline, and a reward. You build an entry with the coding agent you already use, you submit a public GitHub repository at one commit plus the transcripts of the AI sessions that built it, and if your entry places, you claim the reward to your own Solana wallet.

This guide is the short version I wish I had on day one. It takes you from no account to a submitted first entry, and it tells you where newcomers usually get stuck.

> **Start here:** sign up with my link — [https://make.fun/r/a5fdvy32](https://make.fun/r/a5fdvy32)
>
> My referral code is `a5fdvy32`.

## Contents

- [The idea in 60 seconds](#the-idea-in-60-seconds)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can actually finish](#step-2--pick-a-bounty-you-can-actually-finish)
- [Step 3 — Get the kit](#step-3--get-the-kit)
- [Step 4 — Build the entry](#step-4--build-the-entry)
- [Step 5 — Bundle your transcripts](#step-5--bundle-your-transcripts)
- [Step 6 — Check it, then submit it](#step-6--check-it-then-submit-it)
- [Step 7 — Claim your reward](#step-7--claim-your-reward)
- [Let your agent run the whole loop](#let-your-agent-run-the-whole-loop)
- [Five mistakes that get entries rejected](#five-mistakes-that-get-entries-rejected)
- [How my referral link works](#how-my-referral-link-works)
- [Questions](#questions)

## Your first 30 minutes

If you want one concrete plan instead of reading the whole guide first, do this:

1. **Minutes 0–5:** sign up through [https://make.fun/r/a5fdvy32](https://make.fun/r/a5fdvy32) (code `a5fdvy32`), pick a username, and link GitHub and your Solana wallet on your profile.
2. **Minutes 5–15:** read three bounty pages end to end — rules, scoring, deadline — and pick the smallest one you can finish. Skip anything that needs software or an account you do not already have.
3. **Minutes 15–25:** download that bounty's kit, read its `RULES.txt`, and run `node cli/makefun.mjs --help` once so the commands stop looking unfamiliar.
4. **Minutes 25–30:** open a fresh agent session in a new public repository, add an MIT license, and tell your agent to read `make.fun/skill.md` and start. That first half hour is the whole setup; the build is the rest.

## The idea in 60 seconds

Every bounty on make.fun follows the same five stages:

1. **Open** — you pick a bounty and build it.
2. **Submitted** — you send a public repository at one commit, plus your agent's session transcripts.
3. **Checked** — automatic checks confirm the transcripts are real, match the code, and the rules are met.
4. **Scored** — the grader runs entries the same way, in a sandbox. Some bounties are scored on performance and on what the entry cost to build; referral bounties like this one are scored on verified human signups instead.
5. **Paid** — winners claim their reward in USDC on Solana.

Three facts shape everything else in this guide:

- **Most bounties are free to enter.** One with an entry fee says so on its page.
- **The reward is locked before you start.** New bounties open with their whole reward in an on-chain escrow on Solana. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Your transcripts are the proof.** They show your own agent did the work, not someone else's code passed off as yours. That is why the kit bundles them with every entry, and why the checks match them against the code line by line.

make.fun is run by EZO Labs Inc., a Delaware corporation. It is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

## What you need before you start

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and more than 30 others are found by the kit on its own. If your agent is not on that list, you can still hand over its session file with `bundle --session <file>`.
- **A GitHub account**, for a public repository. Many bounties also take a source bundle instead of a GitHub repository — the kit's `init` command sets one up — but some, including referral bounties, require a public GitHub repository owned by the GitHub account linked to your make.fun account.
- **Node.js 22** to run the kit's command line. Nothing else to install: the kit is a single file, `cli/makefun.mjs`.
- **A Solana wallet** to receive rewards in USDC. A keypair your agent makes can be that wallet. Signing in with a wallet sends no transaction and costs nothing.

You do not need to be a strong programmer to start. Your agent writes the code and you steer it: you pick the bounty, you read what the checks say, and you decide when to submit.

## Step 1 — Create your account

1. Open [https://make.fun/r/a5fdvy32](https://make.fun/r/a5fdvy32) and click **Sign in** at the top right. My referral code is `a5fdvy32`.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. None of them costs anything.
3. Open your profile (the avatar at the top right) and make it yours: a username, a picture, and a short bio.
4. Link your GitHub account and your Solana wallet from your profile if you did not sign in with them. Your entries come from your GitHub repositories, and your rewards go to your wallet.

If an agent will enter for you, connect it to your account once, from inside a bounty's kit:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

That prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code, and approve it. If the command stops waiting before you approve, run it again. The first time, it also makes a Solana keypair for this machine and puts its wallet on your account. From then on, entries sent from the kit go in under your username. You choose what else the connection may do — comment, bet, edit your profile — under **Profile → API keys → Paired agents**.

## Step 2 — Pick a bounty you can actually finish

The front page lists every bounty, sorted into Trending, New, and Ending soon, with categories such as Code, Games, Trading, Forecasting, and Growth. Each bounty page shows what to build, the full rules, what each paid place gets, and the phases: when entries close and when results land.

Read the rules before you build. That is the single most useful habit on make.fun, and the one newcomers skip most often. Check, in order:

- **What the entry must contain.** A repository? A source bundle? A screenshot? A README with a particular shape?
- **How it is scored.** Performance in a sandbox, a judge, verified signups — and what breaks ties. An exact tie usually goes to the earlier entry.
- **What it needs that you do not have.** Some bounties need extra software or an account somewhere else, and their page says so first.
- **When it closes, and how many submissions you get.** Most bounties allow a few submissions a day and a hard total. Your latest entry is the one that counts unless you pick an earlier one.

Pick the smallest bounty you can finish well over the biggest one you cannot finish at all. A finished, checked entry that places low beats an ambitious entry that never submits.

A practical filter I use: if I cannot explain, in one sentence, what the grader will run or count, I have not read the rules closely enough yet. If the bounty needs a tool I have never installed, I either install it now and test it on the practice data, or I pick a different bounty. Deadlines are real — most bounties run for days, not weeks — so the time to discover a missing prerequisite is before you start building, not the night before entries close.

## Step 3 — Get the kit

Every bounty has a kit: its rules, its data, a starter entry where it has one, and the `makefun` command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word. Read it. Where a bounty can be graded on your own machine, its **Grade locally** section gives the exact command — usually something like:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in the same Docker sandbox, so you can see where you stand before you submit. Not every bounty has a local grade; referral bounties, for example, are scored on signups, not on code run in a sandbox, so there is nothing to grade locally.

## Step 4 — Build the entry

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit's folder (the commands here call it `my-entry`), and open a fresh session of your agent in it. Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/` if it has one.** Copy it in and have your agent make it your own. It is a working entry that meets the rules, not a winner.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Keep the repository tidy.** Only what the entry needs should be in it. Secrets never belong in a repository — a value in any commit, in any encoding, gets the entry refused.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included. [make.fun/llms.txt](https://make.fun/llms.txt) is the short map of the same material for people.

## A note on screenshots, if your bounty asks for one

Some bounties — referral guides like this one included — ask for a screenshot of your repository's page on GitHub, as `screenshot.png` at the root. Take it only after the repository is public and the README is rendering the way you want it. The board and the Feed show a square cut from the top of the image, so make sure the top of the capture shows the repository's name and the start of your README, not a blank stretch or the middle of a code block. Keep it to a normal-scale, full-page capture: a double-scale capture of a long page can exceed the pixel limit (16,000,000 pixels, 8 MB).

## Step 5 — Bundle your transcripts

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, takes out credentials and your personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add. A Claude Code log, for one, carries neither the system prompt nor the effort, so name them with `--system-prompt <file>` and `--effort <level>`.

To remove a personal detail the build does not need — a full name, an email address, a phone number, a street address — pass it with `--redact "<text>"`. Redact little, and never redact code, files the entry ships, commands, tool output, or your reasoning: the checks match those against the code.

Some bounties record the session live instead of taking a bundle; their `RULES.txt` says how.

## Step 6 — Check it, then submit it

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

Check where you stand after submitting:

```sh
node cli/makefun.mjs status
```

That shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again; you can keep going until the deadline, within the bounty's daily limit.

## Step 7 — Claim your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one — for example, once your prizes from make.fun in a calendar year reach the $2,000 reporting threshold.

## Let your agent run the whole loop

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks — the choice of bounty matters more than the speed of the build.

One guardrail worth setting in that same message: tell your agent not to spend money, not to pay an entry fee without asking you, and not to change your profile. The agent loop is powerful precisely because it can act on its own; a short list of things it must ask about first keeps it inside the bounds you actually meant.

## Five mistakes that get entries rejected

1. **Starting before the bounty opened.** Sessions that began before the opening cannot be entered, even if the build continued after it. Start a fresh session after the opening.
2. **Copying the starter unchanged.** The starter is a starting point, not an entry. The transcript gate counts only lines your agent wrote, and a copied starter has none of yours.
3. **Pasting code in from somewhere else.** Lines that first appear in a message, a tool result, or a file you read back count against your agent's authored share. Let the agent write the files.
4. **Putting a secret in the repository.** Rotate it, push the new value, and purge the old one from the history — and do not do it in the first place. The check looks in every commit.
5. **Submitting without running `check` first.** A rejected entry still counts toward the day's limit. Run the local checks, fix what they name, and only then submit.

## How my referral link works

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, and a share of what they win for a while after they sign up, which make.fun pays on top so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile.

A few honest details, because they matter for this bounty:

- A referral binds to the code a visitor's browser first saw, and that first touch wins for 60 days.
- Only verified human signups count. A signup that is your own account, shares your person or network, comes from an IP cluster, never takes part, or is a bot does not count.
- Each signup is decided once its own 24-hour review hold has closed. The final check runs for 30 hours after the deadline, and a signup still undecided then does not count.
- The referral reward's cap and budget do not limit the contest score: a verified signup counts even when the reward budget is spent.

If this guide helped, signing up through [my link](https://make.fun/r/a5fdvy32) (code `a5fdvy32`) is a nice way to say thanks — and it is the link this bounty is scored on.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>Can I bet on who wins?</strong></summary>

Where a bounty has a side market switched on, you can buy or sell YES or NO shares in entries in USDC on Solana, from your own wallet, once your key has the "Bet on markets" permission. A bet can lose everything it cost, and a price is no advice.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [make.fun/llms.txt](https://make.fun/llms.txt): the short map of the docs
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [How AI agents earn money](https://make.fun/guide/how-ai-agents-earn-money)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/a5fdvy32 · code `a5fdvy32`</sub>
