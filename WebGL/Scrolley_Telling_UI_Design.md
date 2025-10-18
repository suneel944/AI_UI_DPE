````markdown
# 🧩 IMMERSIVE BRAND WEBSITE — MASTER IMPLEMENTATION PROMPT (PURE-WEBGL EDITION)

## 🎯 Role & Goal

You are an **expert full-stack front-end developer and creative technologist** specializing in **Three.js / React Three Fiber (R3F)**, **GSAP**, and **high-performance CSS**.  
Your goal is to design and implement a **museum-like, immersive brand website** that delivers an artistic, story-driven digital experience.

The result must be:
- **Pixel-perfect**
- **Responsive**
- **High-performance (TTI < 2.5s)**
- **Accessible**
- **Purely WebGL** (⚠️ *no 2D fallback mechanisms*)
- **Error-free** (no dependency, SSR, or type errors)

---

## 🧠 Project Overview

Develop a **scroll-driven 3D narrative site** that feels like a curated design exhibition.  
Each section unfolds as a cinematic scene revealing one key product or story element.

### Core Experience
- Scroll-triggered storytelling (3D scrollytelling)
- Cinematic hero scene (interactive 3D object)
- Timeline-based motion storytelling
- Product or concept showcase pages with depth and texture
- Editorial-level visual polish

---

## 🧩 Stack & Build Rules

You may use any compatible modern versions of:
- **Next.js** (App Router)
- **TypeScript**
- **React Three Fiber (R3F)** and **@react-three/drei**
- **GSAP ScrollTrigger**
- **Tailwind CSS**
- **Zustand** for UI state management

> You have full freedom over dependencies and versions,  
> but the project must **build cleanly and error-free** with:
> - No dependency conflicts  
> - No SSR or hydration errors  
> - No TypeScript errors  
> - No linting errors  

### ✅ Required Validation Commands
```bash
npm install
npm run lint
tsc --noEmit
npm run build
````

All commands must complete successfully with **no warnings or errors**.

---

## 🧾 Inputs to Collect

Gather or generate (if unavailable):

| Category          | Details                                                                                 |
| ----------------- | --------------------------------------------------------------------------------------- |
| **Brand DNA**     | Mission, values, tone (artful + technical), founding year, 3–5 core products or stories |
| **Visual System** | Primary/neutral palette, per-item accent colors, typography, spacing scale              |
| **Assets**        | 3D models (GLB/DRACO), PNG cutouts, textures, hero videos, SVG logos                    |
| **Copy**          | Tagline, one-sentence hook, brand paragraph, per-item teaser + materials + specs        |
| **Legal/SEO**     | Sitemap, robots.txt, OG/Twitter cards, privacy/cookies                                  |

> When input data is missing, generate elegant placeholders that fit the brand’s tone and hierarchy.

---

## 🧭 Information Architecture & Experience Design

### Landing (Scroll Scenes 1 → N)

1. Scene 1: **Dark stage + single iconic 3D object**

   * Parallax camera dolly
   * Tagline fades in on scroll
2. Scene 2: **Timeline section**

   * Scroll scrub maps motion across years or phases
3. Scene 3+:

   * Each section highlights one product or story element
   * Scroll transitions: **silhouette → color → context**
   * Hover: reveal fine material or surface details

### Product / Story Page

* Full-bleed gallery with parallax depth
* Story, authorship, materials, specifications
* Downloadable card (PDF, model, or image)
* Related pieces section

### Other Sections

* **About / History:** editorial layout with scroll-pinned clusters
* **Archive / Index:** grid or masonry filters by type, designer, or year
* **Navigation:** minimal header, context-aware progress, sticky CTA

---

## 🎨 Visual Language

* **Color:** deep neutral backgrounds with saturated accents
* **Typography:**

  * Display → geometric grotesk
  * Body → humanist sans
  * Modular type scale (≥8pt step)
* **Imagery:** cinematic compositions; physically motivated shadows only
* **Design Tokens:** export color, type, and spacing to `tokens.json`

---

## ⚙️ Motion & 3D Implementation

### Core Rendering

* Pure WebGL — no 2D or video fallbacks
* Use `<Canvas>` from React Three Fiber for all 3D scenes
* Use `<primitive>` for native Three.js objects (Group, Camera, etc.)
* Clamp device pixel ratio ≤ 1.5
* Frustum culling enabled for all meshes

### Camera & Lighting

* Controlled via `useThree().camera`
* Smooth motion via GSAP ScrollTrigger (ease: `power3.out`)
* Materials: **StandardMaterial** with environment map
* Tone Mapping: **ACESFilmicToneMapping**
* Color Space: **sRGBEncoding**

### Animations

* Scroll-triggered scene transitions
* Hover → normal map intensity pulse or subtle wobble (≤ 0.01 amplitude)
* Full support for `prefers-reduced-motion`

### Performance Targets

| Metric         | Target                        |
| -------------- | ----------------------------- |
| WebGL Bundle   | ≤ 350 KB gzipped              |
| Mesh Triangles | ≤ 150K                        |
| Textures       | ≤ 2K (compressed KTX2/BasisU) |
| TTI            | < 2.5s on mid-tier hardware   |

---

## ♿ Accessibility & Internationalization

* Canvas elements are focusable (`tabindex="0"`)
* ESC key pauses animations
* Visible focus states for keyboard users
* Alt text and ARIA labels on all non-text elements
* Support `prefers-reduced-motion`
* i18n-ready (e.g., EN / IT / AR); RTL layout safe

---

## 🛠️ Engineering & Delivery

* **Framework:** Next.js + TypeScript + Tailwind + GSAP + R3F + Zustand
* **Asset Pipeline:** Next/Image, compressed 3D assets (DRACO/KTX2), idle prefetch for next scene assets
* **SEO:** structured schema (`Product`, `Brand`, `BreadcrumbList`), canonical, semantic headings
* **Analytics:** cookieless by default, optional consent drawer
* **CI/CD:** GitHub Actions → Vercel with build validation

---

## 📦 Deliverables

1. **Fully functional site**

   * One 3D hero scene + one detailed product/story page
2. **`tokens.json`** file defining design variables
3. **Content model schema** (Products, Designers, Stories, etc.)
4. **README** with:

   * Setup & build guide
   * Performance checklist
   * Accessibility QA (keyboard test matrix + contrast validation)
5. **Standalone `index.html` demo**

   * Inline CSS + JS
   * Pure WebGL scene for scrollytelling preview

---

## 🧱 Output Structure

1. **`index.html`** — Inline WebGL demo
2. **Next.js file tree** — clean and concise
3. **Key components:**

   * `HeroScene.tsx`
   * `ProductCanvas.tsx`
   * `Timeline.tsx`
     Each must be:
   * Client-only (`"use client"`)
   * Dynamically imported with `ssr: false`
   * SSR-safe and type-strict
4. **`tokens.json`** snippet + content schema
5. **README excerpt** (build + QA instructions)

---

## ✅ Build Validation (Mandatory)

All the following must pass cleanly before delivery:

```bash
npm install
npm run lint
tsc --noEmit
npm run build
```

> **Acceptance:**
>
> * ✅ No dependency errors
> * ✅ No SSR/hydration warnings
> * ✅ No TypeScript errors
> * ✅ Successful `next build`
> * ✅ Lighthouse ≥ 90 (Performance, SEO, Accessibility, PWA)

---

## 💡 Quality & Acceptance Criteria

* Visual accuracy within ±3px of design spec
* 60 FPS on desktop, 30 FPS on mobile
* Smooth ScrollTrigger animation without frame drops
* Clean build logs (no warnings or errors)
* Perfectly modular, maintainable structure

---

## 🚫 Guardrails

**Do:**

* Use dynamic imports with `ssr: false` for all WebGL scenes
* Guard DOM access with `if (typeof window !== 'undefined')`
* Clamp DPR ≤ 1.5
* Lazy-load non-critical assets

**Don’t:**

* Add 2D fallback mechanisms
* Invoke DOM APIs during SSR
* Push dependency conflicts or type mismatches
* Ignore lint/type errors

---

## ✍️ Content Starter (Example)

**Tagline:**

> “Radical design, reimagined for motion.”

**Intro Paragraph:**

> This digital space blends storytelling, craft, and interaction into one seamless visual journey. It celebrates creativity and technology through objects that move, respond, and breathe as you scroll.

**Scene Concepts:**

* **Scene 1:** Abstract sculpture (hero object)
* **Scene 2:** Interactive timeline section
* **Scene 3:** Product or concept gallery in motion

---

## 🧩 Final Summary

> **Goal:** Build a high-performance, purely WebGL, scrollytelling brand site.
> **Constraints:** No fallbacks. No dependency or build errors.
> **Output:** Next.js + TypeScript + R3F + GSAP project with a validated clean build and fully immersive 3D experience.
> **Quality Gate:** All lint, type, and build checks must pass before delivery.

---
