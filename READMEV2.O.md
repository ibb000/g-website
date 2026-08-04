# g-website

Genie Studio website. Static frontend powered by a GitHub-hosted JSON CMS.

---

## What's in this repo

```
g-website/
├── main.html           # Main website (hero, services, projects, team, testimonials)
├── projects.html       # Full work page with filter tabs by project type
├── project.html        # Individual project detail page with embed support
├── data.json           # GitHub CMS — all dynamic content lives here
├── COLORD_HORIZENTAL.png
├── ICON_VERSION.png
├── head1.png
├── head2.png
├── head3.png
└── README.md
```

> `admin.html` is kept **locally only** — never push it to this repo. Open it from your machine to manage content.

---

## How the CMS works

`data.json` is the single source of truth. All three pages fetch it at runtime from:

```
https://raw.githubusercontent.com/ibb000/g-website/main/data.json
```

Any change saved through `admin.html` commits directly to `data.json` here. Pages update within ~30 seconds of a commit.

---

## Page structure

| File | Purpose |
|---|---|
| `main.html` | Homepage — shows up to 8 featured projects, "View All Work" links to `projects.html` |
| `projects.html` | Full project grid with filter tabs: All / Design / Media / Web / UX / Marketing |
| `project.html` | Project detail page — renders Behance, Vimeo, or YouTube embed from `data.json` |

---

## data.json schema

### projects
| Field | Type | Notes |
|---|---|---|
| `id` | string | Unique ID e.g. `proj_001` |
| `title` | string | Project name |
| `category` | string | Short label e.g. `Rebranding · Identity` |
| `tags` | string[] | Filter tags — `design`, `media`, `web`, `ux`, `marketing` (multi-tag supported) |
| `cover_url` | string | CDN image URL. Leave empty to use gradient. |
| `gradient` | string | CSS gradient fallback e.g. `linear-gradient(135deg, #00ABED, #004362)` |
| `external_url` | string | Behance or live site link |
| `embed_url` | string | Behance / Vimeo / YouTube URL — triggers project detail page routing |
| `description` | string | Shown on the project detail page |
| `sort_order` | integer | Display order. Lowest = first. First item on homepage gets wide card. |
| `is_active` | boolean | `false` hides from all pages |

### team
| Field | Type | Notes |
|---|---|---|
| `id` | string | Unique ID |
| `name` | string | Full name |
| `role` | string | Shown as pill badge |
| `bio` | string | 1–2 sentences |
| `photo_url` | string | Square image, displayed as circle |
| `sort_order` | integer | Left to right |
| `is_active` | boolean | Toggle visibility |

### testimonials
| Field | Type | Notes |
|---|---|---|
| `id` | string | Unique ID |
| `quote` | string | The testimonial text |
| `client_name` | string | Client full name |
| `client_title` | string | e.g. `CEO, Company Name` |
| `sort_order` | integer | Carousel slide order |
| `is_active` | boolean | Toggle visibility |

---

## Embed support

When a project has an `embed_url`, cards link to `project.html?id=...` instead of the external URL directly. The detail page auto-detects the embed type and builds the correct iframe:

- `behance.net/gallery/...` → Behance embed
- `vimeo.com/...` → Vimeo player
- `youtube.com/...` or `youtu.be/...` → YouTube embed

---

## Backend integration (when ready)

Everything is wired to swap from the GitHub CMS to a real API in one line. In `main.html`:

```js
const GITHUB_RAW_URL = 'https://raw.githubusercontent.com/ibb000/g-website/main/data.json';
const API_BASE = null; // swap to 'https://api.genies.studio/v1' when backend is ready
```

---

## Contact

Questions → Abdul
