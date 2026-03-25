# 🔐 DATA//VAULT · Hushh × Kai

> **Hushh × Kai Hackathon 2026 · Challenge 05 — Personal Data Value Explorer**

A glassmorphism-styled, single-page web application that empowers Indian users to visualize the monetary value of their personal data, manage consent across data categories, and leverage Claude AI for intelligent risk profiling, exploitation scoring, and 12-month value forecasting.

---

## ✨ Features

### 🏠 Home
- Hero dashboard displaying total monthly data value (₹/month)
- Live stats: data categories, active corporate buyers, monthly value
- Animated ambient background with particle canvas and glow orbs

### 💎 My Data (Data Explorer)
- 8 personal data category cards with real-time consent toggles
- Per-category sensitivity ratings: `Low` / `Medium` / `High` / `Very High`
- Live monetary value tracker — updates instantly on consent toggle
- Consent coverage progress bar and percentage readout
- Kai-powered contextual insight panel

### 🏢 Who Buys? (Buyer Intelligence)
- Reveals which real Indian corporations buy each data category
- Filter view: All / Consented / Locked
- Locked categories blur buyer data behind a consent gate
- Buyer type badges (Insurance, Banking, FMCG, Big Tech, etc.)

### 📋 Consent Audit Log
- Immutable session-level log of every consent grant / revoke action
- Columns: Timestamp · Category · Action · Value · TX Hash (simulated SHA-256)
- Live counters: total events, granted, revoked, current value
- Clear log with confirmation guard

### ✦ Kai AI · Intelligence Hub
Four AI-powered panels (all powered by **Anthropic Claude**):

| Panel | Description |
|---|---|
| 🧠 Data Shadow Profile | Claude reconstructs how ad algorithms perceive you based on your consent footprint |
| ⚠️ Exploitation Risk Score | Animated SVG gauge (0–100) with per-category risk bar breakdown |
| 🔮 12-Month Value Forecast | Canvas chart projecting your data value vs. market rate over 12 months |
| 🔴 Live Exploitation Feed | Simulated real-time stream of corporate data access events |

---

## 📂 Project Structure

```
datavault/
│
├── index_glass.html        # Single-file application (HTML + CSS + JS)
├── README.md               # Project documentation
└── requirements.txt        # External dependency reference
```

This is a **zero-build, zero-dependency** frontend project. Everything — styles, logic, and AI integration — lives in a single HTML file.

---

## 🚀 Getting Started

### 1. Clone or Download
```bash
git clone https://github.com/your-username/datavault.git
cd datavault
```

### 2. Add Your Anthropic API Key

Open `index_glass.html` and locate the `callClaude()` function (~line 1384). Replace the headers with:

```js
headers: {
  'Content-Type': 'application/json',
  'x-api-key': 'YOUR_ANTHROPIC_API_KEY_HERE',
  'anthropic-version': '2023-06-01',
  'anthropic-dangerous-direct-browser-calls': 'true'
}
```

Get your API key at: **https://console.anthropic.com/settings/keys**

> ⚠️ **Security Warning:** Never commit a real API key to a public repository. For production, proxy all Claude API calls through a backend server.

### 3. Open in Browser

```bash
# Option A — direct open (works for most features)
open index_glass.html

# Option B — local server (recommended to avoid CORS issues)
npx serve .
# or
python3 -m http.server 8080
```

Then navigate to `http://localhost:8080`.

---

## 🧠 AI Features — How They Work

All three Claude-powered features call `https://api.anthropic.com/v1/messages` directly from the browser using the model **`claude-sonnet-4-20250514`**.

### Data Shadow Profile
Sends your consented data categories and their values to Claude. Claude responds with a clinical, ad-algorithm-style description of how you'd be profiled — in plain text, max 4 sentences.

### Exploitation Risk Score
Sends consented + locked category context. Claude returns a structured JSON object:
```json
{
  "score": 72,
  "level": "HIGH",
  "summary": "Finance and health data significantly elevate exploitation risk.",
  "categories": [
    { "name": "Health", "risk": 88, "color": "#EF4444" }
  ]
}
```
Rendered as an animated SVG gauge + bar chart.

### 12-Month Value Forecast
Claude projects 12 monthly data values (in INR) vs. market rate, plus a growth percentage and commentary. Rendered as a Canvas line chart with opportunity zone shading.

---

## 📊 Data Categories

| ID | Category | Sensitivity | Value/mo |
|---|---|---|---|
| `email` | Email & Communications | High | ₹420 |
| `location` | Location & Movement | High | ₹680 |
| `shopping` | Shopping & Purchases | Medium | ₹550 |
| `health` | Health & Fitness | Very High | ₹890 |
| `finance` | Financial Behavior | Very High | ₹760 |
| `social` | Social & Interests | Low | ₹310 |
| `device` | Device & App Usage | Medium | ₹380 |
| `identity` | Identity & Profile | Medium | ₹290 |

**Total maximum value: ₹4,280/month**

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 (custom properties, glassmorphism, backdrop-filter) |
| Fonts | Plus Jakarta Sans · JetBrains Mono (Google Fonts) |
| Animation | CSS keyframes · Canvas 2D API |
| Logic | Vanilla JavaScript (ES2022+) |
| AI | Anthropic Claude API (`claude-sonnet-4-20250514`) |
| Charts | HTML5 Canvas (custom, no library) |
| Build | None — zero build step required |

---

## 🔒 Privacy Notes

- **No data is stored server-side.** All consent state and audit logs exist only in the browser session's memory (JavaScript variables).
- **No cookies, no localStorage** are used.
- The Kai AI features send only your consent selections (category names and values) to the Claude API — no personally identifiable information (PII) is transmitted.
- The Live Exploitation Feed is entirely **simulated** — no real corporate data access occurs.

---

## 🌐 Browser Support

| Browser | Support |
|---|---|
| Chrome / Edge 88+ | ✅ Full |
| Firefox 89+ | ✅ Full |
| Safari 15.4+ | ✅ Full (`backdrop-filter` required) |
| Mobile Chrome / Safari | ✅ Responsive |

---

## 📜 License

MIT License — built for the **Hushh × Kai Hackathon 2026**.

---

## 🙏 Acknowledgements

- **Anthropic** — Claude AI API
- **Hushh × Kai** — Challenge 05: Personal Data Value Explorer
- **Google Fonts** — Plus Jakarta Sans, JetBrains Mono
