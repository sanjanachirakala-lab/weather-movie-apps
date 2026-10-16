# Weather App + Movie Search App

Minor Project 03, Web Development (Unlox Academy)
**Author:** Chirakala Sanjana

Two interactive web apps that fetch live data from public REST APIs using modern JavaScript.

## Apps

### Weather App (`weather.html`)
- Search weather by city name
- Shows current temperature, "feels like", conditions, humidity and wind speed
- 5-day forecast
- Handles errors: empty input, city not found, network or server errors
- Remembers the last searched city (localStorage)
- API: [Open-Meteo](https://open-meteo.com/) (geocoding and forecast). **No API key needed.**

### Movie Search App (`movies.html`)
- Search movies by title using the OMDb API
- Shows posters, year, rating and release date, with full details (genre, cast, plot) in a popup
- Handles invalid searches ("Movie not found", too-short queries), missing posters and network errors
- API: [OMDb API](https://www.omdbapi.com/) (**free API key required**, see setup below)

## Setup

1. Get a free OMDb key at https://www.omdbapi.com/apikey.aspx (it is sent to your email).
2. Open `js/config.js` and replace `YOUR_OMDB_API_KEY` with your key.
3. Serve the folder with a local web server. ES modules do not load when `index.html` is opened by double-clicking.
   - **VS Code:** install the *Live Server* extension, right-click `index.html`, then *Open with Live Server*.
   - **GitHub Pages:** in the repo go to *Settings → Pages* and choose the `main` branch. The site is then available online.

## Concepts Demonstrated

| Focus area | Where |
|---|---|
| Arrow functions | all JS files |
| Template literals | rendering cards in `weather.js` and `movies.js` |
| Destructuring | API responses, e.g. `const { Search } = await ...` |
| ES6 modules | `utils.js` and `config.js` imported with `import`/`export` |
| Promises, `async/await`, Fetch API | `fetchJSON` in `utils.js`, API calls in both apps |
| Error handling | `try/catch`, `response.ok` check, API error messages |
| DOM manipulation | dynamic rendering, event handling, form processing, event delegation, `<dialog>` |
| Responsive UI | CSS Grid, Flexbox and media queries in `css/style.css` |

## Project Structure

```
weather-movie-apps/
├── index.html      # home page linking to both apps
├── weather.html
├── movies.html
├── css/style.css
├── js/
│   ├── utils.js    # shared fetch / status / escape helpers
│   ├── weather.js
│   ├── movies.js
│   └── config.js   # OMDb API key goes here
└── README.md
```

## Notes
- API data is escaped before it is inserted into the page, so it is never treated as HTML.
- The OMDb free key is rate-limited (about 1,000 requests per day).
