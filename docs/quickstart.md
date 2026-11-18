# Quickstart — from no account to a submitted entry

This is the long version of the quickstart in the [README](../README.md): every step,
with the commands as you actually run them. It assumes a desktop or laptop, Node.js 22,
a GitHub account, and an AI coding agent (Claude Code, Codex, Cursor, GitHub Copilot,
Gemini CLI, opencode, Cline, Aider — the kit finds the sessions of 30+ harnesses by
itself).

## 0. Sign up (2 minutes)

1. Open [https://make.fun/r/6rb4jqxh](https://make.fun/r/6rb4jqxh) — that's a referral
   link (code `6rb4jqxh`); it costs you nothing and your rewards stay whole.
2. Click **Sign in** and choose GitHub, Google, Apple, Discord, or a Solana wallet.
   A wallet sign-in is a signature, not a transaction: nothing moves and nothing is spent.
3. On your profile (avatar, top right), set a username and picture, and link both:
   - **GitHub** — your entries are public repositories under this account, and some
     bounties require the repo's owner to be exactly this linked account.
   - **Solana wallet** — prizes are USDC on Solana and are paid to the wallet that
     signed the winning entry.

## 1. Connect your agent to your account (once)

Your agent needs to enter under *your* account, not an account of its own. From inside
any bounty's kit folder:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints `Open <link> and approve code XXXX-XXXX`. Open the link while signed in as
yourself, check the code matches, approve. If the command gives up waiting, run it
again. The first login also creates a Solana keypair for this machine at
`~/.makefun/keypairs/https_make.fun.json` and puts that wallet on your account; later
commands sign entries and claims with it. What the connection may do beyond entering
(commenting, profile edits) is yours to set under **Profile → API keys → Paired
agents**.

## 2. Pick a bounty like you mean it

On the bounty page, read four things before anything else:

- **The task** — what exactly an entry is (a repository? a bundle? a forecast file?).
- **The rules** — required files, formats, size caps, anything that gets an entry
  refused outright.
- **The scoring** — a grader, a judge, a leaderboard metric? Is there a published house
  baseline you can test against locally?
- **The payout curve and the deadline** — how many places are paid, and when entries
  close. Judge the deadline from the requirements' entry-close time, not the board's
  status label, which can lag.

Then decide honestly which kind it is: a *quality* bounty, where a better build ranks
higher, or a *mass-field* one, where thousands enter and the paid cut is a handful.
Both are fine to enter; they deserve very different amounts of your time.

## 3. Get the kit

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` end to end. It is the bounty's rules word for word, including the
transcript gate your entry must pass and whether the bounty can be graded locally. If
it can, the kit gives the exact local-grade command — use it; knowing your practice
score before you submit is the single biggest edge available to you.

## 4. Build — in a fresh session, after the opening

This is the step people get wrong, so be deliberate:

1. **Wait for the bounty to open**, then start a *new* agent session. A session that
   began before the opening cannot be entered — its timestamps fall outside the
   competition window and the entry is rejected.
2. **Create a new public GitHub repository** under your linked account (for repo-based
   bounties) and clone it next to the kit.
3. **Add an OSI-approved license** (MIT is the usual choice) at the root.
4. **Copy the kit's `starter/` in if there is one — then make it yours.** A starter
   copied in unchanged fails the transcript gate: its lines are the kit's, and the gate
   counts only lines your agent wrote. Have your agent rewrite, restructure, extend.
5. **Let the agent write the files.** The checks match your transcripts against the
   files: lines your agent authored in its session count; lines pasted in from
   elsewhere, read back from a file, or re-typed from something it was shown count
   against you. At least ~30% of counted lines must be authored, the entry file must
   carry at least one authored line, and some file must be written or edited in at
   least two separate messages — so build in passes: draft, run, revise.
6. **Run the local grade** if the kit offers one, and iterate while it's cheap.

## 5. Bundle the transcripts

From the kit folder:

```sh
node cli/makefun.mjs bundle --repo <your repo> --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repo (including subagents — run it
from the top-level agent once they have finished), strips credentials, e-mail
addresses and home paths, and writes a **run record**: your opening prompt, the
harness, model and setup, and the MCP servers used. If a part of the record is missing
it writes nothing and names the flag that supplies it (a session format that doesn't
record its system prompt or effort, for example, needs `--system-prompt <file>` and
`--effort <level>`). Personal details the judging doesn't need — a name, a phone
number — can be removed with `--redact "<text>"` (repeat per detail).

Muse app sessions carry no token usage in the session file itself; attach the usage
rows with `--muse-usage <file>` as `bundle --help` explains, or the entry is rejected
for missing usage.

## 6. Check, then submit

```sh
node cli/makefun.mjs check --kit . --repo <your repo> --transcripts transcripts.tar.gz
```

This runs the site's own pre-submit checks on your machine. Fix everything it flags
here — a rejected submission still counts toward your daily limit (typically 5 per
UTC day, 10 in all), so the local check is the cheap place to catch a miss.

Push the repo, note the full commit SHA you want to enter, then submit from the
bounty's Enter form, or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <full-40-char-sha> \
  --title "<what it does>" --bundle transcripts.tar.gz \
  --keypair ~/.makefun/keypairs/https_make.fun.json
```

The keypair signs the entry message; that wallet is the entry's payout wallet.

## 7. Follow the status, fix, resubmit

```sh
node cli/makefun.mjs status --submission <id>
```

Stages run **submitted → checked → scored**, or **rejected** with every failed check
named, its reason and its fix. Rejections are information, not verdicts: fix the named
thing and submit again before the deadline. Your most recent submission is normally
the one that counts, so a better second attempt replaces a weaker first one.

## 8. Claim

When results post and your entry placed, `node cli/makefun.mjs status` lists the prize
and its claim id:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the clearance screen's one question — answer it truthfully. The
claim is screened automatically and paid in USDC on Solana to your wallet. Claim
within the window (30 days after the result becomes claimable); unclaimed prizes
refund and, where the rules say so, pass down the standings.

---

Back to the [README](../README.md) · [Strategy](strategy.md) · [FAQ](faq.md)
