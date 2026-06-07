# Eternal Scrapbook — Interactive Romantic Timeline / Memories

An interactive, scroll-driven romantic timeline page where couples can relive their shared memories. Cards animate into view as users scroll, locked memories unlock progressively, and the experience culminates in a romantic ending section with floating hearts and confetti.

## Files

| File         | Description                                      |
|--------------|--------------------------------------------------|
| `index.html` | Single-page HTML app (HTML + CSS + Vanilla JS)   |
| `config.json`| JSON-driven configuration for all content        |
| `README.md`  | This documentation file                          |

## Config.json Fields

| Field                | Type     | Description                                             |
|----------------------|----------|---------------------------------------------------------|
| `coupleNames`        | string   | Names displayed in the hero headline                    |
| `timeline`           | array    | Array of memory objects (see below)                     |
| `timeline[].date`    | string   | ISO date string (YYYY-MM-DD) for sorting                |
| `timeline[].displayDate` | string | Human-readable date shown on card                   |
| `timeline[].title`   | string   | Memory card title                                       |
| `timeline[].description` | string | Full description shown in modal                     |
| `timeline[].image`   | string   | Image URL for the memory card                           |
| `timeline[].locked`  | boolean  | Whether the memory starts locked (unlocks on scroll)    |
| `endingMessage`      | string   | Romantic message displayed in the ending section        |
| `theme`              | object   | Color overrides (primary, primaryContainer, background) |
| `email.publicKey`    | string   | EmailJS public key                                      |
| `email.serviceId`    | string   | EmailJS service ID                                      |
| `email.templateId`   | string   | EmailJS template ID                                     |
| `email.toEmail`      | string   | Recipient email for notification                        |

## User Flow

1. Page loads → config.json is fetched (falls back to defaults if unavailable)
2. Hero section displays couple names with a fade-in animation
3. User scrolls down through the vertical timeline
4. Memory cards animate in from alternating left/right sides
5. Locked memories auto-unlock as user scrolls past them (shimmer effect)
6. Clicking an unlocked card opens a detail modal with full image and description
7. When the last memory is revealed, the romantic ending section appears
8. Floating hearts animate across the screen; email notification is sent (if configured)
9. Users can replay memories or add new ones via the "Add a Page" button

## Features

- **Timeline scroll** — Vertical timeline with alternating left/right cards
- **Memory cards** — Animate into view on scroll with rotation and scale effects
- **Click to open modal** — Full detail view with image, date, description
- **Unlock effects** — Locked cards have a magical shimmer glow; unlock progressively
- **Romantic ending** — Confetti/hearts animation when all memories are viewed
- **Background music toggle** — Music button in the nav bar
- **Mouse heart trail** — Subtle hearts follow the cursor
- **Add memory** — Form to add new memory entries dynamically
- **EmailJS integration** — Sends notification email when ending section is reached
- **JSON-driven** — All content customizable via config.json

## Tech Stack

- HTML, CSS, Vanilla JavaScript (single file)
- Tailwind CSS via CDN
- Google Material Symbols (icons)
- Google Fonts (Playfair Display, Plus Jakarta Sans)
- EmailJS via CDN (for email notifications)

## Deployment

1. Copy all files (`index.html`, `config.json`) to your hosting provider
2. Edit `config.json` to customize couple names, timeline events, images, and ending message
3. (Optional) Set up EmailJS:
   - Create an account at [emailjs.com](https://www.emailjs.com/)
   - Create a service and email template
   - Fill in `email.publicKey`, `email.serviceId`, `email.templateId`, and `email.toEmail` in config.json
4. Serve via any static hosting (GitHub Pages, Netlify, Vercel, S3, etc.)

No build step required. Works entirely client-side.

## Responsive Design

- Mobile-first layout with Tailwind responsive utilities
- No horizontal scrolling
- Timeline stacks vertically on mobile, alternates left/right on desktop
- All modals and overlays are fully responsive
