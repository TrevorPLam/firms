You are a senior full-stack engineer building a production-ready local service website template in a GitHub repo (developed in GitHub Codespaces).

GOAL
Build “Archetype 6 — Professional Services (trust + consult-first)” as a reusable, modern, high-converting marketing template for firms like legal, accounting/bookkeeping, IT managed services.

Primary conversion: Qualified lead → Book consult.
Secondary conversion: “Request info / contact” (for prospects not ready to book).

STACK (REQUIRED)
- Next.js (App Router)
- TypeScript
- Tailwind CSS
No CMS. No database. Single config file for all content + behavior.

MARKETING + TRUST STANDARDS FOR THIS ARCHETYPE (NON-NEGOTIABLE)
A) Clear positioning + specialization
- Home must state:
  - who you help (industries/segments)
  - outcomes (not features)
  - your “fit” criteria (who you do/don’t serve)
This reduces junk leads and improves consult conversion (consult-first websites focus on clarity + qualification). :contentReference[oaicite:2]{index=2}

B) Authority + E-E-A-T style trust signals
- Must include:
  - Team page with bios + credentials placeholders
  - Case studies/testimonials
  - Transparent “About” responsibility signals (who runs site, how to contact, policies)
Google emphasizes helpful, reliable, people-first content; quality guidelines emphasize trust/authority, especially for sensitive topics. :contentReference[oaicite:3]{index=3}

C) Consult intake is a conversion system
- Implement a 2-step conversion:
  1) Qualification form (short, but structured)
  2) Scheduling (embedded scheduler OR scheduling link)
Legal/firm intake guidance repeatedly emphasizes streamlined, professional intake to improve conversion and client confidence. :contentReference[oaicite:4]{index=4}

D) “Resources” must exist, but be honest
- Include a Resources hub (FAQs + 2–4 guide placeholders) to support trust and local SEO.
- Do NOT invent expert claims or results.

OUTPUT CONTRACT (ANTI-TRUNCATION)
You MUST deliver the repo in STAGES. Do NOT omit code “for brevity”.
Stage A: Repo scaffold + config + layout + libs + SEO endpoints + devcontainer + tooling.
Stage B: Components/sections + pages/routes (Home, Services, Industries/WhoWeServe, Process, Case Studies, Team, Resources, Book Consult, Contact, Policies/Privacy/Terms, Reviews/Testimonials, 404).
Stage C: QA checklist + README + final notes (build/lint/dev).

If you reach output limits mid-stage, STOP and print: “STOPPED AT: <filepath>”.

QUALITY BAR (MUST PASS)
- npm run dev
- npm run build
- npm run lint
- No runtime errors.
- No lorem ipsum. Unknown inputs must be explicit: "TODO:INPUT".

CODE COMMENTARY (FOR AI ITERATION)
- Add concise comments:
  - 1–2 line header per file: purpose.
  - Short “why” comments for non-obvious logic.
  - TODOs must be explicit: TODO:INPUT or TODO:PROD (with next action).
- Do not add excessive commentary.

NON-NEGOTIABLE UX RULES
- Mobile-first.
- Sticky primary CTA = “Book Consult” on every page via layout.
- Secondary CTA on mobile sticky bar: “Call” (tel: link) or “Contact” if phone not configured.
- Sticky bar must NOT cover content (global bottom padding).
- Conversion flow:
  - Book Consult page must show (A) qualification form above fold, then (B) scheduling immediately after submit success.
  - If scheduling is link-mode, show the link immediately after successful qualification.

MODERN DESIGN ACCEPTANCE CRITERIA (STRICT)
- Consistent container + section spacing rhythm (py-12/py-16).
- Typography hierarchy: hero 3xl–5xl, readable body.
- Buttons: primary + secondary with hover + focus-visible.
- Cards: consistent radius + subtle border/shadow.
- Home page section order (MANDATORY):
  1) HeroSection (headline, subheadline, 3 bullets, Book Consult CTA, proof row)
  2) WhoWeHelpSection (industries/segments + “best fit” bullets)
  3) ServicesSection (packaged offers cards)
  4) ProofSection (testimonials + credentials badges placeholders)
  5) ProcessSection (3–5 steps)
  6) CaseStudiesPreviewSection (2–4)
  7) FAQSection (3–6)
  8) CTASection (final Book Consult)

CANONICAL FILE TREE (MUST MATCH EXACTLY)
- src/
  - app/
    - layout.tsx
    - globals.css
    - page.tsx                          (Home)
    - services/page.tsx                 (Packaged offers)
    - who-we-serve/page.tsx             (Industries/segments)
    - process/page.tsx
    - case-studies/page.tsx
    - case-studies/[slug]/page.tsx
    - team/page.tsx
    - resources/page.tsx
    - resources/[slug]/page.tsx
    - book/page.tsx                     (Qualification + scheduling)
    - contact/page.tsx
    - testimonials/page.tsx             (or reviews)
    - policies/page.tsx
    - privacy/page.tsx
    - terms/page.tsx
    - not-found.tsx
    - api/
      - lead/route.ts                   (qualification submit)
    - robots.ts
    - sitemap.ts
  - components/
    - Header.tsx
    - Footer.tsx
    - StickyCTA.tsx
    - JsonLd.tsx
    - NAP.tsx
    - ContactMethods.tsx
    - QualificationForm.tsx
    - SchedulerEmbed.tsx
    - ProofStack.tsx
    - Testimonials.tsx
    - FAQ.tsx
    - ServiceCards.tsx
    - CaseStudyCards.tsx
    - TeamGrid.tsx
    - sections/
      - HeroSection.tsx
      - WhoWeHelpSection.tsx
      - ServicesSection.tsx
      - ProofSection.tsx
      - ProcessSection.tsx
      - CaseStudiesPreviewSection.tsx
      - FAQSection.tsx
      - CTASection.tsx
  - config/site.ts
  - lib/
    - tracking.ts
    - analytics.ts
    - schema.ts
    - seo.ts
    - rateLimit.ts
    - utils.ts
- .devcontainer/devcontainer.json
- README.md
- package.json
- tailwind.config.ts
- postcss.config.js
- tsconfig.json
- eslint config

CONFIG (SINGLE SOURCE OF TRUTH) — EXACT TYPES REQUIRED
In src/config/site.ts define and export these EXACT interfaces and config object. Do not rename fields.

type BookingEmbedConfig =
  | { mode: "iframe"; iframeUrl: string }
  | { mode: "script"; scriptSrc: string; scriptContainerId: string }
  | { mode: "link"; linkUrl: string; linkLabel?: string };

type AnalyticsConfig =
  | { provider: "none" }
  | { provider: "ga4"; ga4MeasurementId: string }
  | { provider: "plausible"; plausibleDomain: string };

type SpamProtectionConfig = {
  turnstileEnabled: boolean;
  turnstileSiteKey?: string;
  turnstileSecretKey?: string;
};

type CopyBlocks = {
  heroHeadline: string;
  heroSubheadline: string;
  heroBullets: [string, string, string];
  ctaSectionHeadline: string;
  ctaSectionSubheadline: string;
};

type PackagedOffer = {
  slug: string;
  name: string;
  outcomeHeadline: string;
  includedBullets: string[];
  startingAtText?: string;              // optional; TODO:INPUT
  whoItsForBullets: string[];
  whoItsNotForBullets: string[];
};

type Segment = {
  slug: string;
  name: string;                         // e.g., “Solo founders”, “Clinics”, “Contractors”
  problemsBullets: string[];
  outcomesBullets: string[];
};

type ProcessStep = { title: string; description: string };

type CaseStudy = {
  slug: string;
  title: string;
  clientType?: string;
  problem: string;
  approach: string;
  resultsText: string;                  // TODO:INPUT if unknown
};

type TeamMember = {
  slug: string;
  name: string;
  role: string;
  bio: string;                          // TODO:INPUT
  credentials?: string[];               // TODO:INPUT
  photoPath?: string;
};

type Resource = {
  slug: string;
  title: string;
  summary: string;
  sections: { heading: string; paragraphs: string[] }[]; // can be placeholders but not lorem ipsum
};

type QualificationField =
  | { name: "name"; label: string; type: "text"; required: true }
  | { name: "email"; label: string; type: "email"; required: true }
  | { name: "phone"; label: string; type: "tel"; required?: boolean }
  | { name: "company"; label: string; type: "text"; required?: boolean }
  | { name: "need"; label: string; type: "textarea"; required: true }
  | { name: "budget"; label: string; type: "select"; required?: boolean; options: string[] }
  | { name: "timeline"; label: string; type: "select"; required?: boolean; options: string[] };

type QualificationFormConfig = {
  fields: QualificationField[];
  requireConsentCheckbox: boolean;      // for contact permission language (copy in config)
  confirmationHeadline: string;
  confirmationBody: string;
};

export interface SiteConfig {
  baseUrl: string;                      // TODO:INPUT
  businessName: string;
  tagline: string;

  phoneDisplay?: string;
  phoneDial?: string;
  email?: string;

  copy: CopyBlocks;

  address: { serviceAreaOnly: true } | { line1: string; line2?: string; city: string; state: string; zip: string };
  hours: { day: string; open: string; close: string; closed?: boolean }[];

  offers: PackagedOffer[];
  segments: Segment[];
  process: ProcessStep[];
  caseStudies: CaseStudy[];
  team: TeamMember[];
  resources: Resource[];

  qualificationForm: QualificationFormConfig;

  bookingEmbed: BookingEmbedConfig;     // scheduler for consult calls
  spamProtection: SpamProtectionConfig;
  leadRouting: { webhookUrl?: string }; // TODO:INPUT

  reviews: { highlightQuotes: { name?: string; text: string }[]; reviewPlatformLinks: { label: string; url: string }[] };
  faqs: { q: string; a: string }[];

  seo: { siteTitle: string; titleTemplate: string; metaDescription: string; primaryServiceKeywords: string[]; ogImagePath?: string };

  analytics: AnalyticsConfig;
}

export const siteConfig: SiteConfig = { ... } // populate with TODO:INPUT placeholders

BOOK / QUALIFICATION FLOW (MANDATORY)
- /book page:
  - Render QualificationForm above fold.
  - On successful submit, show:
    - confirmation message (from config)
    - SchedulerEmbed immediately below (or a scheduling link if link-mode)
- /api/lead:
  - honeypot + reject if filled
  - best-effort in-memory rate limiting per IP (TODO:PROD seam)
  - sanitize inputs
  - verify Turnstile if enabled + secret provided
  - forward to webhookUrl if present; else console.log and return success

ANALYTICS (STRICT)
- Standard events:
  cta_book_click, phone_click, qualification_submit, qualification_success, qualification_error, scheduler_loaded
- If GA4 selected: use @next/third-parties/google GoogleAnalytics in layout (do not hand-roll scripts).
- track() logs to console and forwards to provider if enabled.

SEO RULES (STRICT)
- Canonical URLs via Metadata API: alternates.canonical.
- robots.ts must include Sitemap: `${baseUrl}/sitemap.xml`.
- sitemap.ts must include:
  - /, /services, /who-we-serve, /process, /case-studies, /team, /resources, /book, /contact, /testimonials, /policies, /privacy, /terms
  - plus each case study slug and each resource slug
- Content must be helpful/reliable; avoid thin filler pages per Google guidance. :contentReference[oaicite:5]{index=5}

SCHEMA (JSON-LD)
- Organization (Home)
- LocalBusiness if appropriate (Contact)
- BreadcrumbList on internal pages
- FAQPage where FAQs render

NOW EXECUTE STAGE A, then STAGE B, then STAGE C in the same response if possible.
