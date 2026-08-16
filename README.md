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
- `11-village-selection.png` — clicking a building highlights it in the
  scene (blue border) and its `DepartmentPanel` now lists real residents
  with status, not just a count (Takenbord T004).
- `12-village-agent-from-dept.png` — clicking a resident inside that new
  department resident list opens their own `AgentPanel`, and the matching
  dot in the village scene is highlighted too.
- `13-knowledge-library.png` — the Knowledge Library department, previously
  always empty, now shows a real "Dorpskennis" section: a genuine
  village-scoped memory item written by an `improvement_agent` task,
  visible to (and recallable by) every other agent (Takenbord T005).

## Session 4 — PermissionEngine beyond tools (T008), money-making vertical
slice (T009), Business District ranking (T010), POWER BREAK-EVEN (T011)

- `14-power-break-even.png` — the Dashboard's new compact "POWER BREAK-EVEN"
  strip, backed by real `GET /api/power/summary` data: cumulative
  compute/electricity cost (€11.70, split measured/estimated) seeded via the
  real API for this screenshot, and — correctly — €0.00 realized revenue,
  since nothing in this MockProvider-only environment can produce a real
  sale. The strip stays in its "not reached" (red net) state, proving the
  milestone can't be gamed by simulated activity: it only ever flips on
  genuine `RevenueEvent.realized:true` rows.
