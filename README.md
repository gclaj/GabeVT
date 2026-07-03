# Gabe for Vermont — Campaign Website

A professional, fully static campaign website for **Gabe Lajeunesse**, Democrat for
Vermont State Senate (Washington District), built to replace the previous
gabeforvt.com setup.

No frameworks, no build step, no database — just HTML, CSS, and a little vanilla
JavaScript. Any web host (or free static hosting) can serve it, and anyone on the
campaign can edit it with a text editor.

## Pages

| Page | Purpose |
|---|---|
| `index.html` | Home — hero, three priority pillars, record stats, plan teaser, news, calls to action |
| `about.html` | Meet Gabe — full biography: Air Force service, Georgetown Law, teaching, family, community roles |
| `priorities.html` | Six issue platforms: housing, healthcare, economy, flood resilience, working lands & rural trust, welcoming communities |
| `plan.html` | **The Green Mountain Compact** — signature five-point plan with measurable commitments |
| `record.html` | A Builder's Record — service timeline + housing record ($20M+ built, 33 homes, 75+ entitled) |
| `news.html` | Op-eds (VTDigger, Waterbury Roundabout), campaign coverage, press contact |
| `get-involved.html` | Volunteer sign-up, house parties, yard signs, letters to the editor, email list |
| `vote.html` | Voter guide — 2026 dates, registration, early/mail voting, open-primary FAQ |
| `donate.html` | Donation tiers + Vermont campaign-finance fine print |
| `404.html` | Friendly not-found page |

Shared assets live in `css/styles.css`, `js/main.js`, and `assets/`.

## Launch checklist (do these before going live)

1. **Photos.** Campaign photography is in place: `assets/gabe-statehouse.jpg`
   (home hero, about page), `assets/gabe-headshot.jpg` (home "Meet Gabe"
   section), and `assets/og-image.jpg` (the social-share card used by every
   page's `og:image` tag). To swap a photo, replace the file and keep the name.
2. **Donations.** In `donate.html`, replace the `#donate-pending` hrefs on the
   donation tiers with the campaign's real payment link (e.g. an ActBlue page),
   then delete the "Online donations are being set up" notice.
3. **Forms.** The volunteer and email-list forms in `get-involved.html` are
   marked `data-placeholder="true"` and show a fallback notice on submit.
   Point their `action` at a real endpoint (Formspree, Action Network, Google
   Forms, NGP VAN…) and remove the `data-placeholder` attribute.
4. **Contact email.** The site uses `info@gabeforvt.com` throughout — confirm
   that inbox exists, or search-and-replace with the real address.
5. **Social links.** Fill in the `#` placeholders in the footer (`<div class="social">`).
6. **Legal disclaimer.** In the footer of every page, add the committee's
   registered mailing address next to "Paid for by Gabe for Vermont" as
   required by Vermont campaign finance law (17 V.S.A. ch. 61).
7. **Fact-check.** Bio and record claims were compiled from the previous
   website's press coverage and Gabe's published op-eds. New framing (e.g.
   "The Green Mountain Compact" and per-issue commitments) is draft campaign
   copy — the candidate should review every page before launch.
8. **Election dates.** The banner and vote page use Tuesday, Aug 11, 2026
   (primary) and Tuesday, Nov 3, 2026 (general) — verify against the Secretary
   of State's official calendar.

## Deployment

**GitHub Pages is already wired up.** Every push to `main` publishes the site
to the `gh-pages` branch via `.github/workflows/deploy-pages.yml`.

**One-time step to go live** (requires repo admin, ~15 seconds): go to
**Settings → Pages → Build and deployment**, set Source to **"Deploy from a
branch"**, choose branch **`gh-pages`** with folder **`/ (root)`**, and Save.
The site then serves at `https://<owner>.github.io/GabeVT/` and updates
automatically on every push to `main` from then on.

To serve the site at **gabeforvt.com**: in the repo's Settings → Pages, enter
the custom domain, then at the domain registrar create a `CNAME` record
pointing `www.gabeforvt.com` at `<owner>.github.io` (plus the four GitHub
Pages `A` records on the apex domain), and enable "Enforce HTTPS" once the
certificate is issued.

Alternative hosts (Netlify / Cloudflare Pages) also work: connect the repo
and deploy the root directory — no build command needed.

To preview locally: `python3 -m http.server 8000` in the repo root, then open
<http://localhost:8000>.

## Editing content

Every page is plain HTML — open it, edit the text, save. Site-wide styles are
CSS custom properties at the top of `css/styles.css` (colors, fonts, spacing),
so a rebrand is a five-line change. The palette follows the campaign's
green, white, and blue. `js/main.js` handles the mobile menu,
stat count-up animation, and placeholder-form notices; nothing else depends on it.

## Sources for site content

- [The Bridge — LaJeunesse and Kohn announce campaigns (Mar 2026)](https://thebridgevt.org/2026/03/lajeunesse-and-kohn-announce-campaigns-for-vermont-legislature/)
- [VTDigger — "The lesson of Act 181 is that trust matters" (Apr 2026)](https://vtdigger.org/2026/04/02/opinion-gabe-lajeunesse-the-lesson-of-act-181-is-that-trust-matters/)
- [VTDigger — "Update CHIP to build flood-ready housing" (Mar 2026)](https://vtdigger.org/2026/03/06/gabe-lajeunesse-update-chip-to-build-flood-ready-housing/)
- [VTDigger — "Vermont's future depends on restoring legal immigration" (May 2026)](https://vtdigger.org/2026/05/14/opinion-vermonts-future-depends-on-restoring-legal-immigration/)
- [Waterbury Roundabout — "Vermont can't afford another year of drift" (Jun 2026)](https://www.waterburyroundabout.org/opinion-archive/letter-vermont-cant-afford-another-year-of-drift)
