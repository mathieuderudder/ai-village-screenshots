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

## Session 5 — pixel-art village overhaul (T014-T016), business UI (T017),
automatic compute-cost lifecycle (T018), collaboration cues (T019)

- `15-village-pixel-art-overview.png` — the village is now the primary
  screen: fixed pixel-art buildings (CSS shapes, no image assets) connected
  by dirt paths radiating from a central plaza, scattered decorative trees,
  and every real `Agent` rendered as a small two-shape NPC sprite standing
  in front of its actual department building — not a dashboard card list.
- `16-village-collaboration-cue.png` — T019's state-driven collaboration
  cue: a glowing link between Research Lab and Business District plus a
  highlighted helper sprite, rendered only because real `Task` data shows
  a parent task genuinely "waiting" on a child subtask actively worked by a
  different agent. Disappears the instant that backend state changes —
  never a random or decorative walk.
- `17-business-district-economic-flows.png` — the new `BusinessInsights`
  panel (T017) surfacing the session-4 economic flows against the real API:
  opportunity ranking with composite scores, and real opportunities in
  every honest state (STOPPED after a failed validation, ACTIVE awaiting
  build/outcome, and SUCCESS with its outcome correctly labeled a
  projection, never realized revenue).

## Session 6 — Functional Complete gate (T020), approved dashboard
composition (T023), Approval Queue UI (T024), Head Agent briefing (T021)

- `18-command-center-dashboard.png` — the new primary screen, matching the
  layout the user explicitly approved in tab 1 as "exact wat ik wil": left
  nav/Village Status/quick actions, top Head Agent briefing (with
  clickable navigation chips) + a real KPI strip, a dominant center
  village, and a right column showing real active projects, ranked
  opportunities, recent activity, and a genuine pending `ApprovalRequest`
  (T024) with working Approve/Reject controls — created via the real API
  for this screenshot, not mocked.
- `19-agent-info-panel.png` — the rich bottom Agent Info bar (T023) for a
  selected resident: portrait, role, department, AI provider, a live
  Current Focus/Stats/Logs tab set showing real recent-task counts, and an
  active conversation — the chat message shown was actually sent and
  answered through `POST /api/agents/:id/messages` for this screenshot.
- `20-laptop-responsive.png` — the same composition at a 1366×800 laptop
  viewport: every panel reflows without overlap and the village stays the
  visually dominant element, per T023's explicit responsive requirement.

## Session 7 — pixel-art pass (T025), village camera/gamefeel, Head Agent
briefing with real recent lessons

- `21-pixel-art-village.png` — every building now has a distinct
  hand-built roof silhouette (spire/flat/dome/sawtooth/awning/gable), not
  just a color, and every resident is a small inline-SVG pixel person
  (status-colored torso, role-colored collar) — still no image assets.
  The Head Agent briefing now surfaces real recent business-experiment
  failure lessons ("Les: ...", from actual stored `MemoryItem` text), not
  just live counts.
- `22-village-closeup.png` — a 115% zoom close-up showing the roof/window/
  door detail and the new status legend, taken by actually dragging and
  scroll-zooming the real village camera (T025's "drag to move, scroll to
  zoom" gamefeel), not a cropped screenshot.

## Session 8 — final art direction: Kenmi "Cute Fantasy RPG", camera fixes

The hand-rolled inline-SVG pixel art (and a since-abandoned mid-session
detour into kit-bashing free CC0 tile packs) is replaced by real sprite
art from the purchased, commercially licensed Kenmi "Cute Fantasy RPG"
pack. Source files themselves are never published here or anywhere
public — only these rendered app screenshots. See the main repo's
`apps/web/public/assets/village/ASSET_LICENSES.md` for full attribution.

- `23-cute-fantasy-village-overview.png` — the default camera view: real
  building sprites per department (church for HQ, inn for Business
  District, blacksmith for Development, etc.), organic curved paths, a
  denser wilderness ring of trees/rocks/bushes at the world's edge, no
  exposed canvas boundary anywhere in view.
- `24-hq-nametag-closeup.png` — close-up on the HQ cluster showing the
  label cleanup: a small building sign is the primary ID, the full
  department name sits quieter underneath, and the three HQ agent
  nametags (Hoofd/Finance/Support) are clearly spaced with no overlap.
- `25-agent-selected.png` — a selected agent: a visible highlight ring
  under the sprite and a brightened nametag border distinguish it from
  unselected agents, with the real Current Focus/chat panel open below.
- `26-laptop-responsive.png` — the same village at a 1366×800 laptop
  viewport, confirming the composition still reads cleanly at the
  smaller size.
- `27-full-world-50pct-zoom.png` — maximum zoom-out: the entire village
  and its surrounding forest fit in frame with continuous terrain, no
  "rectangle inside a rectangle" seam between the core and the padding
  band.
- `28-camera-bug-before-fix.png` / `29-camera-bug-after-fix.png` — the
  same real drag-pan gesture at 150% zoom, before and after a genuine bug
  fix. What looked like a GPU rendering artifact (solid blue rectangles
  behind trees) turned out to be the browser's native text/image
  selection highlight: the custom drag-to-pan handler never set
  `user-select: none`, so a click-drag pan was indistinguishable from a
  native selection drag, and Chromium painted its default blue selection
  highlight across every image the cursor crossed. Confirmed via
  `document.getSelection()` returning a real, non-empty `Range` after the
  drag; fixed with a single `user-select: none` on the viewport.

## T027 — Major Village Experience & Command Center visual expansion

A full composition redesign, not a polish pass: the village map moved from
"buildings on a green card with roads between them" to eight loosely
clustered districts with their own environmental identity, plus a real
path hierarchy (one wide civic<->market spine, narrower district spurs).
The surrounding Command Center UI got a matching visual-system pass —
panel depth, a gold accent identity, KPI/approval-card hierarchy, a real
POWER BREAK-EVEN progress bar. See `apps/web/public/assets/village/
ASSET_LICENSES.md` for the newly re-inventoried assets used this pass
(2 more confirmed front-facing character sprites, mushrooms/lilypads/
cattails/butterfly, a shed+silo workshop pair) — same purchased pack,
nothing new bought or downloaded.

- `30-village-overview-default-camera.png` — the default camera view:
  HQ off-center in its own civic core, Business District's market plaza
  with striped stall awnings, curved organic paths (visibly wider on the
  civic<->market spine than on the district spurs), no world edge.
- `31-village-closeup.png` — a closer zoom on the same view, showing
  terrain variation (a second grass tone blended in) and path texture.
- `32-hq-plaza.png` — the HQ civic square: three agent nametags
  (Hoofd/Finance/Support) clearly spaced with zero overlap even this
  close together.
- `33-business-market-district.png` — the market quarter with its pond/
  Research corner and workshop yard (shed + silo) all visible together,
  showing how the districts read as distinct neighborhoods rather than
  buildings scattered on bare grass.
- `34-development-research-district.png` — Development District's
  workshop yard (shed, silo, crates) next to Research Lab's quiet pond
  (lilypads/cattails from this pass's asset re-inventory), with
  Improvement/R&D Lab — deliberately the most isolated department —
  visible further out, correctly labeled "R&D" (previously collided with
  Research Lab's "LAB" tag; both share the same buildingType).
- `35-agent-cluster-nametags.png` — the HQ agent cluster at a different
  zoom level, confirming nametag spacing holds up across zoom.
- `36-selected-agent-info.png` — a selected agent: the world-space glow
  ring plus the redesigned bottom Agent Info panel (bigger portrait, gold
  frame, pill-shaped tabs) reading as a character-management card.
- `37-selected-building.png` — a selected building's department panel.
- `38-approval-state.png` — the "Needs Your Approval" card with its new
  gold border + count badge, now visibly higher priority than the other
  right-column cards instead of looking identical to them.
- `39-power-breakeven-card.png` — POWER BREAK-EVEN's new progress bar,
  computed directly from the same realized-revenue/compute-cost numbers
  already shown as text (no separate estimate).
- `40-command-center-desktop.png` — the full redesigned shell: gold
  brand mark, card-based left sidebar, KPI cards with colored top
  accents, panel-depth right column.
- `41-command-center-laptop-1366x800.png` — the same shell at
  1366×800: village stays dominant, no overlap, all panels reflow
  cleanly.
- `42-zoomed-out-world-wilderness.png` — full world at 50% zoom: every
  district visible at once, dense wilderness ring, no rectangle-in-
  rectangle terrain seam.
- `43-high-zoom-building-detail.png` — a close zoom on building/prop
  detail. No building-interior proof was built this pass (T022 stays
  open, as the brief explicitly allowed if it risked needing a larger
  architecture change than a visual pass justifies) — this is the
  highest-detail view actually shipped instead.

## T028 — Visual Reference Match: closing the gap to the approved Tab 1
mockup

T027 was technically complete but still visually "a pixel-art village",
not yet "clearly the same product" as the approved reference mockup
compared against fresh screenshots. This pass closes that gap on three
fronts: the default camera is now close enough that buildings dominate the
viewport instead of a wide overview (default zoom raised, and the
mount-time camera target re-centered on HQ itself — the old target had
been tuned for a lower zoom and, at the new closer default, was cropping
HQ almost entirely off the top of frame); the Head Agent briefing, Agent
Info panel, and bottom idle-state footer now show the real character
portrait sprites (shared via the new `characterSprites.ts`) instead of
flat gradient/color placeholders, plus a live per-status agent-count strip
where the footer used to be nearly empty; and the right-column cards got
small category-color icon marks. A genuine bug was found and fixed along
the way: `.village-path--main`'s explicit `z-index` was painting the path
over any building caption it happened to run past (regardless of DOM
order), which is what made HQ's "HOOFDKWARTIER" label look visually
broken — fixed by giving buildings their own stacking level and, more
fundamentally, by making the full department name a hover/select-only
label instead of always-on (the small pixel sign stays the permanent
at-a-glance ID).

- `44-village-dominant-default.png` — the new default view: HQ fills a
  large share of the frame with visible tree density around it, versus
  T027's smaller, more distant default framing.
- `45-village-only-hero.png` — the village viewport alone, no shell
  chrome, showing how much closer the default camera now sits.
- `46-hq-civic-core.png` — HQ close-up with the department name label
  showing on hover (previously always-on and visually broken by the path
  z-index bug described above; now clean because it renders above the
  path and only appears on hover/select).
- `47-market-business-district.png` — panned down to the market plaza/
  Business District, confirming the closer default camera still reads
  well once the user pans to a different district.
- `48-selected-agent-full-info.png` — a selected Head Agent: the Agent
  Info identity panel now shows the real in-world character sprite
  (farmer-bob) instead of a flat status-colored block.
- `49-approval-state.png` — the "Needs Your Approval" card with its new
  category icon mark, gold border, and count badge, showing a real
  pending `budget_allocation` approval with working Goedkeuren/Afwijzen
  controls.
- `50-power-breakeven-card.png` — the POWER BREAK-EVEN card's real
  progress bar, unchanged in data source from T027, shown alongside this
  pass's new card icon mark.
- `51-laptop-1366x800.png` — the same default view at 1366×800: village
  stays dominant, all panels reflow without overlap.
- `52-village-closeup-150pct.png` — zoomed in further from the new
  default, showing building/prop/path detail holds up at higher zoom.
- `53-zoomed-out-world.png` — the full world at minimum zoom, confirming
  "zoomed out" is still fully reachable on demand even though it's no
  longer the default framing.
