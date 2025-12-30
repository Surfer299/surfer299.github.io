---
title: TFVC to Git Migration - How Did It Go?
date: 2025-12-30 12:36:00 -0500
categories: [DevOps, Migration]
tags: [git, tfvc, azure-devops, migration]
---

Before the year ends, I want to share something I'm most proud of right now 🥁 — leading the migration of our TFVC repositories to Git.

It was daunting at first, but I learned a lot along the way. Below are a few key lessons from the experience.

## The Actual Migration (TFVC → Git)

To me, the actual migration—converting TFVC repositories to Git—wasn't that bad. There is a tool that makes this process fairly straightforward.

The tool that did the heavy-lifting was [git-tfs](https://github.com/git-tfs/git-tfs), which allows you to clone a TFVC repository into a Git repository while preserving history. The tool is pretty straightforward and you can learn to use it by following its documentation.

One thing to note: you'll want to be comfortable with Git fundamentals before diving into this. Understanding branching, merging, and basic Git workflows will make the migration much smoother.

What took the most time wasn't the conversion itself, but the *ceremonies* around making sure Git version control worked well for the team.

## Cleaning Up with `.gitignore`

Making sure irrelevant files are not checked in is one of the first tasks to complete.

Using the .NET CLI made this easy. The following command generates a `.gitignore` file tailored for .NET projects:
```bash
dotnet new gitignore
```

It added a .NET-specific .gitignore template, which removed the overhead of figuring out which files to ignore.

Depending on your solution structure, you may still need to tweak the file, but it's a great starting point.

## Moving to YAML Pipelines

The next step was replacing our classic build pipelines with YAML pipelines, along with updating certain steps in the release pipelines.

YAML pipelines are great, although the indentation rules and specificities still annoy me 😄. That said, they come with solid benefits:
- CI as code
- Easier pipeline versioning
- Lower cost when creating new build pipelines for new branches

## Picking a Git Branching Strategy

Choosing a branching strategy is important, but honestly, pick what works for your team.

In my case, I decided to keep the same branching strategy we used in TFVC, which helped make the transition smoother. No need to change everything at once.

## Final Thoughts

Overall, it was a great learning experience and very rewarding to complete.

One of the most satisfying migrations I've worked on so far.

Until next time!
