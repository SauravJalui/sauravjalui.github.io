---
title: 'The Tool Was Faster. They Still Wanted the Spreadsheet Back.'
date: 2026-07-18
authors:
  - name: Saurav Jalui
    link: https://github.com/sauravjalui
    image: https://github.com/sauravjalui.png
tags:
  - Case Study
  - Product Strategy
  - Internal Tools
category: 'Case Studies'
excludeSearch: false
images:
  - /images/post-scheduling.webp
---

We spent a long time building a scheduling portal to kill the spreadsheets it replaced — thousands of students, hundreds of teachers, a shared pool of video links, all of it held together in Sheets and WhatsApp until the whole thing started tearing at the seams. The portal was, by every measure I cared about, better. Booking a year of recurring classes went from copying a weekly sheet dozens of times to a single click.

![The old scheduling spreadsheet — colour-coded by hand, full of strikethroughs and pasted links, past its breaking point (names blurred).](/images/sheet-before.webp)

And the team still wanted the spreadsheet back.

![What replaced it — a portal with structured classes, teacher availability, and status at a glance (names blurred).](/images/portal-after.webp)

I sat with that for a while, because it didn't make sense on paper. The tool was faster. People hated it anyway. That gap — _faster, and still rejected_ — turned out to be the whole story, and unlearning my first instinct about it was the most useful thing I did on this project.

## It wasn't the tool

My first instinct, of course, was that we'd built it wrong. More polish, fewer bugs, better UX — the usual reflexes. And there was real breakage to fix, so that wasn't nothing. But it wasn't the thing.

The thing was upstream of the code entirely. Features were landing in the portal because _management_ wanted them, not because the people scheduling all day needed them — and they'd show up with no warning, no training, no one asking the team first. So every release, even the good ones, made the tool feel a little more like something being done _to_ them rather than something built _for_ them. The portal wasn't failing on what it could do. It was failing on trust. And you can't patch trust with a sprint.

## The problem was trust, not speed

That reframe changed what the actual work was. If the problem is speed, you optimize code. Because the problem was trust, the work was about _who gets to decide what ships_ — which is a governance problem wearing a technical costume, and a much less fun one to fix because it means telling powerful people no.

## What actually moved the needle

A few decisions did most of the lifting.

The first was just naming who the tool is actually for. Internal tools have a pile of roles — coordinators, managers, teachers, everyone — and when their needs collide, somebody has to win. So I said it plainly: the coordinators living in this thing all day are the primary user. Everyone else is secondary. And management is a _stakeholder, not a user_ — they don't operate the tool, so their requests don't get to walk straight into it. Writing that sentence down was uncomfortable and clarifying in equal measure.

From there came the rule I'm proudest of: requests from the people who use the tool are needs; requests from management are good-to-haves. A good-to-have only ships after the people it affects sign off, and only when nothing they actually need is still waiting. It's a small rule that deliberately makes someone senior wait their turn — which is exactly the point, and exactly why it was hard to hold.

The last piece was figuring out how we'd even know if it worked, and this is where I almost fooled myself. Usage was mandatory, so every usage metric was a lie — logins looked great because nobody had a choice. What I actually needed to measure was whether people would _leave if they could_. So: an anonymous monthly pulse, anonymous being non-negotiable, because a team that's nervous will tell a survey with their name on it whatever they think management wants to hear. And alongside it, just watching people work — because you can't intimidate someone's behavior into politeness the way you can a feedback form.

## The sentence I didn't want to write

The part I'm most sure about is the part that was hardest to write: the line where I said, out loud, that if we stabilized and polished the thing and people _still_ wanted the spreadsheet — then scheduling should go back to the spreadsheet, and the portal should keep only what a spreadsheet genuinely can't do. That's a deeply uncomfortable sentence to put in a memo about a tool you helped build. It's also the only thing that made the rest of the plan believable, because it proved I was trying to fix the _problem_ and not defend the _tool_.

## What I'd carry into the next one

If there's one thing I took from this that outlives this one project, it's that adoption is a trust problem far more often than a capability problem — and when you force people to use something, you lose the only honest signal you had. You stop being able to tell whether they're using it because it's good or because they can't escape. And at that point the most valuable thing you can build isn't another feature. It's a way to find out whether they'd stay if you opened the door.
