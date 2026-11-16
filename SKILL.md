---
name: human-ui
description: >
  Design and build distinctive, high-end frontend UI that does not look AI-generated.
  Use whenever creating, refactoring, or reviewing any frontend page, landing page,
  dashboard, component, or web app UI. Triggers: "高级感 UI", "没有 AI 味",
  "不要 AI 味", "高端页面", "premium UI", "high-end landing page", "make it look
  designed not generated", "avoid AI slop", "generic-looking UI", or /human-ui.
---

# Human UI — design pages that don't look AI-generated

AI-generated UI has a recognizable default look (generic gradients, Inter everywhere,
identical rounded cards, three-feature grids). This skill exists to break that default.
The full catalog of tells and fixes lives in `references/anti-patterns.md`; ready-made
aesthetic directions (including classic design languages like Bauhaus and Art Deco)
with concrete font/color specs live in `references/directions.md`; GSAP motion
recipes live in `references/motion-gsap.md`.

## Core principle

Commit to a specific design direction BEFORE writing any code, then let that direction
make every decision. Generic output comes from skipping this step and falling back to
framework defaults. A page with a strong, consistent point of view reads as designed;
a page assembled from "safe" defaults reads as generated.

## Workflow

1. **Pick a direction.** Choose one direction from `references/directions.md` that fits
   the product (or derive one from the user's brand), and state it in one sentence
   before coding, e.g. "Editorial magazine: serif display headlines, off-white paper
   background, hairline rules, one vermilion accent." If the user already named an
   aesthetic, honor it and use the directions file only for concrete specs.
2. **Build the type system first.** Load real fonts via Google Fonts or a CDN (never
   rely on the default font stack), define a display/body/mono pairing, and set an
   explicit size scale and line-height rhythm. Typography carries "高级感" more than
   any other single decision.
3. **Build the color system.** One dominant neutral background, one restrained accent
   used sparingly, text colors at 2–3 opacity levels of one ink color. Derive the
   palette from the chosen direction, not from framework defaults.
4. **Lay out with intent.** Use asymmetric grids, oversized or undersized elements on
   purpose, visible structure (hairlines, ruled sections, numbered items), and real
   content hierarchy. Whitespace is a design material, not leftover space.
5. **Add motion and micro-detail last.** Use GSAP + ScrollTrigger (with Lenis smooth
   scroll) for anything beyond simple CSS transitions — follow the recipes and easing
   rules in `references/motion-gsap.md` exactly, including the
   `prefers-reduced-motion` gate. Hover/focus/active states on every interactive
   element; borders and texture instead of drop shadows.
6. **Self-audit before delivering.** Read `references/anti-patterns.md` and check the
   page against every tell. Fix what you find, then verify in the browser (desktop and
   mobile widths) before declaring done.

## Hard rules — the worst AI tells, never ship these

- No purple/blue gradient backgrounds, no gradient text on headings.
- No Inter/Roboto/system-default font used for everything with no pairing or scale.
- No emoji as UI icons. Use an SVG icon set (Lucide, Phosphor, Heroicons) or custom SVG.
- No grids of identical `rounded-2xl shadow-lg` cards as the page's main structure.
- No "Welcome to X" / "Lorem ipsum" / "Feature 1 · Feature 2 · Feature 3" placeholder copy.
  Write real, specific copy in the product's voice.
- No glassmorphism panels, glow effects, or animated blobs used as decoration without function.
- No uniform 8px-multiple spacing applied mechanically — vary density deliberately.

## Reviewing existing UI

When asked to fix or review an existing page for "AI 味": audit it against
`references/anti-patterns.md` first and report findings grouped by severity, then
propose a direction from `references/directions.md`, then implement. Do not rewrite
everything at once if the user asked for a review only.
