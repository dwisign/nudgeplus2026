# Nudgeplus Design System

The design standard for the Nudgeplus 2026 site. **`style.css` is the single stylesheet for every page.** It holds all tokens and components; `homepage2.html` is the reference page that shows them in use.

Pages built on this system:

| Page | Stylesheet | Notes |
|---|---|---|
| `homepage2.html` | `style.css` | **Reference page.** Hero visual, logo ticker, grants carousel, services, KALIBER, proof, news, testimonials |
| `services.html` | `style.css` | Inner page: KALIBER, formats, projects, sectors, process + FAQ |
| `academy.html` | `style.css` | Inner page: track selector, modules, events, formats |
| `gap-finder.html` | `style.css` + page `<style>` | Quiz widget. Its page styles use shared tokens only |
| `team.html` | `style.css` | Inner page: team grid |

> Every token and component lives in `style.css`. Don't create per-page stylesheets. If a page needs a new component, add it to `style.css` under a `/* SECTION NAME */` comment.

---

## 1. Design principles

1. **Warm, editorial, evidence-led.** Use white and warm ivory surfaces, a sage-teal primary, and an orange call to action. It should read like a research journal, not a SaaS dashboard.
2. **Square cards, pill buttons.** All card radii are `0`. Only buttons, badges and avatars are rounded.
3. **One serif accent per heading.** Headings use Inter. The key word or phrase goes in `<em>`, which renders in *Instrument Serif* italic, teal.
4. **Orange is for conversion.** `--secondary` (orange) is reserved for the main CTA (WhatsApp / "Talk to us"), the pulse dot, footer column headings, timeline dots and the "featured" badge. Everything else uses teal.
5. **Quiet motion.** Cards lift 3–4px on hover. Sections fade up once on scroll (`.sr`). Nothing bounces or loops, apart from the hero pulse dot and the logo ticker.

---

## 2. Design tokens

All tokens are CSS custom properties on `:root`. **Never hard-code a color, font, shadow or easing that already has a token.**

### 2.1 Color: surfaces

| Token | Value | Use |
|---|---|---|
| `--bg` | `#ffffff` | Page background, default sections, hero |
| `--surface` | `#ffffff` | Buttons, stat tiles, inputs |
| `--surface-subtle` | `#f6f4ee` | Warm ivory band for alternating sections (`#services`, `#testimonials`, `#formats`, FAQ) |
| `--surface-card` | `#ffffff` | Card fill |
| `--surface-dark` | `#0f172a` | Reserved, not currently used |

### 2.2 Color: brand

| Token | Value | Use |
|---|---|---|
| `--primary` | `#2d8a85` | Teal. Links, tags, `<em>`, stat numbers, primary buttons, footer bottom bar |
| `--primary-hover` | `#236f6b` | Hover for primary |
| `--primary-dark` | `#19524f` | Deep teal |
| `--primary-light` | `rgba(45,138,133,.08)` | Tinted fills: featured card gradient, `.btnb` hover, selected option |
| `--primary-border` | `rgba(45,138,133,.22)` | Featured card border, outline buttons |
| `--primary-glow` | `rgba(45,138,133,.18)` | Glow shadow on `.ncta`, avatars |
| `--secondary` | `#e68400` | Orange. Main CTA, `#cta h2`, footer `h4`, dots, badges |
| `--secondary-hover` | `#cc7600` | |
| `--secondary-dark` | `#a35f00` | |
| `--secondary-light` | `rgba(230,132,0,.08)` | |
| `--secondary-border` | `rgba(230,132,0,.25)` | `.fmt.featured` border |
| `--secondary-glow` | `rgba(230,132,0,.18)` | |

The gradient used on hover bars and avatars is `linear-gradient(135deg, var(--primary) 0%, #165b57 100%)`.

### 2.3 Color: warm accents (Ascone-style neutrals)

| Token | Value | Use |
|---|---|---|
| `--accent-gold` | `#b08d4f` | Star ratings, award-badge text, `.kcopy-box strong` |
| `--accent-gold-bg` | `#efe8d6` | Award badge and notice box fill |
| `--accent-gold-border` | `#e2d9c2` | |
| `--accent-mint-bg` | `#dbe6e1` | Highlight tile fill |
| `--accent-mint-border` | `#c7d6cf` | |

### 2.4 Color: text and borders

| Token | Value | Use |
|---|---|---|
| `--text` | `#16221e` | Headings and body (a green-black, not pure black) |
| `--text-muted` | `#6b756f` | Paragraphs, leads, nav links |
| `--text-dim` | `#98a19b` | Meta, captions, breadcrumbs, labels |
| `--text-inverse` | `#ffffff` | Text on teal or orange |
| `--border` | `rgba(22,34,30,.09)` | Default hairline |
| `--border-strong` | `rgba(22,34,30,.16)` | `.btnb` outline |
| `--border-hover` | `rgba(45,138,133,.35)` | Hover border |

### 2.5 Typography

| Token | Value |
|---|---|
| `--font-H` | `'Inter', -apple-system, BlinkMacSystemFont, sans-serif` (headings) |
| `--font-B` | `'Inter', -apple-system, BlinkMacSystemFont, sans-serif` (body) |
| `--font-mont` | `'Inter', sans-serif` (KALIBER wordmark, brand emphasis) |
| `--font-em` | `'Instrument Serif', serif` (italic accent inside headings) |

Load the fonts once per page, before `style.css`:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:ital,wght@0,400;0,500;0,600;0,700;0,800;0,900;1,400&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet">
```

### 2.6 Radius

| Token | Value |
|---|---|
| `--radius-sm` / `--radius-md` / `--radius-lg` / `--radius-xl` | `0` (square) |
| `--radius-pill` | `9999px` (buttons, badges, kicker, "show more") |

Always reference the token, e.g. `border-radius: var(--radius-xl)`, rather than writing `0`. That way a future radius change is a one-line edit. Circles (avatars, dots, team photos) use `50%`.

### 2.7 Shadow

| Token | Value | Use |
|---|---|---|
| `--shadow-sm` | `0 2px 8px rgba(22,34,30,.04)` | FAQ items, small buttons |
| `--shadow-md` | `0 10px 30px -5px rgba(22,34,30,.06)` | Button hover |
| `--shadow-lg` | `0 20px 40px -10px rgba(45,138,133,.14)` | Large floating elements |
| `--shadow-card` | `0 1px 3px rgba(0,0,0,.04), 0 10px 25px -5px rgba(22,34,30,.04)` | **Default card resting state** |
| `--shadow-card-hover` | `0 20px 35px -8px rgba(45,138,133,.14), 0 1px 3px rgba(0,0,0,.04)` | **Default card hover state** |

### 2.8 Motion

| Token | Value | Use |
|---|---|---|
| `--transition-fast` | `0.2s cubic-bezier(.4,0,.2,1)` | Color, border, button lift |
| `--transition-normal` | `0.3s cubic-bezier(.4,0,.2,1)` | Card lift and shadow |
| Scroll reveal | `0.6s cubic-bezier(.16,1,.3,1)` | `.sr`, which moves from `translateY(20px)` and opacity 0 |

---

## 3. Type scale

| Element | Size | Weight | Line-height | Tracking | Notes |
|---|---|---|---|---|---|
| `h1` | `clamp(2.6rem, 5.4vw, 4rem)` | 700 | 1.04 | -0.02em | One per page, in the hero. `text-wrap: balance` |
| `h2` | `clamp(2rem, 4vw, 2.9rem)` | 700 | 1.2 | -0.015em | Section title. `text-wrap: balance` |
| `h1 em`, `h2 em` | inherit | 400 | | | `--font-em`, italic, `--primary` |
| Card `h3` (e.g. `.svc h3`) | 1.35rem | 800 | 1.25 | | |
| `body` | 16px | 400 | 1.7 | | Antialiased |
| `.hsub` (hero sub) | 1.15rem | 400 | 1.8 | | max-width 660px, `--text-muted` |
| `.lead` (section intro) | 1.05rem | 400 | 1.75 | | max-width 640px, `--text-muted`, mb 2.5rem |
| `.tag` (eyebrow) | 0.72rem | 700 | | 0.14em | Uppercase, `--primary`, no background |
| Card eyebrow (`.pcsvc`, `.tcctx`) | 0.68rem | 800 | | 0.12em | Uppercase, `--primary` |
| Meta / source (`.pcs`) | 0.72rem | 700 | | 0.06em | Uppercase, `--text-dim`, top hairline |
| Big stat (`.pcn`) | 3.2rem | 800 | 1 | -0.06em | `--primary` |
| Hero stat (`.hs-n`) | 2.2rem | 800 | 1 | -0.04em | `--primary` |

**Heading pattern.** Break the line with `<br>` and put the payoff word in `<em>`:

```html
<h2 id="proof-h2">What the work has<br><em>produced.</em></h2>
```

---

## 4. Layout

| Rule | Value |
|---|---|
| Container | `.container`: max-width **1340px**, centered, side padding **2rem** |
| Section rhythm | `section { padding: 128px 0 }`, dropping to **72px** at ≤768px |
| Hero | `min-height: 92vh`, `padding-top: 200px` (clears the fixed 76px nav), `padding-bottom: 80px` |
| CTA section | `padding: 110px 0`, centered, inner max-width 680px |
| Card grid gap | **1.5rem** throughout (`.scards`, `.pgrid`, `.tgrid`, `.team-grid`) |
| Section backgrounds | Alternate `--bg` (white) and `--surface-subtle` (ivory). Ivory bands get `border-top` and `border-bottom: 1px solid var(--border)` |

### Breakpoints

Desktop-first `max-width` queries. Use these values; don't invent new ones.

| Breakpoint | What changes |
|---|---|
| `1024px` | Logo grid density |
| `960px` | 3-col grids go to 2-col (team grid) |
| **`900px`** | **Main collapse point.** Hero goes to 1 column, card grids go to 1 column, nav switches to burger |
| `768px` | Section padding drops to 72px. Footer goes to 2 columns |
| `700px` | 2-col proof grid goes to 1 column. WhatsApp button becomes icon-only |
| `640px` | Small-screen card padding. Team grid goes to 1 column |
| `560px` | Footer goes to 1 column |

---

## 5. Page skeleton

Every page follows this order. Copy the shared blocks (nav, mobile menu, WhatsApp, CTA, footer, scripts) from `homepage2.html` verbatim and change only the active link.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page | Nudgeplus</title>
  <meta name="description" content="…">
  <link rel="canonical" href="https://nudgeplus.net/…">
  <!-- OG + Twitter meta -->
  <!-- Fonts (§2.5) -->
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <!-- NAVIGATION -->        <nav id="navbar">…</nav>
  <!-- MOBILE MENU -->       <div class="mobile-overlay" id="mobileOverlay"></div>
                             <div class="mobile-menu" id="mobileMenu">…</div>
  <!-- FLOATING WHATSAPP --> <a class="wa">…</a>
  <!-- HERO -->              <section id="hero">…</section>
  <!-- SECTIONS -->          <section id="…" aria-labelledby="…-h2">…</section>
  <!-- CTA -->               <section id="cta">…</section>
  <!-- FOOTER -->            <footer aria-label="Site footer">…</footer>
  <script>/* nav scroll, dropdown, mobile menu, .sr observer */</script>
</body>
</html>
```

**Conventions**

- Mark each block with an uppercase HTML comment: `<!-- SERVICES -->`.
- Section IDs are short lowercase nouns (`#services`, `#proof`, `#tracks`, `#team`). They double as anchor targets.
- Every content section has `aria-labelledby` pointing at its `h2` id (`services-h2`, `team-h2`).
- Decorative elements get `aria-hidden="true"`. SVG icons always get `aria-hidden="true"` plus a `viewBox`.
- External links always get `target="_blank" rel="noopener"`.

---

## 6. Components

### 6.1 Navigation

Fixed, 76px tall, white, `z-index: 300`. There is no border; JS adds `.scrolled` after 20px, which applies a soft shadow.

```html
<nav id="navbar" aria-label="Main navigation">
  <div class="container nav-inner">
    <a href="index.html" class="logo" aria-label="Nudgeplus home">
      <img src="image/Nudgeplus_transparent.png" alt="Nudgeplus" class="logo-img">
    </a>
    <div class="navr">
      <a href="homepage2.html" class="nl">Home</a>
      <a href="services.html" class="nl active" aria-current="page">Services</a>
      <a href="academy.html" class="nl">Training</a>
      <div class="nl-drop">
        <button type="button" class="nl nl-drop-btn" aria-haspopup="true" aria-expanded="false">
          News & Update
          <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M6 9l6 6 6-6"/></svg>
        </button>
        <div class="nl-drop-menu" role="menu">
          <a href="…" role="menuitem">News</a>
        </div>
      </div>
      <a href="team.html" class="nl">The Team</a>
      <a href="https://wa.me/…" class="ncta" target="_blank" rel="noopener">Talk to us</a>
    </div>
    <button type="button" class="nav-burger" id="navBurger" aria-label="Open menu"
            aria-expanded="false" aria-controls="mobileMenu"><span></span><span></span><span></span></button>
  </div>
</nav>
```

- `.nl` links are 0.9rem/600, `--text-muted`. On hover they turn teal and a 2px teal underline grows from 0 to 100%.
- **Current page:** add `class="nl active"` and `aria-current="page"`. Homepage2 itself has no active link.
- `.ncta` is the teal pill CTA with a `--primary-glow` shadow.
- Mobile uses an off-canvas `.mobile-menu` (with `.mnl` links and a `.mnl-drop` accordion) and a `.mobile-overlay`. Toggle `.open` on both, set `aria-hidden` and `aria-expanded`, and lock body scroll.

### 6.2 Buttons

| Class | Look | Use |
|---|---|---|
| `.btna` | Teal fill, white text, pill, `0.85rem 1.7rem`, 0.9rem/600 | Primary action |
| `.btna.btn-orange` | Orange fill. Hover gives an orange gradient and glow | **The** conversion CTA (WhatsApp / free call). Use at most one per view |
| `.btnb` | White fill, 1.5px `--border-strong` outline. Hover gives a teal border, teal text, `--primary-light` fill and 2px lift | Secondary action |
| `.ncta` | Compact teal pill | Nav only |
| `.scta` | Teal text link with top hairline. Arrow gap widens on hover | Card footer link: "Explore … →" |
| `.smbtn` | White pill with teal outline. Fills teal on hover | "Show more" toggles |
| `.kmore` | Teal text link | Inline "Full explanation →" |

A WhatsApp button pairs the `.wsv` icon (17px, `fill: currentColor`) with its label:

```html
<a href="https://wa.me/447729735806?text=…" class="btna btn-orange" target="_blank" rel="noopener">
  <svg class="wsv" viewBox="0 0 24 24" aria-hidden="true">…</svg>
  Describe Your Challenge — Free Call
</a>
<a href="#services" class="btnb">Explore Services</a>
```

Group buttons in `.hctas` (hero) or `.ctabtns` (CTA): flex, `gap: 1rem`, wrapping.

### 6.3 Hero

**Home variant** (two columns: text left, animated visual right):

```html
<section id="hero">
  <div class="hgrid" aria-hidden="true"></div>       <!-- faint 64px grid, radially masked -->
  <div class="container">
    <div class="hc">                                   <!-- 1.3fr / 0.7fr, gap 4rem -->
      <div class="hc-left">
        <div class="hkick"><div class="hdot" aria-hidden="true"></div>Kicker text · Since 2019</div>
        <h1>Headline line one<br>then the <em>payoff.</em></h1>
        <p class="hsub">…</p>
        <div class="hctas">…buttons…</div>
      </div>
      <div class="hc-right">…</div>
    </div>
    <div class="hstats" role="list" aria-label="Key results">
      <div class="hs" role="listitem"><div class="hs-n">30%</div><div class="hs-l">Label · source</div></div>
      <!-- ×4 -->
    </div>
  </div>
</section>
```

**Inner-page variant** (single column with breadcrumb), used by services, academy and team:

```html
<section id="hero" class="hero-white">
  <div class="hgrid" aria-hidden="true"></div>
  <div class="container">
    <div class="hc single">
      <div class="hc-left">
        <div class="hbreadcrumb" aria-label="Breadcrumb">
          <a href="index.html">nudgeplus.net</a><span>›</span><span class="current">Page</span>
        </div>
        <div class="hbadges">
          <div class="hkick" style="margin-bottom:0"><div class="hdot" aria-hidden="true"></div>…</div>
          <div class="hbadge-award">🏆 Award name</div>   <!-- optional, gold pill -->
        </div>
        <h1>…<em>…</em></h1>
        <p class="hsub">…</p>
        <div class="hctas">…</div>
        <div class="hstats" role="list">…</div>
      </div>
    </div>
  </div>
</section>
```

- `.hkick` is teal 0.8rem/700 text. It is preceded by `.hdot`, an 8px orange dot that pulses.
- `.hstats` is a 4-column grid of square white `.hs` tiles with a hairline border.
- `.hero-white` forces a plain white background. It is optional, because `#hero` is already white, but inner pages keep it to stay explicit.

### 6.4 Section header

Every content section opens with this trio:

```html
<section id="services" aria-labelledby="services-h2">
  <div class="container">
    <span class="tag">what we offer</span>
    <h2 id="services-h2">Pioneer in behavioral science.<br>Two ways to <em>engage.</em></h2>
    <p class="lead">One or two sentences, max ~640px wide.</p>
    <!-- content grid -->
  </div>
</section>
```

### 6.5 Cards

All cards share the same base: square corners, `--surface-card` fill, `--shadow-card`, `--transition-normal`. On hover they lift (`translateY(-3px)` or `-4px`) and switch to `--shadow-card-hover`. Add `.sr` to each card for the scroll reveal.

| Card | Grid | Border | Anatomy |
|---|---|---|---|
| **Service** `.svc` | `.scards` (3-col) | none. A 4px teal gradient bar appears on top on hover | `.snum` (big dim number) → `h3` → `p` → `ul > li` (teal check SVG) → `.scta` |
| **Proof / result** `.pc` | `.pgrid` (3-col), `.pgrid.pg2` (2-col) | 1.5px `--border`, `--primary-border` on hover | `.pcsvc` eyebrow → `.pcn` big number → `.pcd` claim → `.pce` italic quote → `.pcs` source |
| **Testimonial** `.tc` | `.tgrid` (3-col) | none | `.tcs` gold stars → `.tcctx` eyebrow → `blockquote.tcq` → `.tcp` (`.tcav` initials avatar + `.tcnm` / `.tcrl`) |
| **Format / pricing** `.fmt` | `.formats-grid` | 1.5px `--border` | `.fmt-tag` → `h3` → `.fmt-duration` → `.fmt-desc` → `.fmt-list` → `.fmt-foot` |
| **Team** `.team-card` | `.team-grid` (3 → 2 → 1 col) | none | `.team-head` (`img.team-photo` 72px circle + `.team-name` / `.team-role`) → `.team-bio` → `.team-social > a.team-li` |
| **News** `.news-card` | `.news-row` (horizontal scroll-snap) | 1px `--border` | `.news-thumb` → `.news-title` → `.news-readmore` |

**Featured modifiers:**

- `.pc.ft` and `.tc.ft` get a white-to-`--primary-light` vertical gradient (and `.pc.ft` also gets a `--primary-border`). Use them to highlight the strongest proof point.
- `.fmt.featured` gets a `--secondary-border` and an orange shadow, plus a `.fmt-badge` orange pill pinned at `top: -13px`.

Example (proof card):

```html
<div class="pc ft sr">
  <div class="pcsvc">Consultancy · British Embassy × East Java</div>
  <div class="pcn">30%</div>
  <div class="pcd">Increase in handwashing compliance — one low-cost nudge during COVID-19</div>
  <div class="pce">"Quote…" — Name, Role</div>
  <div class="pcs">Published: Journal · 2022 · DOI …</div>
</div>
```

Example (team card):

```html
<div class="team-card sr">
  <div class="team-head">
    <img class="team-photo" src="…" alt="Full Name" loading="lazy">
    <div>
      <div class="team-name">Full Name</div>
      <div class="team-role">Role</div>
    </div>
  </div>
  <p class="team-bio">…</p>
  <div class="team-social">
    <a class="team-li" href="…" target="_blank" rel="noopener" aria-label="Full Name on LinkedIn">
      <svg viewBox="0 0 24 24" aria-hidden="true">…</svg>
    </a>
  </div>
</div>
```

### 6.6 Accordions

- **KALIBER steps** `.kstep` (inside `.ksteps`): flat rows separated by a bottom hairline. Each `.ksh` header holds `.klt` (teal letter), `.knm` (name), `.ktg` (step tag) and `.kcv` (chevron). `.kbod` holds the body. Toggle `.open` with `toggleK(el)`. Headers carry `tabindex="0"` and open on Enter.
- **FAQ** `.faq` (inside `.faq-list`): bordered white boxes. `.faq-q` holds `.faq-qt` and `.faq-icon`, and `.faq-a` holds the answer. Toggle `.open`.
- **Academy modules** `.mod`: `.modh` holds `.modcode`, `.modtitle`, `.moddur` and `.modchev`, and `.modb` holds the body. Toggle `.open`.

### 6.7 KALIBER wordmark

```html
<div class="kwm sr" aria-label="KALIBER">
  <span class="kl">K</span><span class="kg">A</span><span class="kl">L</span><span class="kg">I</span><span class="kl">B</span><span class="kg">E</span><span class="kl">R</span>
</div>
```

The letters alternate teal (`.kl`) and dim (`.kg`) at 900 weight. In running text, write the brand as `<strong style="color:var(--primary);font-family:var(--font-mont);font-weight:900">KALIBER</strong>`.

### 6.8 Trust strips

- **Logo ticker** `#logos > .ticker-wrap > .ticker-track > .tlogo`: monochrome logos that auto-scroll. Duplicate the full set (with `aria-hidden="true"`) for a seamless loop. Give each real logo `role="img"` and an `aria-label`. The label above it is `.llbl` (uppercase, dim, centered).
- **Grants timeline** `.awards-wrapper > .splide.grants-splide`: a Splide 4.1.4 carousel. Each `li.grants-item` holds `.grants-year`, `.grants-dot-row > .grants-dot` (orange), `.grants-title`, `.grants-desc` and `.grants-more`. Arrows and pagination only appear when slides exceed `perPage`.
- **Publication strip** `.pubstrip > .publist > .pub`: `.pubbdg.aw` (award) or `.pubbdg.pr` (peer-reviewed) badges, plus `.pubt` and `.pubm`.

### 6.9 CTA section

Centered, transparent background, with two soft radial glows (`.ctabg`, teal and gold). The `h2` is **orange** (`#cta h2 { color: var(--secondary) }`).

```html
<section id="cta">
  <div class="ctabg" aria-hidden="true"></div>
  <div class="container">
    <div class="ctain">
      <span class="tag">Start the Conversation</span>
      <h2>Not sure where to start?<br>Describe your <em>situation.</em></h2>
      <p class="ctasub">…</p>
      <div class="ctabtns">
        <a class="btna" href="https://wa.me/…">…WhatsApp — Free Scoping Call</a>
        <a class="btnb" href="mailto:info@nudgeplus.net" style="background:rgba(255,255,255,0.08); color:#e68400; border-color:#e68400">Email info@nudgeplus.net</a>
      </div>
      <p class="ctanote">Free · No commitment · <span>We respond within 1 business day</span></p>
    </div>
  </div>
</section>
```

### 6.10 Footer

White, with a hairline top border. `.ftgrid` is `1.8fr 1fr 1fr 1fr`; the `.ft-brand` column spans 2 rows. It collapses to 2 columns at ≤768px and 1 column at ≤560px. Column headings `.fc h4` are **orange**, uppercase, 0.75rem/800. The bottom bar `.fbot` is a **solid teal** band with white text.

### 6.11 Floating WhatsApp

`.wa` is fixed bottom-right (`2rem`), `z-index: 400`, green gradient `#25D366 → #128C7E`. It shows an icon plus `.wa-text`, and becomes a 52px icon-only circle at ≤700px. Include it on every page.

---

## 7. Behaviour (JS)

Each page has an inline `<script>` before `</body>` with these behaviours. Keep the names identical across pages.

| Behaviour | Hook |
|---|---|
| Nav shadow | Add `.scrolled` to `#navbar` when `scrollY > 20` |
| Desktop dropdown | Click `.nl-drop-btn` to toggle `.nl-drop.open` and `aria-expanded`. Clicking outside closes it |
| Mobile menu | `#navBurger`, `#mobileMenu`, `#mobileOverlay`, `#mobileClose` toggle `.open`. Body scroll is locked |
| Scroll reveal | `IntersectionObserver` with `{ threshold: 0.07, rootMargin: '0px 0px -24px 0px' }`. It adds `.vis` to `.sr` once, then unobserves |
| KALIBER accordion | `toggleK(el)` |
| Show more | `showMore(btn)` opens `.more-grid` and staggers `.vis` at 80ms per item |
| Carousel | Splide 4.1.4 from jsDelivr (`splide-core.min.css` + `splide.min.js`). Only load it on pages that use `.grants-splide` |

---

## 8. Do / Don't

**Do**
- Use tokens for every color, shadow, radius and transition.
- Start each section with `.tag` → `h2` (with one `<em>`) → `.lead`.
- Alternate white and ivory section bands.
- Add `.sr` to cards and major blocks so they reveal on scroll.
- Keep one orange `.btna.btn-orange` per view.
- Reuse existing classes before writing new ones. When a page needs a new component, put it in the stylesheet under a `/* SECTION NAME */` comment, not in inline styles.

**Don't**
- Don't add `border-radius` values to cards. They stay square.
- Don't use pure black (`#000`) or cool slate greys. The neutrals are warm and green-tinted.
- Don't put orange on body links or decorative elements.
- Don't use more than one `<em>` accent per heading. (Testimonials currently uses two; avoid repeating that.)
- Don't add new inline `style=""` attributes. Existing ones (e.g. the eyebrow under `.svc h3` or the CTA email button) should be promoted to classes over time.
- Don't add new breakpoints outside the list in §4.

---

## 9. Adding a new page: checklist

1. Duplicate the closest existing inner page (`team.html` is the leanest).
2. Update `<title>`, meta description, canonical and OG tags.
3. Move `class="nl active" aria-current="page"` to the correct nav link.
4. Use the inner hero (`#hero.hero-white > .hc.single`) with a breadcrumb.
5. Build sections with the section header pattern (§6.4) and the existing card types (§6.5).
6. Keep the shared CTA, footer, WhatsApp button and script block unchanged.
7. Add the page to the footer and mobile menu links on **all** pages.
8. Check it at 1340, 900, 768 and 375px widths.

---

## 10. Stylesheet structure

`style.css` is organised top to bottom in this order. Add new rules to the matching section; don't append them to the end of the file.

1. `:root` tokens
2. Reset, `body`, `.container`, `section`
3. Typography and tags (`.tag`, `h2`, `.lead`)
4. Buttons (`.btna`, `.btnb`)
5. Scroll reveal (`.sr`)
6. Nav, dropdown, burger, mobile menu
7. Floating WhatsApp
8. Hero (`#hero`, `.hero-white`, `.hc`, video and animated visual, `h1`, `.hstats`, video modal)
9. Logos wall and ticker
10. Team grid
11. Awards and the grants timeline (Splide)
12. KALIBER
13. Services
14. Proof (cards, pinned scroll panels, publication strip)
15. News and articles
16. Testimonials
17. CTA
18. Footer
19. Inner-page shared pieces (active nav, breadcrumb, badges, KALIBER notice)
20. Services page: formats, pricing, projects, sectors, process + FAQ, gallery, lightbox
21. Academy page: track selector, modules, help-me-choose, KALIBER tiles, feature cards, events, 4-col formats

Each section starts with an uppercase comment, e.g. `/* TESTIMONIALS SECTION */`. Responsive overrides sit directly below the rule they modify, not in a block at the end of the file.
