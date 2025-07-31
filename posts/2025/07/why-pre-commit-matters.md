---
title: Why pre-commit matters
date: 2025-07-31
tags:
  - DevEx
  - pre-commit
---

# Why pre-commit matters

As you may know, I’ve been at Block for about six months now.

During this time, I’ve learned a lot about the company and our team’s infrastructure.

But one thing that surprised me the most is that many of the repos we commonly use don’t have pre-commit hooks set up, and there’s quite a bit of inconsistency in the developer experience (DevEx) from repo to repo.

Coming from my first startup job, I was already used to leveraging pre-commit hooks to streamline my workflow.

Over time, I’ve made it a habit to spend my own time updating and maintaining these hooks to keep them relevant and effective.

Why do I do this? Simply because I’m lazy — I don’t want to waste my time or others’ on repetitive formatting comments during code reviews.

Let’s be honest, nobody enjoys nitpicks about spacing or semicolons, yet these small issues often become huge distractions that slow down development and impact morale.

Pre-commit hooks serve as an automated gatekeeper.

They catch common errors early, enforce formatting standards, and prevent broken code from slipping into the main branch.

This automation frees up mental space for developers to focus on logic, architecture, and meaningful discussions rather than trivial style debates.

In my experience, having these checks in place leads to smoother pull requests, faster reviews, and ultimately, a more efficient development cycle.

---

## The simplest way to set up pre-commit

One practical question I often get is: **How hard is it to set up pre-commit hooks?**

The good news is — it’s usually very straightforward. Most projects use the [pre-commit](https://pre-commit.com/) framework, which makes installing and managing hooks easy and consistent across different languages and tools.

Here’s a quick example of how to get started:

1. **Install pre-commit** (using pip for Python projects, but it works for many languages):

   ```bash
   pip install pre-commit
   ```

2. Add a `.pre-commit-config.yaml` file to your repo root with the hooks you want. For example:

    ```yaml
    repos:
      - repo: https://github.com/pre-commit/pre-commit-hooks
        rev: v4.3.0
        hooks:
          - id: trailing-whitespace
          - id: end-of-file-fixer
          - id: check-yaml
    ```

3. Install the git hook scripts:

    ```bash
      pre-commit install
    ```

From now on, every time you run `git commit`, the hooks will automatically check for common issues before the commit is finalized.

This saves time during reviews and helps keep the codebase clean.

You can customize the hooks with linters or formatters for your language or team. The key is to start simple and improve over time.

When I join a new team, improving developer experience (DevEx) is often my first priority. It may seem minor compared to feature work, but it pays off greatly in the long run. I’m aware of my own preferences on some rules, but I believe a bad rule is better than no rule—without any, chaos and inconsistencies grow.

Integrating pre-commit hooks with a CI pipeline sets a clear baseline. Everyone knows what to expect, which reduces confusion and encourages ownership of code quality from the start.

No rules fit everyone perfectly, so I encourage open feedback channels—RFCs, meetings, or PRs—to suggest improvements. The goal is continuous improvement and shared understanding.

Without pre-commit hooks, I’ve seen painful merge conflicts, slow reviews, and low morale. These issues directly hurt productivity.

In short, pre-commit hooks are a small investment with big returns in code quality, developer happiness, and speed. They show respect for each other’s time and the craft of engineering.

To promote pre-commit hooks team-wide, pair them with a CI pipeline like GitHub Actions.

Start by making CI checks optional so your team can adjust, then require them once everyone sees the benefits.

This gradual approach builds buy-in and eases adoption.
