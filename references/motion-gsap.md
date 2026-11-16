# Motion with GSAP — high-end animation recipes

Motion is the layer that most separates award-level pages from generated ones — and
also where AI output fails hardest (animating everything, bounce easing, no reduced-
motion handling). This file is the single source for how this skill does motion.

## Setup

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<script src="https://unpkg.com/lenis@1.1.14/dist/lenis.min.js"></script>
```

```js
gsap.registerPlugin(ScrollTrigger);

// Smooth scroll (Lenis) wired into GSAP's ticker — this pairing is the standard
// for high-end sites. Skip Lenis only if the project forbids dependencies.
const lenis = new Lenis({ lerp: 0.1 });
lenis.on('scroll', ScrollTrigger.update);
gsap.ticker.add((t) => lenis.raf(t * 1000));
gsap.ticker.lagSmoothing(0);

// Always honor reduced motion. When set, render final states instantly.
const reduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
```

## Easing and timing rules

- Entrances: `expo.out` or `power3.out`. UI state changes: `power2.out`, 150–300ms.
- Never `bounce`/`elastic` on interfaces. Never linear except marquees.
- Stagger: 0.06–0.12s between siblings. Long cinematic moves: 0.8–1.4s.
- One choreography per view: the hero gets a timeline; everything else gets one
  simple scroll reveal. Stillness is a feature.

## Recipe 1 — Masked line-reveal headline (the signature entrance)

Split the headline into lines wrapped in overflow-hidden masks, then slide up.
Do it manually — no paid SplitText needed:

```html
<h1 class="hero-title">
  <span class="line"><span class="line-inner">Design is the</span></span>
  <span class="line"><span class="line-inner">silent ambassador</span></span>
</h1>
```
```css
.line { display: block; overflow: hidden; }
.line-inner { display: block; transform: translateY(110%); }
```
```js
if (!reduced) {
  gsap.timeline({ defaults: { ease: 'expo.out' } })
    .to('.line-inner', { y: 0, duration: 1.2, stagger: 0.12 }, 0.2)
    .from('.hero-meta', { opacity: 0, y: 20, duration: 0.8 }, '-=0.6');
}
```

## Recipe 2 — Scroll reveals (the only one you need)

```js
if (!reduced) {
  gsap.utils.toArray('[data-reveal]').forEach((el) => {
    gsap.from(el, {
      y: 40, opacity: 0, duration: 1, ease: 'expo.out',
      scrollTrigger: { trigger: el, start: 'top 85%', once: true },
    });
  });
}
```

Add `data-reveal` to section blocks. Resist the urge to invent a different reveal
per section — consistency reads as intention.

## Recipe 3 — Clip-path image reveal + parallax

```js
// Image unmasks as it enters
gsap.utils.toArray('[data-clip]').forEach((el) => {
  gsap.fromTo(el, { clipPath: 'inset(15% 8% 15% 8%)' }, {
    clipPath: 'inset(0% 0% 0% 0%)', ease: 'none',
    scrollTrigger: { trigger: el, start: 'top 90%', end: 'top 40%', scrub: true },
  });
});
// Parallax: inner image drifts slower than scroll
gsap.utils.toArray('[data-parallax] img').forEach((img) => {
  gsap.fromTo(img, { yPercent: -8 }, {
    yPercent: 8, ease: 'none',
    scrollTrigger: { trigger: img.parentElement, start: 'top bottom', end: 'bottom top', scrub: true },
  });
});
```

## Recipe 4 — Infinite marquee (linear is correct here)

```css
.marquee { overflow: hidden; white-space: nowrap; }
.marquee-track { display: inline-flex; animation: marquee 20s linear infinite; }
@keyframes marquee { to { transform: translateX(-50%); } }
```
Duplicate the track content once so `-50%` loops seamlessly. Pause on hover with
`animation-play-state: paused`. CSS handles marquees better than GSAP — no JS needed.

## Recipe 5 — Magnetic button (use on ONE primary CTA)

```js
const btn = document.querySelector('[data-magnetic]');
if (btn && !reduced && matchMedia('(pointer: fine)').matches) {
  btn.addEventListener('mousemove', (e) => {
    const r = btn.getBoundingClientRect();
    gsap.to(btn, { x: (e.clientX - r.left - r.width / 2) * 0.3,
                   y: (e.clientY - r.top - r.height / 2) * 0.3, duration: 0.4 });
  });
  btn.addEventListener('mouseleave', () =>
    gsap.to(btn, { x: 0, y: 0, duration: 0.6, ease: 'elastic.out(1, 0.4)' }));
}
```
`elastic` is acceptable here because the overshoot IS the interaction metaphor.

## Recipe 6 — Pinned horizontal section (use sparingly, max one per page)

```js
const track = document.querySelector('.h-track');
if (track && !reduced && matchMedia('(min-width: 768px)').matches) {
  gsap.to(track, {
    x: () => -(track.scrollWidth - window.innerWidth), ease: 'none',
    scrollTrigger: { trigger: '.h-section', start: 'top top',
      end: () => `+=${track.scrollWidth - window.innerWidth}`,
      pin: true, scrub: 1, invalidateOnRefresh: true },
  });
}
```
On mobile, fall back to a normal vertical stack — pinned horizontal scroll on touch
devices is a usability regression.

## Anti-patterns (motion edition)

| Tell | Fix |
|---|---|
| Every element animates on load | One hero timeline; rest is still until scrolled to |
| `bounce`/`elastic` on cards and modals | `expo.out`; elastic only for magnetic/drag metaphors |
| Animating `top/left/width/height` | Transform + opacity only (GPU-composited) |
| Scroll-jacking that fights the user | Lenis `lerp 0.1` smooths; never hijack scroll delta |
| No `prefers-reduced-motion` handling | Gate all GSAP setup behind the `reduced` flag |
| Reveal animations replaying on every scroll | `once: true` on entrance ScrollTriggers |
| Motion without a resting state | Every animation ends at a stable, readable layout |
