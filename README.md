# Runway — Does the money last?

A Canadian retirement drawdown calculator that runs entirely in your browser.
Type your own figures into the form and it models the whole thing — year by
year, out to whatever age you pick — and recomputes the answer as you type.

**Use it here: <https://christhefarmer.github.io/runway/>**

**Nothing you type ever leaves your browser.** There's no server, no account,
no analytics, no upload. The page loads no scripts, no fonts and no images
from anywhere — open the network tab and you will see one request, for the
page itself. Download `index.html`, disconnect from the internet, open it, and
it still works.

**No AI does the calculating.** Every figure comes from arithmetic written out
in the source of the file — brackets, rates and rules you can read in order
and check against the CRA's own tables. The file was written with AI
assistance, as most software now is; the calculation itself contains none,
makes no network request, and gives the same answer every time from the same
inputs.

## What it does

- Models one or two people, with a second person who can be left out, join
  partway through, or leave partway through (with a chosen share of joint
  accounts staying behind).
- Tracks account types separately per person, because the tax differs:
  chequing, savings, RRSP/RRIF, TFSA, non-registered, GIC, FHSA, and an
  optional RDSP.
- Applies CPP, OAS and mandatory RRIF minimums at the right ages, and models
  the **OAS recovery tax** (the clawback) per person rather than per household.
- Pays the **Guaranteed Income Supplement** where you qualify, on last year's
  income, from the current quarter's published tables.
- Estimates income tax with real federal and provincial brackets for all 13
  provinces and territories. The tax year it was built against is shown above
  every result.
- Taxes non-registered holdings properly: interest and eligible Canadian
  dividends yearly with the gross-up and credit, the taxable half of gains
  realized to fund spending, and a deemed disposition at death.
- Shows the **tax still owed on an RRSP**, so you can compare plans on what
  actually reaches you rather than on a headline balance that counts pre-tax
  and tax-free dollars as if they were the same.
- Models the **RDSP** including the taxable/non-taxable split and the ten-year
  assistance holdback, which repays $3 per $1 withdrawn too early.
- Models housing: rent, or a mortgage with an editable home value, plus an
  optional second property and a home sale. Home equity is a reference column
  and is never drawn on to cover a shortfall.
- Handles a mid-plan province move, a chosen death age for either person with
  a survivor-spending adjustment, and one-time inheritances.
- An **Uncertainty** switch reruns the plan hundreds or thousands of times
  with randomized investment returns and shades the range over the same
  projection, so you see a spread instead of one optimistic line.
- **Menu → Print** opens a two-page report of the plan: the answer, the
  savings curve and what would change it on page one, the year-by-year table
  on page two. Print it or save it as a PDF.

## How to use it

1. Open <https://christhefarmer.github.io/runway/>, or download `index.html`
   and open it in any modern browser. Chrome, Firefox, Safari and Edge all
   work, online or off.
2. Fill in the form. There is no Run button: the answer at the top of the
   window recomputes as you type. **The defaults are placeholders, not real
   or typical numbers** — replace every field with your own before trusting
   the output.
3. Hover or tab to any **?** for an explanation. Every heading in the results
   table has one too.
4. Not sure what it can do? Pick a worked example from the **Plan** dropdown
   at the top right. Each one fills in a whole plan and runs it — a couple where one partner dies partway
   through, a household that sells up and moves province, an RDSP drawn early
   enough to trigger the repayment rule. They are worked examples, not
   recommendations.
5. Every file action lives in **Menu** at the top right: **Save** keeps a
   plan in this browser, **Export** writes it to a plain-text file and
   **Import** reads one back, **Copy**/**Paste** move a plan as text, and
   **Print** makes the two-page report. A file is the reliable way to keep
   your numbers; the browser also auto-saves, but clearing browser data
   wipes that.
6. Change one assumption at a time and re-run. Whatever moves the result most
   is what's worth attention in real life — usually spending first, then how
   long you work, then investment returns.
7. Once a result looks good, stress-test it: rerun with returns about 1% lower
   and spending about 10% higher. If it still holds, that's a more trustworthy
   answer than the first pass.

## What this is not

- **Not tax advice or a tax return.** Tax is a graduated approximation
  (federal and provincial brackets, basic personal amounts and the main
  senior credits), not what the Canada Revenue Agency would actually
  calculate. Several province-specific rules aren't modelled. The page's own footer lists
  the specific gaps.
- **Not financial advice.** It's arithmetic on assumptions you supply. Garbage
  in, garbage out — the answer is only as good as your inputs.
- **Not a full economic model, even in Monte Carlo mode.** Only the investment
  return is randomized; inflation and guaranteed-rate accounts stay fixed in
  every trial.
- **Not personalized.** It has no idea what's true about your finances, your
  health, your family or your risk tolerance. You are the one supplying that
  judgment.

If you want a real plan, a fee-only financial planner with no product to sell
you is worth far more than any calculator. This is for building intuition and
asking better questions, not for replacing that conversation.

## Source, and checking you have the real file

`index.html` is the whole program. It ships unminified on purpose: the maths
is meant to be read, not taken on trust. Open it in any editor and the tax
tables, the drawdown order and the model are all there in order.

That also means anyone can modify a copy. If someone hands you this file
rather than a link, check it against the published one:

```
shasum -a 256 index.html
curl -sL https://christhefarmer.github.io/runway/index.html | shasum -a 256
```

If those differ, you do not have the file from here. For a page you type your
net worth into, that is worth thirty seconds.

## Reporting a problem

Open an issue: <https://github.com/christhefarmer/runway/issues>.

A wrong number is worth reporting even if you are not certain it is wrong.
Say which fields you entered and what you expected, and it can be checked
against the tax tables. **Do not paste your real balances** — round them, or
use whatever smallest example still shows the problem. Tax brackets and
benefit amounts are re-verified periodically, and the date they were last
checked is shown directly above every result.
