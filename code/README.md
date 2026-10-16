# ALTA MALE LAB — Homepage Code Delivery
### Divi Code Module Integration Guide
**Version 1.1 — October 2026**

---

## Overview

This package contains 10 standalone HTML/CSS blocks for the ALTA MALE LAB homepage.
Each block is a self-contained Divi Code Module — drop it in, set the section
background to `#000000`, and it renders correctly without touching any other file.

**Design system:**
- Background: `#000000`
- Primary text: `#EDEDED`
- Gold accent: `#C8B568`
- Fonts: Poppins (titles) + Lato (body) via Google Fonts
- No shadows. No animations. No gradients (except the hero veil).
- Max-width 760px centered. Section padding 120px top/bottom.

---

## Global Setup (do once)

### 1. Load fonts in your theme
All blocks include an `@import` for Google Fonts as a fallback. To avoid
loading them 10 times, add this once to your theme's `<head>` or
Divi > Theme Options > Custom CSS, then remove the `@import` line from
each Code Module:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400;1,500&family=Lato:ital,wght@0,300;0,400;0,700;1,300;1,400&display=swap" rel="stylesheet">
```

### 2. Disable Divi's default section padding
For every section that holds a Code Module from this package:
- Go to Section Settings → Design → Spacing
- Set Top Padding and Bottom Padding to `0px`
- Each block manages its own 120px padding internally

### 3. Set section background color
Every Divi section: Design → Background → Background Color → `#000000`

---

## Section-by-Section Integration

---

### Section 1 — Hero
**File:** `section-01-hero-v3.html`

The hero uses a left-to-transparent dark gradient veil designed to ensure
text legibility over a B&W editorial photograph.

**V3 note:** the `.alta-hero` background is `transparent` so the Divi section
background image stays visible. Keep the Divi section background color at
`#000000` and add the photo as the section Background Image.

**To add the background photo:**
1. In Divi Section Settings → Design → Background → Background Image
2. Upload your B&W editorial portrait
3. Set Position: Center Right, Size: Cover
4. The `.alta-hero__veil` gradient activates automatically over the image

**To update the issue number and date:**
Find this line in the HTML and edit in place:
```html
Issue N°&nbsp;12 &nbsp;·&nbsp; <b>Out now</b> &nbsp;·&nbsp; 18.05.2026
```

**CTAs:** Update `href="#journal"` and `href="#framework"` to your live page URLs.

---

### Section 2 — Beyond Alpha
**File:** `section-02-beyond-alpha.html`

Standalone typographic block. No assets required.

**CTA:** Update `href="#long-game"` to your Manifesto or About page URL.

---

### Section 3 — The Metabolic Upgrade Quiz
**File:** `section-03-quiz.html`

Lead-magnet block with bordered card treatment.

**CTA:** Update `href="#quiz"` to your quiz page or external quiz tool URL
(Typeform, Outgrow, etc.).

---

### Section 4 — The Alta Framework
**File:** `section-04-framework.html`

Three-pillar grid. Pillar titles are invariable brand terms —
do not translate: *Metabolic Intelligence / Strength & Muscles /
Mind & Nervous System*.

**CTA:** Update `href="#framework"` to your Framework page URL.

**To update pillar body copy or micro-signatures:**
Each pillar is a `.alta-fw__col` div. Edit `.alta-fw__p` (body)
and `.alta-fw__sig` (italic micro-signature) directly.

---

### Section 5 — Featured Article
**File:** `section-05-featured-article.html`

Two-column card: image left, text right.

**To add the editorial photograph:**
Replace the `.alta-feat__image-slot` div inside `.alta-feat__image` with:
```html
<img src="YOUR-IMAGE-URL" alt="Article title">
```
The CSS already applies `filter: grayscale(1) contrast(1.04)` to any `<img>`
inside `.alta-feat__image`.

**To update the featured article:** Edit the eyebrow, `h2`, deck paragraph,
and `href` on `.alta-feat__cta` directly in the HTML.

---

### Section 6 — Latest Articles
**File:** `section-06-latest-articles.html`

3×2 article grid. Each card is an `<a>` tag — update `href` attributes
to live article URLs.

**To update article data:** Each card follows this structure:
```html
<a href="#article-XX" class="alta-idx__card">
  <div class="alta-idx__card-num">N° XX</div>
  <div class="alta-idx__card-pillar">Pillar Name</div>
  <h3 class="alta-idx__card-title">Article title here.</h3>
  <div class="alta-idx__card-meta">DD.MM.YYYY · X min</div>
</a>
```

**All issues CTA:** Update `href="#journal"` to your full journal archive URL.

---

### Section 7 — The Long Game Starts At 40
**File:** `section-07-manifesto.html`

Full-width prose section. Four paragraphs from the Manifesto.

**CTA:** Update `href="#manifesto"` to your Manifesto page URL.

**To update body copy:** Edit the `<p>` tags inside `.alta-man__prose` directly.
Keep Lato 18px / line-height 1.78 — this is the maximum reading comfort
setting from the design system.

---

### Section 8 — A Note From The Founder
**File:** `section-08-founder.html`

Two-column layout: text left, portrait photo right.

**To add the founder portrait:**
Replace the `.alta-founder__photo-slot` div inside `.alta-founder__photo` with:
```html
<img src="YOUR-PORTRAIT-URL" alt="Anthony K.">
```
The CSS already applies `filter: grayscale(1) contrast(1.02)`.

**Photo specs:** Portrait orientation recommended. Aspect ratio 4:5 is
enforced by CSS — any image will crop to fit. Minimum 600px wide.

---

### Section 9 — From Knowledge To Transformation
**File:** `section-09-academy-bridge.html`

Academy bridge block. Links the journal to the ALTA Body & Mind Academy.

**CTA:** Update `href="#academy"` to your Academy page URL.
This is a secondary-style CTA (`#EDEDED` text, `#2A2A2A` border) — intentionally
quieter than the gold primary CTAs elsewhere on the page.

---

### Section 10 — Newsletter + Footer
**File:** `section-10-newsletter-footer.html`

Contains both the newsletter block and the full site footer in one module.

**Newsletter form:**
Wire the `<form>` action to your email service provider:
```html
<form class="alta-nl__row" action="YOUR-ESP-ENDPOINT" method="post">
```
Common providers:
- **Mailchimp:** replace `action="#"` with your Mailchimp embed action URL
- **ConvertKit:** replace with your ConvertKit form action URL
- **Brevo / others:** follow your ESP's HTML embed instructions

The `name="email"` attribute on the input is standard — most ESPs expect it.

**Footer links:**
All `href="#"` placeholders in `.alta-ft__link` anchors must be updated
to live page URLs before launch.

**Copyright year:**
```html
<div class="alta-ft__copyright">© Alta Male Media 2026 · ALTA MALE LAB</div>
```
Update year annually.

---

## Invariable Brand Terms

These terms must never be translated, abbreviated, or restyled:

| Term | Context |
|---|---|
| `The Long Game` | Tagline, section titles, footer closer |
| `The Alta Framework` | Section 4 eyebrow and CTA |
| `Metabolic Intelligence` | Pillar 01 title |
| `Strength & Muscles` | Pillar 02 title |
| `Mind & Nervous System` | Pillar 03 title |
| `ALTA MALE LAB` | All caps, always |
| `ALTA Body & Mind Academy` | Full name when referenced |

---

## Color Reference

| Token | Hex | Usage |
|---|---|---|
| Black | `#000000` | All section backgrounds |
| Black soft | `#0A0A0A` | Footer background, image slots |
| Line | `#1F1F1F` | Hairline dividers, card borders |
| Line strong | `#2A2A2A` | Quiz card border, input border |
| Gold | `#C8B568` | Primary CTAs, wordmark, gold bullets |
| fg-1 | `#EDEDED` | Primary text |
| fg-2 | `#B8B8B8` | Secondary text, footer links |
| fg-3 | `#8A8A8A` | Meta, dates, discreet text |
| fg-4 | `#5A5A5A` | Copyright, placeholder text |
| White | `#FFFFFF` | Hero H1 only |

---

## File Index

```
alta-male-lab-homepage/
├── README.md                           ← this file
├── section-01-hero-v3.html             ← Hero (V3)
├── section-02-beyond-alpha.html        ← Beyond Alpha
├── section-03-quiz.html                ← Metabolic Upgrade Quiz
├── section-04-framework.html           ← The Alta Framework
├── section-05-featured-article.html    ← Featured Article
├── section-06-latest-articles.html     ← Latest Articles
├── section-07-manifesto.html           ← The Long Game Starts At 40
├── section-08-founder.html             ← A Note From The Founder
├── section-09-academy-bridge.html      ← From Knowledge To Transformation
└── section-10-newsletter-footer.html   ← Newsletter + Footer
```

---

*ALTA MALE LAB — The Long Game for Men 40+*
*© Alta Male Media 2026*
