# Capital One Price Match Automation

A lightweight browser tool for handling Capital One Travel price match calls. The UI lives in a single `index.html` file, with a small Vercel runtime config endpoint in `api/pricematch-config.js`.

## Current Stack

- Gemini is used for live voice preview and the live call session
- OpenAI is used only for email import parsing with `gpt-5.4-nano`
- Call history, notes, and theme preference are stored in `localStorage`
- A minimal password gate is shown before the app loads

## Project Layout

- `index.html`
  The full client UI, styles, and browser-side logic
- `api/pricematch-config.js`
  A tiny Vercel endpoint that returns `OPENAI_API_KEY` and `GEMINI_API_KEY` from environment variables

## Setup

### Local

1. Open `index.html` in Chrome.
2. Update `ACCESS_PASSWORDS` in the script if you want different passwords.
3. If you are opening the file directly from disk, voice preview, email import, and live calls will only work if you also provide a runtime config path for the API keys.

### Vercel

1. Deploy the repo as a Vercel project.
2. Add these environment variables:
   - `OPENAI_API_KEY`
   - `GEMINI_API_KEY`
3. Vercel will expose them to the page through `/api/pricematch-config`.

## Features

- Minimal lock screen before the app becomes visible
- Email import for booking details
- Live call controls for start, end, mute, and pause
- Voice preview with `Charon` selected by default
- Transcript, call log, and summary stats tabs
- Light theme by default, with saved theme preference

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `Enter` | Start or end the call |
| `Space` | Mute/unmute, or resume if paused |

Shortcuts are disabled while focus is inside a text field.

## Notes

- This project currently keeps the Gemini live stack in the browser, so the runtime config endpoint is intended for convenience rather than strict secret isolation.
- If you want stronger secret handling later, the next step would be proxying provider calls through server-side routes instead of returning raw keys to the client.
