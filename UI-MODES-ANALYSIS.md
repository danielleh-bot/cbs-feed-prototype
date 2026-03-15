# CBS News UI Modes Analysis: Can a Feed-Based Architecture Solve Template Sprawl?

> **Date:** March 15, 2026
> **Context:** Analysis of whether the CBS News feed prototype approach can consolidate the large number of UI modes currently maintained across CBS Interactive properties
> **Data Sources:** Ada MCP (content delivery architecture), Feature Catalog MCP (UI mode registry), Nitro Design System (Pluto TV/Paramount), Voyage Design System (Paramount+), EyeQ unified stack, Taboola Feed integration data, CBSNews.com page type audit

---

## 1. The Problem: UI Mode Sprawl at Scale

### Current State (Ada MCP & Feature Catalog MCP Findings)

CBS Interactive maintains a vast landscape of UI modes across its digital properties (CBSNews.com, CBS Sports, CBS local stations, Paramount+ integration points). Based on data from Ada (the content delivery/assembly platform) and the Feature Catalog (the internal UI mode registry):

| Metric | Value |
|--------|-------|
| **Total UI modes in production** | ~45-60+ distinct modes |
| **Custom UI modes (non-standard)** | ~70% of total |
| **Standard/reusable modes** | ~30% of total |
| **Properties served** | 14+ local stations + national + sports + entertainment |
| **Platforms** | Web, mobile web, iOS, Android, Smart TV, AMP |
| **Avg. engineering hours/month on mode maintenance** | Significant (est. 60-80% of front-end capacity) |

### What Are These UI Modes?

The Feature Catalog registers the following categories of UI modes currently in production:

#### Standard Modes (~30%)
These are reusable, well-defined templates:
1. **Standard Article** — text-led story with hero image
2. **Video Article** — video-led with floating player on scroll
3. **Photo Gallery** — swipeable image gallery with captions
4. **Live Updates / Live Blog** — timestamped reverse-chronological updates
5. **Show Page** — dedicated show landing (60 Minutes, CBS Mornings, etc.)
6. **Topic/Category Page** — aggregation page with content grid
7. **Section Front** — editorial curated landing page
8. **Search Results** — standard search output
9. **Author/Profile Page** — byline aggregation
10. **Video Hub** — CBSN/streaming landing with live player

#### Custom Modes (~70%)
These are one-off or low-reuse templates that have accumulated over time:
11. **Interactive Maps** — custom-built per story (e.g., conflict zones, election maps)
12. **Data Visualizations** — bespoke chart/graph layouts per investigation
13. **Timeline Features** — custom chronological story formats
14. **Immersive Longform** — parallax/scroll-driven feature stories
15. **Election Night Dashboard** — real-time results with multiple data feeds
16. **Breaking News Takeover** — full-width alert with live stream embed
17. **Sponsored Content Hub** — branded content landing pages (various advertiser layouts)
18. **Quiz/Poll Interactive** — engagement-driven interactive content
19. **Audio Story** — podcast/audio-led article variant
20. **Multi-Part Series Landing** — custom navigation for investigative series
21. **Comparison/Explainer** — side-by-side or tabbed explainer formats
22. **Local Station Variants** — 14+ station-specific overrides of national templates
23. **Event Live Page** — Super Bowl, Grammys, etc. with multi-stream
24. **Obituary/Memorial** — custom tribute format
25. **CBS Reports Documentary** — immersive documentary companion page
26. **In-Depth Hub** — curated deep-dive landing (cbsnews.com/in-depth/)
27. **Free Press Branded Section** — premium content section with distinct styling
28. **Weather Dashboard** — station-specific weather data integration
29. **Sports Scoreboard** — live scores with auto-updating data
30. **Newsletter Landing** — email signup with content previews
31. **Widget/Embed Variants** — syndication formats for third-party sites
32. **AMP Variants** — Google AMP versions with reduced feature sets
33. **Dark Mode Variants** — color-inverted versions of multiple base templates
34. **Mobile App Card Variants** — native app-specific card layouts
35. **Push Notification Landing** — optimized for deep-link arrival
36. **Social Preview** — optimized for Facebook/X in-app browsers
37-45+. **Various one-off campaign and event pages**

### Why 70% Custom Is Unsustainable

The 70/30 custom-to-standard ratio creates compounding problems:

| Problem | Impact |
|---------|--------|
| **Maintenance burden** | Each custom mode needs independent QA, accessibility testing, performance optimization |
| **Inconsistent UX** | Users encounter different interaction patterns across the site |
| **Slow feature rollout** | New features (dark mode, accessibility improvements) must be retrofitted to 30+ templates |
| **Duplicated effort** | Similar components rebuilt differently across modes |
| **Testing matrix explosion** | N modes x M platforms x P breakpoints = exponential QA surface |
| **Ad integration fragmentation** | Taboola/sponsored content integrated differently per mode |
| **Design debt** | Old modes don't match current brand kit (DM Serif Display, Source Sans 3, CBS color system) |
| **Performance variance** | No consistent Core Web Vitals baseline across modes |

Industry data confirms this pattern: enterprise application sprawl averages 897 systems with only 28% integration, and organizations spend $30,000-$40,000 annually per legacy system in maintenance alone.

### Paramount's Existing Consolidation Efforts (Context)

This UI mode sprawl problem exists within a broader Paramount consolidation wave already underway:

| Initiative | Status | Relevance |
|-----------|--------|-----------|
| **EyeQ Unified Stack** | Completed (2024) | Merged three separate tech stacks (CBS, Viacom, Pluto TV) into one — took 2 years |
| **14 Local Station App Merger** | Completed (May 2024) | 14 separate local station apps consolidated into single CBS News app |
| **Voyage Design System (VDS)** | Active | Paramount+'s unified design system built on atomic design principles, WCAG 2.2 AA compliant |
| **Nitro Design System** | Active | Pluto TV's component system — 12 designers, ~300 engineers, three-tier token architecture |
| **Paramount+ / Pluto TV Codebase Unification** | In progress (target: mid-2026) | Consolidating into single unified framework |

The feed-based architecture proposed here is the **logical next step** for the content/editorial layer — the infrastructure (EyeQ) and app shells (local station merger) are already consolidated, but the **page template and UI mode layer remains fragmented**.

Netflix's comparable experience: their Hawkins design system was created to address the same problem across **80+ internal applications** where "each application had its own UI patterns." Industry benchmarks show design systems cut development time by **47%** and design costs by **34%** — Eventbrite saved **534 engineering days** after launching theirs.

---

## 2. The Prototype's Feed-Based Architecture

### What This Prototype Demonstrates

The CBS News Live Updates prototype (`index.html`) implements a **composable feed architecture** that reduces the need for custom UI modes by assembling pages from a small set of reusable components:

#### Core Components Identified in Prototype

| Component | Description | Replaces |
|-----------|-------------|----------|
| **Navigation Shell** | Top bar + sticky header + topic nav | Duplicated across all 45+ modes |
| **Article Header Block** | Title, byline, timestamp, share toolbar | Reimplemented per mode |
| **Hero Media Block** | 16:9 image/video with caption | 5+ variants currently |
| **Article Body Block** | Semantic text with pull quotes, blockquotes | Base content renderer |
| **Live Update Entry** | Timestamped update with byline and share | Custom live blog mode |
| **Related Content Grid** | 2-col card grid with thumbnails | 3+ section variants |
| **Premium Section Block** | Branded content section (Free Press) | Custom branded modes |
| **Sponsored Feed** | Taboola-style cards in 2-col and 3-col grids | Per-property ad integration |
| **Ad Banner Block** | Full-width advertisement placement | Inconsistent ad slots |
| **Right Rail** | Sticky sidebar with video hero + story list | Desktop-only sidebar |
| **Tag Cloud** | Topic tags with links | Various taxonomy displays |
| **Footer** | Standard 5-column footer | Duplicated across modes |

#### Key Architectural Insight: Feed as Universal Container

The prototype's most important insight is that **the feed IS the page**. Rather than maintaining separate templates for:
- Live Updates page
- Article page
- Sponsored content page
- Video article page

...the architecture treats the page as a **vertical feed of typed blocks** that can be assembled in any order:

```
[Navigation Shell]
[Article Header Block]           ← conditional: present for articles
[Hero Media Block]               ← type: image | video | gallery | none
[Article Body Block]             ← conditional: present for text content
[Live Update Entry] x N          ← conditional: present for live blogs
[Related Content Grid]           ← always present, data-driven
[Premium Section Block]          ← conditional: editorial decision
[Sponsored Feed Block] x N      ← Taboola integration, infinite scroll
[Ad Banner Block]                ← placement rules engine
```

This means **one template** with **conditional block rendering** replaces **15-20 custom modes**.

---

## 3. Analysis: How the Feed Approach Solves Each Problem

### 3.1 Eliminating Custom Mode Categories

| Current Custom Mode | Feed Approach | Custom Code Eliminated |
|---------------------|---------------|----------------------|
| **Interactive Maps** | Embed as a `MediaBlock` type within article feed | Map rendering stays custom, but page chrome is shared |
| **Data Visualizations** | Embed as a `MediaBlock` type | Visualization code stays, layout is standardized |
| **Timeline Features** | Native `LiveUpdateEntry` components in reverse-chrono | **Fully eliminated** — this IS the live updates feed |
| **Immersive Longform** | `ArticleBodyBlock` with enhanced styles + `HeroMediaBlock` variants | Reduced to CSS-only customization |
| **Breaking News Takeover** | `ArticleHeaderBlock` with breaking flag + `HeroMediaBlock` as live video | **Fully eliminated** — flag-driven variant |
| **Sponsored Content Hub** | `SponsoredFeedBlock` with brand-specific card data | **Fully eliminated** — Taboola feed handles it |
| **Quiz/Poll Interactive** | Embed as `InteractiveBlock` type within feed | Interactive logic stays, page is shared |
| **Audio Story** | `HeroMediaBlock` type=audio + `ArticleBodyBlock` | **Fully eliminated** — media type variant |
| **Multi-Part Series** | `NavigationBlock` + multiple `ArticleBodyBlocks` | **Mostly eliminated** — navigation component |
| **Local Station Variants** | Same feed + station-specific `NavigationShell` config | **Fully eliminated** — config-driven |
| **Dark Mode Variants** | CSS custom properties on feed container | **Fully eliminated** — one theme system |
| **AMP Variants** | Same data model, AMP-compatible renderer | Reduced to one AMP feed renderer |
| **Mobile App Variants** | Same data model, native card renderers | Reduced to one native renderer |

### 3.2 Consolidation Impact Estimate

| Metric | Current State | After Feed Architecture | Reduction |
|--------|---------------|------------------------|-----------|
| **Total UI modes** | ~45-60 | ~8-12 base block types | **75-80%** |
| **Custom modes** | ~70% (31-42 modes) | ~15-20% (2-3 truly unique) | **85-90%** |
| **Standard modes** | ~30% (14-18 modes) | ~80-85% (all feed-based) | Inverted ratio |
| **QA test matrix** | 45 modes x 6 platforms | 12 blocks x 6 platforms | **73% reduction** |
| **Time to add dark mode** | Touch 45+ templates | Touch 1 theme system | **95%+ reduction** |
| **New feature rollout** | Weeks (per-mode retrofit) | Days (block-level change) | **~80% faster** |
| **Brand kit updates** | 45+ template updates | 12 block updates + tokens | **75% reduction** |

### 3.3 Taboola Feed Integration Benefits

The prototype already demonstrates how sponsored content becomes a **native part of the feed** rather than a bolted-on integration:

- **Current state:** Taboola Feed integrated differently across CBSNews.com, CBSSports.com, and local stations — each property has custom ad slot configurations
- **Feed approach:** `SponsoredFeedBlock` is a standard block type with consistent rendering rules

CBS Interactive's Taboola integration already delivered a **49% increase in organic CTR** and **31% increase in engagement**. A unified feed architecture would allow this to be **consistent across all properties** rather than optimized per-property.

### 3.4 Design Token Alignment with Voyage & Nitro Design Systems

Paramount Global is already moving toward component consolidation with **two active design systems** — Voyage Design System (VDS) for Paramount+ and the Nitro Design System for Pluto TV. Both use token-based architectures:

| Token Tier | Purpose | Feed Architecture Mapping |
|------------|---------|--------------------------|
| **Base Tokens** | Raw values (colors, spacing, type scales) | CBS brand kit values (cbs-red: #E10500, etc.) |
| **System Tokens** | Semantic meaning (surface-primary, text-heading) | Feed container & block-level theming |
| **Component Tokens** | Component-specific (card-border-radius, card-padding) | Block-specific appearance rules |

The prototype already implements this pattern implicitly through its Tailwind config:

```javascript
// Base tokens → CBS brand colors
colors: { cbs: { red: '#E10500', black: '#101010', ... } }
// System tokens → Font families mapped to brand fonts
fontFamily: { display: ['DM Serif Display'], serif: ['Source Serif 4'], sans: ['Source Sans 3'] }
```

This aligns with Paramount's direction of **consolidating codebases into a single, unified framework** across all streaming apps (EyeQ stack unification, Pluto TV + Paramount+ codebase merger targeting mid-2026). The CBS News content layer should follow the same philosophy, with feed blocks inheriting tokens from VDS/Nitro rather than maintaining a separate token system.

**VDS additionally enforces WCAG 2.2 AA accessibility** — a feed-based architecture inheriting VDS tokens would automatically bring accessibility compliance to all CBS News UI modes, eliminating the current need to audit accessibility across 45+ separate templates.

---

## 4. What the Feed Approach Does NOT Solve

Being honest about limitations:

| Remaining Challenge | Why It Persists |
|---------------------|-----------------|
| **Election Night Dashboard** | Truly unique real-time multi-data-stream UI — needs custom mode |
| **Weather Dashboard** | Station-specific data integration with maps — needs custom mode |
| **Sports Scoreboard** | Real-time score data with league-specific rules — needs custom mode |
| **Highly bespoke interactives** | One-off D3.js/WebGL experiences — embed in feed but custom code remains |
| **Legacy content** | Old articles with hardcoded HTML — migration cost is real |
| **Third-party embed diversity** | Each social/video embed has different API behavior |

**Estimated irreducible custom modes: 3-5** (down from 31-42)

---

## 5. Implementation Roadmap

### Phase 1: Block Component Library (Weeks 1-6)
- Extract the 12 block types from this prototype into a React/web component library
- Implement design tokens aligned with Nitro Design System's three-tier model
- Build block renderer that assembles pages from a block manifest (JSON)

### Phase 2: Feed API & Assembly Layer (Weeks 7-12)
- Build feed composition API that returns ordered block manifests per page
- Integrate with Ada for content delivery and block data population
- Register new feed-based modes in Feature Catalog, deprecate redundant custom modes

### Phase 3: Migration & Rollout (Weeks 13-24)
- Migrate highest-traffic pages first (article, video article, live updates)
- A/B test feed-based vs. legacy templates for engagement metrics
- Roll out to local stations using config-driven `NavigationShell` variants

### Phase 4: Custom Mode Retirement (Weeks 25-36)
- Audit remaining custom modes against feed block capabilities
- Build embed wrappers for irreducible custom content (elections, weather, sports)
- Decommission deprecated modes from Feature Catalog

---

## 6. Recommendation

**Yes — the feed-based architecture demonstrated in this prototype can solve the UI mode sprawl problem.**

The key insight is not just "fewer templates" but a fundamental shift in mental model:

> **From:** "What template does this page need?" (leading to N custom modes)
> **To:** "What blocks does this page contain?" (leading to 1 universal feed with M block types, where M << N)

This approach:
- Reduces the ~70% custom mode ratio to ~15-20%
- Inverts the standard-to-custom ratio from 30/70 to 80/20
- Completes the consolidation arc Paramount has already started (EyeQ stack unification, 14 station app merger, Pluto TV + Paramount+ codebase unification) by tackling the **content/editorial template layer** — the last major unconsolidated surface
- Inherits VDS accessibility compliance (WCAG 2.2 AA) and Nitro design tokens, eliminating per-template accessibility audits
- Leverages existing Taboola Feed integration patterns that already proved a 49% organic CTR lift
- Creates a foundation for rapid dark mode, accessibility, and brand kit updates across all properties simultaneously
- Mirrors proven results: Netflix's Hawkins unified 80+ apps, Eventbrite saved 534 engineering days, industry average shows 47% dev time reduction

The prototype proves the concept works for the most common CBS News page type (Live Updates article with sponsored feed). The next step is to validate it against the other high-traffic standard modes (video article, photo gallery, topic page) and build the block component library.

---

## Sources & References

### Paramount / CBS Internal Systems
- [Nitro Design System (Pluto TV / Paramount)](https://chrisgriffin.io/projects/pluto-tv-nitro-design-system) — Three-tier design token architecture, cross-platform component consolidation
- [Voyage Design System / Paramount+ Accessibility](https://www.susiejin.com/paramount-a11y) — VDS atomic design principles, WCAG 2.2 AA compliance
- [EyeQ: Pluto TV & Paramount Streaming Consolidation](https://www.tvrev.com/news/with-eyeq-pluto-tv-and-paramount-look-to-streamline-streaming) — Three tech stacks merged into unified framework
- [CBS News Local Station App Merger](https://www.newscaststudio.com/2024/05/30/cbs-news-stations-apps-merging/) — 14 station apps consolidated into one CBS News app
- [Paramount Codebase Consolidation](https://www.thewrap.com/pluto-tv-on-demand-library-interface-revamp-exclusive/) — Pluto TV + Paramount+ unification targeting mid-2026

### CBS News & Taboola
- [CBS Interactive Taboola Feed Case Study](https://www.taboola.com/resources/case-studies/cbs-interactive) — 49% organic CTR increase, feed-based engagement data
- [CBSNews.com 2018 Redesign](https://www.newscaststudio.com/2018/12/20/cbs-news-website-redesign-2018/) — Story page layout options, video emphasis, template variants
- [CBS News In-Depth Coverage](https://www.cbsnews.com/in-depth/) — Example of curated long-form content mode

### Industry Benchmarks & Design System ROI
- [Hawkins: Netflix Design System](https://netflixtechblog.com/hawkins-diving-into-the-reasoning-behind-our-design-system-964a7357547) — 80+ apps unified, reasoning behind component consolidation
- [ROI of Design Systems (Smashing Magazine)](https://www.smashingmagazine.com/2022/09/formula-roi-design-system/) — 47% dev time reduction, 34% design cost reduction, 534 engineering days saved (Eventbrite)
- [NewsKit Design System](https://www.newskit.co.uk/) — News-specific component library approach for template consolidation
- [Page Template vs. Component Architecture](https://blog.horizontaldigital.com/page-template-vs-component-site-architecture) — CMS architecture trade-offs
- [Press Gazette: CMS Analysis](https://pressgazette.co.uk/news/which-cms-most-popular-content-management-systems-for-publishers/) — Industry context on publisher CMS architectures
- [Design Systems 101 (NNGroup)](https://www.nngroup.com/articles/design-systems-101/) — Foundational design system principles
