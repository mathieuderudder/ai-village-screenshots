# Screenshots

Real Playwright screenshots against a running `npm run dev` (MockProvider,
local SQLite) — not mockups. Referenced from `BUILD_STATUS.md`.

## Session 1 — first vertical slice

- `01-village-overview.png` — village view: departments as buildings,
  agents as residents, colored by real `Agent.status`.
- `02-dashboard-task.png` — dashboard after creating a task; Head Agent
  delegated it and it completed.
- `03-task-detail.png` — task detail: full event timeline + stored result.
- `04-agent-panel.png` — clicking an agent opens its profile/activity panel
  (Head Agent's own event log, since it acknowledges every result).

## Session 2 — tools, Business/Content/Investment, memory, department panel

- `05-dashboard-all-roles.png` — five tasks created via the specialist
  selector (business/content/investment/development + the automatic QA
  review subtask), all completed.
- `06-business-district-panel.png` — clicking the Business District
  building opens its department panel showing a real, persisted
  `Opportunity` record with a status-advance control.
- `07-investment-office-panel.png` — same for Investment Office: a real
  `InvestmentProposal`, explicitly labeled as advice/research only.
- `08-devtask-tool-usage.png` — a `development_agent` task result; its
  event log (scroll down in the app) shows the real `list_project_files`
  tool call made before generating this result.

## Session 3 — direct agent chat (Takenbord T001), real dev vertical slice (T003)

- `09-agent-chat.png` — clicking a resident opens their panel's new Chat
  section: a live conversation with that agent via `/api/agents/:id/messages`,
  showing a real, role-flavored MockProvider reply persisted through the
  existing Message table.
- `10-devtask-real-fix.png` — a `development_agent` task against the real
  `demo-app` project: the event log shows the genuine tool chain
  (`list_project_files` → `read_project_file` → `write_project_file` →
  `run_project_tests`) that found, fixed, and verified the seeded bug —
  not just a file listing.
