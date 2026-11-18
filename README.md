# J.A.R.V.I.S. — PROJECT NOVA (v1.1)

A fresh mobile-first PWA interface featuring the custom blue Arc Reactor artwork, voice input, spoken replies, Hindi/English selection, and an optional Cloudflare Worker AI gateway.

## Included
- `index.html`, `style.css`, `app.js`: complete client app.
- `assets/jarvis-arc-reactor.png`: generated Arc Reactor artwork used in the interface.
- `icon.svg`, `assets/icon-192.png`, `assets/icon-512.png`: app icons.
- `manifest.webmanifest`, `sw.js`: installable/offline PWA foundation.
- `worker/`: Cloudflare Worker proxy for Groq API.

## Run locally
Serve this folder over HTTP (not `file://`). For example, use the VS Code Live Server extension or `python -m http.server 8000`, then open `http://localhost:8000`.

## Deploy the AI gateway
1. Create a Cloudflare Worker using the files in `worker/`.
2. Add a Worker secret named `GROQ_API_KEY` with your Groq API key.
3. Deploy the Worker and copy its HTTPS URL.
4. Open the app and paste that URL into **Neural Link**.
5. Keep API keys only in Worker secrets, never in browser JavaScript or GitHub.

Groq free-tier limits and model availability can change. API use may be subject to provider quotas and terms.

## Deploy the web app
Upload the contents of this folder to a GitHub repository and connect that repository to Cloudflare Pages (or another static host). The app must be served over HTTPS for microphone and PWA features.

## Voice and wake-word limits
The reactor button starts a one-shot browser speech-recognition session. The wake-word toggle is only a UI placeholder in this web build; it does **not** continuously detect “Hey JARVIS”. Browsers and Android restrict background microphone use. Real screen-off wake-word support requires a native Android app with an appropriately permissioned foreground microphone service and local wake-word engine; Android may still restrict operation for privacy and battery reasons.

## Security before public launch
The Worker currently uses permissive CORS (`*`) for easy initial setup. Restrict it to your deployed app origin, add rate limiting/authentication, and monitor provider usage before sharing publicly.

## Notes
This is an original JARVIS-inspired project, not an official Stark Industries product and not the Iron Man movie character. It does not include copyrighted film voice recordings.
