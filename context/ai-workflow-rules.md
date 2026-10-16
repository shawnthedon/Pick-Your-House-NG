# AI Workflow Rules - PickAHouse

## Approach
Development proceeds incrementally based on feature specifications. AI coding agents must construct one modular unit at a time, verify functionality, and update progress docs before moving to subsequent specs.

## Scoping Rules
- Work on exactly one feature unit per prompt execution.
- Never cross system boundaries in a single pass (e.g., do not combine Express database migration scripts with Next.js frontend header redesigns).
- Preserve existing working Radix UI components, responsive layouts, and visual design themes.

## When to Split Work
Split a task immediately if it requires:
- Modifying backend database schemas while simultaneously writing frontend page components.
- Building more than 3 API endpoints in a single step.
- Writing unit tests alongside major architectural refactoring.

## Protected Files
Do not alter or overwrite the following unless explicitly instructed in a feature spec:
- `components/ui/*` (Base Radix UI design primitives).
- `context/*` (System context specifications).

## Definition of Done
A feature unit is complete only when:
1. `pnpm build` or `npm run build` compiles with 0 TypeScript/ESLint errors.
2. The code adheres strictly to `code-standards.md`.
3. Verification steps outlined in the feature spec pass successfully.
4. `context/progress-tracker.md` is updated with completed items and session notes.
