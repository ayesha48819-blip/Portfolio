# Ayesha Nadeem — portfolio (React 18 + Vite)

Conversion-focused single-page portfolio for winning US small-business clients.
Dark teal `#041A19` + gold `#E9B44C` (gold is a highlight colour only; body copy is near-white
for AA contrast). Fraunces for display type, Inter for UI. Both fonts are self-hosted with `display=swap`.

## WhatsApp + calmer layout update

- One quiet, fixed WhatsApp shortcut: a labelled pill on desktop, a 52px icon on mobile.
  It opens a pre-filled chat with **+971 58 208 5220**. No auto-opening popup, pulse, or notification badge.
- The floating shortcut hides while the main Contact WhatsApp button is visible, avoiding duplicate actions.
- Edit the number in `config.whatsappNumber` and the greeting in `whatsapp.message`, both in `src/data.js`.
  The floating, Contact and footer links all use the same generated URL.
- Hero copy is shorter, with one filled call CTA and a quieter work link. The photo stays visible in the first mobile screen.
- All five case studies expand inline only when requested. Service inclusions use native, keyboard-friendly disclosure controls.
- Services use two roomy columns instead of four cramped ones. Process steps and skills no longer have individual boxes.
- Email and CV remain available as links rather than competing full-size buttons. The nav remains sticky.

## Run it

```bash
npm install
npm run dev       # local dev server
npm run build     # production build into dist/
npm run preview   # serve the production build
```

Form key (never commit it): copy `.env.example` to `.env` and set `VITE_WEB3FORMS_KEY`,
or set the same variable in Vercel → Settings → Environment Variables.

## File map — what each file does

| File | Purpose |
|---|---|
| `index.html` | Vite entry + all SEO: title, meta, Open Graph, Twitter card, JSON-LD (Person + ProfessionalService), favicon set, fonts with `display=swap`, commented Plausible snippet |
| `vite.config.js` | React plugin + relative base so the build works from any path |
| `src/main.jsx` | Mounts `<App/>` in StrictMode, imports the stylesheet |
| `src/App.jsx` | Page order + skip link: Hero → Work → Services → Process → Experience → About → FAQ → Contact → Footer |
| **`src/data.js`** | **Every word, price and link on the site.** Edit here only. ✏️ SLOT markers show the four placeholders waiting on you |
| `src/styles.css` | The whole design system, mobile-first: tokens, buttons, nav, sections, cards, form, reduced-motion fallback |
| `src/components/Nav.jsx` | Sticky nav (never hides), burger drawer under 860px, gold "Book a call" |
| `src/components/Hero.jsx` | Value prop, CTAs, honest-fresher line, trust row, photo |
| `src/components/Work.jsx` | 2 feature case studies + 3 compact cards with inline expand/collapse (`aria-expanded`, animated region) |
| `src/components/Services.jsx` | 4 packages from `data.js` + "every package includes" strip |
| `src/components/Process.jsx` | 4 steps + communication line |
| `src/components/Experience.jsx` | TechPock + Arfa timeline, a plain skills list |
| `src/components/About.jsx` | First-person copy + "working with me" card |
| `src/components/Faq.jsx` | Accessible accordion, one panel open at a time |
| `src/components/Contact.jsx` | Web3Forms submit (key from env), honeypot, honest no-key/error/success states, WhatsApp + email + CV + Cal.com slot |
| `src/components/Footer.jsx` | Links, privacy note, payment line |
| `src/components/WhatsAppButton.jsx` | Compact floating WhatsApp shortcut, hides when Contact's button is visible |
| `src/components/Icons.jsx` | Lightweight inline SVGs — no icon dependency |
| `src/assets/fonts/` | Local Fraunces and Inter WOFF2 fonts |
| `public/` | `robots.txt`, `sitemap.xml`, `manifest.webmanifest`, `404.html`, `og.png`, favicons, CV PDF |
| `src/assets/img/` | Hero photo + 5 project screenshots (WebP, width/height set in data) |
| `docs/` | 01 positioning · 02 approved copy · 03 pre-launch checklist + Vercel steps · 04 90-day plan |

## Honesty rules baked into the code

- No testimonial, client-logo, review or experience-year components exist — there is nothing to
  fake with.
- Every project card renders its `label` ("Personal project") from data; flip to "Course
  project" per project in one word.
- Missing repo/live URLs render "Code available on request" or hide the button — never a dead link.
- The contact form cannot fake success: without a Web3Forms key it says so plainly.

## Deploy

See `docs/03-prelaunch-checklist.md` section C for exact Vercel steps (env var, framework
preset, domain, sitemap/domain search-replace).
