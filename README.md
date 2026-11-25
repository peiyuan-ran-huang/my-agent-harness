# My AI agent harness (for Claude Code)

*Version 3.2 · 24 November 2026 · Peiyuan (Ran) Huang*

> **Please read this first.** I share this page for my personal interest only. It is
> a record of several months spent learning to work with AI agents in my day-to-day
> work. Nothing here claims to be the right way to do things, and better designs are
> warmly welcome. The material is not for commercial use. I also want to be clear
> that I use these tools cautiously. No restricted data and no sensitive material is
> given to the AI, and much of the setup described here exists to enforce
> exactly that.

## About me, honestly

I am not an IT engineer (not even a tech person!). My day-to-day work is in
epidemiological research, a field that seems to sit a long way from AI. I only started
using AI agents in early 2026, after a chance encounter and out of curiosity, and
everything here has been learnt in practice since then, detours and dead ends
included. I am nowhere near an expert, and this page makes no claim to expertise. It
is one beginner's working notes, written down in the hope of trading experience with
people on the same road. If you spot something wrong, or you do something better, I
would very much like to hear about it!

## What this is

A web page describing the personal Claude Code configuration (the "harness") I use
in my day-to-day work:

- **[Read the page online][page]** (source file:
  [`my-agent-harness-for-claude.html`](my-agent-harness-for-claude.html)): the whole
  tour. It covers the task lifecycle contract, safety architecture, verification
  machinery, the learning loop, and an item-by-item catalogue of the harness's
  components, including the skills and commands in regular use, each named,
  summarised and credited to its source.

Claude Code is not the only agent I work with. I also use Codex and DeepSeek Harness
(DSH), with Codex leaning towards verification and DSH towards low-level execution.
When I get the chance I will tidy those set-ups up and share them as well.

The page is a single self-contained file. You can open it locally in any browser,
and nothing is fetched from the network. If you only have ten minutes, scroll the
page from top to bottom and skip the fold-outs, which are there for question time.

## Why I made this

If anyone is curious about what my setup actually looks like, I hope this page
helps.

None of this arrived fully formed. The harness came out of some top-down design and
a lot of stumbling - something went wrong, I wrote down why, patched the design, and
went round that loop again for months. The polish you see here is hindsight.

If you build your own, it will grow the same way, and it should. Take what seems
useful rather than the whole configuration.

## Why not share the whole harness?

This page describes the harness without reproducing it. That is deliberate -
publishing the configuration wholesale would be both impractical and unwise.

What the page promises instead is that everything it describes was checked against
the live configuration on the date shown. Every layer, mechanism, count and trade-off
was probed from the live configuration rather than recalled from memory. The
description is also complete at the architecture level. A small number of individual
items are not listed, but no load-bearing part of the design has been left out of the
tour. If the page does its job, you come away with the design ideas, and those are the
part worth taking. The concrete implementation is the kind of work you can figure out
together with your own AI agent, and a version built to fit your needs will serve you
better than a copy of mine.

If anything here does not make sense, or you would like a fuller explanation of any
mechanism, please feel free to get in touch.

## Known limitations, and where this goes next

I have put a lot of work into this harness, and it still has clear weaknesses. I list
them here because they mark where the next round of work will go, and because they may
save you from making the same mistakes.

- **The resident context is too large.** A good deal of instruction text is loaded
  into every session, whether or not the task at hand needs it. That spends tokens
  unnecessarily, and too much material unrelated to the task can also distract the
  model.
- **Skills, commands and memory files can pile up.** Each was added for a reason, but
  there is a real risk that the collection grows beyond what earns its keep.
- **The tuning has not been evaluated rigorously.** My changes to the harness rest
  mainly on feel, experience and process metrics, such as how often a review has to be
  reopened. I have not built a dedicated evaluation framework that treats the harness
  itself as the object of study and tests it with controlled comparisons, so I cannot
  show robustly that it also improves the outcome metrics that matter in real work.

Beyond these three, as models become more capable, a heavy harness may start to hold
the agent back rather than help it.

So the direction from here is to subtract, to refine, and to judge changes by their
actual effect. I am NOT aiming for 500+ skills, hooks or memory files. I am
aiming for fewer resident instructions, fewer QC (quality-check) rounds that achieve
nothing, less need for me to step in by hand, and a final task accuracy that is higher
and can be measured.

## A few notes

- Counts were probed live from the configuration on 24 November 2026, so they will
  drift.
- Names tied to people, projects and data providers are withheld. The mechanisms and
  component names are real.
- This page was prepared with the assistance of Claude Code (designed by Fable 5,
  executed and verified by Opus 5; updated in October and November 2026 with
  Opus 5.5), the same agent the harness is built around, which seemed like the
  only honest way to make it.
- The page is about working with Claude Code, so its layout and colours deliberately
  borrow Claude's classic look (the cream background and orange accent). It is a
  small homage for context and implies no official affiliation.
- This is a personal project. It states personal views and describes a personal
  setup. It is not institutional policy or advice, and no endorsement by my employer
  or by Anthropic is implied.
- Effectiveness figures quoted on the page (e.g., review reopen rates) come
  from the harness's own operational logs. They are internal and descriptive, and
  they have not been independently audited.

[page]: https://peiyuan-ran-huang.github.io/my-agent-harness/my-agent-harness-for-claude.html
