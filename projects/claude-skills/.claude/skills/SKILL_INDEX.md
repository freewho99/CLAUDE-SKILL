# RoninOS · Claude Skill Index (Angular 20)

This index defines all available Claude skills for the RoninOS system.
Each skill is enforceable, Angular-native, and Signals-first.

Claude must reference this index when:
- selecting a skill
- validating output
- creating new skills
- reviewing existing implementations

---

## Skill Discovery Rules

- Skills are **opt-in** and **explicit**
- Claude must not invent capabilities outside listed skills
- If no skill applies, Claude should ask for clarification
- Meta-skills (e.g. Skill Creator) govern all others

---

## 📦 Available Skills

---

### 1️⃣ Browser Agent UI Skill

**Path:**
`.claude/skills/browser-agent-ui.ts`

**Type:**
Domain Skill · UI / Dashboard

**Purpose:**
Design, critique, and scaffold Angular dashboards for controlling and observing headless browser agents.

**Primary Responsibilities:**
- Operator-grade state visibility
- Safe action gating
- Real-time data clarity
- Error-first UI handling

**Modes:**
- `default` — Design and reasoning
- `critique` — Senior operator review
- `scaffold` — Generate clean Angular UI structure

**Key Constraints:**
- Status is always visible
- Conflicting actions are never allowed
- Stale data must be clearly marked
- All live data must be timestamped

---

### 2️⃣ Payments & Stripe Skill

**Path:**
`.claude/skills/payments/SKILL.md`

**Type:**
Domain Skill · Fintech

**Purpose:**
Implement safe, explicit, failure-aware payment and checkout flows.

**Primary Responsibilities:**
- Payment state modeling
- Clear processing / success / failure UX
- Secure Stripe integration via backend proxy

**Key Constraints:**
- Payments treated as state machines
- No secret keys on client
- UI must clearly indicate when money may be moving

---

### 3️⃣ Domain Finder Skill

**Path:**
`.claude/skills/domain-finder/SKILL.md`

**Type:**
Domain Skill · Search / Forms

**Purpose:**
Build high-performance, controlled search interfaces for domain availability.

**Primary Responsibilities:**
- Reactive search with debounce
- Immediate but intentional feedback
- Clear availability signaling

**Key Constraints:**
- No `ngModel`
- Reactive Forms + Signals only
- No blocking UI during search

---

### 4️⃣ Lead Finder / Data Grid Skill

**Path:**
`.claude/skills/lead-finder/SKILL.md`

**Type:**
Domain Skill · Data / Enterprise UI

**Purpose:**
Display and manage large datasets with clarity, performance, and scalability.

**Primary Responsibilities:**
- Centralized state via `signalStore`
- Predictable pagination and export
- Cognitive hierarchy for dense data

**Key Constraints:**
- No data logic in templates
- Always use `track` with unique IDs
- Virtualize when datasets are large

---

### 5️⃣ Skill Creator (Meta-Skill)

**Path:**
`.claude/skills/skill-creator/SKILL.md`

**Type:**
Meta Skill · Governance

**Purpose:**
Define how all new Claude skills are created, structured, and validated.

**Primary Responsibilities:**
- Enforce Angular 20 + Signals defaults
- Prevent React or ad-hoc patterns
- Guarantee enforceable skill structure

**Key Constraints:**
- Required sections enforced
- Markdown output only
- Skills without contracts are invalid

---

### 6️⃣ Ronin Angular Designer

**Path:**
`.claude/skills/ronin-angular-designer.ts`

**Type:**
Core Skill · UI / Design System

**Purpose:**
Design high-clarity, accessible, modern UIs using Angular, Signals, Tailwind CSS, and disciplined layout-first thinking.

**Primary Responsibilities:**
- Visual hierarchy and spacing
- State modeling with Signals
- Accessibility enforcement
- Component architecture

**Modes:**
- `default` — Design Angular-first UIs
- `critique` — Senior-level design review
- `autoSimplify` — Refactor for clarity
- `scaffold` — Generate new components

**Key Constraints:**
- Clarity over cleverness
- Structure before style
- No React patterns
- Templates project state, not compute it

---

## 🧭 Skill Selection Guidance

When a user request involves:

- **Dashboards / Agents / Control Panels** → Browser Agent UI Skill
- **Payments / Checkout / Stripe** → Payments Skill
- **Search / Availability / Fast Forms** → Domain Finder Skill
- **Large Tables / Scraped Data** → Lead Finder Skill
- **Creating New Skills** → Skill Creator
- **General UI / Components / Design** → Ronin Angular Designer

If multiple skills apply:
- Prefer **domain-specific** over generic
- Prefer **meta-skills** only when authoring skills

---

## RoninOS Index Rule

If a capability is not listed here,
Claude must not assume it exists.

---

_End of Skill Index_
