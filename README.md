# execution-closer

A lightweight Agent Skill for turning stalled projects into verified progress.

Inspect what's actually there. Close the nearest meaningful loop toward the goal. Verify it.

Agents can produce another plan, summary, or TODO list when the useful next step is already in the project. This instruction-only skill steers execution toward that step, with a short account of what changed and what was checked.

## When to use it

Use it to resume unfinished project work, implement an established plan, or finish an existing feature or analysis. A requested audit package, research report, or manuscript revision can itself be the deliverable.

Do not use it to decide whether a project is worth continuing, brainstorm directions, compare options, prioritize a backlog, explain code, or request only a plan or summary.

## Install and invoke

This skill uses the open [Agent Skills format](https://agentskills.io/specification). The format does not mandate a discovery path: `.agents/skills/` is a [cross-client convention](https://agentskills.io/client-implementation/adding-skills-support), not a location every host necessarily supports. Follow your host's documentation.

For Codex specifically, the [current official documentation](https://learn.chatgpt.com/docs/build-skills) lists `$HOME/.agents/skills` for user skills and `.agents/skills` within the project directory hierarchy for repository skills. For a fresh user-level Codex installation, run from this repository checkout:

```sh
mkdir -p "$HOME/.agents/skills/execution-closer"
cp SKILL.md "$HOME/.agents/skills/execution-closer/SKILL.md"
```

If already installed, review the existing file before replacing it. The skill requires only `SKILL.md`; no scripts, service, or credentials are needed. Other compatible agents should use their own supported skill location.

```text
Use $execution-closer to finish the existing export feature.
The acceptance criteria and unfinished implementation are already in the repo.
```

Codex can also select it from its description when a request asks to resume or finish existing work. Automatic selection is host/model dependent; use explicit invocation when desired. See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills).

## Compatibility

Execution Closer follows the open Agent Skills `SKILL.md` format. Its instructions contain no Codex-specific tools, hooks, or runtime dependencies.

- **Currently tested:** Codex.
- **Format-compatible, not tested here:** [Claude Code](https://code.claude.com/docs/en/skills) and other agents implementing the Agent Skills format.

Installation paths and automatic skill invocation may vary by host. Equivalent behavior across hosts has not been verified.

## Before / after

Illustrative, not a measured comparison:

> Before: “I'll write a new status document and implementation plan.”

> Materially changed: Fixed the existing export's empty-input handling.  
> Verified: Focused check and regression suite passed.  
> Attention / Blocked: None.  
> Next action: None; the requested fix is complete.

## Observed uses

Anonymized response excerpts reported these outcomes; the underlying project runs were not independently reproduced:

- **Scientific analysis:** Completed a pending calculation and reported an independent check while leaving interpretation open.
- **Data preparation:** Prepared collection and validation tools while the required remote inputs remained unavailable.
- **Game development:** Completed a scoped change and regression checks, with an external submission step still pending.
- **Software audit:** Delivered the requested review package and distinguished static checks from unperformed device validation.

See [examples/use-cases.md](examples/use-cases.md) for the evidence boundaries. Original screenshots and identifying details are excluded.

## Design and limits

Inspect reality first; reuse existing decisions; advance the main objective; verify before building further; stay within scope. Avoid extra status documents, not documents the user actually requested. Preparation should be named as preparation.

This skill cannot supply missing data, credentials, permissions, domain judgment, or a test device. It does not authorize publication, external changes, or broader work. Verification quality depends on the available checks; a reported check is not proof of scientific validity or real-world behavior.

## Evaluation

[evals/cases.md](evals/cases.md) contains 18 small routing and behavior cases, including negative controls. Review description matching separately from actual execution. Use isolated fixtures and judge observable changes and checks, not exact response wording. Semantic review is not a host auto-routing benchmark, and small fixture runs do not establish a general productivity improvement.

## License

[MIT](LICENSE).
