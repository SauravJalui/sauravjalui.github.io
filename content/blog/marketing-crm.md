---
title: 'The Most Ambitious Thing I Haven''t Built Yet'
date: 2026-07-23
authors:
  - name: Saurav Jalui
    link: https://github.com/sauravjalui
    image: https://github.com/sauravjalui.png
tags:
  - Design Note
  - Product Strategy
  - Internal Tools
category: 'Design Notes'
excludeSearch: false
images:
  - /images/post-crm.webp
---

{{< hextra/hero-badge >}}Design Note · Before the Build{{< /hextra/hero-badge >}}

Everything our marketing team knows about a prospective student lives in someone's phone. A parent enquires through the website, someone WhatsApps them, a trial gets scheduled in a message thread, the student either turns up or doesn't, and somewhere in that chain the only record of what happened is a coordinator's memory. We know how many leads arrive. We are much fuzzier on where they die.

So I've spent the last stretch designing a marketing portal to sit inside the platform we already run — lead capture, pipeline stages, WhatsApp at each stage, tasks, campaigns, reporting. **None of it is built.** What exists is a clickable prototype and a five-sprint plan, and I'm writing this before a line of production code on purpose. More on why at the end.

## Why not just buy a CRM

This was the first question, and it deserved more than the answer I wanted to give.

Plenty of CRMs do pipelines and messaging better than anything I'd build in five sprints. HubSpot, Zoho, LeadSquared — all of them are more mature than what I've drawn, and buying one would have been faster. The honest case for buying is strong, and I want to state it properly rather than knock down a strawman.

The case for building comes down to one thing: **a bought CRM doesn't know our students.** It sits outside the platform, so it sees a phone number and a form submission. It cannot tell you that the lead you're about to send a cold SAT welcome to is already enrolled in your IBDP course, or that their sibling took a trial in March, or that the tutor they're being pitched is the one who taught them last year. That context is already in our database. Getting it into an external CRM means building and maintaining a sync, and a sync is a thing that breaks quietly.

In the prototype, this shows up as an unglamorous detail: a small **STUDENT** badge on leads who already exist in the portal. It's the whole argument in one label. Same student records, same teacher records, same admins, same permissions model — the one we already fought for during the migration off spreadsheets. Nobody needs a second login or a second set of roles.

If that badge turns out not to matter, the build-versus-buy call was wrong. I'd rather write that sentence now than defend it later.

## Making "WhatsApp Sent" a stage

The pipeline has six stages: lead captured, WhatsApp sent, trial scheduled, trial taken, feedback collected, enrolled or nurture.

Most CRMs wouldn't make the second one a stage. Sending a message is an *activity* — something you log against a lead, not a place the lead sits. Modelling it as a stage is arguably wrong.

I did it anyway, because of what it forces the funnel to measure. If "WhatsApp sent" is just an activity, the funnel tracks how prospects behave. If it's a stage, the funnel also tracks **how fast we respond** — and a lead sitting in "captured" for two days becomes visibly our failure rather than an unremarkable row in a list. Most of our leakage, I suspect, isn't people saying no. It's people not being contacted while they still cared.

Messages are mapped to stages automatically, and branch on exam type: an SAT lead gets a different welcome from an IBDP lead. Eighteen templates covering welcomes, tips, trial invitations, demo confirmations and reminders, post-demo follow-up, enrollment, cross-sell, re-engagement, deadline nudges, new batches, and festival greetings.

![The six-stage pipeline, with leads grouped by stage](/images/crm-pipeline.webp)

## The part that nags you

The last internal tool I worked on taught me an expensive lesson: adoption is a trust problem, and a tool that arrives as something done *to* people gets rejected no matter how fast it is.

So the feature I care most about isn't the pipeline. It's the task queue — the tab that tells a coordinator what's gone wrong: leads with no WhatsApp after 24 hours, demos that finished with no follow-up, anything stale for a week or more. A database waits to be searched. This is supposed to interrupt you.

![The task queue: overdue follow-ups, stale leads, missed post-demo contact](/images/crm-tasks.webp)

That's the difference between a system of record and a system that does work, and it's the thing I'd protect if scope has to be cut. Alongside it sit two guardrails that exist purely because messaging at volume goes wrong in predictable ways: duplicate detection when logging a call, and a spam-health warning when someone is about to bulk-send to a segment that's heard from us too recently.

## Sequencing is the strategy again

Five sprints: core pipeline, then WhatsApp and bulk send, then trial and enrollment, then tasks and campaigns, then reports and calendar.

The constraint I set was that every sprint has to leave behind something usable on its own. Sprint 1 with nothing after it is still a shared lead list with stages, which beats a phone. Sprint 2 makes the messaging real. Nothing depends on sprint 5 existing.

This isn't a project-management preference, it's the same lesson as the spreadsheet migration: what determines whether a rollout works is the order you do it in and how much people can trust each step. If the first thing the team touches is half a product that only makes sense once all five sprints land, I've already lost them.

## What the prototype gets wrong

There is no consent model in it. Not a weak one — none.

Leads get messaged automatically on stage transition, and there is no opt-in captured, no unsubscribe path, and no record of who asked us to stop. WhatsApp's own rules require opt-in for template messages, and under the DPDP Act this isn't a formality. I built an automation engine and forgot to build the brakes, which is a fairly damning thing to notice about your own design, and exactly the kind of omission that's cheap to fix now and expensive after the first complaint.

It goes into sprint 1. Not sprint 5.

## What I think will happen

Here's the part I'd normally leave out. Predictions, on record, before the build:

- **The biggest leak is trial scheduled → trial taken.** Not enquiry-to-contact, which is where everyone assumes the problem is. People book and then don't turn up.
- **The task queue gets used more than the reports.** Reporting is what gets asked for in meetings; the overdue list is what people open on a Tuesday morning.
- **Automated messages will out-perform manual ones on speed and under-perform on replies.** Faster, and slightly more ignorable.
- **The STUDENT badge will matter more than I can currently justify** — mostly by preventing embarrassment rather than by creating revenue, which makes it hard to measure and easy to cut.
- **Something in sprints 4–5 won't survive contact with the team.** I don't know which. Campaign tracking is my guess.

## Why publish this now

Because a plan you wrote down can be wrong in a way you can check, and a plan you kept in your head gets quietly edited to match whatever happened.

Once this ships, I'll come back and grade every prediction above. That's the actual point of putting it up before the build — not to look decisive, but to make the follow-up honest. If I'm wrong about most of it, that's a more useful post than the one where I explain how it all went according to plan.
