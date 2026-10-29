# commute-page

A single-file phone page that answers "which bus gets me there fastest right now" in Taipei.

- Live arrival estimates come from the Taipei City open bus data feed
  (`tcgbusfs.blob.core.windows.net/blobbus/GetEstimateTime.gz`, no key, fetched in the browser).
- The candidate itineraries and the ride-time statistics are **not in this repository**. They are passed in the
  URL fragment (`#d=...`, deflate-raw JSON, base64url). Browsers do not send the fragment to the server, so the
  host only ever serves this code.
- If the live feed cannot be reached, the page ranks by the statistics in the fragment.
- First screen: when to leave (countdown) and when you arrive; route badges; a vertical timeline per option.
  Within 150 m of a boarding stop (only when location permission was already granted) it switches to a
  stop board; "missed this one" re-ranks without the bus that just left.
- Official ETAs are corrected with measured early/late bias passed in the fragment; "leave by" uses the 10th
  percentile so you catch the bus about nine times in ten.
- Metro hop times, transfer walks, fares and exits are built offline from data.taipei open data (no key).
- No web fonts, no analytics. Usage counts (opens, followed recommendations, estimated minutes saved) stay in
  the browser's localStorage; the "copy report" button copies counts only, never places or times.

Works in iOS Safari 16.4+ (needs `DecompressionStream("deflate-raw")`); add it to the home screen from Safari.
