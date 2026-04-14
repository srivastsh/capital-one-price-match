# Capital One Price Match Automation

A single-file browser tool that handles Capital One travel price match calls using the OpenAI Realtime API over WebRTC. The AI agent listens to the Capital One rep and responds with your booking details on your behalf.

## Setup

1. Open `index.html` in Chrome
2. Paste your OpenAI API key where it says `YOUR_OPENAI_API_KEY_HERE` at the top of the `<script>` block
3. Fill in your call details and hit **START CALL**

## How it works

- Uses the [OpenAI Realtime API](https://platform.openai.com/docs/guides/realtime) via WebRTC — no server, runs entirely in the browser
- Model: `gpt-4o-realtime-preview` with server-side VAD turn detection
- Input transcription via `whisper-1` (powers the AGENT side of the live transcript)
- The agent is prompted with your confirmation code, name, retailer, and price found — it answers questions naturally and only responds to what's directly asked
- Live transcript shows both sides of the conversation in real time

## Fields

| Field | Description |
|---|---|
| Confirmation Code | Your Capital One booking confirmation |
| Full Name | Name on the reservation |
| Retailer / Where Found | Where you found the lower price (e.g. Google Flights, Expedia) |
| Price Found | The lower price you want to match |
| Voice | Choose from 8 voices — preview any before the call |
| Additional Context | Optional extra info for the agent (card digits, passenger count, etc.) |

## Controls

| Control | Description |
|---|---|
| START CALL / END CALL | Begin or end the session |
| 🎤 MUTE / UNMUTE | Silence your mic without ending the call |
| ⏸ PAUSE / RESUME | Silence mic and clear the audio buffer — use while on hold |
| Session Notes | Appears after the call ends — jot outcome, reference number, etc. Auto-saves to the log |

## Keyboard shortcuts

| Key | Action |
|---|---|
| `Enter` | Start or end the call |
| `Space` | Mute/unmute (or resume if paused) |

Shortcuts are disabled when focus is inside a text field.

## Call log

Every completed call is saved to the **LOG** tab (persisted in `localStorage`). Each entry shows the date, time, duration, call details, and any session notes you added. Entries can be deleted individually.

## Quick links

- **Capital One Travel** — opens your trips dashboard
- **Price Match Call Center** — `tel:` link to 844-422-6922

## Requirements

- Chrome (WebRTC + `getUserMedia`)
- OpenAI API key with Realtime API access
- Microphone permission
