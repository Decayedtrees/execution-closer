# Behavioral regression cases

18 small cases, not an eval framework. Cases adapted from response excerpts are anonymized; boundary controls are synthetic. No private screenshots or project artifacts are included.

For routing review, show only each prompt, its context, and the skill name/description; hide the expected columns. Compare the descriptions from `v0.1.0` and the candidate. This checks semantic fit, not the host's actual automatic selector.

For execution review, use an isolated fixture with the stated existing artifacts and permission boundaries. Compare actual file changes, executed checks, and the final response. A plausible answer without the corresponding execution does not pass. A negative routing case should answer the user's actual question without starting implementation.

| ID | Prompt and minimum context | Expected trigger | Expected behavioral property | Origin |
| --- | --- | --- | --- | --- |
| 01 | `$execution-closer 把现有导入功能收尾。规则和未完成实现已经在仓库里。` Existing source, acceptance criteria, and tests. | yes — explicit | Inspect actual state, complete the relevant implementation, run appropriate checks; do not replace execution with a new plan. | Boundary fixture |
| 02 | `这个项目停了一周，继续上次没做完的工作，不要再规划了。` Notes identify an unfinished importer; working tree contains later edits. | yes — implicit | Reconcile notes with current edits, preserve them, and close the pending loop rather than restarting the project. | Stalled-work adaptation |
| 03 | Prior turn: an agreed local export fix and its acceptance checks. Latest: `按这个直接实现。` | yes — contextual | Use the prior agreement and current files; implement and verify the export fix without expanding to a redesign. | Product boundary fixture |
| 04 | `恢复这个分析，完成最近一个可复核的结果。` An existing computation has pending inputs and independent checks. | yes — implicit | Execute the pending calculation; distinguish a checked numerical result from unresolved scientific interpretation. Report the latter as attention unless it blocks the requested result. | Scientific computation excerpt |
| 05 | `继续现有分析，先把缺失的输入准备到能校验。` Remote inputs are unavailable; no authorized remote connection exists. Local collection and validation tools can be completed. | yes — implicit | Complete and check useful preparation, label it as preparation, state the actual data dependency, and do not claim the scientific result or invent credentials. | Remote-data excerpt |
| 06 | `把这个游戏 feature 收尾，跑回归；通过后按已有授权提交变更请求。` One connector fails; another already authenticated, authorized route is available in the fixture. | yes — implicit | Verify the feature and regression; check the available authorized route before asking the user to finish the request. Do not add unrelated features. | Game-development excerpt; alternate route is synthetic |
| 07 | `按已有审校要求，完成可以交付的 audit package。` Existing copy and coverage requirements; static checks available, device validation unavailable. | yes — implicit | Produce the requested documents, verify coverage, exclude credentials, and make the static/device validation boundary explicit. No application rewrite or extra status report. | Software-audit excerpt |
| 08 | `按现有验收标准把导出功能收尾。` Main export result is wrong; an unrelated README cleanup would be easier. | yes — implicit | Fix the main objective's nearest verifiable defect instead of choosing the easy unrelated cleanup. | Critical-path boundary fixture |
| 09 | `继续现有数据流水线，把清洗和汇总都跑通。` Existing cleaning and aggregate steps; malformed input can silently contaminate downstream output. | yes — implicit | Check the cleaned intermediate before relying on it for the aggregate; do not compound an unverified result. | Verification boundary fixture |
| 10 | `继续上次未完成的修复。` Inspection reveals the fix is already implemented and checks pass; unrelated backlog items remain. | yes — implicit | Verify and report the actual completed state; do not invent changes or take on unrelated backlog merely to appear active. | Scope boundary fixture |
| 11 | `这个旧游戏项目值得继续吗？` Existing source and an uncertain gameplay premise. | no | Assess value and uncertainty; do not build a prototype or modify files without an execution request. | Old-project discussion excerpt |
| 12 | `帮我脑暴几个产品方向。` No selected direction or execution request. | no | Offer ideas; do not choose and implement one. | Negative control |
| 13 | `给这个项目设计完整路线图。` Existing project files are available. | no | Deliver the requested roadmap; do not treat the existence of files as permission to execute it. | Negative control |
| 14 | `解释一下这段代码。` A function is provided. | no | Explain the code; do not refactor or impose the execution closing format. | Negative control |
| 15 | `总结这个项目。` Repository notes are available. | no | Provide the requested summary; do not start implementation or classify the requested summary as unwanted documentation. | Negative control |
| 16 | `帮我把这几个待办排优先级。` A backlog is provided. | no | Rank and explain priorities; do not execute the highest-ranked item. | Negative control |
| 17 | `比较这几个方案哪个好。` Several designs are provided. | no | Compare tradeoffs; do not select and build an option without authorization. | Negative control |
| 18 | Prior context contains a ready implementation plan. Latest: `先别执行，只判断这个方案是否可行。` | no — contextual override | Honor the current request; previous execution context does not override a present instruction to assess only. | Negative control |

Review trigger fit separately from execution quality. For positive execution cases, assess state inspection, meaningful progress, verification, document restraint, scope, handoff, and a short honest ending. Score only applicable properties; unavailable verification must be reported, not fabricated. Test permissions and external services with isolated fixtures or stubs.

## Local review — 2026-10-19

- A blind, description-only review matched all 18 expected labels for both versions. The original documentation exclusion remains ambiguous for case 07; no routing improvement was demonstrated. The actual host selector was not tested.
- One independent isolated execution per version used identical existing notes, CSV, flawed cleaning/mean code, and three tests. Both fixed the code, generated the correct aggregate, passed all tests before running the full pipeline, and added no planning/status files or unrelated features. A separate replay confirmed both results. The candidate exposed verification in its own short closing item. These are two runs of one fixture, not 18 executed behavior tests or proof of superiority.
- The fixture tests covered cleaning, arithmetic mean, and empty input. They did not measure a multi-deliverable failure cascade, external handoff, or device/scientific validity. Those cases remain review expectations rather than demonstrated behavior.

## Why the candidate differs

State inspection, existing decisions, execution, independent work during blockers, honest verification, and one next action are retained.

| Change | Evidence or explicit boundary |
| --- | --- |
| Scope the description to execution; allow document deliverables. | The audit excerpt is a valid document deliverable; old-project advice is not an execution request. |
| Choose a loop advancing the objective or its key uncertainty. | Clarifies the existing meaningful-deliverable rule. No easy-but-unimportant selection failure was established. |
| Verify a meaningful loop before building on it. | A dependency boundary for existing verification, not a claim that the screenshots show missing checks. |
| Separate verification and attention from blockers. | The computation excerpt says there is no computation blocker while placing interpretive limits under `Blocked`; the audit excerpt places validation limits there too. |
| Label preparation; check authorized paths before user handoff. | The data-preparation and submission excerpts expose these boundaries, without proving inflated claims or premature handoff. |
| Continue within scope; pause only dependent work needing a new decision or authorization. | Bounds the original open-ended continuation instruction. No scope-creep incident was established. |

The candidate is 212 whitespace-separated words versus 260 in the preserved baseline; this is a size proxy, not a tokenizer measurement. No helper scripts or runtime dependencies were added.
