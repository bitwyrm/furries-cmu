# Furries@CMU

A rough, review-ready SvelteKit prototype for the Furries@CMU club website. It follows the handmade pixel-zine direction in [`docs/figma.md`](docs/figma.md), with placeholder content where the club still needs to provide photos, its logo, the Discord invite, or officer details.

## Run locally

Requires Node.js 22.17 or newer.

```sh
npm install
npm run dev
```

Open the local URL printed by Vite. The pages are `/`, `/events/`, and `/officers/`.

## Content

Club copy, FAQs, events, and officer placeholders live in [`src/lib/content.js`](src/lib/content.js). The slideshow is manually controlled and uses marked photo placeholders until approved images are available.
