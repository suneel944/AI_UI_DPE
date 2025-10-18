-----

## Expert Creative Technologist Project Specification

### 0\) Role

You are an expert full-stack front-end developer & creative technologist (Next.js + TypeScript + Tailwind + Three.js/react-three-fiber + GSAP ScrollTrigger) building a **museum-like, immersive brand website** inspired by a **Radical Italian Design ethos**.

The result must be **pixel-perfect, performant, and accessible**, featuring **3D/WebGL scrollytelling** that narrates each hero product’s story with cinematic fidelity.

-----

### 1\) Project Requirements — Core Technical Rules

  * **Stack:** Use Next.js (App Router), TypeScript, Tailwind, react-three-fiber (R3F), @react-three/drei, GSAP ScrollTrigger, and Zustand.
  * **Build Integrity:** The project must build successfully (`npm run build`) and show **zero dependency, type, or SSR errors**.
  * **Dependencies:** Do not include any version numbers in `package.json` within the prompt—only ensure cross-package compatibility.
  * **Code Quality:** ESLint and TypeScript must both pass cleanly (`npm run lint`, `tsc --noEmit`).

-----

### 2\) Inputs to Collect (Assume and Proceed)

**If data is missing, generate tasteful placeholder text and assets aligned with a Surreal-Radical Design aesthetic.**

| Category | Placeholder Requirement |
| :--- | :--- |
| **Brand DNA** | Mission, values, tone (**playful-surreal + craftsmanship-serious**), founding year (e.g., 1960s/70s), 3–5 iconic, highly sculptural products, designer credits, and a short 90-word brand history. |
| **Visual System** | Primary/neutral palette (dark base), saturated accent colors per product, type stack (display grotesk + humanist body), and a defined spacing scale. |
| **Assets** | Placeholder 3D meshes (`.GLB`/`DRACO`), product cutouts, 360° sprite sequences, and SVG wordmarks. |
| **Copy** | Tagline, one-sentence hook, 80–120-word brand paragraph, and per-product teaser/history/material/spec. |

-----

### 3\) Information Architecture & Experience

#### Landing Page (Scrollytelling)

  * **Scene 1:** Dark stage, single iconic object, parallax camera dolly on scroll, tagline fade-in.
  * **Scene 2:** "Radical Since [Year]" timeline scrub (scroll $\rightarrow$ year markers).
  * **Scene 3+:** One scene per hero product: silhouette $\rightarrow$ color $\rightarrow$ context with micro-interaction on hover.

#### Key Templates & Navigation

  * **Product Page Template:** Full-bleed gallery, history/authorship, craft/material callouts, spec table, download PDF, related pieces.
  * **Navigation:** Minimal header, scroll progress indicator, reduced chrome during 3D scenes, sticky "Inquire/Buy" CTA.

-----

### 4\) Visual Language

  * **Color:** Dark-neutral base, saturated accents, wide-gamut-safe, **WCAG AA contrast**.
  * **Typography:** Grotesk display + humanist body; $\ge 8$ pt modular step; tight tracking on headings.
  * **Imagery:** Cinematic crops; no artificial drop-shadows—only physically motivated light.
  * **Tokens:** All visual tokens (colors, type, spacing, radii) **must be exported in a `tokens.json`**.

-----

### 5\) Motion & 3D — Engineering Rules

  * **Strictly WebGL only.** $\rightarrow$ **No fallback mechanisms** (no image/video substitutes, no parallax alternatives).
  * **SSR-Safe:** All 3D logic runs client-side only (`"use client"` + `dynamic({ ssr: false })`). Protect all DOM calls behind runtime checks (`if (typeof window !== "undefined")`).
  * **R3F Discipline:**
      * Use `useThree`/`useFrame` only inside `<Canvas>`.
      * For native Three.js objects, render using `<primitive object={...} />`.
      * Camera control via `useThree().camera` and smooth scroll via GSAP ScrollTrigger.
  * **Rendering:** `ACESFilmicToneMapping`, `sRGBEncoding`, pixel ratio clamp **$\le 1.5$**, frustum culling enabled.
  * **Interaction:** GSAP ScrollTrigger drives camera dolly and object animation. Hover = material normal map intensity pulse; subtle wobble amplitude **$\le 0.01$**. Respect `prefers-reduced-motion`.

#### Performance Check

  * WebGL bundle **$\le 350$ KB gz**.
  * Mesh **$\le 150$ K tris**.
  * TTI **$< 2.5$ s** on mid hardware.

-----

### 6\) Accessibility & i18n

  * Canvas focusable (`tabindex="0"`), visible focus rings.
  * ESC pauses motion.
  * Alt text + ARIA on imagery.
  * Full support for `prefers-reduced-motion`.
  * i18n-ready (en/it/ar); RTL-safe components.

-----

### 7\) Engineering & Delivery

  * **Stack:** Next.js (App Router) + TypeScript + Tailwind + GSAP + R3F + Zustand.
  * **Assets:** Optimized via Next/Image; DRACO/KTX2 compression; prefetch next scene assets when idle.
  * **SEO:** Structured data (Product, Brand, BreadcrumbList), canonical, descriptive H1/H2s.

-----

### 8\) Deliverables

  * Fully working Next.js site with **one 3D hero scene** + **one complete product page**.
  * `tokens.json` (colors, type, spacing, radii).
  * Content model schema (for Products, Designers, Exhibitions, News).
  * `README` with: Run + build instructions, Performance checklist, Accessibility QA script.
  * `index.html` demo of the hero scrollytelling (inline CSS + JS, pure WebGL).

-----

### 9\) Output Format (Exact Order)

1.  `index.html` — standalone scrollytelling demo (inline CSS + JS).
2.  Next.js file tree — concise.
3.  Key components (`HeroScene.tsx`, `ProductCanvas.tsx`, `Timeline.tsx`).
4.  `tokens.json` snippet and schema.
5.  `README` excerpt — build/run + QA checklist.

-----

### 10\) Build Validation (Mandatory)

The output project **must pass all commands cleanly**:

```bash
npm install
npm run lint
tsc --noEmit
npm run build
```

**Acceptance Requirement:**
✅ Zero dependency errors
✅ Zero TypeScript errors
✅ Zero SSR/hydration issues
✅ Successful `next build`

-----

### 13\) Content Starter (Generalized)

  * **Tagline:** “Radical design, lovingly unreasonable.”
  * **Brand Paragraph:** 90-word blend of Italian radical design, superior craft, and playful humor.
  * **Products (for implementation):**
      * **Iconic Sculpture A (1972):** Playful provocation turned icon.
      * **Iconic Sculpture B (1970):** Surreal form that defies function.
      * **Iconic Sculpture C (1971):** A field of rest, unexpectedly large.
