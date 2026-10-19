# South Africa, 1652

The chart of the VOC's Cape of Good Hope Project v5, a.k.a. RSA: the founding of the Dutch East India Company station at Table Bay, read as the chart of a project imposed on the land and its people (Dlozi Mthethwa's reading). The repo holds the chart data, the source charts, and an HTML study of the chart in three pages: the chart itself, a history timeline, and a look ahead to 2040.

## Chart data

| | |
|---|---|
| **Date** | Sunday 7 April 1652 (Gregorian), the day Van Riebeeck's command began |
| **Time** | 12:12 LMT (10:58:32 UT), divined by Dlozi Mthethwa |
| **Place** | Table Bay, Cape Town · 33°55′S, 18°22′E |
| **System** | Tropical zodiac · Placidus houses · geocentric · True Node |
| **Ascendant** | 2°08′ Cancer |
| **Midheaven** | 20°54′ Aries |

## Files

| File | What it is |
|---|---|
| `site/index.html` | The study: one HTML file with three pages (Chart, Timeline, Future) |
| `site/fonts/` | Self-hosted Fraunces and IBM Plex fonts (latin subset, woff2) with their SIL Open Font License texts |
| `site/favicon.svg`, `site/favicon-32.png`, `site/apple-touch-icon.png` | Placeholder favicon, to be replaced by the Ascensys site-wide favicon |
| `site/og-image.png` | 1200 × 630 preview image for links shared on WhatsApp, LinkedIn, X and similar |
| Astro.com chart (PDF) | The Astrodienst chart for 7 April 1652, 12:12 LMT, Cape Town |
| Astrodienst ephemeris 1652 (PDF) | Planetary positions for March and April 1652 at 00:00 UT, used to verify the calculated positions |

## Deployment

The site lives at **https://rsa.ascensys.co.za/**. Upload the contents of `site/` straight into the subdomain's `public_html` folder, keeping the `fonts/` folder beside `index.html`. There's no build step, no server code and no database.

The Home link in the nav and footer goes to https://ascensys.co.za/. The canonical URL and the preview-image address in the page head both point to rsa.ascensys.co.za, so update them if the address changes.

Everything is free and open source. The fonts are self-hosted under the SIL Open Font License, so the page makes no calls to Google. The only outside request is the hero painting, loaded from Wikimedia Commons (public domain). The planetary data was computed with the Swiss Ephemeris, used under its AGPL licence.

## Pages

The HTML is a single file. Its pages show and hide in place, with no separate HTML files. Each page has its own address, so links and the browser's back button work.

| Page | Address | Contents |
|---|---|---|
| **Home** | https://ascensys.co.za/ | Back to the Ascensys home page |
| **Chart** | `#/chart` | The 1652 wheel and placements, chart shape, angles, rulership and dispositors, planetary condition, aspects, the Moon and the 8 April 1652 eclipse, houses, and sources |
| **Timeline** | `#/timeline` or `#/timeline/1994-04-27` | 26 events from 1657 to 2024, grouped by era. Clicking an event shows a summary, a bi-wheel (the 1652 chart inside, the sky on the day outside), the slow-planet contacts, and a reading of what the event meant for South Africa |
| **Future** | `#/future` or `#/future/2033-04` | A live "today" panel; seven chapters covering 2026 to 2040; an explorer with a month slider and a live bi-wheel; a calendar of every slow-planet crossing, filterable by planet; and a table of the eclipses that fall on the 1652 chart |

## Viewing

Open `site/index.html` in any browser, or visit https://rsa.ascensys.co.za/. It uses plain HTML, CSS and JavaScript, with no libraries and no network calls.

## How it's built

All planetary data is precomputed with the Swiss Ephemeris and embedded in the file as `SKY`. It includes:
- the sky on each event date,
- the sky on the 1st of each month from 2026 to 2040,
- every window from 2026 to 2040 in which Saturn, Uranus, Neptune or Pluto is within 1° of an aspect to the 1652 chart,
- the eclipses in that period that fall within 3° of a 1652 point.

The JavaScript is split into separate modules:

| Module | Does one thing |
|---|---|
| `CHART`, `EVENTS`, `CHAPTERS` | Content and chart data |
| `Astro`, `Dates`, `Dom` | Shared utilities |
| `SkyAt` | Works out the sky for any date by interpolating the monthly data (used by the live "today" panel) |
| `Wheel` | Draws the single wheel and the bi-wheel for every page |
| `ContactsTable` | Fills a contacts table and links its rows to the wheel |
| `ChartView`, `TimelineView`, `FutureView` | One module per page |
| `Router` | Shows the right page for the address |

To add an event, add an entry to `EVENTS` and its transit data to `SKY.events`, keyed by date.

## Method

- **Transits:** cast for 12:00 SAST (10:00 UT). The Moon is left out because most event times aren't recorded.
- **Contacts:** slow planets (Jupiter to Pluto) in major aspect to the 1652 chart. The orb is 2° for Jupiter and 3° for the others, with sextiles held to two thirds of that.
- **Future calendar:** windows within 1° of exact, from 2026 to 2040.

## Key findings

- **Venus in Taurus is the sole final dispositor**, and Venus rules the 4th house of land.
- **Saturn rises in Cancer** in the 1st house and squares the Midheaven within 1°01′.
- **A total solar eclipse at 19°10′ Aries** fell about 23½ hours after the chart moment, 1°44′ from the Midheaven.
- **History:**
  - Pluto squared the 1652 Jupiter, ruler of the 6th house of servants, within 0°07′ on the day of emancipation in 1834.
  - Pluto squared its own place in the 12th house of prisons within 0°18′ when the Rivonia sentences were passed in 1964.
  - Uranus opposed Mars, ruler of the 5th house of the young, within 0°47′ on the day of the Soweto Uprising in 1976.
- **Future:**
  - Neptune crosses every body in the 9th house between 2026 and 2036, then the Midheaven.
  - Uranus crosses the Ascendant from 2032 to 2034, alongside the chart's Saturn return.
  - Total solar eclipses fall on the North Node in 2033 and on Mercury in 2034.

## Sources and method

The **positions** come from the Swiss Ephemeris (Astrodienst AG). They were checked against the Astro.com chart and the Astrodienst ephemeris for 1652.

The **date** comes from the historical record: the ships anchored on 6 April 1652, and Van Riebeeck's command began on 7 April. The **time** was divined by Dlozi Mthethwa.

The **interpretive frameworks** are borrowed from these sources:
- Ptolemy, *Tetrabiblos*, for dignities, sect and the use of eclipses.
- William Lilly, *Christian Astrology* (1647).
- Baigent, Campion and Harvey, *Mundane Astrology* (1984).
- Nicholas Campion, *The Book of World Horoscopes*.

The **history** draws on SA History Online and Wikipedia. Full links are in the HTML.

## Changelog

| Version | Date | Change |
|---|---|---|
| 2.3 | 2026-10-19 | Chart page hero now carries Charles Davidson Bell's *Jan van Riebeeck se aankoms aan die Kaap* (c. 1850, public domain), loaded from Wikimedia's 1280px thumbnail with a fallback address, under a dark overlay, with a credit line. |
| 2.2 | 2026-10-19 | Added the project frame: the VOC's Cape of Good Hope Project v5, a.k.a. RSA. New Thesis section on the Chart page (Dlozi Mthethwa's reading in her words, the Heeren XVII, Terreblanche's research, the five versions, and the board question). "Read as a project" table in Rulership; "In the project" column in the houses table. Timeline eras renamed as versions v1 to v5, with an "In the project" line for every event. Future intro and a "For the project" line for every chapter. Sources, meta tags, footer and preview image updated. |
| 2.1 | 2026-10-19 | Prepared for rsa.ascensys.co.za. Renamed to `index.html`; fonts self-hosted instead of loaded from Google; added a page description, canonical URL, sharing tags, a preview image and a placeholder favicon; the "today" panel now updates from the visitor's date; added a Home link to ascensys.co.za; noted that the Future data runs to December 2040; tightened the nav for small phones. |
| 2.0 | 2026-10-12 | Rebuilt as a three-page site in one file, with a nav and a footer. Added the Timeline page (26 events, bi-wheels, contacts, readings) and the Future page (today panel, seven chapters, month explorer, crossing calendar, eclipse table). Added the 5th and 12th house rulers to the rulership table. |
| 1.0 | 2026-10-12 | First release of the HTML deep dive, the chart PDFs and the README |