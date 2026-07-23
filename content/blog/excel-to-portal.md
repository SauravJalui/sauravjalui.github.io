---
title: 'Getting a Company Off Excel Without a Revolt'
date: 2026-07-12
authors:
  - name: Saurav Jalui
    link: https://github.com/sauravjalui
    image: https://github.com/sauravjalui.png
tags:
  - Case Study
  - Product Strategy
  - Change Management
category: 'Case Studies'
excludeSearch: false
images:
  - /images/post-migration.jpg
---

{{< hextra/hero-badge >}}Case Study · Migration{{< /hextra/hero-badge >}}

![From a wall of spreadsheets to one system](/images/post-migration.webp)

For years, the entire operation ran on spreadsheets. Scheduling, teacher availability, who owed how many hours: all of it lived in a sprawl of Sheets, held together by a handful of people who just _knew_ how it worked. It had run the business for half a decade, and to its credit, it mostly worked.

Until it didn't, on every axis at once. A typo in the wrong cell quietly broke someone's schedule. Anyone with the link could edit anything, so there was no real notion of permissions. Nothing was logged, so when something went wrong there was no way to reconstruct what happened or who'd done it. And none of it scaled: every new teacher, every new cohort made the sheets heavier and the humans holding them more overloaded. The sheet wasn't one problem. It was four, and they were compounding.

## The easy version of this project would have failed

The tempting way to do this is a big-bang cutover: build the whole portal, pick a Monday, turn off the sheets, send an email. It's clean on a Gantt chart and it's a disaster in practice, because it asks an entire organization to abandon five years of muscle memory overnight and trust software they've used for a week. The day something breaks (and something always breaks), everyone's instinct is to reach back for the spreadsheet they _know_, and now you're running both, badly, with no plan for it.

So I didn't do that. The migration went team by team, deliberately, and the sequencing was itself a design decision.

## Starting where it would break

I didn't start with the easiest team. I started with one of the harder ones, the group whose workflows were the least standardized and most likely to surface the ugly edge cases. The logic: if the portal could survive the messy team, the tidy teams would be easy. And if it _couldn't_, I wanted to find that out early and cheaply, with one group, instead of discovering it mid-rollout with everyone watching.

That group knew they were the stress test, and I told them so plainly. Being the guinea pig is more palatable when it's framed as _your feedback shapes what everyone else gets_ rather than _you're the ones we're experimenting on._ The distinction is entirely in the framing, and it matters more than it should.

## Running two systems on purpose

For each team, the sheet didn't die the day the portal arrived. They ran in parallel for a stretch: portal for real work, sheet as the safety net nobody was forced to let go of yet. This is inefficient and I did it anyway, because the alternative, demanding a leap of faith, is how you turn nervous users into hostile ones.

What actually retires a spreadsheet isn't a mandate. It's the moment someone realizes they haven't opened it in two weeks and don't miss it. You can't order that feeling into existence; you can only make the portal good enough that it happens on its own, and give people the safety net until it does. Once a team stopped reaching for the sheet, _then_ it went away, team by team, on their timeline, not mine.

## The hard part was never the software

I could have gotten the permissions model, the approval chains, and the timezone-aware scheduling technically right and still failed completely, because none of that was the actual obstacle. The obstacle was that I was asking people to give up the thing they trusted for the thing they didn't, and no feature list wins that argument. Trust does.

Building the trust looked like small, unglamorous things. Migrating a team's real data in clean so their first impression of the portal wasn't a mess they had to fix. Making the single most common task genuinely faster than the sheet had been, before touching anything fancy. Sitting with people while they used it instead of reading their complaints in a form. Letting the pilot team's frustrations visibly change the product, so the _next_ team could see that feedback here actually went somewhere. None of that shows up on a roadmap. All of it was the real work.

## What I'd carry into the next one

The lesson that outlives this project: a migration is a trust exercise disguised as a technical one, and the sequencing _is_ the strategy. Who goes first, how long the old thing survives alongside the new, whether people feel like participants or test subjects: those decisions determined whether this worked far more than any feature did. Excel is gone across the org now, but not because we switched it off. It's gone because, one team at a time, people stopped reaching for it.
