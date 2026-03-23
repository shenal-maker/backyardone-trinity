# BackyardOne — Customer Discovery Brain

**Live:** https://shenal-maker.github.io/backyardone-trinity/
**Firebase:** `backyardone-trinity` project (Firestore: `backyardone_discovery/shared`)
**Team:** Adele, Carter, Peter, Dale, Austin, Libby, Connor, Tobasum, Mark, Michael

---

## What this is

A shared, real-time graph for the BackyardOne team to run structured customer discovery toward product-market fit. Everyone edits the same canvas. No login. No friction.

Built on the **Trinity schema** — a three-layer knowledge graph:

| Node type | What it represents | Color |
|---|---|---|
| **WHO** | People — interview targets, team members, referrals | Blue border |
| **WHAT** | Facts — validated pain points, constraints, market data | Green border |
| **WHAT_IF** | Hypotheses — product bets being tested | Orange border |
| **SITUATION** | Interview events — each conversation is a node | Purple border |
| **COMMUNITY** | Segments — GCs, Homeowners, Lenders | Red border |

---

## Interview status (fill color)

| Color | Meaning |
|---|---|
| 🔘 Grey | Unclaimed — needs outreach |
| 🟡 Yellow | Claimed — interview scheduled or in progress |
| 🟢 Green | Completed — notes logged |

---

## How the team uses it

### 1. Claim an interview target
Click any **grey WHO node** → select your name → **Claim Interview →**
- Node turns yellow
- A line draws from your WHO node to the target
- No one else will double-book it

### 2. Log the interview
After the call, click your claimed node → paste notes → add a doc link (Zoom transcript, Google Doc, Notion) → **Mark Complete ✓**
- Node turns green
- Notes stamped with your name and date
- Link stored on the node permanently

### 3. Update hypotheses
After each interview, find the **WHAT_IF node** that hypothesis was testing → update its resistance rating and WTP signal with what you heard.

### 4. Connect new knowledge
- **Add a node:** "+ Add Target" in the sidebar
- **Connect nodes:** "Connect nodes" button → drag between two nodes
- **Edit anything:** click the name or description in the panel → type → click away to save
- **Delete:** select a node → Delete key, or use the delete button in the panel
- **Voice note:** 🎙 button bottom-right → speak → text appears

---

## Build plan

### ✅ Phase 1 — Core graph (done)
- Trinity graph with vis-network (WHO/WHAT/WHAT_IF/SITUATION/COMMUNITY)
- Shared Firestore canvas — one doc, all teammates edit simultaneously
- Soft-claim workflow (grey → yellow → green)
- Inline editing everywhere — contenteditable, saves on blur
- Node labels show owner name for claimed/completed nodes
- Drag to connect nodes, delete key to remove
- Voice recording via Web Speech API
- Links field per node (Google Doc, Notion, Loom, etc.)
- Toast notifications

### 🔨 Phase 2 — Hypothesis engine (next)
Make WHAT_IF nodes first-class PMF instruments:

- **Resistance rating** on every WHAT_IF node: 🟢 Low / 🟡 Med / 🔴 High (manually set after interviews)
- **WTP signal field**: verbatim quote from the strongest "I'd pay for this" moment
- **Interview count**: auto-counted from connected SITUATION nodes
- **Status badge**: Untested → Testing → Validated → Invalidated

### 🔨 Phase 3 — Interview signal capture (next)
Make every SITUATION node a structured evidence record:

- **Verbatim quote** field (the single most important thing they said)
- **WTP strength**: Strong / Weak / None
- **Referral**: did they give you another name to talk to? (Y/N) — the strongest PMF signal
- **Resistance type**: Price / Awareness / Trust / Inertia
- **Links array**: multiple labeled URLs per node (not just one field)

### 🔨 Phase 4 — Scoreboard sidebar (next)
Replace the static legend with a live intelligence panel:

- All WHAT_IF hypotheses ranked by interview count + WTP signal strength
- Surfaces the path of least resistance at a glance
- Color-coded by resistance level
- Shows which team member owns each interview thread

### 🔨 Phase 5 — Network import (later)
- LinkedIn CSV import → auto-creates WHO nodes from your connections
- Blinq CSV import → already built, expose the button
- Google Contacts export → import to WHO nodes

---

## Current hypotheses being tested

| Hypothesis | Segment | Resistance | WTP signal | Status |
|---|---|---|---|---|
| GCs pay for pre-screened homeowner leads with confirmed lot feasibility | Local GCs | 🟢 Low | — | Untested |
| Homeowners pay for instant lot feasibility report | Homeowners | 🟡 Med | — | Untested |
| Builders pay for parcel data outside LA | LA GCs | 🟡 Med | — | Untested |
| HELOC lenders pay for pre-qualified ADU borrowers | Credit unions | 🔴 High | — | Untested |

**Priority order based on research:** GCs first (lowest resistance, highest and fastest WTP), homeowners second, lenders later.

---

## Why GCs first

- They understand ROI immediately — one good lead = thousands in revenue
- They already spend money on tools and lead gen
- They have a clear, specific pain: wasted site visits on lots that can't build
- Short sales cycle vs. enterprise (lenders) or education-heavy (homeowners)
- A GC who loves the tool will refer you to 10 more GCs

---

## Tech stack

- **Frontend:** Vanilla JS, single `index.html` — no build step
- **Graph:** [vis-network](https://visjs.github.io/vis-network/docs/network/)
- **Database:** Firebase Firestore (`backyardone-trinity` project)
- **Hosting:** GitHub Pages (`main` branch)
- **Auth:** None — open canvas, team access by URL

---

## Local dev

```bash
cd /Users/adeleshen/backyardone-trinity
bash start.sh   # serves on http://localhost:3001
```

Auto-deploys to GitHub Pages on every push to `main`.
