# RoninOS Claude Skills (Angular 20)

A collection of enforceable Claude skills for building Angular 20 applications with Signals-first architecture.

## What Are Claude Skills?

Claude Skills are structured prompts that define how Claude behaves when working on specific domains. Each skill includes:

- **Role** - Who Claude becomes
- **Purpose** - What problem the skill solves
- **State Model** - Required Signals and computed values
- **Modes** - Different operational modes (default, critique, scaffold, auto-simplify)
- **Hard Rules** - What Claude must never do

## Available Skills

| Skill | Type | Purpose |
|-------|------|---------|
| [Ronin Angular Designer](/.claude/skills/ronin-angular-designer.ts) | Core | UI/UX design with Tailwind, accessibility, layout-first thinking |
| [Browser Agent UI](/.claude/skills/browser-agent-ui.ts) | Domain | Real-time dashboards for headless browser agents |
| [Payments & Stripe](/.claude/skills/payments/SKILL.md) | Domain | Safe, failure-aware payment flows |
| [Domain Finder](/.claude/skills/domain-finder/SKILL.md) | Domain | Reactive domain availability search |
| [Lead Finder / Data Grid](/.claude/skills/lead-finder/SKILL.md) | Domain | Enterprise data grids with SignalStore |
| [Skill Creator](/.claude/skills/skill-creator/SKILL.md) | Meta | Governs how new skills are created |

## Tech Stack

All skills enforce:

- **Framework:** Angular 20 (Standalone Components)
- **State:** Angular Signals (`signal`, `computed`, `effect`)
- **State Management:** SignalStore (`@ngrx/signals`) for complex state
- **Styling:** Tailwind CSS (mobile-first)
- **Icons:** Lucide Angular
- **Change Detection:** OnPush
- **Zoneless Compatible**

## Skill Modes

Each skill supports multiple modes:

| Mode | Purpose |
|------|---------|
| **Default** | Design and implement |
| **Critique** | Review existing code without rewriting |
| **Scaffold** | Generate minimal valid structure |
| **Auto-Simplify** | Reduce complexity while preserving intent |

## Usage

### Discovery

Check [SKILL_INDEX.md](/.claude/skills/SKILL_INDEX.md) to find the right skill for your task.

### Activation

Skills activate based on context or explicit triggers:

```
"scaffold a data grid"        → Lead Finder skill, scaffold mode
"review this payment flow"    → Payments skill, critique mode
"create a new component"      → Ronin Angular Designer, scaffold mode
```

### Hard Rules (All Skills)

- No React patterns
- No logic in templates
- No implicit state
- Signals for all UI state
- Semantic HTML first
- Accessibility is non-negotiable

## File Structure

```
.claude/skills/
├── SKILL_INDEX.md              # Central discovery
├── ronin-angular-designer.ts   # Core UI skill
├── browser-agent-ui.ts         # Browser agent dashboards
├── payments/
│   └── SKILL.md                # Stripe payment flows
├── domain-finder/
│   └── SKILL.md                # Domain availability search
├── lead-finder/
│   └── SKILL.md                # Enterprise data grids
└── skill-creator/
    └── SKILL.md                # Meta-skill for governance
```

## Creating New Skills

Use the **Skill Creator** meta-skill. Before creating:

1. Check `SKILL_INDEX.md` for existing coverage
2. Confirm no existing skill applies
3. Prefer extending an existing skill over creating new
4. If overlap exists, stop and explain the conflict

Required sections for every skill:

1. Role
2. Purpose
3. Tech Stack
4. State Model
5. Principles
6. Modes
7. Triggers
8. Output Format
9. Hard Rules
10. Run Function

## License

MIT
