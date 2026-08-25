---
layout: post
title: "I Compared 46 Pairs of Vibe-Coded and Traditional Repos. I Couldn't Tell Them Apart."
date: 2026-08-25
---

**TLDR:** I compared 46 pairs of Python repos on GitHub, half written with AI tools and half written traditionally, matched by size, age, and popularity. I measured them with code-quality tools while not knowing which was which. Result: no measurable difference. The vibe-coded repos actually leaned slightly simpler and better-commented. Details and caveats below.

I ran a small study to find out whether "vibe-coded" repos are worse code. After comparing 46 pairs of GitHub projects, the honest answer is that I couldn't tell them apart.

## The setup

I found public Python repos where the author openly used AI tools. Some had bot accounts (Claude, Copilot, Cursor) in the commit history, others said it right in the README. Then I paired each one with a traditionally-written repo of similar size, age, and popularity.

Next I measured both sides without knowing which was which. The measuring script counted how complicated the functions are, how long they run, how well they're commented, and how many documentation mistakes they contain. Only after all the numbers were collected did I reveal which repos were the AI ones.

## The results

Nothing was statistically significant. Every single test came back inconclusive.

But the direction of the numbers was more interesting. Across five different measures, the AI-assisted repos leaned slightly cleaner:

- Fewer overly complicated functions (4.6% vs 6.5%)
- Lower average function complexity
- Shorter functions
- Fewer documentation mistakes per 1,000 lines
- A higher share of comments in the code

None of these gaps were big enough to prove anything with 46 pairs. Still, they all pointed the same way. The vibe-coded repos weren't sloppier. If anything, they trended toward smaller, simpler, better-commented functions.

![Head-to-head win rate per metric](/assets/chart_winrate.png)

![Median values per metric, AI-assisted vs traditional](/assets/chart_medians.png)

![All p-values at a glance](/assets/chart_pvalues.png)

![How the sample was built](/assets/card_sample.png)

## Honest caveats

First, this is a pilot. 46 pairs is enough to see shapes, not enough to claim findings.

Second, these are repos whose authors chose to announce their AI use and publish the result. That selects for people who cared enough to ship something. It says nothing about the abandoned half-projects nobody uploaded.

Third, these measurements don't check whether code is correct. A repo can look simple and well-commented and still compute the wrong thing. It can also leak your API keys, ship with a license it has no right to use, or break in production on a Tuesday. None of that shows up in a complexity score.

Fourth, matching wasn't perfect. I only kept repos with proper open-source licenses, which eliminated 40% of my first batch and forced some awkward substitutions.

![Where repos dropped out of the sample](/assets/chart_attrition.png)

## Method in one picture

![The pipeline from GitHub search to paired statistics](/assets/chart_method.png)

## What's next

The plan from here: expand the sample, add checks that actually test whether the code works, and write it all up properly. Every script, every raw number, and the exact recipe for building the sample is public at [github.com/adamafzainizam/vibe-code-quality-study](https://github.com/adamafzainizam/vibe-code-quality-study). Future posts in this series will go deeper on the methodology, including why 40% of my first batch got filtered out by license checks alone.

*This post is part of an ongoing series on vibe-coding and code quality. Updates will appear on this blog.*

## Full disclosure

I used AI tools to build the analysis pipeline and draft this post. Using AI to study AI felt appropriately on-theme.

## Where I land on all this

Coding is one of the few places where AI use should be actively encouraged, because it's verifiable: the code runs or it doesn't, the tests pass or they fail. But "encouraged" doesn't mean "blind". If you vibe-code without learning anything, you ship security holes you can't see, violate licenses you didn't read, and build things you can't fix at 2am when they break. The skill isn't optional; it just moved up a level. You still need to review, test, and understand what you're shipping. AI should assist the work, not replace the judgment, and it's not a substitute for learning fundamentals the traditional way.

And this is where coding differs from a lot of other AI use cases. Alongside task automation and data crunching, software is a domain where AI takes the repetitive work and leaves humans the interesting parts: architecture, tradeoffs, deciding what's worth building in the first place.

I keep coming back to one line: I want AI to do my laundry so I can make art. Not AI making art so I can do laundry.

After all the talk about AI slop flooding GitHub, the measurable difference between published vibe-coded Python and its traditional counterparts is roughly nothing. Maybe the interesting question isn't whether AI code is worse. It's why we expected it to be.
