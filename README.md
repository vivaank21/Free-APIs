# Free APIs, Mapped

An interactive radial map of **29 free-to-use APIs**, grouped into 9 categories and colour-coded by what you need before your first request. Built as a single HTML file with no dependencies and no build step.

<!-- Add a screenshot after your first run:
![Free APIs, Mapped](docs/screenshot.png)
-->

## Features

- **Radial chart:** every API is a glowing dot on a ring, with category arcs around it.
- **Magnify:** click a dot to zoom in 2.6×, or click a category name to zoom into that group. Press `Esc`, click the background, or use **Zoom out** to return.
- **Detail card:** hover or focus a dot to read its description, auth requirement, and usage notes.
- **Auth filters:** dim everything except No key, Free key or token, or Optional token.
- **Light and dark themes:** follows the system setting.
- **Accessible:** keyboard navigable (`Tab`, `Enter`, `Space`, `Esc`), visible focus states, and reduced-motion support.
- **Responsive:** works on desktop and mobile.

## What's in this repo

| File | Purpose |
|---|---|
| `index.html` | The interactive chart (HTML, CSS, and JavaScript in one file) |
| `free_apis.xlsx` | The same data as a spreadsheet, with a filterable list and a summary sheet |
| `README.md` | This file |

> If you saved the chart as `free-apis-chart.html`, rename it to `index.html` so GitHub Pages serves it at the root.

## Quick start

No install needed.

```bash
git clone https://github.com/vivaank21/Free-APIs.git
cd Free-APIs
open index.html        # macOS
# start index.html     # Windows
# xdg-open index.html  # Linux
```

Or serve it locally:

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

## Deploy with GitHub Pages

1. Push the repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. Your chart will be live at `https://vivaank21.github.io/Free-APIs/`.

## The data

| Category | APIs | Count |
|---|---|---|
| Weather | Open-Meteo, OpenWeatherMap, wttr.in | 3 |
| Maps & Geo | Nominatim, Overpass, REST Countries, ipapi / ip-api | 4 |
| Images | Unsplash, Pexels, Pixabay | 3 |
| Finance | CoinGecko, Frankfurter, Alpha Vantage | 3 |
| News & Content | NewsAPI, Hacker News, Wikimedia REST | 3 |
| Dev & Data | GitHub REST, JSONPlaceholder, PokéAPI, httpbin | 4 |
| Entertainment | TMDB, Open Library, Jikan | 3 |
| Utilities | QR Server, Dictionary API, Nager.Date, Random User | 4 |
| AI / ML | Hugging Face Inference, Google Gemini | 2 |

**Authentication breakdown:** 19 need no key, 9 need a free key or token, and 1 has an optional token (GitHub).

## Customise it

All data lives in the `D` array near the top of the `<script>` tag. Each entry is:

```js
["Category", "Full name", "Short label", "Description", "Auth type", "Notes"]
```

Example:

```js
["Weather", "Open-Meteo", "Open-Meteo", "Forecasts, historical weather, air quality", "None", ""]
```

- **Auth type** must be `"None"`, `"Optional token"`, or any other string (treated as a free key or token).
- **Short label** is the text printed beside the dot, so keep it under about 15 characters.
- The layout, hub count, and filter counts update automatically when you add or remove entries.
- Colours, fonts, and light and dark themes are CSS variables at the top of the `<style>` tag.

## Tech

- Vanilla HTML, CSS, and JavaScript
- SVG rendered from data at load time
- Fonts: [Unbounded](https://fonts.google.com/specimen/Unbounded) and [Figtree](https://fonts.google.com/specimen/Figtree) from Google Fonts, with system fallbacks if offline

## Notes on the APIs

Free-tier limits, terms, and endpoints change often. Check each provider's documentation before you build on one. A few things to keep in mind:

- **No-key APIs** (Open-Meteo, Frankfurter, PokéAPI) are the quickest way to prototype.
- **Keyed APIs** should not have their keys exposed in frontend code in production. Route them through a small backend.
- **Nominatim** has a strict usage policy: send a valid User-Agent and avoid bulk requests.
- For a much larger catalogue, see the community-maintained [public-apis](https://github.com/public-apis/public-apis) repository.

## Contributing

Suggestions are welcome. To add an API, open a pull request that adds one entry to the `D` array, and add a matching row to `free_apis.xlsx`. Please confirm the API has a genuine free tier and link its docs in the PR description.

## License

Released under the [MIT License](LICENSE). Add a `LICENSE` file to the repository root, or swap in the licence you prefer.
