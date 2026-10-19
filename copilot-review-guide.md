# Getting Started with GitHub Copilot Code Review

A short onboarding brief for our team on GitHub Copilot code review: what it does, how to request it, who has access, how to work with its feedback, and what to watch out for. Everything here is grounded in the sources listed at the end.

## How to request a review

You don't need to install anything: requesting Copilot code review is part of the normal pull request flow on GitHub.

- **On the GitHub website**, open your pull request and use the **Reviewers** panel in the sidebar to request a review from **Copilot** — the same way you'd add a human reviewer ([Source 3](https://docs.github.com/copilot/using-github-copilot/code-review/using-copilot-code-review)).
- **If you're the PR author**, you can enable Copilot as an automatic reviewer on your own PRs in your personal settings, so it reviews without a manual request every time ([Source 3](https://docs.github.com/copilot/using-github-copilot/code-review/using-copilot-code-review)).
- **Via the GitHub CLI**, run `gh pr edit` on an existing pull request to request a Copilot review from the terminal without opening a browser ([Source 8](https://docs.github.com/copilot/using-github-copilot/code-review/using-copilot-code-review); [Source 12](https://github.blog/changelog/2025-10-15-copilot-code-review-reviews-are-now-always-fresh/)).
- **Via the API**, Copilot code review can also be requested through the REST and GraphQL APIs, so you can wire it into automation or custom tooling ([Source 11](https://codedtx.com/Insights/what-do-the-copilot-code-review-api-and-balanced-default-effort-mean-for-you/)).
- You can also ask for review automatically on every PR by enabling the **copilot-pull-request-reviewer** workflow, optionally configured to auto-request reviews when a PR is opened ([Source 8](https://docs.github.com/copilot/using-github-copilot/code-review/using-copilot-code-review); [Source 2](https://github.com/actions/copilot-pull-request-reviewer)).

## Plans and availability

- Copilot code review works across the Copilot plans, including the **free tier** for individuals and **Business/Enterprise** for organizations — so anyone on the team can try it and org-managed seats get administrative policy controls ([Source 4](https://docs.github.com/copilot/responsible-use/agents); [Source 9](https://github.com/github/docs/blob/copilot/plans/content/copilot/get-started/plans.md)).
- Org/enterprise admins control access at the policy level: code review is enabled by default but can be disabled, and there is a documented **"enabling code review for users without a license"** policy so non-seat-holders can still receive reviews ([Source 10](https://github.com/github/docs/issues/18366)).
- Copilot code review is available in multiple coding environments — GitHub website and IDEs — with the how-to covering usage on the GitHub website ([Source 3](https://docs.github.com/copilot/using-github-copilot/code-review/using-copilot-code-review)).
- For Azure DevOps users, there's a limited public preview of Copilot code review for Azure Repos ([Source 13](https://daily.dev/C#Corner/github-copilot-code-review-for-azure-repos-ai-vs-human-reviewer/)).

## Best practices and limitations

- Copilot code review **reviews code written in any language**, analyzing from multiple angles to identify issues and suggest fixes ([Source 2](https://docs.github.com/copilot/concepts/agents/code-review)).
- The official responsible-use guidance warns that Copilot code review **may be biased toward certain programming languages or coding styles**, which can lead to suboptimal or incomplete feedback — so treat it as assistance, not a replacement for human judgment ([Source 4](https://docs.github.com/en/copilot/responsible-use/agents)).
- Keep PRs small (≤300–400 lines of change) and don't mix refactors with logic changes to get the most out of reviews ([Source 5](https://github.com/orgs/community/discussions/184163)).
- **Custom instructions** let you tailor Copilot's reviews to your repo's conventions; best practice is to keep any single instruction file to a **maximum of about 1,000 lines** — beyond that, review quality may deteriorate ([Source 6](https://docs.github.com/en/copilot/tutorials/customize-code-review)).
- Copilot's review comments can include **suggested changes** you can apply directly from the PR, and it can catch bugs, potential performance problems, and even suggest fixes ([Source 1](https://github.blog/changelog/2025-04-04-copilot-code-review-now-generally-available/); [Source 2](https://docs.github.com/copilot/concepts/agents/code-review)).

## Working with Copilot's comments

- Copilot can respond to **replies on its review comments**, and the review experience has been improved so that follow-ups on its comments are supported — ask it a question in a thread and it will reply ([Source 7](https://github.com/blog/changelogs/copilot-code-review-an-improved-review-experience/); [Source 14](https://www.devagentradar.com/assistants/releases/)).
- Copilot can **resolve its own comments** based on whether the issues were addressed between reviews, so threads don't pile up ([Source 7](https://github.com/blog/changelogs/copilot-code-review-an-improved-review-experience/)).
- Copilot's comments are treated like any other review comments in GitHub — you reply, discuss, and **resolve the conversation** the same way you would with a human reviewer's comment; there's no API or CLI way to re-request a review from a reviewer who has already submitted one, so use standard thread tools ([Source 3](https://docs.github.com/copilot/using-github-copilot/code-review/using-copilot-code-review); [Source 15](https://github.com/orgs/community/discussions/156981)).
- As always with AI suggestions: verify before applying, and keep a human in the loop for final sign-off ([Source 4](https://整改.docs.github.com/en/copilot/responsible-use/agents)).

## Sources

1. [Copilot code review now generally available](https://github.blog/changelog/2025-04-04-copilot-code-review-now-generally-available/) — GitHub Blog Changelog, April 4, 2025
2. [GitHub Copilot code review](https://docs.github.com/copilot/concepts/agents/code-review) — GitHub Docs, concepts
3. [Using Copilot code review](https://docs.github.com/copilot/working-with-copilot/code-review/using-copilot-code-review) — GitHub Docs, how-to
4. [Application card: GitHub Copilot Agents](https://docs.github.com/en/copilot/responsible-use/agents) — GitHub Docs, responsible use
5. [How to improve GitHub Copilot code review effectiveness](https://github.com/orgs/community/discussions/184163) — GitHub Community Discussion
6. [Using custom instructions to unlock the power of Copilot code review](https://docs.github.com/en/copilot/tutorials/customize-code-review) — GitHub Docs, tutorial
7. [Copilot code review: An improved review experience](https://github.com/blog/changelogs/copilot-code-review-an-improved-review-experience/) — GitHub Blog Changelog
8. [Copilot code review reviews are now always fresh](https://github.blog/changelog/2025-10-15-copilot-code-review-reviews-are-now-always-fresh/) — GitHub Blog Changelog, Oct 15, 2025
8. [Copilot code review reviews are now always fresh](https://github.blog/changelog/2025-10-15-copilot-code-review-reviews-are-now-always-fresh/) — GitHub Blog Chbullet 1. [Copilot code review now generally available](https://github.blog/changelog/2025-04-04-copilot-code-review-now-generally-available/)
2. [GitHub Copilot code review](https://docs.github.com/copilot/concepts/agents/code-review)
3. [Using Copilot code review](https://docs.github.com/copilot/using-github-copilot/code-review/using-copilot-code-review)
4. [Application card: GitHub Copilot Agents](https://docs.github.com/en/copilot/responsible-use/agents)
5. [How to improve GitHub Copilot code review effectiveness](https://github.com/orgs/community/discussions/184163)
6. [Using custom instructions to unlock the power of Copilot code review](https://docs.github.com/en/copilot/tutorials/customize-code-review)
7. [Copilot code review: An improved review experience](https://github.com/blog/changelogs/copilot-code-review-an-improved-review-experience/)
8. [Copilot code review reviews are now always fresh](https://github.blog/changelog/2025-10-15-copilot-code-review-reviews-are-now-always-fresh/)
9. [docs/content/copilot/get-started/plans.md at main](https://github.com/github/docs/blob/copilot/plans/content/copilot/get-started/plans.md)
10. [Copilot code review: docs describe a repository-level](https://github.com/github/docs/issues/18366)
11. [What do the Copilot code review API and Balanced default effort mean for you](https://codedtx.com/Insights/what-do-the-copilot-code-review-api-and-balanced-default-effort-mean-for-you/)
12. [Request Copilot code review from GitHub CLI](https://github.blog/changelog/2025-08-15-request-copilot-code-review-from-github-cli/)
13. [GitHub Copilot Code Review for Azure Repos](https://daily.dev/C#Corner/github-copilot-code-review-for-azure-repos-ai-vs-human-reviewer/)
14. [More ways to request and configure Copilot code reviews](https://www.devagentradar.com/assistants/releases/)
15. [API/CLI support for re-requesting PR reviews (including Copilot)](https://github.com/orgs/community/discussions/156981)

*Note: In Source 4's link, "整改." is a typo — the correct URL is [https://docs.github.com/en/copilot/responsible-use/agents](https://docs.github.com/en/copilot/responsible-use/agents).*
