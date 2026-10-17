# NSA Care × Kopi Kenangan fundraiser

A mobile-first pre-order menu made for a school charity fundraiser. Visitors can browse and search the drink catalog, add up to five individual drinks, optionally add one 1 Liter bottle, and see the order total update before submitting.

## How it is organized

- `index.html` contains the menu, order form, and user interface.
- `catalog.js` holds the product catalog and browser-side price calculations.
- `order.js` handles the form and submits orders to the configured endpoint.
- `google-sheets-backend.gs` validates product IDs and quantities, recalculates prices on the server, then records the request in Google Sheets.
- `assets/products/` contains the menu imagery and image-source notes.

## Run locally

From this directory, run a small static server, for example:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000`. The menu and live total work without the order endpoint.

## Configure order submission

1. In `google-sheets-backend.gs`, replace `PASTE_GOOGLE_SHEET_ID_HERE` with the destination Sheet ID.
2. Deploy the script as a Google Apps Script web app.
3. Add its web app URL to `ORDER_ENDPOINT` in `order.js`.
4. Replace the `REPLACE_WITH_FUNDRAISER_NUMBER` links in `index.html` with the fundraiser's approved WhatsApp contact, if those links should be used.

The repository copy leaves these deployment-specific values unconfigured. Do not commit private contact details or deployment credentials to a public repository.

## Checks

Run `node --test order.test.mjs` to check order calculations and Rupiah formatting.
