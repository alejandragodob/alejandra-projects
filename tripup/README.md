# TripUp · interactive prototype

The Lisbon scenario from the design challenge as a working, mobile-optimised web app. React + Vite, no backend, mock data in `src/data.js`. Designed at iPhone 15 (393 × 852); on desktop it renders inside a phone frame, on a phone it fills the screen.

## Run it

```bash
npm install
npm run dev        # http://localhost:5173
npm run build      # static output in dist/
```

## Deploy to Vercel (2 minutes)

1. Go to https://vercel.com/new and import this GitHub repository.
2. Under **Root Directory** click *Edit* and choose `tripup`.
3. Framework preset: **Vite** (picked up from `vercel.json`). Build command `npm run build`, output `dist`.
4. Deploy. Every push to the connected branch redeploys.

Alternative without Vercel: the workflow in `.github/workflows/tripup-pages.yml` publishes `tripup/dist` to GitHub Pages on every push to `main`. Enable it once under **Settings → Pages → Source: GitHub Actions**.

## The journey the demo walks through

| # | Screen | What happens |
|---|---|---|
| 01 | Home | Lisbon is the live trip. Tap it. |
| 02 | Trip group view | Members, tonight's open slot, today's plan, money. Tap **+** to add Ren. |
| 03 | Add Ren (sheet) | Join link or contacts. "Joining tonight only" keeps her out of earlier splits. |
| 03b | Ren's side | Browser page: phone number, 4-digit code, no app. "See what Ren sees". |
| 04 | Create poll | Three options drafted from the group's Google Maps wishlist. Remove or swap any. |
| 05 | Push + chat | The poll lands in the group chat as a live card. Vote from there. |
| 06 | Live poll | Votes arrive live (Theo votes after ~4 s, bars animate, cards re-sort). Close once a majority exists. |
| 07 | Plan updated | Winner is in tonight's itinerary, tagged "poll", with directions and booking. |
| 08 | Log expense | Receipt scanned into items. Wine split excludes Nic and Ren; tap names to change. |
| 09 | Balances | 7 debts simplified to 3 transfers, each explained. Tap one to settle. |
| 10 | Settled | Group-wide confirmation posted to the chat. |

Tabs (Trips / Polls / Plan / Money) work throughout; Polls shows a badge while a poll is live.

## Structure

- `src/App.jsx` · all screens and the app state (members, poll, votes, expense, balances)
- `src/ui.jsx` · shared pieces: status bar, top bar, avatars, pill button, chips, rows, tab bar, sheet, toast
- `src/styles.css` · design tokens from the handoff spec (cream `#F7F3EC`, ink `#141414`, Newsreader + Figtree, Material Symbols Rounded)
- `public/img/` · photos (Unsplash placeholders from the design file; swap before shipping)

## Non-goals

Real payments, Google auth and WhatsApp integration are mocked with convincing UI, per the brief.
