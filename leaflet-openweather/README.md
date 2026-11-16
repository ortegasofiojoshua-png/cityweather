# Lesson 3: Leaflet.js + OpenWeather API

## Goal
Click a city marker, fetch *current weather* for its latitude/longitude, and display temperature, description, humidity, wind speed, and a weather icon.

## Run it
1. Sign up at https://openweathermap.org/ and obtain an API key. Confirm the **Current Weather Data** API is accessible for your account. A new key may take up to two hours to activate.
2. Open this folder with VS Code and run `index.html` using the Live Server extension or a local development server such as `python -m http.server 8000`.
3. Paste your OpenWeather API key into the input field. Click a city marker.
4. Look at the popup, information panel, and DevTools > Network tab.

No real API key is included. Internet access is required. To protect credentials, do **not** publish a real key in a public Git repository. This basic educational browser-only approach exposes a key to browser tools and network traffic; production applications should call OpenWeather from a backend, with credentials in server-side secrets and request limiting.

## Important code concepts
- `L.marker([lat, lon])` — represents a location.
- `marker.on('click', ...)` — registers an event handler.
- `fetch(url)` — sends a request to OpenWeather.
- `await response.json()` — parses a JSON response.
- `response.ok` — tests request success.
- `data.main.temp`, `data.main.humidity`, `data.weather[0].description` — read weather response properties.
- `cache` — avoids repeating identical requests within 10 minutes (per location/key).
- `.textContent` / `replaceChildren` — avoid injecting untrusted API text as HTML.

## API request
`GET https://api.openweathermap.org/data/2.5/weather?lat=14.5995&lon=120.9842&units=metric&appid=YOUR_API_KEY`

## Assessment (100 points)
- Leaflet map + 5 markers: 20
- Click-to-fetch current weather: 30
- Correct response parsing and displayed weather: 25
- Loading/error handling: 15
- Clean code / explanation: 10

## Challenges
1. Add three more Philippine cities with correct coordinates.
2. Display `main.feels_like` in the popup.
3. Add a refresh button that bypasses the cache.
4. Advanced: migrate the API call into a backend proxy so your secret is never sent to a browser.

## References
https://openweathermap.org/api/current
https://openweathermap.org/faq
https://leafletjs.com/reference.html
https://operations.osmfoundation.org/policies/tiles/
