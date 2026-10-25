# Savora: QR Digital Menu System

**Savora** is a mobile-first digital menu system for hotels and restaurants. Guests scan a QR code, browse the menu on their phone, and contact the venue. It is a **menu only**: there is no cart, checkout or payment.

**First deployment:** Essentia Premier Hotel, Chennai: In-Room Dining Menu

**Live site:** https://essentia-premier-hotel.ritviksharma119.workers.dev/

> The live website keeps the Essentia Premier Hotel branding. Savora is the name of the menu system behind it.

## About Savora

- One lightweight page per venue, with no app to install and no login for guests
- Venue name, timings, contact number, menu items, descriptions and allergen key are all kept in one file, so each new venue is a copy with its own details
- Works from a QR code on a card, table or room
- A generic template, with the venue settings in one block at the top of the file, is planned. Essentia is the first venue built on it.

## Scan to open the menu

<p align="center">
  <img src="essentia-qr-card.png" alt="Scan to discover our menu: QR card for the Essentia Premier Hotel in-room dining menu" width="300">
</p>

The QR card above is the printable A6 design (`essentia-qr-card.png`).

## What it includes

- Welcome page, then a Food / Beverages category page, then the menu
- 61 dishes across Breakfast, Salads, Soups, Starters, Main Course (Vegetarian and Non-Vegetarian), Staples & Indian Breads, Round the Clock sandwiches and Beer
- Search by dish name, and vegetarian / non-vegetarian filters
- Dish detail sheet with price, serving details, variants and a short description
- Meal timings, room service extension and allergen key
- Light and dark mode, and layouts built for phones

## Project structure

```
essentia-premier-hotel/
├── README.md
├── wrangler.jsonc        Cloudflare deploy settings
├── essentia-qr-card.png  QR card shown above
└── public/
    └── index.html        the whole website (HTML, CSS, JS and menu data in one file)
```

## Updating the menu

All menu items are in one list near the top of the `<script>` section of `public/index.html`. Each dish is one line:

```
["Dish name", "category", price, "diet", "serving details", "variants"]
```

- `category`: `bf` Breakfast, `sa` Salads, `so` Soups, `st` Starters, `mv` Main Course (Veg), `mn` Main Course (Non-Veg), `sp` Staples & Breads, `rc` Round the Clock, `be` Beer
- `price`: a number, or `null` to show "Price unavailable"
- `diet`: `"v"` vegetarian, `"n"` non-vegetarian, or `""` if not confirmed

Dish descriptions are in the `DRAFT` list just below it, keyed by dish name.

## Deployment (Cloudflare)

The site is a static page and needs no build step. It deploys from this repo with:

- **Deploy command:** `npx wrangler deploy`
- **Assets directory:** `public` (set in `wrangler.jsonc`)
- **Production branch:** `main`

Every push to `main` updates the live site automatically.

> The QR code points to the live address above. If the address changes (for example, a custom domain), the QR code and printed cards must be regenerated.

## Still to confirm with the hotel

- Prices for Sweet Corn Soup, Manchow Soup and Clear Soup
- Full beverages list (only Kingfisher Strong 650 ml is included)
- Chef approval of all dish descriptions (currently drafts, labelled as such)
- Vegetarian / non-vegetarian marking for breakfast items, soups, staples and the egg sandwich
- Allergen details per dish (only the general allergen key is shown)
- Which dishes are served at lunch and dinner, beyond the timings already shown
- Official hotel logo file and dish photographs, and permission to use the current food and beverage photos
- Whether 5508 is dialled from the room phone only, or also has an outside number

## Notes

- Dish photos are not shown on individual dishes, because no verified photos of the served dishes are available.
- Prices are in INR.
