# BackyardOne — Customer Discovery Brain

**Live:** https://shenal-maker.github.io/backyardone-trinity/
**Firebase:** `backyardone-trinity` project (Firestore: `backyardone_discovery/shared`)
**Team:** Adele, Carter, Peter, Dale, Austin, Libby, Connor, Tobasum, Mark, Michael

---

## What this is

A shared, real-time graph for the BackyardOne team to run structured customer discovery toward product-market fit. Everyone edits the same canvas. No login required — pick your name on first visit, locked from then on.

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
Click any **grey WHO node** → select your name → **Claim Interview**
- Node turns yellow
- No one else will double-book it

### 2. Log the interview
After the call, click your claimed node → fill in the Mom Test form → add a link (Zoom transcript, Google Doc, Notion) → **Mark Complete ✓**
- Node turns green
- Mom Test fields: Context · Struggle · Current solution · WTP moment · Referral
- Link stored on the node permanently (paste URL → domain becomes label)

### 3. Update hypotheses
After each interview, find the **WHAT_IF node** being tested → update its resistance rating and WTP signal with what you heard.

### 4. Connect new knowledge
- **Add a node:** "+ Add Target" in the sidebar
- **Connect nodes:** "Connect nodes" → click node 1 → click node 2
- **Edit anything:** click the name or description in the panel → type → click away to save
- **Delete:** select a node → ⌫, or use the delete button in the panel

### 5. Read the dashboard
Switch to **Dashboard** tab in the sidebar to see:
- Sprint progress toward 20-interview goal
- Segment funnel (LA GCs / Homeowners / Lenders)
- Hypothesis board ranked by evidence
- Team activity leaderboard
- Resistance pattern across interviews

---

## Current hypotheses being tested

| Hypothesis | Segment | Resistance | WTP signal | Status |
|---|---|---|---|---|
| GCs pay for pre-screened homeowner leads with confirmed lot feasibility | Local GCs | 🟢 Low | — | Untested |
| Homeowners pay for instant lot feasibility report | Homeowners | 🟡 Med | — | Untested |
| Builders pay for parcel data outside LA | LA GCs | 🟡 Med | — | Untested |
| HELOC lenders pay for pre-qualified ADU borrowers | Credit unions | 🔴 High | — | Untested |

**Priority order:** GCs first (lowest resistance, fastest WTP), homeowners second, lenders later.

---

## Why GCs first

- They understand ROI immediately — one good lead = thousands in revenue
- They already spend money on tools and lead gen
- They have a clear, specific pain: wasted site visits on lots that can't build
- Short sales cycle vs. enterprise (lenders) or education-heavy (homeowners)
- A GC who loves the tool will refer you to 10 more GCs

---

## What's built

### ✅ Done
- Trinity graph with vis-network (WHO/WHAT/WHAT_IF/SITUATION/COMMUNITY)
- Shared Firestore canvas — one doc, all teammates edit simultaneously
- Firebase Anonymous Auth — stable identity per device, name picked once
- Real-time presence — see who's on the canvas (Google Docs style avatars)
- Soft-claim workflow (grey → yellow → green)
- Inline editing everywhere — contenteditable, saves on blur
- Mom Test capture form on every SITUATION node (Context / Struggle / Current solution / WTP moment / Referral)
- Links field per node — paste URL, domain becomes label automatically
- Discovery Dashboard tab — sprint progress, segment funnel, hypothesis board, team activity
- 2-click connect mode, delete key to remove nodes/edges
- LA seed data: ADU GCs, credit unions, homeowner archetypes, WHAT_IF hypotheses

### 🔨 Next — cleanup
Remove leftover views from earlier product concept (Flourish, Field Notes, old People/Situations board, sketch canvas, emotion picker). These add confusion for new teammates.

### 🔨 Next — additions
- **"Who's next?" prompt on dashboard** — surfaces top unclaimed WHO nodes by segment priority with one-tap Claim
- **Copy summary for Slack** — one button generates a paste-ready team update
- **Weekly sprint counter** — interviews done Mon–Sun, resets automatically
- **Verbatim quote on node** — strongest quote visible as tooltip on completed WHO nodes
- **Hypothesis confidence vote** — team dot-votes on each WHAT_IF before data exists to decide

---

## Tech stack

- **Frontend:** Vanilla JS, single `index.html` — no build step
- **Graph:** [vis-network](https://visjs.github.io/vis-network/docs/network/)
- **Database:** Firebase Firestore (`backyardone-trinity` project)
- **Auth:** Firebase Anonymous Auth — stable UID per device, display name locked after first pick
- **Hosting:** GitHub Pages (`main` branch)

---

## Local dev

```bash
cd /Users/adeleshen/backyardone-trinity
bash start.sh   # serves on http://localhost:3001
```

Auto-deploys to GitHub Pages on every push to `main`.
