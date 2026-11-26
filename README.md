# Holden Beach Low Tide Dashboard

A single-page dashboard for daylight and twilight low tides near Holden Beach, North Carolina. It displays the daily sunrise and sunset times alongside tide predictions and hourly weather around each qualifying low tide.

## Features

- Shows the next seven days of NOAA CO-OPS high/low tide predictions.
- Displays sunrise and sunset times and includes low tides from 30 minutes before sunrise through 30 minutes after sunset.
- Shows the National Weather Service (NWS) hourly temperature, wind, and precipitation probability for the hour before, during, and after each qualifying low tide.
- Displays data-source retrieval times after all source data loads successfully.
- Reports which provider failed and offers a Retry button.

## Run locally

The dashboard is a standalone HTML file and has no build step or package dependencies. Because it requests data from external APIs, run it from a local web server rather than opening it as a `file://` URL:

1. Open a terminal in this folder.
2. Start a static server, for example with Python:

   ```sh
   python -m http.server 8000
   ```

3. Open <http://localhost:8000/> in a browser.

An internet connection is required to retrieve current data. API availability, browser connectivity, and provider rate limits can affect loading.

## Configuration

The location and tide station are configured near the beginning of the script in [`index.html`](./index.html):

- `STATION_ID` — NOAA CO-OPS station identifier (`8659665`, Bowen Point at Shallotte Inlet).
- `LAT` and `LNG` — coordinates used for sunrise/sunset and the NWS forecast.
- `TWILIGHT_BUFFER_MINUTES` — how many minutes before sunrise and after sunset qualify as daylight/twilight.

If you change the location, verify that the NOAA station is appropriate for it and that all three providers support the requested coordinates.

For ongoing/public use, update the NWS `User-Agent` in `index.html` to include a maintained contact address or site URL. NWS requests require an identifying User-Agent, and contact information helps the service operators reach the maintainer if needed.

## Data sources and attribution

The application requests data directly from these services:

- [NOAA CO-OPS Tides and Currents](https://tidesandcurrents.noaa.gov/) — high/low tide predictions.
- [Sunrise-Sunset.org](https://sunrise-sunset.org/) — sunrise and sunset times. The service requires a visible link to Sunrise-Sunset.org; the dashboard provides one in its data credits.
- [National Weather Service API](https://www.weather.gov/documentation/services-web-api) — hourly forecast. Weather data is reformatted for display and is not an official NWS product; no government endorsement is implied.
- [Sunrise and sunset icons by Icon Hubs on Flaticon](https://www.flaticon.com/free-icons/sunrise) — embedded, resized 16 × 16 PNG images. The dashboard links to Flaticon and credits Icon Hubs in the visible data credits. Resizing or embedding an asset does not remove its license or attribution requirements; verify the applicable asset terms before redistribution.

Provider data and third-party assets are not covered by the project-code license. Check each provider's current terms and attribution requirements before reuse or redistribution. Data timestamps are displayed in Eastern Time.

## License and authorship

Copyright (c) 2026 Stephen G Keilholz. Original project code is licensed under the [PolyForm Noncommercial License 1.0.0](./LICENSE). Commercial use is not permitted under that license.

The project license applies to the original project code only; it does not grant rights to third-party data, icon artwork, trademarks, or other materials. See the relevant provider and asset terms for those materials.
