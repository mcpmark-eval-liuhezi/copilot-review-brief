# GitHub Copilot Code Review: Team Onboarding Guide

GitHub Copilot code review lets a Copilot agent review your pull requests, flag issues, and suggest fixes you can apply in a couple of clicks. It became generally available in April 2025 [7] and now runs inside the normal pull request flow — no extra tooling to install. This one-page guide covers how to request it, who can use it, how to work with its feedback, and its known limitations.

## How to request a review

- **On the GitHub website (default flow):** open or create a pull request, then under **Reviewers** in the right sidebar, click **Request** next to Copilot. A review usually takes less than 30 seconds; read Copilot's comments in the conversation once it's done. [2]
- **Via the REST API:** request `copilot-pull-request-reviewer[bot]` as a reviewer on the pull request, using the REST endpoint for requesting reviewers for a pull request. [2]
- **From the GitHub CLI:** code review is supported in the GitHub CLI, and the docs describe using `gh pr edit` on an existing pull request to request a Copilot review without leaving the terminal. [2]
- **Automatically on every PR:** instead of requesting manually each time, enable automatic code review for the repository so Copilot reviews all pull requests (once they're out of draft mode). [2] [6]
- **Re-review after changes:** Copilot won't automatically re-review after you push. Click the re-request (sync) button next to Copilot's name in the **Reviewers** menu, or enable **Review new pushes** in the ruleset settings when automatic review is on. [2]

## Plans and availability

- Code review is **available for all paid GitHub Copilot plans** — Copilot Pro, Pro+, Max, Business, and Enterprise. The free Copilot plan only includes limited feature access. [1] [3]
- It's supported across environments: GitHub.com, GitHub CLI, GitHub Mobile, VS Code, Visual Studio, Xcode, JetBrains IDEs, and Azure DevOps (public preview). [1]
- If you receive Copilot through an organization, an organization or enterprise owner must enable the **Copilot code review** option in the Copilot policy settings. [1]
- **Members without a Copilot license** can still use code review on GitHub.com, but only on Copilot Business or Enterprise plans, and only after an admin first enables AI credits paid usage and then the "allow members without a license" policy. It's not available in IDEs for users without a license. [1]
- Each review consumes **AI credits**. [4]

## Best practices and limitations

- Copilot reviews code in **any language**, from multiple angles, to identify issues and suggest fixes — treat it as a first pass, not a final gate. [1]
- By default it leaves a **"Comment" review**, not "Approve" or "Request changes", so by default its reviews don't count toward required approvals (approving reviews are possible only when explicitly configured). [2]
- **Custom instructions** (`copilot-instructions.md`, path-specific `*.instructions.md`) tailor reviews to your conventions. Keep each instruction file to a **maximum of about 1,000 lines**, use distinct headings, bullet points, and short directives — very long files may be partially overlooked. [5]
- GitHub's responsible-use guidance warns that Copilot code review **may be biased toward certain programming languages or coding styles**, and that hallucinations can produce feedback about problems that don't exist. Always carefully review suggestions before accepting and committing them. [4] [6]
- Keep PRs small (roughly ≤300–400 lines of change) and don't mix refactors with logic changes — focused diffs get much better reviews. [8]
- If GitHub Actions is unavailable or the review workflows fail, reviews are still generated, but without the agentic extras such as full-project context gathering. [1]

## Working with Copilot's comments

- Copilot's review comments **behave like review comments from humans**: you can add reactions, comment, resolve, and hide them. Each comment is labeled **High, Medium, or Low** severity to help you prioritize. [2]
- Comments you add to Copilot's review comments are visible to humans but **not to Copilot — it won't reply** to follow-ups. Use thread replies for team discussion, not for asking Copilot questions. [2]
- Where possible, its feedback includes **suggested changes you can apply with a couple of clicks** — accept a single suggestion and commit it, or accept a group of suggestions together in one commit. [2]
- To have Copilot implement its own feedback, click **"Fix with Copilot"** on one of its review comments: this hands the suggestion to the Copilot cloud agent (public preview), which can open a new PR or commit the fix to the same branch. [1] [2]
- After addressing feedback — or deciding it doesn't apply — resolve the thread the same way you would with a human reviewer, then re-request a review once you've pushed your fixes. [2]

## Sources

1. GitHub Copilot code review — GitHub Docs (concepts): https://docs.github.com/copilot/concepts/agent-capabilities/agent-powered-workflows-and-operations/code-review
2. Using GitHub Copilot code review — GitHub Docs (how-to): https://docs.github.com/copilot/how-tos/use-copilot-agents/use-code-review
3. Plans for GitHub Copilot — GitHub Docs: https://docs.github.com/copilot/get-started/plans
4. Application card: GitHub Copilot Agents — GitHub Docs (responsible use): https://docs.github.com/copilot/responsible-use/agents
5. Using custom instructions to unlock the power of Copilot code review — GitHub Docs (tutorial): https://docs.github.com/copilot/tutorials/customize-code-review
6. Build an optimized review process with GitHub Copilot — GitHub Docs (tutorial): https://docs.github.com/copilot/tutorials/optimize-code-reviews
7. Copilot code review now generally available — GitHub Blog changelog, April 4, 2025: https://github.blog/changelog/2025-04-04-copilot-code-review-now-generally-available/
8. How to improve GitHub Copilot code review effectiveness — GitHub Community discussion: https://github.com/orgs/community/discussions/184163
