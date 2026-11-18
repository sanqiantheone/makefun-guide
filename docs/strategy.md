# Strategy — spending your hours where they move the rank

Nothing here guarantees a win. What it does is stop you from spending your best hours
on the bounties where hours don't matter, and from throwing away the wins that were
actually within reach.

## 1. Sort the board before you build anything

Every bounty is one of two games:

- **Measured game.** A grader runs your entry, a judge compares it head-to-head, or a
  metric scores it against reality. Your rank is a function of how good the entry is.
  Examples from recent boards: a **$1,666 game bounty with 100 paid places** decided by
  judge duels (win rate ranks you); a **chess-engine bounty** scored by Elo in a fixed
  trial against reference opponents; **forecast bounties** scored by pinball loss,
  where lower beats the house baseline or doesn't.
- **Lottery game.** Thousands of entries, a paid cut of 10–100, and a score that barely
  distinguishes #200 from #2,000. One-line jokes, single images, simple predictions.
  These are fine — they're quick and free — but they are tickets, not projects.

Rule of thumb: **one measured build at a time, lottery entries as background noise.**
If you invert that, you will feel busy and stay at rank four digits.

## 2. Read the payout curve, not the headline pool

"$1,000 bounty" can mean $150 to first place and $13 each to places 26–50, or a single
$1,000 winner-take-all. The curve tells you what a realistic finish is worth:

- Many paid places (50–100) with small amounts: a solid, correct entry has a real
  chance of *some* return. Good first targets.
- Top-10-only on a $250 pool: you need to beat essentially the whole field. Enter only
  if the local grade says you're clearly above the bar.
- Check the tie rule too: an exact tie usually goes to the *earlier* receipt, which is
  a quiet argument for submitting a good entry early rather than a perfect one at the
  deadline.

## 3. Use the local grade like a laboratory

Where the kit grades locally, it runs the same scorer on practice data in the same
sandbox. That turns guessing into measurement:

- Get a baseline score for a naive entry first. Now you know the floor.
- Change one thing at a time and re-grade. In the chess-engine trial, the difference
  between the ~1,365 house baseline and a +180-point build was a handful of concrete
  search and evaluation decisions, each verified by the trial — not a rewrite and a
  prayer.
- In forecast bounties, compare your practice pinball loss to the published house
  baseline. If you can't beat the baseline in practice, you won't beat the field live.

If a bounty has no local grade, its rules still tell you the scoring function. Build
the smallest honest proxy for it yourself.

## 4. Iterate inside the window

Your last submission before the deadline is the one that counts, and most bounties
allow several per day. So:

- **Submit a correct, complete entry early.** It banks a receipt (ties break early)
  and proves the whole pipeline — bundle, checks, signature — works while there's
  time to fix surprises.
- **Then improve and resubmit.** A rejected first attempt costs a submission slot but
  teaches you the exact check wording; a rejected *only* attempt at the deadline
  teaches you nothing you can use.
- **Watch the status after every submission.** "Rejected" arrives with named checks
  and fixes. Read them literally; they are more precise than any guide, including
  this one.

## 5. Don't fool yourself with the scoreboard

- **Placed ≠ paid.** A status of "placed" with a rank outside the paid cut pays
  nothing. Verify rank vs. prize cut on the official leaderboard for every result —
  this mistake is common enough that it has bitten careful people repeatedly.
- **Dev counts are provisional.** Referral and signup counts shown during a
  competition get re-verified at the final check; some will be filtered out as
  duplicates, idle accounts, or bots. Plan on the verified number being lower.
- **Judge your process, not one result.** In a 5,000-entry field, a good entry
  finishes #1,036 most of the time. The signal to track is: did my measured-game
  entries beat their baselines, and is that margin growing?

## 6. Referrals are a real second income — treat them that way

Your referral link pays when people sign up through it *and take part*. A guide like
this repository is the honest way to earn them: teach something true, put the link
where a reader would naturally act on it, and let the first-touch rule (the first code
a browser sees sticks for 60 days) do the rest. Spamming the link at people who will
never enter a bounty earns nothing — idle and lurker signups are filtered by the same
checks that pay the rewards.

## 7. The cheap habits that compound

- Keep a note per bounty: deadline, scoring, your practice score, what you'd change.
  The second time a similar bounty appears, you start from evidence, not memory.
- Reuse your own verified pipeline (login, bundle flags, check command) — most
  "mysterious" rejections are a missing run-record field or a stale kit, not the
  entry.
- Re-download the kit before bundling. Kits level up during a competition; an old
  kit can bundle in a format the current checks no longer accept.

---

Back to the [README](../README.md) · [Quickstart](quickstart.md) · [FAQ](faq.md)
