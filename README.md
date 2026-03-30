# Body Awareness Massage Therapy

Website for Body Awareness massage therapy practice in Caro, MI.

**Live site:** [body-awareness.us](https://body-awareness.us)

## Stack

- **[Astro](https://astro.build)** — static site generator
- **Plain CSS** — custom properties

## Getting Started

```bash
npm install
npm run dev       # dev server → http://localhost:4321
npm run build     # production build → ./dist
npm run preview   # preview locally
```

## External Services

| Service | Purpose | Config Location |
|---------|---------|-----------------|
| **Google Fonts** | Typography | `src/layouts/` · Inter, Playfair Display |
| **Google Maps Embed** | Location map on contact page | `src/pages/contact.astro` · Embedded iframe |

No analytics, email, or payment services configured.

## Deployment

Static build deployed to Cloudflare Pages.
