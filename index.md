# PropertyFacts — Privacy Policy

Last updated: 28 July 2026

PropertyFacts is a browser extension that adds public property data to listings
on spitogatos.gr. It is not affiliated with, authorised by, or endorsed by
Spitogatos.

## The short version

**PropertyFacts has no server, no account, and no analytics.** The developer does not receive user data. Extension data stays in your browser profile and is deleted when you remove the extension.

## What the extension stores, and where

All extension data lives in `chrome.storage.local` on your device. The extension does not transmit stored settings or cached results to the developer.

| What | Why | Retention |
|---|---|---|
| Your settings (on/off, language, light/dark) | To remember your choices | Until you change or uninstall |
| Cached public data about map areas (amenities, air quality, seismic history, land registry, forest map) | Avoid repeat requests for the same area | 30-180 days by source; oldest entries are dropped when cache storage exceeds 6 MB |
| Optional zone value entered by you | Remember the value for that neighbourhood when calculating the ENFIA estimate | Until you change it or uninstall |

The current release does not create price history records.

**You can clear cached public-data results at any time** from the extension toolbar popup ("Clear cached data"). Settings and optional zone values remain until you change them or remove the extension; removing the extension deletes all extension data.

## What is sent over the network, and to whom

To describe a listing's surroundings, the extension asks public data services
about **a location** — a latitude and longitude. It never sends the listing
URL, the listing ID, a price, an identifier, or anything about you.

| Service | Operator | What is sent |
|---|---|---|
| Overpass API (`overpass-api.de`, `overpass.private.coffee`) | OpenStreetMap community | A coordinate, rounded to about 1 km |
| Open-Meteo Air Quality (`air-quality-api.open-meteo.com`) | Open-Meteo | A coordinate, rounded to about 1 km |
| USGS Earthquake Catalog (`earthquake.usgs.gov`) | U.S. Geological Survey | A coordinate, rounded to about 1 km |
| Hellenic Cadastre (`services-eu1.arcgis.com`, `gis.ktimanet.gr`) | Ελληνικό Κτηματολόγιο | A listing coordinate; the map image request is made only when you open the aerial photo |

These are third-party services with their own privacy practices, and each will
see your IP address as any website you visit does. The extension sends them no
identifier of any kind, so they cannot link one request to another or to you
beyond what your IP already reveals.

Listed buildings, traditional settlements and Greek regional statistics are
**bundled inside the extension**, so looking them up sends no request at all.

## What the extension does not do

- No accounts, logins, or profiles
- No analytics, telemetry, crash reporting, or advertising
- No selling, sharing, or transfer of user data to anyone — there is nobody to
  transfer it to
- No tracking across sites; it runs only on spitogatos.gr pages
- No reading or altering of the Spitogatos page beyond adding its own panel
- No remotely hosted code

## Permissions, and why each is needed

- **storage** — to keep your settings and the local cache described above
- **declarativeNetRequest** — to set a descriptive `User-Agent` on requests to
  the OpenStreetMap Overpass API, which its usage policy asks clients to do so
  they can be identified. It is used for nothing else and applies only to those
  two hosts.
- **Host permissions** — one entry per public data service listed above, so the
  extension can query it. No wildcard or all-sites access is requested.

## Payments

The panel footer contains a single optional donation link, which opens Buy Me a
Coffee in a new tab. It is an ordinary external link: nothing is behind a
paywall, no feature is withheld, and the extension has no payment processing of
any kind. Nothing is sent to that service unless you click the link.

## Children

PropertyFacts is a tool for property research and is not directed at children.

## Changes

Material changes to this policy are published at
<https://mariosbikos.github.io/propertyfacts-privacy/>, where the full revision
history is public.

## Contact

Questions or corrections: <mariosbikos@gmail.com>
