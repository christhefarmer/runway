# Runway — Does the money last?

A simple retirement drawdown calculator that runs entirely in your browser.
Fill in your numbers, hit Run, and see whether your savings outlast your
spending — year by year, out to whatever age you pick.

**Nothing you type ever leaves your browser.** There's no server, no
account, no analytics, no upload. Open `runway.html` locally or via GitHub
Pages and it just works — you can even disconnect from the internet and it
will still run.

## What it does

- Models two people (or edit it for one) — ages, income, retirement dates.
- Tracks separate account types per person: checking, savings, RRSP, TFSA,
  non-registered, GIC, FHSA, and an optional RDSP.
- Applies CPP, OAS, and mandatory RRIF withdrawals at the right ages.
- Estimates income tax using real federal + provincial brackets for every
  Canadian province and territory.
- Draws down accounts in a sensible order when spending exceeds income, and
  parks any surplus back into tax-advantaged room automatically.
- Handles a mid-plan province move, a chosen death age for either person
  (with a survivor-spending adjustment), and one-time inheritances.
- Includes a Monte Carlo mode that reruns the plan hundreds or thousands of
  times with randomized investment returns, so you can see a range of
  outcomes instead of one optimistic line.

## How to use it

1. Download `runway.html` (or clone this repo) and open it in any modern
   browser — Chrome, Firefox, Safari, Edge all work.
2. Every field on the left is editable. **The defaults are placeholders,
   not real financial advice or typical numbers** — replace every field
   with your own figures before trusting the output.
3. Click **Run simulation** for one deterministic projection, or
   **Run Monte Carlo** to see a range of outcomes under randomized returns.
4. Use **Save my numbers** / **Load my numbers** to export your inputs to a
   JSON file and reload them later — this is the reliable way to keep your
   numbers between sessions. (It also auto-saves to your browser's local
   storage as a convenience, but don't rely on that alone — clearing
   browser data will wipe it.)
5. Change one assumption at a time and re-run. Whatever moves the result
   the most is the thing worth paying attention to in real life — usually
   spending first, then how long you work, then investment returns.
6. Once a result looks good, stress-test it: rerun with returns about 1%
   lower and spending about 10% higher. If it still holds up, that's a
   more trustworthy answer than the first pass.

## What this is not

- **Not tax advice or a tax return.** Tax is a graduated approximation
  (federal + provincial brackets and basic personal amounts), not what the
  Canada Revenue Agency would actually calculate. Surtaxes, most credits,
  and some province-specific rules aren't modeled.
- **Not financial advice.** It's arithmetic based on assumptions you
  supply. Garbage in, garbage out — the answer is only as good as your
  inputs.
- **Not a full economic model, even in Monte Carlo mode.** Only the
  investment return is randomized; inflation and guaranteed-rate accounts
  (GICs, savings, checking) stay fixed every trial.
- **Not personalized.** It has no idea what's actually true about your
  finances, your health, your family, or your risk tolerance. You are the
  one supplying that judgment.

If you want a real plan, a fee-only financial planner who has no product to
sell you is worth far more than any spreadsheet — this tool is for building
intuition and asking better questions, not replacing that conversation.

## Privacy

This is a static HTML file with no external requests, no analytics, and no
tracking. Your numbers stay in your browser's memory (and optionally its
local storage, if you don't clear it) unless you explicitly download a
save file. Nobody else — including whoever shared this file with you — can
see what you enter.
