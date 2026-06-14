# GAHIZ DESIGN SYSTEM
## Extracted from UI/UX Pro Max Skill v2.5.0 — Locked for All Roles
### This section governs every UI component, page, and screen Claude builds for Gahiz.

---

## PART A — PRODUCT CLASSIFICATION

Gahiz maps to two product categories from the UI/UX Pro Max database:

| Primary Match | **Educational App / Career Prep Platform** |
|---|---|
| Secondary Match | **B2B Service + Trust & Authority** |
| Closest Color Palette | Educational App (#9 in database) + customized to Gahiz brand |
| Landing Pattern | **Funnel (3-Step Conversion)** + **Hero-Centric Design** |
| Dashboard Pattern | **User Behavior Analytics** style |

---

## PART B — LOCKED DESIGN SYSTEM (GAHIZ-SPECIFIC)

### B1. Color Tokens

These are the ONLY colors used across all Gahiz UI. Never deviate.

```css
:root {
  /* Brand Core */
  --gahiz-crimson: #DC143C;        /* Primary CTA, score highlights, verdict badges */
  --gahiz-black: #080808;          /* Page backgrounds, dark sections, nav */
  --gahiz-off-white: #F4F4F2;      /* Body backgrounds, card surfaces */

  /* Semantic Tokens */
  --primary: #DC143C;
  --primary-foreground: #FFFFFF;
  --background: #F4F4F2;
  --foreground: #080808;
  --card: #FFFFFF;
  --card-foreground: #080808;
  --muted: #E8E4E0;
  --muted-foreground: #5A5450;
  --border: #D8D4D0;
  --destructive: #DC143C;
  --destructive-foreground: #FFFFFF;
  --ring: #DC143C;

  /* Score Dimension Colors (always used in this order) */
  --score-clarity: #2563EB;        /* Blue */
  --score-confidence: #DC143C;     /* Crimson */
  --score-relevance: #059669;      /* Green */
  --score-fluency: #D97706;        /* Amber */
  --score-energy: #7C3AED;         /* Purple */

  /* Verdict Colors */
  --verdict-pass: #059669;         /* Green */
  --verdict-borderline: #D97706;   /* Amber */
  --verdict-fail: #DC143C;         /* Crimson */

  /* UI Functional */
  --success: #059669;
  --warning: #D97706;
  --info: #2563EB;
  --shadow-card: rgba(8, 8, 8, 0.08);
  --shadow-cta: rgba(220, 20, 60, 0.35);
}
```

### B2. Typography System

**Heading Font:** Barlow Condensed — Bold, uppercase for impact. Used for all H1–H3.
**Body Font:** Cairo — Arabic-first, excellent Latin support. Required for all Arabic copy.
**Score Labels:** Always in English. Always in Barlow Condensed or Inter Medium.
**Fallback Stack:** system-ui, sans-serif

```css
/* Google Fonts Import */
@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@600;700;800&family=Cairo:wght@400;500;600;700;900&family=Inter:wght@400;500;600;700&display=swap');

/* Type Scale */
--font-display: 'Barlow Condensed', sans-serif;   /* Hero headlines, verdict badges */
--font-arabic: 'Cairo', sans-serif;               /* All Arabic UI copy */
--font-english: 'Inter', sans-serif;              /* Score labels, English body copy */

/* Scale */
--text-hero: clamp(2.5rem, 8vw, 5rem);    /* Landing page hero */
--text-h1: clamp(2rem, 5vw, 3.5rem);
--text-h2: clamp(1.5rem, 3vw, 2.25rem);
--text-h3: clamp(1.125rem, 2vw, 1.5rem);
--text-body: 1rem;                          /* 16px — never smaller on mobile */
--text-small: 0.875rem;                    /* 14px */
--text-caption: 0.75rem;                   /* 12px */

/* Arabic-specific line heights */
--leading-arabic: 1.8;   /* Arabic text needs more breathing room */
--leading-english: 1.5;
```

**Rationale from typography database:**
- Barlow Condensed delivers the "bold, direct, tough mentor" personality — it's a compressed display font used in sports/performance branding, which matches Gahiz's BPO stamina theme
- Cairo is the only Google Font with full Arabic support that also works in English — critical for bilingual RTL/LTR switching
- This pairing replaces the previously used Plus Jakarta Sans/Fraunces pair — Barlow Condensed is more on-brand for the "no-nonsense" voice

---

## PART C — LANDING PAGE PATTERN (gahiz.eg/start)

**Pattern from database:** Funnel (3-Step Conversion) + Hero-Centric Design

```
Section Order:
1. Hero (full-bleed, dark #080808 bg)
   - Headline: Barlow Condensed, bold, uppercase
   - Subhead: Cairo Arabic, colloquial tone
   - Single CTA: WhatsApp link button, --gahiz-crimson
   - No nav clutter above fold

2. Problem Strip (dark bg)
   - 3 pain points with icons
   - Short Arabic sentences — max 1 line each

3. Step 1 — Problem (crimson accent)
   - Stage 1: The Hero (60 seconds)

4. Step 2 — Process (amber accent)
   - Stage 2: The Warning (120 seconds)
   - Stage 3: The Wall (240 seconds)

5. Step 3 — Action (green accent)
   - Moment of Truth reveal
   - 200 EGP conversion option

6. Social Proof
   - 3 candidate testimonials with before/after scores
   - Score bars (5 dimensions) shown visually

7. Final CTA (crimson section)
   - Single WhatsApp button, centered
   - Fawry + Vodafone Cash logos below

8. Footer (minimal)
```

**Color Strategy per section (from landing.csv):**
- Step 1 (Problem): Crimson/Red tone — urgency
- Step 2 (Process): Amber/Orange — transition
- Step 3 (Action): Green — resolution + success
- CTA: #DC143C with shadow: rgba(220, 20, 60, 0.35)

---

## PART D — UI STYLE RULES (from styles.csv)

**Primary Style:** Trust & Authority + Flat Design
**Secondary Style:** Micro-interactions with purpose

### What This Means in Code:

```css
/* Cards */
.gahiz-card {
  background: #FFFFFF;
  border: 1px solid var(--border);
  border-radius: 0px;               /* Sharp edges — not rounded. Gahiz is tough, not soft. */
  box-shadow: 0 2px 12px var(--shadow-card);
  padding: 24px;
}

/* CTAs */
.gahiz-btn-primary {
  background: #DC143C;
  color: #FFFFFF;
  border-radius: 0px;               /* No border radius — sharp, direct */
  padding: 14px 28px;
  font-family: 'Barlow Condensed', sans-serif;
  font-weight: 700;
  font-size: 1rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  transition: all 200ms ease-out;
  box-shadow: 0 4px 16px rgba(220, 20, 60, 0.3);
}
.gahiz-btn-primary:hover {
  background: #b8102f;
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(220, 20, 60, 0.4);
}

/* Score bars */
.score-bar {
  height: 6px;
  border-radius: 0px;
  background: var(--muted);
}
.score-fill {
  height: 100%;
  transition: width 1.2s ease-out;
  /* Color from score dimension tokens */
}

/* Verdict badge */
.verdict-pass    { background: #059669; color: #fff; }
.verdict-borderline { background: #D97706; color: #fff; }
.verdict-fail    { background: #DC143C; color: #fff; }
.verdict-badge {
  font-family: 'Barlow Condensed', sans-serif;
  font-weight: 800;
  font-size: 1.25rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  padding: 6px 16px;
  border-radius: 0px;
}
```

### Micro-interaction Rules (from ux-guidelines.csv):
- All hover transitions: **200ms ease-out** — never longer than 300ms
- Button press scale: **0.97** — subtle, not playful
- Score bar fill: **1.2s ease-out** on mount — makes score feel earned
- Skeleton loading on all async content — no blank states
- Reduced motion: always respect `prefers-reduced-motion`

---

## PART E — ANTI-PATTERNS (NEVER USE IN GAHIZ)

From the UI/UX Pro Max reasoning database — these are violations:

| ❌ Anti-Pattern | Why It Kills Gahiz |
|---|---|
| AI purple/pink gradients (#6366F1, pink-to-purple) | Generic AI aesthetic — destroys trust signal |
| Rounded corners everywhere (border-radius > 8px) | Makes Gahiz look soft/playful — brand is tough |
| Corporate blue as primary | Wrong emotion — Gahiz is urgent red, not safe blue |
| Excessive animation (>2 animated elements per view) | Distracts from the score — kills conversion |
| MSA Arabic in UI copy | Culturally wrong for target candidate |
| Light gray text on white (#999 on #fff) | Fails contrast on Android screens outdoors |
| Emoji as icons | Never. Use SVG only (Heroicons or Lucide) |
| Multiple equal-weight CTAs on one screen | One primary action per screen — always |
| Centered Arabic body text | RTL left-align is correct for Arabic prose |
| WhatsApp green (#25D366) in brand colors | Confuses Gahiz brand with WhatsApp brand |

---

## PART F — NEXT.JS 14 IMPLEMENTATION RULES (from nextjs.csv)

These are locked for all code Claude produces for Gahiz:

```
ARCHITECTURE:
✅ /app directory (App Router) — always
✅ Server Components by default — add 'use client' only for interactivity
✅ Arabic routes use safe slugs: /start not /ابدأ
✅ API routes in /app/api/[route]/route.ts
✅ fetch with explicit cache config (Next.js 15 uncached by default)

IMAGES:
✅ Always next/image — never <img>
✅ priority prop on hero images
✅ width + height always specified or fill + relative parent

FONTS:
✅ next/font/google — never external <link> imports
✅ Applied in root layout.tsx to <body>

SECURITY:
✅ Zod validation on ALL API route inputs
✅ HMAC verification before trusting Paymob callbacks
✅ ADMIN_EMAIL env var check before any admin route renders
✅ JWT tokens for candidate auth (single-use, 48h expiry)

ENV VARS:
✅ NEXT_PUBLIC_ prefix only for client-side vars
✅ All secrets in .env.local — never committed
✅ Validate required env vars on startup

PERFORMANCE:
✅ dynamic() import for heavy components (score charts, audio players)
✅ Skeleton screens on all async content — no layout shift
✅ Partial Prerendering: static shell + Suspense for dynamic data
```

---

## PART G — SHADCN/UI COMPONENT RULES (from shadcn.csv)

When building Gahiz UI with shadcn:

```
SETUP:
✅ CSS variables in globals.css match Gahiz tokens above
✅ Both :root and .dark defined (even if dark mode is Phase 2)
✅ @/components/ui path aliases always

THEMING:
✅ --primary maps to #DC143C
✅ --background maps to #F4F4F2
✅ --foreground maps to #080808
✅ All shadcn color tokens overridden with Gahiz tokens

COMPONENTS TO USE:
✅ <Dialog> for payment confirmation modals
✅ <Sheet side="bottom"> for mobile verdict reveal
✅ <Form> + react-hook-form + Zod for all forms
✅ <Skeleton> for loading states on dashboard + session cards
✅ <Accordion> for FAQ section on landing page
✅ <Tabs> for switching between simulation sessions
✅ <AlertDialog> for unlock confirmation
✅ <Progress> for score bars (customized with dimension colors)
✅ toast.success / toast.error from Sonner for feedback

NEVER USE:
❌ shadcn's default blue primary without overriding to crimson
❌ rounded-lg or rounded-xl on primary elements (use rounded-none)
❌ Default Dialog without overriding border-radius to 0
```

---

## PART H — RTL & ARABIC IMPLEMENTATION

```tsx
// Root layout — bilingual setup
<html lang="ar" dir="rtl">
  <body className={cairo.className}>

// English-only sections (scores, labels, company names)
<span lang="en" dir="ltr" className="font-[Inter]">
  Clarity — 8.2
</span>

// Arabic candidate copy
<p lang="ar" dir="rtl" className="font-[Cairo] leading-[1.8]">
  يلا نبدأ — احنا هنا معاك
</p>

// Score label — always English regardless of page language
<span className="font-[Inter] uppercase tracking-wider text-sm">
  Clarity
</span>
<span className="font-[Cairo]" dir="rtl">
  الوضوح — 8.2
</span>
```

**RTL Rules:**
- `dir="rtl"` and `lang="ar"` on root `<html>` element
- Use `ms-` and `me-` (margin-start/end) instead of `ml-`/`mr-` for RTL-safe spacing
- Tailwind: add `rtl:` variant prefix for direction-specific overrides
- Flexbox row-reverse for RTL: use `flex-row` + RTL — it auto-mirrors
- Score bars fill left-to-right regardless of RTL (use `dir="ltr"` on score container)
- Sticky mobile bottom bar CTA button: full-width, centered, RTL-safe

---

## PART I — MOBILE-FIRST BREAKPOINTS

Gahiz's primary device: Android A-series (390px width, 844px height)

```css
/* Mobile baseline — design here first */
@media (min-width: 390px)  { /* base */ }
@media (min-width: 640px)  { /* sm — larger phones */ }
@media (min-width: 768px)  { /* md — tablets */ }
@media (min-width: 1024px) { /* lg — desktop */ }

/* Touch targets — mandatory */
.interactive {
  min-height: 44px;
  min-width: 44px;    /* Never smaller — from ux-guidelines.csv */
}

/* Sticky WhatsApp CTA — mobile only */
.sticky-cta-mobile {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 12px 16px;
  background: linear-gradient(to top, #080808 60%, transparent);
  z-index: 50;
}
@media (min-width: 768px) {
  .sticky-cta-mobile { display: none; }
}
```

---

## PART J — PRE-DELIVERY CHECKLIST

Before presenting any Gahiz UI deliverable, verify:

```
COLORS:
☐ Only --gahiz-crimson, --gahiz-black, --gahiz-off-white + semantic tokens used
☐ No AI purple (#6366F1) or generic gradients anywhere
☐ Text contrast minimum 4.5:1 on all text (7:1 preferred for body)
☐ Crimson only on primary CTAs and score highlights — not decoration

TYPOGRAPHY:
☐ Barlow Condensed on all display/headline text
☐ Cairo on all Arabic body copy
☐ Inter on all English score labels
☐ Score labels always in English regardless of page language

LAYOUT:
☐ Mobile designed at 390px first
☐ No border-radius > 4px on cards or buttons (Gahiz is sharp, not soft)
☐ Single primary CTA per screen
☐ Sticky mobile bottom bar present on landing page
☐ Arabic text is dir="rtl", line-height 1.8
☐ Emoji nowhere — SVG icons only (Lucide or Heroicons)

CONTENT:
☐ Zero placeholder content — all copy uses real Gahiz text
☐ Real company names: Teleperformance, Vodafone, Concentrix, Amazon
☐ Prices in EGP only — never USD
☐ Verdict always English label + Arabic description

NEXT.JS:
☐ Server Components by default — 'use client' only where needed
☐ next/image for all images
☐ next/font for all fonts
☐ Zod validation on all API inputs
☐ Env vars validated on startup
☐ Skeleton loading on all async sections

ACCESSIBILITY:
☐ All interactive elements ≥ 44×44px touch target
☐ focus:ring-2 focus:ring-[#DC143C] on all focusable elements
☐ prefers-reduced-motion respected
☐ No hover-only interactions (mobile has no hover)
☐ Form inputs have visible labels (not just placeholders)
```

---

*GAHIZ Design System | Extracted from UI/UX Pro Max v2.5.0 | May 2026*
*Source databases: products.csv, styles.csv, colors.csv, typography.csv, landing.csv, ui-reasoning.csv, ux-guidelines.csv, nextjs.csv, shadcn.csv*
