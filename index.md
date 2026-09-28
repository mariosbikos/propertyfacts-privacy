# PropertyFacts — Privacy Policy

Last updated: 28 September 2026

PropertyFacts is a browser extension that adds public property data to listings
on spitogatos.gr, xe.gr and rightmove.co.uk. It is not affiliated with, authorised by, or endorsed by
Spitogatos, xe.gr or Rightmove.

## The short version

**PropertyFacts has no server, no account, and no analytics.** The developer does not receive user data. Extension data stays in your browser profile and is deleted when you remove the extension.

## What the extension stores, and where

All extension data lives in `chrome.storage.local` on your device. The extension does not transmit stored settings or cached results to the developer.

| What | Why | Retention |
|---|---|---|
| Your settings (on/off, language, light/dark) | To remember your choices | Until you change or uninstall |
| Cached public data about map areas (amenities, transport, administrative areas, air quality, seismic history, land registry, forest map) | Avoid repeat requests for the same area | 30-180 days by source; oldest entries are dropped when cache storage exceeds 6 MB |
| Optional zone value entered by you | Remember the value for that neighbourhood when calculating the ENFIA estimate | Until you change it or uninstall |
| Compare list (up to 5 listings you added: title, link, photo, and the listing and area details shown in the panel) | Show them side by side on the compare page | Until you remove them or uninstall |
| Price history (listing ID, asking price each time it changed, first and last time you viewed it) | Show whether a listing you viewed before has changed price | Up to 500 listings, least recently viewed dropped first; until uninstall |
| Which site and language you last used | Word the compare page to match | Until overwritten or uninstall |

Price history is built only from listings you open yourself; nothing is fetched to create it and it is never sent anywhere.

**You can clear cached public-data results at any time** from the extension toolbar popup ("Clear cached data"). Settings and optional zone values remain until you change them or remove the extension; removing the extension deletes all extension data.

## What is sent over the network, and to whom

To describe a listing's surroundings, the extension asks public data services
about **a location** — a latitude and longitude. It never sends the listing
URL, the listing ID, a price, an identifier, or anything about you.

| Service | Operator | What is sent |
|---|---|---|
| QLever OSM (`qlever.dev`) | University of Freiburg | The listing's coordinate |
| UK only: police.uk (`data.police.uk`) | Home Office | The listing's coordinate |
| UK only: postcodes.io (`api.postcodes.io`) | Ideal Postcodes | The listing's coordinate |
| UK only: Environment Agency flood map (`services-eu1.arcgis.com`) | Environment Agency | The listing's coordinate |
| UK only: Historic England (`services-eu1.arcgis.com`) | Historic England | The listing's coordinate |
| UK only: ONS neighbourhood centres (`services1.arcgis.com`) and Nomis (`www.nomisweb.co.uk`) | Office for National Statistics | The listing's coordinate (ONS); neighbourhood codes, not the coordinate (Nomis) |
| UK only: EPC register (`find-energy-certificate.service.gov.uk`) | Department for Energy Security and Net Zero | The listing's postcode and street name, not the coordinate |
| UK only: UK House Price Index (`landregistry.data.gov.uk`) | HM Land Registry | The listing's local authority name, not the coordinate |
| UK only: Esri World Imagery (`server.arcgisonline.com`) | Esri | The listing's coordinate, only when you open the aerial photo |
| Overpass API (`overpass-api.de`, `overpass.private.coffee`, `overpass.openstreetmap.fr`) | OpenStreetMap community (OpenStreetMap France runs the last) | The listing's coordinate |
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

### Listing pages only

The extension looks anything up only on a listing page you have actually
opened (a spitogatos.gr or xe.gr property page, or a Rightmove
`/properties/` page), never on a search-results page. An earlier version
looked ahead on results pages to fill the panel before you clicked through;
that has been removed, so no coordinate is sent for a listing you only
scrolled past.

Listed buildings, traditional settlements, Greek regional statistics, UK council
tax rates, UK average rents and the UK crime scale are **bundled inside the
extension**, so looking them up sends no request at all.

## What the extension does not do

- No accounts, logins, or profiles
- No analytics, telemetry, crash reporting, or advertising
- No selling, sharing, or transfer of user data to anyone — there is nobody to
  transfer it to
- No tracking across sites; it runs only on spitogatos.gr, xe.gr and rightmove.co.uk pages
- No reading or altering of those pages beyond reading the listing details and adding its own panel
- No remotely hosted code

## Permissions, and why each is needed

- **storage** — to keep your settings and the local cache described above
- **declarativeNetRequest** — to set a descriptive `User-Agent` (and `Referer`)
  on requests to the OpenStreetMap Overpass and QLever hosts, whose usage
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
