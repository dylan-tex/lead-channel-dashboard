# Lead Channel Dashboard

A single-page planning dashboard for distributing apartment-locating leads across marketing channels. Adjust lead allocations and business assumptions to compare estimated deals and invoiced revenue.

## Technology

HTML, inline CSS, browser JavaScript, and Chart.js 3.9.1 loaded from cdnjs. The repository has no package dependencies to install, build step, or backend. An internet connection is required to load Chart.js.

## Run locally

```sh
git clone https://github.com/dylan-tex/lead-channel-dashboard.git
cd lead-channel-dashboard
python3 -m http.server 8000 --bind 127.0.0.1
```

Open [localhost:8000](http://localhost:8000). You can also open `index.html` directly in a browser.

## Usage

1. Set the monthly lead target, target deals, invoiced revenue goal, amount per invoice, and close rate at the top of the page.
2. Move the sliders for Bandit Signs, Brochures, Business Cards, Networking Events, Booths & Stands, TV/Radio, YouTube, Podcasting, TikTok, Instagram, and Facebook.
3. Review the lead distribution chart, estimated-deals chart, and channel breakdown table.
4. Compare **Total allocated** with the lead target. Each slider is capped individually; the combined allocation can exceed the target.

The breakdown table calculates each channel's estimated deals as `Math.round(leads × close rate / 100)` and its invoiced amount as `estimated deals × amount per invoice`. Totals sum the rounded channel values, so they may differ from rounding the combined lead count once. Target deals and the overall revenue goal are planning inputs displayed on the page; they do not automatically change the allocations.

The values are scenario estimates based on the selected assumptions. The dashboard does not fetch CRM records or marketing results, and changes reset when the page reloads.

## Structure and deployment

- [index.html](index.html) contains the entire dashboard: layout, styles, controls, charts, and calculations.
- [CNAME](CNAME) contains `lead-dashboard.dylansilver.org`, the repository's custom-domain configuration for GitHub Pages. The file alone does not establish that Pages or DNS is active.

Deploy by serving the repository root on a static host, or configure GitHub Pages to publish the root of the desired branch. No build command is needed. Review `CNAME` before publishing under another domain.

## Manual checks

No automated tests are included. Confirm both charts load, change a channel's slider and the close rate, and verify the table recalculates. For example, 25 leads at an 8% close rate produce 2 estimated deals for that channel. Refresh to restore the defaults.
