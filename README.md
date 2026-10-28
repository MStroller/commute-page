# commute-page

A single-file phone page that answers "which bus gets me there fastest right now" in Taipei.

- Live arrival estimates come from the Taipei City open bus data feed
  (`tcgbusfs.blob.core.windows.net/blobbus/GetEstimateTime.gz`, no key, fetched in the browser).
- The candidate itineraries and the ride-time statistics are **not in this repository**. They are passed in the
  URL fragment (`#d=...`, deflate-raw JSON, base64url). Browsers do not send the fragment to the server, so the
  host only ever serves this code.
- If the live feed cannot be reached, the page ranks by the statistics in the fragment.

Works in iOS Safari 16.4+ (needs `DecompressionStream("deflate-raw")`); add it to the home screen from Safari.
