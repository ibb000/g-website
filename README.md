# g-website

Genie Studio website. Static frontend — your job is to build the CMS backend that powers it.

Full spec is in `handoff.html` — open it in a browser and read it before writing anything.

---

## What's in this repo

```
g-website/
├── index.html          # The entire frontend (single file)
├── handoff.html        # Backend spec — schemas, endpoints, JSON contracts
├── COLORD_HORIZENTAL.png
├── ICON_VERSION.png
├── head1.png           # Team photo placeholders
├── head2.png
├── head3.png
└── README.md
```

---

## How the frontend works

Single HTML file, vanilla JS, no framework, no build step. On page load it fires `fetch()` calls to the API and renders each section dynamically. While `API_BASE` is `null` it falls back to hardcoded static data so the site stays functional.

When you have a staging URL ready, I update one line at the top of the script:

```js
const API_BASE = null; // swap to 'https://staging-api.genies.studio/v1'
```

That's the entire integration handoff point between us.

---

## Your starting checklist

1. Read `handoff.html` fully before starting
2. Set up the DB with the 6 collections defined in the spec
3. Stand up a staging API and send me the base URL
4. Configure CORS for `https://genies.studio` and `http://localhost:*` — do this before sending the URL, I can't test without it
5. Seed it with the current content (it's all visible in `index.html` as the static fallback data)
6. We test staging together, then flip to prod

---

## Collections to build

| Collection | Type | Notes |
|---|---|---|
| `projects` | Collection | Cover cards in the Work section |
| `services` | Collection | 3×2 grid in the What We Do section |
| `team_members` | Collection | Board section, 3 cards |
| `testimonials` | Collection | Dark carousel |
| `stats` | Singleton | 4 count-up numbers |
| `site_globals` | Singleton | Hero copy, marquee, footer, contact email |

Full field definitions, required flags, and example values are all in `handoff.html`.

---

## Contact

Questions → Abdul
