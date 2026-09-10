# Eurotrip 2026 — trip site

A single-page static site about Aaron's 23 Aug – 3 Sep 2026 trip:
Chicago → Paris → Florence → Rome → Israel → home. Built to share with
friends and family. Everything lives in `index.html` — no build step, no
dependencies. Open it in a browser to view.

## Current state

Complete except for photos. All 28 photo frames are captioned placeholders.

## The one remaining job: photos

Each contact sheet holds `.frame` figures with a striped placeholder well:

```html
<figure class="frame"><div class="well"><span>PAR-01</span></div><figcaption>Arrival, CDG Terminal 1</figcaption></figure>
```

To fill one, swap the `.well` div for an `img` and keep the figcaption:

```html
<figure class="frame"><img src="photos/par-01.jpg" alt="Arrival at CDG Terminal 1"><figcaption>Arrival, CDG Terminal 1</figcaption></figure>
```

`.frame img` is already styled (4:3, `object-fit: cover`, same border as the
wells) so no CSS changes are needed. Put images in `photos/`.

Frame slots: PAR-01…06, FLR-01…07, ROM-01…07, TLV-01…08.

Captions are placeholders written from the itinerary, not from the actual
images. **Look at each photo and rewrite its caption to match what is really
in it.** Add or remove frames freely — the sheets are auto-fill grids, and
the "N frames" count in each `.sheet-head` should be updated to match.

### Photo source

Google Photos, 23 Aug – 3 Sep 2026. Three days span two cities, so use
timestamps to split them:

- **26 Aug** — Paris until the ~09:30 Orly flight, Florence from 11:20
- **28 Aug** — Florence until the 09:03 train, Rome from 11:05
- **31 Aug** — Rome until the 05:30 flight, Israel from 10:00

Two experiences were run by hosts who shoot photos — a Rome Vespa tour with
a photographer (Vahid) and a Florence hills e-bike ride (Gabriele). Those
sets may be in Airbnb Messages and are likely the best images available.

## Design

Concept: the trip as a book of ticket stubs. Each leg is a ticket — signage
header band, perforated tear line (`.perf`, with punched notches at both
edges), a mono data strip of the real record locators, and for the three
Airbnb cities a second torn-off `.ticket-stay` stub underneath.

- **Type** — Archivo Narrow (signage: city names, headings), Newsreader
  (narrative), IBM Plex Mono (all ticket data, labels, times)
- **Color** — pale grey-green security-print stock, deep teal accent,
  muted stamp red used once on the footer stamp
- **Themes** — full light and dark palettes as CSS custom properties on
  `:root`, redefined under `prefers-color-scheme` and `[data-theme]`.
  Never set a color outside the token system; both themes must work.
- **Numbering** — LEG 01…05 is a real sequence (legs of one journey), not
  decoration. Keep it meaningful if sections are added.

## Facts and sources

Every number on the page came from a booking confirmation or the Airbnb app.
Do not invent details; if something is unverified, leave it off.

| Leg | Detail | Source |
|---|---|---|
| Paris | UA987 ORD 18:10 → CDG 09:20, 787-10, rec BPFH7K | Air Canada email |
| Paris | Louvre VIP tour, Mon 24 15:45, Arc de Triomphe du Carrousel | Viator 1440148467 |
| Paris | Le Bazar, Mon 24 20:30, Levallois-Perret | Google/Zenchef |
| Paris | Versailles e-bike + hamlet, Tue 25 12:15 | Unlimited Biking #18330649 |
| Paris | Safrane, Tue 25 20:00, 17th | Uniiti |
| Paris | Crazy Horse, Tue 25 evening | order 862506 |
| Paris | Stay: Xavier, Aug 24–26, Pompidou/Bastille | Airbnb app |
| Florence | VY1503 ORY 09:30 → FLR 11:20, rec LMGZ6Q | Vueling email |
| Florence | Accademia + Bargello 72h, Wed 26 13:30 | order 24018019 |
| Florence | E-bikes in the hills, Wed 26 17:00–19:00, Gabriele | Airbnb app |
| Florence | Stay: Lorenzo, Aug 26–28, by the Fortezza da Basso | Airbnb app |
| Rome | Italo 8951, Firenze SMN 09:03 → Roma 11:05, coach 6 seat 77, IYG5JI | Italo email |
| Rome | Vespa tour w/ photographer, Fri 28 15:00–16:45, Vahid | Airbnb app |
| Rome | Ba' Ghetto, Fri 28 19:30, Via del Portico d'Ottavia 57 | Superb email |
| Rome | Stay: Andrea, Aug 28–31, Campo de' Fiori / the Ghetto | Airbnb app |
| Israel | Wizz W4 6041 FCO T3 05:30 → TLV 10:00, seat 31A, PSH5HK | Wizz email |
| Israel | ETA-IL approved 28 Aug | piba.gov.il email |
| Home | SWISS LX8 ZRH 13:05 → ORD T5 15:55, 777-300ER, business, 07K, gate E23, ACKRAO | Air Canada / SWISS |

**Known gap:** there is no confirmation anywhere for the Tel Aviv → Zurich
leg. The page deliberately does not claim one. If Aaron supplies it, add it
to the Home ticket.

## Publishing

Not yet published. Options: publish as a Claude Artifact for a private
shareable link, or serve `index.html` from GitHub Pages on this repo.
