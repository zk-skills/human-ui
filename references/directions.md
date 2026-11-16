# Design directions — pick ONE and commit

Each direction is a complete, coherent point of view with concrete specs.
Fonts are all on Google Fonts. Do not mix signature moves across directions.

## 1. Editorial / Magazine

Best for: landing pages, portfolios, content products, brands wanting sophistication.

- **Fonts**: display serif (Playfair Display, Fraunces, or Cormorant) for headlines;
  neutral grotesque (Inter Tight, Archivo) for body; optional italic serif for pull quotes.
- **Palette**: paper off-white `#faf9f6` / warm `#f5f1ea`, ink `#1a1a1a`, one accent
  (vermilion `#e4572e`, forest `#2d5a3d`, or cobalt `#2541b2`).
- **Signature moves**: oversized headlines (64–120px) with tight tracking; hairline
  rules (`1px #1a1a1a1a`) separating sections; numbered sections (01, 02, 03);
  drop caps or oversized pull quotes; asymmetric two-column text blocks.
- **Radius/shadow**: 0 radius, no shadows — structure comes from rules and whitespace.
- **Avoid**: cards, gradients, centered everything.

## 2. Swiss / International Typographic Style

Best for: agencies, tools, portfolios, anything that should feel precise and rational.

- **Fonts**: one neo-grotesque family only (Inter Tight, Archivo, Space Grotesk),
  used across many weights and sizes.
- **Palette**: white `#ffffff`, black `#0a0a0a`, one signal color (Swiss red `#e30613`
  or international orange `#ff4d00`). Nothing else.
- **Signature moves**: strict visible grid; flush-left text, ragged right; huge type
  contrast (12px labels vs 96px headlines); uppercase micro-labels with `0.1em`
  tracking; elements aligned to an unapologetic baseline grid.
- **Radius/shadow**: 0 radius, no shadows.
- **Avoid**: rounded corners, soft colors, decorative illustration.

## 3. Brutalist / Raw Web

Best for: indie products, hacker tools, personal sites, anti-corporate brands.

- **Fonts**: monospace everywhere (JetBrains Mono, Space Mono) or mono + one raw
  grotesque; system fonts are acceptable here as a statement.
- **Palette**: raw white or paper `#fffff0`, black text, one acidic accent
  (`#0000ee` link blue used straight, or `#ccff00` acid yellow).
- **Signature moves**: visible `2px solid #000` borders on everything; default
  cursor styles; exposed structure (tables, raw lists); hover = invert colors;
  marquees or blinking elements used sparingly with intent.
- **Radius/shadow**: 0 radius, optional hard offset shadow (`4px 4px 0 #000`).
- **Avoid**: gradients, blur, anything "soft".

## 4. Neo-brutalist / Playful

Best for: consumer apps, creative tools, Gen-Z products, playful brands.

- **Fonts**: chunky display (Clash Display via Fontshare, Archivo Black, or Lexend Mega)
  + clean body (Archivo, Space Grotesk).
- **Palette**: cream background `#fffdf5`, black outlines, 2–3 saturated flat accents
  (`#ff6b6b`, `#4ecdc4`, `#ffd93d`) used as solid blocks.
- **Signature moves**: `2–3px solid #000` borders on all components; hard offset
  shadows (`4px 4px 0 #000`) that translate on hover (`2px 2px 0` + element moves);
  sticker-like rotated badges; flat color-block sections.
- **Radius**: small (6–10px) and consistent.
- **Avoid**: blur, gradients, thin borders, subtlety in general.

## 5. Minimal Luxury

Best for: premium products, fashion, finance, high-ticket services.

- **Fonts**: light-weight grotesque or elegant serif (Cormorant, Instrument Serif)
  for display; thin grotesque (Inter Tight 300–400) for body.
- **Palette**: deep charcoal `#0e0e0c` or warm stone `#f4f2ed` backgrounds; muted
  metallic accent (champagne `#c8b287`, sage `#9caf88`). Never saturated.
- **Signature moves**: extreme whitespace (sections 120px+ apart); small uppercase
  labels with `0.2em` tracking; hairline dividers; slow, long transitions
  (500–700ms ease-out); imagery given full-bleed room to breathe.
- **Radius/shadow**: 0–2px radius, shadow only as very soft ambient blur, rarely.
- **Avoid**: dense layouts, saturated color, anything loud.

## 6. Technical / Instrument Panel (dark)

Best for: dev tools, dashboards, infra/AI products, trading/data UIs.

- **Fonts**: geometric grotesque (Space Grotesk) for UI + mono (JetBrains Mono,
  IBM Plex Mono) for data, labels, and numbers.
- **Palette**: true dark background (`#0a0a0b` or `#0d1117`-style), borders at
  `#ffffff12`, text at `#e6e6e6` / `#8a8a8a`, ONE phosphor accent
  (`#00ff88`, `#4d9fff`, or `#ffb454`) used only for live/interactive states.
- **Signature moves**: `1px` hairline borders as the main container style (no cards
  with shadows); dense data rows with tabular numbers (`font-variant-numeric:
  tabular-nums`); status dots and mono micro-labels (`UPPERCASE 10–11px`);
  fine dot-grid or crosshair background texture at very low opacity.
- **Radius**: small and consistent (4–6px).
- **Avoid**: glow overload, purple gradients, big rounded panels.

## 7. Retro-futurism / Y2K

Best for: music, games, fashion, experimental brands.

- **Fonts**: display with character (Unbounded, Zen Dots, or Orbitron) + clean body.
- **Palette**: chrome/silver surfaces, black, plus holographic or single neon accent.
- **Signature moves**: metallic gradients (silver, not purple); outlined display type;
  scanline/grain overlays; star/sparkle motifs as SVG (never emoji).
- **Avoid**: combining with soft/rounded "friendly" SaaS patterns — commit fully.

## 8. Bauhaus

Best for: design studios, education, exhibitions, products that want intellectual confidence.

- **Fonts**: geometric sans only (Josefin Sans, Montserrat, or Archivo); uppercase
  display with wide tracking; type treated as geometric shape.
- **Palette**: white or raw canvas `#f2efe9`, black `#111111`, and the three primaries
  used flat and unmixed: red `#e63946`-style `#d62828`, yellow `#fcbf49`, blue
  `#1d4ed8`-style `#2255a4`. Never gradients, never pastels.
- **Signature moves**: pure geometry — circles, triangles, quarter-arcs, and bars as
  flat SVG shapes; diagonal compositions (rotate whole sections 5–15°); grid made
  visible with black rules; primary-color blocks used as wayfinding, one color per
  section; form follows function — zero ornament that doesn't structure.
- **Radius/shadow**: 0 radius (except true circles), no shadows.
- **Avoid**: rounded friendliness, decoration, muted palettes.

## 9. Art Deco

Best for: luxury events, hotels, spirits/jewelry brands, award sites, ceremonial pages.

- **Fonts**: engraved display (Cinzel, Marcellus) for headlines; light geometric
  (Poiret One) for sub-heads; small caps body (Cormorant or Jost).
- **Palette**: deep black `#0d0d0d` or midnight green `#0f1e1a`, metallic gold
  `#c9a227` with a lighter `#e6c86e` for highlights, cream `#f5eeda` for text.
- **Signature moves**: strict symmetry around a center axis; thin gold hairlines and
  double-ruled frames; fan / sunburst / chevron ornaments drawn as SVG (never emoji
  or clip-art); stepped, ziggurat-like section silhouettes; uppercase type with
  `0.3em` tracking; generous vertical ceremony — slow reveals fit here.
- **Radius/shadow**: 0 radius; glow only as a faint gold ambient on ornaments.
- **Avoid**: asymmetry, casual rounded UI, saturated modern colors.

## How to choose

- User gave a brand/aesthetic → follow it, borrow specs from the closest direction.
- Product type → suggested mapping above (dev tool → 6, premium service → 5, etc.).
- Genuinely unsure → direction 1 (Editorial) is the hardest to make look cheap.
