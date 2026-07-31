# PropertyFacts — Privacy Policy

Last updated: 31 July 2026

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
| Cached public data about map areas (amenities, transport, administrative areas, air quality, seismic history, land registry, forest map) | Avoid repeat requests for the same area | 30-180 days by source; oldest entries are dropped when cache storage exceeds 6 MB |
| Optional zone value entered by you | Remember the value for that neighbourhood when calculating the ENFIA estimate | Until you change it or uninstall |

The current release does not create price history records.

**You can clear cached public-data results at any time** from the extension toolbar popup ("Clear cached data"). Settings and optional zone values remain until you change them or remove the extension; removing the extension deletes all extension data.

## What is sent over the network, and to whom

To describe a listing's surroundings, the extension asks public data services
about **a location** — a latitude and longitude. It never sends the listing
URL, the listing ID, a price, an identifier, or anything about you.

| Service | Operator | What is sent |
|---|---|---|
| QLever OSM (`qlever.dev`) | University of Freiburg | The listing's coordinate |
| Overpass API (`overpass-api.de`, `overpass.private.coffee`) | OpenStreetMap community | The listing's coordinate |
| Overpass API fallback (`maps.mail.ru`) — see below | VK (Russia) | The listing's coordinate |
| Open-Meteo Air Quality (`air-quality-api.open-meteo.com`) | Open-Meteo | A coordinate rounded to about 1 km |
| USGS Earthquake Catalog (`earthquake.usgs.gov`) | U.S. Geological Survey | A coordinate rounded to about 1 km |
| Hellenic Cadastre (`services-eu1.arcgis.com`, `gis.ktimanet.gr`) | Ελληνικό Κτηματολόγιο | The listing's coordinate; the map image request is made only when you open the aerial photo |

Amenities, transport and administrative areas are looked up on QLever first;
the Overpass servers cover terrain (coast, forest, roads) and stand in for
QLever when it is slow. Both receive the same coordinate and nothing else.

### How precise is "the listing's coordinate"?

It is the position the listing itself publishes, and for most listings that is
already an approximate one: the site offsets the pin by roughly 300–500 m, and
the panel labels those listings "approximate". Some listings publish an exact
pin, and for those the coordinate is the building.

Two of the services above receive **less** than that. Air quality is read from a
roughly 11 km climate grid and seismicity is a count within a 100 km radius, so
neither answer changes if the point moves a kilometre — the extension rounds the
coordinate to about 1 km before sending it to them, because it costs nothing.

The others cannot be coarsened without making the answer wrong: a walking time
is not a walking time if the starting point moved 700 m, and the cadastre parcel
is a specific piece of ground. Those services receive the coordinate as
published. An earlier version of this page said every service got a rounded
coordinate; that was not true of the amenity and cadastre lookups, and saying so
plainly is better than a comforting sentence the code did not honour.

These are third-party services with their own privacy practices, and each will
see your IP address as any website you visit does. The extension sends them no
identifier of any kind, so they cannot link one request to another or to you
beyond what your IP already reveals.

### About the `maps.mail.ru` fallback

The OpenStreetMap community's own Overpass servers are heavily overloaded and
periodically refuse or queue requests. `maps.mail.ru` is the only other free
full-planet Overpass instance there is, and it is run by VK, a Russian company.

It is a **last resort, not a mirror in rotation**. A request goes there only
after the community servers have been tried and failed within the same request,
which is the difference between a panel that works and one that shows nothing.
What it receives is the same as what the other Overpass servers receive: the
listing's coordinate as described above, and nothing else — no listing, no
identifier, no account. If you
would rather that never happen, turn the extension off on the listings you do
not want looked up; there is no partial mode.

### Look-ahead on search-results pages

On a results page the extension may look up the surroundings of a listing you
have not opened yet, so the panel is already filled in if you click it. It is
the same request with the same coordinate and nothing else, it is capped at one
area per page, and it yields to real requests — but it does mean a coordinate
can be sent for a listing you only scrolled past. Turning the extension off
stops it.

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
- **declarativeNetRequest** — to set a descriptive `User-Agent` (and `Referer`)
  on requests to the four OpenStreetMap Overpass and QLever hosts, whose usage
  policies ask clients to identify themselves. It is used for nothing else and
  applies only to those hosts.
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
