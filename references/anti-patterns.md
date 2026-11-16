# Anti-patterns — the "AI 味" catalog

Each entry: the tell, why it reads as generated, and what to do instead.
Use this as the audit checklist in step 6 of the SKILL.md workflow.

## Color

| Tell | Why it reads as AI | Do instead |
|---|---|---|
| Purple/blue gradient backgrounds (`from-indigo-500 to-purple-600`) | The single most common AI default | Solid, intentional background color; if a gradient is needed, make it subtle, same-hue, and directional with a reason |
| Gradient text on headings | Decoration standing in for a design idea | Strong type at a strong size in one ink color |
| Every accent the same saturated blue/violet | Tailwind default palette untouched | One accent chosen from the design direction; desaturate supporting colors |
| Pure black `#000` text on pure white | No color thinking at all | Ink color slightly off-black (`#1a1a1a`, `#111827`-style warm/cool dark) on off-white paper |
| Too many hues | No restraint | 1 neutral family + 1 accent + semantic colors only |

## Typography

| Tell | Why it reads as AI | Do instead |
|---|---|---|
| Inter/Roboto/system-ui for everything, one weight | The default output of every generator | Load a display face + body face (+ mono for labels/data); use 3+ weights with intent |
| All headings `font-bold text-4xl` | No scale design | Explicit type scale (e.g. 12/14/16/20/28/40/64) with consistent ratios |
| No letter-spacing or line-height tuning | Defaults shipped | Tight tracking on large display text (`-0.02em` to `-0.05em`), generous line-height on body, uppercase + wide tracking on small labels |
| Same-size text everywhere | Flat hierarchy | Extreme hierarchy: oversized display, small dense labels |

## Layout

| Tell | Why it reads as AI | Do instead |
|---|---|---|
| Centered hero → 3-card feature grid → CTA → footer | The one layout every model generates | Editorial grids, asymmetric splits, oversized numbers, horizontal scroll sections, sticky sidebars — pick from the direction |
| Cards as the only container primitive | Default component thinking | Hairline-ruled sections, full-bleed bands, table-like rows, bare typography blocks |
| Uniform gaps and padding everywhere | Mechanical 8px rhythm | Deliberate density contrast: cramped data areas next to generous breathing room |
| Everything centered | Avoids commitment | Left-aligned editorial text, right-aligned metadata, off-grid accents |

## Components

| Tell | Why it reads as AI | Do instead |
|---|---|---|
| `rounded-2xl shadow-lg` on every card | Tailwind defaults verbatim | One radius philosophy per design (0 for brutalist/swiss, small 4–6px for technical, large only when the direction calls for it); hairline borders instead of shadows |
| Emoji as icons 🚀✨💡 | No icon system installed | Lucide / Phosphor / Heroicons at consistent stroke width, or custom SVG |
| Glassmorphism panels everywhere | Trend decoration without function | Frosted glass only where content genuinely sits over imagery |
| Glow, blob, and grid-pattern background decorations | Filler for empty design | Texture with purpose: paper grain, fine dot grid on technical designs, or honest flat color |
| Buttons all identical pill shape | One component reused | Button hierarchy: solid primary, quiet ghost secondary, text-link tertiary — with distinct hover/active states |

## Copy

| Tell | Why it reads as AI | Do instead |
|---|---|---|
| "Welcome to X", "Empower your workflow", "Seamless, powerful, intuitive" | LLM marketing filler | Specific copy: what it does, for whom, with concrete nouns and numbers |
| Feature cards titled "Fast / Secure / Easy" | Generic trio | Named features with one concrete sentence each |
| Lorem ipsum or obviously fake data | Placeholder shipped | Realistic sample content with believable names, dates, and amounts |

## Motion

| Tell | Why it reads as AI | Do instead |
|---|---|---|
| Everything animates on load | Generated pages over-animate to feel "alive" | One primary entrance pattern; stillness elsewhere |
| Bounce/elastic easing on UI elements | Playful default | `cubic-bezier` ease-out/expo curves, 150–400ms, consistent across the page |
| Hover states missing or only `opacity-80` | States not designed | Every interactive element gets hover + active + focus-visible states that match the direction |
