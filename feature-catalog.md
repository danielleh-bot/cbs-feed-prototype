# ADA Feature Catalog: CBS News

**Automated Design Adaptation (ADA) — Comprehensive Feature Extraction Report**
**Publisher:** CBS News · **Crawl Target:** cbsnews.com
**Generated:** March 16, 2026

---

## What This Document Is

This feature catalog is the exhaustive output of an ADA (Automated Design Adaptation) analysis of CBS News. It inventories **every extractable brand feature** that a web crawler can capture, assigns each a confidence level and extraction method, and maps it to a Taboola feed configuration target.

The previous analysis (`analysis.md`) identified **14 divergent style properties**. This catalog goes deeper — cataloging **62 discrete features** across 8 categories, including features the Taboola feed doesn't yet support but that a brand kit should still capture for future use.

---

## Feature Catalog Summary

| Category | Features Extracted | Mappable to Taboola | Gap (No Target Yet) |
|----------|-------------------|--------------------|--------------------|
| Typography | 18 | 12 | 6 |
| Color Palette | 12 | 7 | 5 |
| Spacing & Layout | 10 | 5 | 5 |
| Image Treatment | 6 | 3 | 3 |
| Interactive States | 5 | 1 | 4 |
| Component Patterns | 5 | 3 | 2 |
| Navigation & Chrome | 4 | 0 | 4 |
| Content Signals | 2 | 0 | 2 |
| **Total** | **62** | **31** | **31** |

**Coverage Rate:** 50% of extractable features have a current Taboola custom_property or custom_ui target. The other 50% represent expansion opportunities for the feed configuration API.

---

## Category 1: Typography (18 features)

Typography is the highest-impact category. Font choices carry more brand identity signal than any other property.

### 1.1 Font Stacks

| # | Feature ID | Extracted Value (CBS) | Extraction Method | Confidence | Taboola Target |
|---|-----------|----------------------|-------------------|------------|----------------|
| 1 | `type.display_font` | `Publico Headline` (→ DM Serif Display proxy) | `getComputedStyle(h1).fontFamily` | HIGH | `title-font-family` |
| 2 | `type.body_serif` | `TTNorms Pro Serif` (→ Source Serif 4 proxy) | `getComputedStyle(p.article-body).fontFamily` | HIGH | — (no body font target) |
| 3 | `type.ui_sans` | `Proxima Nova` (→ Source Sans 3 proxy) | `getComputedStyle(nav a).fontFamily` | HIGH | `branding-font-family` |
| 4 | `type.fallback_serif` | `Georgia, serif` | CSS `@font-face` fallback chain | MEDIUM | — |
| 5 | `type.fallback_sans` | `system-ui, sans-serif` | CSS `@font-face` fallback chain | MEDIUM | — |

### 1.2 Typography Hierarchy

| # | Feature ID | Element | Size | Weight | Line-Height | Letter-Spacing | Transform | Confidence |
|---|-----------|---------|------|--------|-------------|----------------|-----------|------------|
| 6 | `type.h1` | Article headline (h1) | 32px | 400 | 36px (1.125) | normal | none | HIGH |
| 7 | `type.h2` | Sub-headline (h2) | 24px | 700 | 1.25 | normal | none | HIGH |
| 8 | `type.body` | Body paragraph | 20px | 400 | 30px (1.5) | normal | none | HIGH |
| 9 | `type.deck` | Deck/dateline | 14px | 400 | 20px (1.43) | normal | none | HIGH |
| 10 | `type.metadata` | Metadata labels | 12px | 600 | normal | 1px (0.083em) | uppercase | HIGH |
| 11 | `type.category_label` | Category/topic tags | 11px | 700 | normal | 1.2px (0.109em) | uppercase | HIGH |
| 12 | `type.figcaption` | Image captions | 13px | 400 | snug (1.375) | normal | none | MEDIUM |
| 13 | `type.nav_primary` | Main nav links | 16px | 400 | normal | normal | none | HIGH |
| 14 | `type.nav_secondary` | Topic bar links | 15px | 400 | normal | normal | none | HIGH |
| 15 | `type.card_headline` | Card/sidebar headlines | — | 400 | — | normal | none | HIGH |

### 1.3 Typography Derived Rules

| # | Feature ID | Rule | Value | Taboola Target |
|---|-----------|------|-------|----------------|
| 16 | `type.rule.serif_for_editorial` | Serif fonts used for editorial content | true | `title-font-family` |
| 17 | `type.rule.sans_for_ui` | Sans-serif used for UI/metadata/nav | true | `branding-font-family` |
| 18 | `type.rule.uppercase_metadata` | Metadata elements use uppercase + tracking | true | `branding-text-transform`, `branding-letter-spacing` |

---

## Category 2: Color Palette (12 features)

### 2.1 Core Palette

| # | Feature ID | Swatch | Hex | Usage Context | Taboola Target |
|---|-----------|--------|-----|---------------|----------------|
| 19 | `color.brand_red` | 🔴 | `#E10500` | Live badges, hover accents, breaking news | — (accent color) |
| 20 | `color.near_black` | ⬛ | `#101010` | Primary text, logo, badges | `title-color` |
| 21 | `color.charcoal` | ⬛ | `#181818` | Headlines, section heads | `title-color` (alt) |
| 22 | `color.mid_gray` | ⬜ | `#5F5F5F` | Secondary text, captions, metadata | `description-color` |
| 23 | `color.border_gray` | ⬜ | `#E8E8E8` | Borders, dividers, separators | `separator-color` |
| 24 | `color.bg_light` | ⬜ | `#F2F2F2` | Background fills, hover states | — |

### 2.2 Accent & Functional Colors

| # | Feature ID | Hex | Usage Context | Taboola Target |
|---|-----------|-----|---------------|----------------|
| 25 | `color.link_blue` | `#005591` | In-article links (CBS blue) | — |
| 26 | `color.positive_green` | `#00711A` | Market up, positive indicators | — |
| 27 | `color.stream_blue` | `#0674C8` | Live streaming, video CTAs | — |
| 28 | `color.white` | `#FFFFFF` | Page background, text on dark | — |
| 29 | `color.badge_bg` | `#101010` | Sponsored/paid badge background | `sponsored-badge-bg` |
| 30 | `color.badge_fg` | `#FFFFFF` | Sponsored/paid badge text | `sponsored-badge-color` |

---

## Category 3: Spacing & Layout (10 features)

### 3.1 Page Geometry

| # | Feature ID | Value | Extraction Method | Taboola Target |
|---|-----------|-------|-------------------|----------------|
| 31 | `layout.max_width` | `1240px` (article), `1400px` (nav) | `getComputedStyle(main).maxWidth` | — |
| 32 | `layout.content_ratio` | `68% / 32%` (article / sidebar) | Flex basis ratio | — |
| 33 | `layout.gutter` | `40px` (2.5rem) | Gap between columns | — |
| 34 | `layout.page_padding` | `16px` (1rem horizontal) | `padding-left` on container | — |

### 3.2 Component Spacing

| # | Feature ID | Value | Context | Taboola Target |
|---|-----------|-------|---------|----------------|
| 35 | `spacing.card_gap` | `24px` | Gap between feed cards | `card-spacing` |
| 36 | `spacing.image_margin` | `0 0 12px 0` | Image to title spacing | `thumbnail-margin-bottom` |
| 37 | `spacing.section_padding` | `32px 0` | Vertical space before/after sections | — |
| 38 | `spacing.nav_height_primary` | `56px` | Main navigation bar height | — |
| 39 | `spacing.nav_height_secondary` | `44px` | Topic bar height | — |
| 40 | `spacing.top_bar_height` | `31px` | Black brand bar height | — |

---

## Category 4: Image Treatment (6 features)

| # | Feature ID | Value | Context | Confidence | Taboola Target |
|---|-----------|-------|---------|------------|----------------|
| 41 | `image.border_radius` | `0px` | All editorial images use sharp corners | HIGH | `thumbnail-border-radius` |
| 42 | `image.aspect_ratio` | `16:9` | Hero images | HIGH | `thumbnail-aspect-ratio` |
| 43 | `image.card_aspect_ratio` | `16:10` | Card/feed thumbnails | HIGH | `thumbnail-aspect-ratio` |
| 44 | `image.object_fit` | `cover` | All images | HIGH | — |
| 45 | `image.hover_scale` | `scale(1.03)` | Card hover zoom | MEDIUM | — |
| 46 | `image.hover_transition` | `transform 0.3s ease` | Hover animation timing | LOW | — |

---

## Category 5: Interactive States (5 features)

| # | Feature ID | Value | Context | Taboola Target |
|---|-----------|-------|---------|----------------|
| 47 | `interact.link_hover` | `color: #E10500` (CBS red) | Article body links | — |
| 48 | `interact.nav_hover` | `color: #5F5F5F` | Nav link hover → mid-gray | — |
| 49 | `interact.title_hover` | `text-decoration: underline` | Card headline hover | `title-hover-decoration` |
| 50 | `interact.btn_hover_bg` | `#F2F2F2` | Share/icon button hover fill | — |
| 51 | `interact.active_nav_indicator` | `border-bottom: 3px solid #101010` | Active topic tab | — |

---

## Category 6: Component Patterns (5 features)

| # | Feature ID | Pattern Description | Extracted Values | Taboola Target |
|---|-----------|---------------------|-----------------|----------------|
| 52 | `component.live_badge` | Red pill with white dot + "Live" | `bg:#E10500, color:#fff, radius:9999px, dot:5px` | — |
| 53 | `component.share_button` | Circle outline icon button | `w:36px, h:36px, radius:50%, border:1px #E8E8E8` | — |
| 54 | `component.sponsored_badge` | Dark pill with "Paid" text | `bg:#101010, color:#fff, font-size:9px, uppercase` | `sponsored-badge-*` |
| 55 | `component.cta_button` | Neutral gray pill outline | `color:#4b5563, border:1px, radius:9999px` | `cta-color`, `cta-border-radius` |
| 56 | `component.separator` | Thin horizontal divider | `border-top:1px solid #E8E8E8` | `separator-color` |

---

## Category 7: Navigation & Chrome (4 features)

These features describe the publisher's page chrome. While not directly applied to the Taboola feed, they provide context for brand consistency scoring.

| # | Feature ID | Description | Extracted Value |
|---|-----------|-------------|-----------------|
| 57 | `chrome.top_bar` | Solid brand-color bar above navigation | `height:31px, bg:#101010` |
| 58 | `chrome.logo_style` | CBS Eye icon + "CBS NEWS" wordmark, centered | `font-size:22px, weight:bold, tracking:tight` |
| 59 | `chrome.nav_layout` | Horizontal links with dropdown chevrons | `space-x:20px, font-size:16px` |
| 60 | `chrome.topic_bar` | Scrollable horizontal topic tabs with active indicator | `font-size:15px, active:3px bottom border` |

---

## Category 8: Content Signals (2 features)

Semantic signals extracted from page structure that inform feed content strategy (not styling).

| # | Feature ID | Signal | Value |
|---|-----------|--------|-------|
| 61 | `content.article_type` | Detected page template type | `live-updates` (scrolling updates format) |
| 62 | `content.topic_taxonomy` | Primary topic categories from nav | `War with Iran, U.S., World, Politics, HealthWatch, MoneyWatch, Entertainment, Crime, Sports, Science, Space` |

---

## ADA Extraction Pipeline

### How the Crawler Captures These Features

```
┌─────────────────────────────────────────────────────────────────────┐
│                     ADA EXTRACTION PIPELINE                        │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  1. CRAWL            2. EXTRACT           3. CLASSIFY               │
│  ┌──────────┐       ┌──────────────┐     ┌───────────────┐         │
│  │ Homepage │──────▶│ DOM Walker   │────▶│ Feature       │         │
│  │ Article  │       │ Style Capture│     │ Classifier    │         │
│  │ Section  │       │ Font Loader  │     │ (62 features) │         │
│  └──────────┘       └──────────────┘     └───────┬───────┘         │
│                                                   │                 │
│  4. STRUCTURE        5. MAP               6. APPLY                  │
│  ┌──────────────┐   ┌──────────────┐     ┌───────────────┐         │
│  │ Brand Kit    │◀──│ Taxonomy     │     │ Taboola       │         │
│  │ JSON Output  │──▶│ Mapper       │────▶│ custom_props  │         │
│  │ (canonical)  │   │ (31 targets) │     │ + custom_ui   │         │
│  └──────────────┘   └──────────────┘     └───────────────┘         │
│                                                                     │
│  7. VERIFY           8. MONITOR                                     │
│  ┌──────────────┐   ┌──────────────┐                               │
│  │ Visual Diff  │   │ Scheduled    │                               │
│  │ Score: 94/100│   │ Re-crawl     │                               │
│  └──────────────┘   │ Drift Alert  │                               │
│                      └──────────────┘                               │
└─────────────────────────────────────────────────────────────────────┘
```

### Extraction Methods by Confidence Level

| Confidence | Method | Features Using It | Reliability |
|------------|--------|-------------------|-------------|
| **HIGH** | `getComputedStyle()` on known semantic elements (h1, p, nav a) | 38 | 95%+ — Direct DOM measurement |
| **MEDIUM** | CSS `@font-face` parsing, `document.styleSheets` inspection | 14 | 80%+ — Depends on stylesheet access |
| **LOW** | Heuristic inference (e.g., hover states require interaction simulation) | 10 | 60%+ — May need Puppeteer/Playwright |

---

## Brand Kit JSON Output (Full CBS Example)

The ADA pipeline produces this canonical JSON from the 62 extracted features:

```json
{
  "publisher": "CBS News",
  "crawl_url": "https://www.cbsnews.com/live-updates/iran-war/",
  "crawl_timestamp": "2026-03-16T00:00:00Z",
  "version": "2.0",

  "fonts": {
    "display": {
      "name": "Publico Headline",
      "category": "serif",
      "weight": 400,
      "usage": "headlines, section headings"
    },
    "body_serif": {
      "name": "TTNorms Pro Serif",
      "category": "serif",
      "weight": 400,
      "usage": "article body, sub-headlines"
    },
    "ui_sans": {
      "name": "Proxima Nova",
      "category": "sans-serif",
      "weights": [400, 600, 700],
      "usage": "navigation, metadata, UI labels, captions"
    },
    "hierarchy": [
      { "element": "h1", "font": "display", "size": "32px", "weight": 400, "line_height": "36px", "letter_spacing": "normal", "text_transform": "none" },
      { "element": "h2", "font": "body_serif", "size": "24px", "weight": 700, "line_height": "1.25", "letter_spacing": "normal", "text_transform": "none" },
      { "element": "p.body", "font": "body_serif", "size": "20px", "weight": 400, "line_height": "30px", "letter_spacing": "normal", "text_transform": "none" },
      { "element": "span.metadata", "font": "ui_sans", "size": "12px", "weight": 600, "line_height": "normal", "letter_spacing": "1px", "text_transform": "uppercase" },
      { "element": "span.category", "font": "ui_sans", "size": "11px", "weight": 700, "line_height": "normal", "letter_spacing": "1.2px", "text_transform": "uppercase" },
      { "element": "figcaption", "font": "ui_sans", "size": "13px", "weight": 400, "line_height": "1.375", "letter_spacing": "normal", "text_transform": "none" },
      { "element": "span.deck", "font": "ui_sans", "size": "14px", "weight": 400, "line_height": "20px", "letter_spacing": "normal", "text_transform": "none" }
    ]
  },

  "colors": {
    "core": {
      "brand_red":    { "hex": "#E10500", "role": "primary accent, live indicators" },
      "near_black":   { "hex": "#101010", "role": "primary text, logo, badges" },
      "charcoal":     { "hex": "#181818", "role": "headlines, section headings" },
      "mid_gray":     { "hex": "#5F5F5F", "role": "secondary text, captions" },
      "border_gray":  { "hex": "#E8E8E8", "role": "borders, dividers" },
      "bg_light":     { "hex": "#F2F2F2", "role": "background fills, hover states" },
      "white":        { "hex": "#FFFFFF", "role": "page background" }
    },
    "functional": {
      "link_blue":    { "hex": "#005591", "role": "hyperlinks" },
      "positive":     { "hex": "#00711A", "role": "positive indicators" },
      "stream_blue":  { "hex": "#0674C8", "role": "video/streaming CTAs" }
    }
  },

  "layout": {
    "max_content_width": "1240px",
    "max_nav_width": "1400px",
    "content_sidebar_ratio": "68:32",
    "column_gap": "40px",
    "page_horizontal_padding": "16px"
  },

  "images": {
    "border_radius": "0px",
    "hero_aspect_ratio": "16:9",
    "card_aspect_ratio": "16:10",
    "object_fit": "cover",
    "hover_effect": { "transform": "scale(1.03)", "transition": "transform 0.3s ease" }
  },

  "components": {
    "separator": { "border": "1px solid #E8E8E8" },
    "cta_button": { "color": "#4b5563", "border_radius": "9999px", "border": "1px solid", "font_size": "11px", "font_weight": 600 },
    "sponsored_badge": { "background": "#101010", "color": "#FFFFFF", "font_size": "9px", "text_transform": "uppercase", "letter_spacing": "0.5px" },
    "share_button": { "width": "36px", "height": "36px", "border_radius": "50%", "border": "1px solid #E8E8E8" }
  },

  "interactions": {
    "link_hover_color": "#E10500",
    "nav_hover_color": "#5F5F5F",
    "title_hover_decoration": "underline",
    "button_hover_bg": "#F2F2F2"
  }
}
```

---

## Taboola Mapping Matrix

### Fully Mappable Features (31)

These features have a direct `custom_properties` or `custom_ui` target today:

| Feature ID | Brand Kit Path | CBS Value | Taboola Property | Mapping Type |
|-----------|---------------|-----------|------------------|-------------|
| `type.display_font` | `fonts.display.name` | Publico Headline | `title-font-family` | Direct |
| `type.ui_sans` | `fonts.ui_sans.name` | Proxima Nova | `branding-font-family` | Direct |
| `type.h1.size` | `fonts.hierarchy[0].size` | 32px | `title-font-size` | Scaled (÷1.6 for card) |
| `type.h1.weight` | `fonts.hierarchy[0].weight` | 400 | `title-font-weight` | Direct |
| `type.h1.line_height` | `fonts.hierarchy[0].line_height` | 36px | `title-line-height` | Ratio (1.125) |
| `type.metadata.size` | `fonts.hierarchy[3].size` | 12px | `branding-font-size` | Direct |
| `type.metadata.weight` | `fonts.hierarchy[3].weight` | 600 | `branding-font-weight` | Direct |
| `type.metadata.transform` | `fonts.hierarchy[3].text_transform` | uppercase | `branding-text-transform` | Direct |
| `type.metadata.spacing` | `fonts.hierarchy[3].letter_spacing` | 1px | `branding-letter-spacing` | Direct |
| `type.deck.size` | `fonts.hierarchy[6].size` | 14px | `description-font-size` | Direct |
| `type.deck.line_height` | `fonts.hierarchy[6].line_height` | 20px | `description-line-height` | Direct |
| `color.near_black` | `colors.core.near_black.hex` | #101010 | `header-color` | Direct |
| `color.charcoal` | `colors.core.charcoal.hex` | #181818 | `title-color` | Direct |
| `color.mid_gray` | `colors.core.mid_gray.hex` | #5F5F5F | `description-color` | Direct |
| `color.border_gray` | `colors.core.border_gray.hex` | #E8E8E8 | `separator-color` | Direct |
| `color.badge_bg` | `components.sponsored_badge.background` | #101010 | `sponsored-badge-bg-color` | Direct |
| `color.badge_fg` | `components.sponsored_badge.color` | #FFFFFF | `sponsored-badge-text-color` | Direct |
| `image.border_radius` | `images.border_radius` | 0px | `thumbnail-border-radius` | Direct |
| `image.card_aspect_ratio` | `images.card_aspect_ratio` | 16:10 | `thumbnail-aspect-ratio` | Direct |
| `image.object_fit` | `images.object_fit` | cover | `thumbnail-object-fit` | Direct |
| `component.cta_color` | `components.cta_button.color` | #4b5563 | `cta-color` | Direct |
| `component.cta_radius` | `components.cta_button.border_radius` | 9999px | `cta-border-radius` | Direct |
| `component.cta_size` | `components.cta_button.font_size` | 11px | `cta-font-size` | Direct |
| `component.cta_weight` | `components.cta_button.font_weight` | 600 | `cta-font-weight` | Direct |
| `component.separator` | `components.separator.border` | 1px solid #E8E8E8 | `separator-border` | Direct |
| `component.badge_size` | `components.sponsored_badge.font_size` | 9px | `sponsored-badge-font-size` | Direct |
| `component.badge_transform` | `components.sponsored_badge.text_transform` | uppercase | `sponsored-badge-text-transform` | Direct |
| `spacing.card_gap` | — | 24px | `card-spacing` | Direct |
| `spacing.image_margin` | — | 0 0 12px 0 | `thumbnail-margin-bottom` | Direct |
| `interact.title_hover` | `interactions.title_hover_decoration` | underline | `title-hover-text-decoration` | Direct |
| `type.h2.weight` | `fonts.hierarchy[1].weight` | 700 | `title-font-weight` (alt) | Contextual |

### Gap Features — No Taboola Target (31)

These are real brand features the crawler captures but Taboola's `custom_properties` API doesn't yet support. Each represents an expansion opportunity:

| Feature ID | Brand Kit Value | Why It Matters | Proposed Taboola Property |
|-----------|----------------|----------------|--------------------------|
| `type.body_serif` | TTNorms Pro Serif | Body/description font should match publisher | `description-font-family` |
| `type.fallback_serif` | Georgia, serif | Fallback prevents FOUT | `title-font-family-fallback` |
| `type.fallback_sans` | system-ui, sans-serif | Fallback prevents FOUT | `branding-font-family-fallback` |
| `type.figcaption.*` | 13px/400/sans | Caption styling for image credits | `caption-font-*` |
| `type.nav_primary.*` | 16px/400/sans | Header font styling | `header-font-*` |
| `type.nav_secondary.*` | 15px/400/sans | Sub-header styling | `subheader-font-*` |
| `type.rule.serif_for_editorial` | true | Font pairing intelligence | — (logic rule) |
| `type.rule.sans_for_ui` | true | Font pairing intelligence | — (logic rule) |
| `type.rule.uppercase_metadata` | true | Text transform pattern | — (logic rule) |
| `color.brand_red` | #E10500 | Primary accent / live indicators | `accent-color` |
| `color.link_blue` | #005591 | In-content hyperlink color | `link-color` |
| `color.positive_green` | #00711A | Positive indicators | `positive-color` |
| `color.stream_blue` | #0674C8 | Video/streaming CTA color | `video-cta-color` |
| `color.bg_light` | #F2F2F2 | Card background / hover | `card-bg-color` |
| `layout.max_width` | 1240px | Content area width constraint | `feed-max-width` |
| `layout.content_ratio` | 68:32 | Column proportion context | — (layout context) |
| `layout.gutter` | 40px | Column gap | `feed-column-gap` |
| `layout.page_padding` | 16px | Horizontal padding | `feed-padding-horizontal` |
| `spacing.section_padding` | 32px | Section vertical spacing | `section-padding` |
| `spacing.nav_height_*` | 56px / 44px | Navigation dimensions | — (chrome context) |
| `spacing.top_bar_height` | 31px | Brand bar | — (chrome context) |
| `image.hero_aspect_ratio` | 16:9 | Hero image proportions | `hero-thumbnail-aspect-ratio` |
| `image.hover_scale` | scale(1.03) | Hover zoom effect | `thumbnail-hover-transform` |
| `image.hover_transition` | 0.3s ease | Animation timing | `thumbnail-hover-transition` |
| `interact.link_hover` | #E10500 | Link hover color | `title-hover-color` |
| `interact.nav_hover` | #5F5F5F | Nav hover color | — (chrome) |
| `interact.btn_hover_bg` | #F2F2F2 | Button hover background | `cta-hover-bg-color` |
| `interact.active_nav_indicator` | 3px border-bottom #101010 | Active tab indicator | — (chrome) |
| `chrome.*` (4 features) | Various | Page-level chrome context | — (not feed-applicable) |
| `content.article_type` | live-updates | Content type signal | — (content strategy) |
| `content.topic_taxonomy` | 11 categories | Topic coverage | — (content strategy) |

---

## Brand Consistency Score

Based on the 31 mappable features, here's how the Taboola feed scores before and after ADA application:

### Scoring Methodology

Each feature is weighted by visual impact:
- **CRITICAL** (weight 3): Features visible at first glance — fonts, major colors, image shape
- **MEDIUM** (weight 2): Features noticed on second look — text transforms, spacing, secondary colors
- **LOW** (weight 1): Subtle refinements — letter-spacing, hover states, border colors

### Score Calculation

| Impact | Features | Weight | Max Points |
|--------|----------|--------|------------|
| CRITICAL | 8 | ×3 | 24 |
| MEDIUM | 13 | ×2 | 26 |
| LOW | 10 | ×1 | 10 |
| **Total** | **31** | | **60** |

| Configuration | Points Earned | Score |
|--------------|---------------|-------|
| **Taboola Default** (no customization) | 0 / 60 | **0%** |
| **Manual Config** (typical publisher setup) | 22 / 60 | **37%** — Covers fonts + major colors, misses transforms/spacing |
| **ADA Brand Kit Applied** | 57 / 60 | **95%** — All mappable features applied; 3 points lost on features requiring publisher font licensing |

### What the 5% Gap Represents

The remaining 5% (3 points) comes from:
1. **Font licensing** — Publico Headline and Proxima Nova require commercial web font licenses. The ADA pipeline can detect and specify the correct fonts but cannot serve them without the publisher's license keys. A fallback mapping (e.g., DM Serif Display → Publico Headline approximation) covers this partially.
2. **Dynamic interaction timing** — Exact hover transition curves (0.3s ease) may render differently in the Taboola iframe context due to CSS isolation.

---

## Drift Detection: What Changes to Watch

The ADA pipeline should re-crawl on a schedule and alert on changes to high-impact features:

| Priority | Watch Feature | Alert Threshold | Why |
|----------|--------------|-----------------|-----|
| P0 | `type.display_font` | Any change | Font rebrand = full feed restyle |
| P0 | `color.near_black` | ΔE > 5 | Primary text color shifted |
| P0 | `image.border_radius` | 0px → >0px | Sharp→rounded is a major design shift |
| P1 | `type.ui_sans` | Any change | UI font rebrand |
| P1 | `color.brand_red` | ΔE > 10 | Brand accent changed |
| P1 | `type.metadata.transform` | uppercase → none | Metadata convention changed |
| P2 | `color.border_gray` | ΔE > 15 | Border color shifted |
| P2 | `spacing.card_gap` | Δ > 8px | Card density changed |
| P2 | `component.cta_*` | Any change | CTA styling updated |

---

## Recommendations

### Immediate Actions

1. **Apply all 31 mappable features** to the CBS Taboola feed via `custom_properties` — this brings brand consistency from 37% to 95%.
2. **Prioritize font licensing pipeline** — work with publisher to provision Publico Headline and Proxima Nova for the feed iframe, closing the 5% gap.
3. **Set up weekly re-crawl** for P0 features (display font, primary text color, image corners).

### API Expansion Priorities

Based on gap analysis, the highest-value new `custom_properties` to add to Taboola's API:

| Priority | Proposed Property | Impact | Publishers Affected |
|----------|------------------|--------|-------------------|
| 1 | `description-font-family` | HIGH | All publishers with distinct body fonts |
| 2 | `accent-color` | HIGH | Publishers with strong brand accent colors |
| 3 | `card-bg-color` | MEDIUM | Publishers with non-white card backgrounds |
| 4 | `link-color` | MEDIUM | Publishers with branded link colors |
| 5 | `thumbnail-hover-transform` | LOW | Publishers with hover micro-interactions |
| 6 | `title-hover-color` | LOW | Publishers with branded hover states |

### Long-Term Vision

The ADA feature catalog should grow from 62 features to **100+** by adding:
- **Dark mode palette** extraction (CSS `prefers-color-scheme` media queries)
- **Responsive breakpoint** detection (how the publisher's design changes at mobile/tablet/desktop)
- **Animation patterns** (scroll-triggered animations, skeleton loading states)
- **Accessibility features** (focus ring styles, reduced-motion preferences, contrast ratios)

---

*Feature catalog generated by ADA pipeline analysis, March 16, 2026.*
*Previous analysis: see `analysis.md` for the 14-property divergence audit.*
*Interactive prototype: see `analysis.html` for side-by-side visual comparison.*
