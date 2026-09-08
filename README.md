# Pine Park — Edmonds

Marketing site for **Pine Park**, fourteen new townhomes at 614 5th Ave S, Edmonds, WA 98020.

Built by NuCon Construction & Development. Offered by Windermere Real Estate GH LLC.
Listing broker **Adam E. Cobb**, co-listing agent **Ryan Forbus**.

---

## What's here

| Path | |
|---|---|
| `index.html` | The entire site — markup, styles and script in one file. No build step, no dependencies. |
| `*.jpg` / `*.png` | Photography, logos, favicons and the social preview image. |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is. |

**Every file sits at the repository root, deliberately.** GitHub's browser
uploader flattens folders and silently drops nested ones, so a flat layout is
the only structure that survives a drag-and-drop upload intact. Photo files are
named by building: `a_*` Building A, `b102_*` the B102 home, `c_*` Building C.

The site is a single page with hash routing: the home page lives at `/`, and each
residence at `/#/home/A101`, `/#/home/C104`, and so on. Because routing happens in
the URL fragment, it works on any static host with no server configuration.

## Publishing with GitHub Pages

1. Push this folder to a repository.
2. **Settings → Pages → Build and deployment**: source **Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
3. The site goes live at `https://<user>.github.io/<repo>/` within a minute or two.

### Using the pinepark614.com domain

1. Add a file named `CNAME` at the root containing one line: `pinepark614.com`
2. At your DNS provider, point the apex record at GitHub Pages
   (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`),
   and add a `CNAME` record for `www` pointing at `<user>.github.io`.
3. Back in **Settings → Pages**, enter the custom domain and tick **Enforce HTTPS**.

## Updating prices and availability

Everything the site displays comes from one block near the top of the `<script>`
in `index.html`, labelled **PINE PARK — EDITABLE DATA**. The site map, the
availability table, the floor plan summaries and each residence page all read
from it, so a single edit updates the whole site.

```js
{id:"C103", bldg:"C", plan:"C2", sqft:1446, price:949000, status:"available", beds:"", baths:""},
```

- **Mark a home sold** — set `status:"sold"` and `price:null`. It goes hatched and
  inert on the site map, drops out of the "available" counts, and its page shows
  as sold.
- **Change a price** — edit `price` as a plain number, no commas or dollar sign.
- **Add bedrooms and bathrooms** — fill in `beds:"3"` and `baths:"2.5"`. Those
  fields are hidden while they are empty and appear automatically once set.

Floor plan descriptions live in `PLANS`, the finish list in `FEATURES`, and the
nearby businesses in `NEIGHBORS`, all in the same block.

## Notes before going live

- `og:image` in the `<head>` must be an **absolute** URL for link previews to
  appear when the site is texted or emailed. Update the host if you are not
  serving from pinepark614.com.
- Photography is representative of the community; finishes, orientation and views
  vary by residence. Square footage is approximate and taken from builder plans.

---

© Windermere Real Estate GH LLC. Equal Housing Opportunity.
