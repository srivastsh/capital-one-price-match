# Capital One Price Match Automation

A single-file browser tool that handles Capital One travel price match calls using the OpenAI Realtime API over WebRTC. The AI agent listens to the Capital One rep and responds with your booking details on your behalf.

## Setup

1. Open `index.html` in Chrome
2. Paste your OpenAI API key where it says `YOUR_OPENAI_API_KEY_HERE` at the top of the `<script>` block
3. Fill in your call details and hit **START CALL**

## How it works

- Uses the [OpenAI Realtime API](https://platform.openai.com/docs/guides/realtime) via WebRTC — no server, runs entirely in the browser
- Establishes a live audio session with `gpt-4o-realtime-preview`
- The agent is prompted with your confirmation code, name, retailer, and price found — it answers questions naturally and only responds to what's directly asked
- Live transcript shows both sides of the conversation in real time

## Fields

| Field | Description |
|---|---|
| Confirmation Code | Your Capital One booking confirmation |
| Full Name | Name on the reservation |
| Retailer / Where Found | Where you found the lower price (e.g. Google Flights, Expedia) |
| Price Found | The lower price you want to match |

## Requirements

- Chrome (WebRTC + `getUserMedia`)
- OpenAI API key with Realtime API access
- Microphone permission
