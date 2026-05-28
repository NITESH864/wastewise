# ♻️ WasteWise — AI-Powered Smart Waste Classifier

> Know exactly where your waste belongs. Powered by Claude AI.

![WasteWise](https://img.shields.io/badge/AI-Claude%20Sonnet-green?style=flat-square) ![HTML](https://img.shields.io/badge/Stack-HTML%20%2F%20CSS%20%2F%20JS-blue?style=flat-square) ![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square) ![Status](https://img.shields.io/badge/Status-Live-brightgreen?style=flat-square)

**Live demo:** [NITESH864.github.io/wastewise](https://NITESH864.github.io/wastewise)

---

## 🌍 What is WasteWise?

WasteWise is a fully client-side web app that uses Claude AI to classify any waste item from a photo. It tells you:

- Which **bin** to use (recycle, compost, landfill, e-waste, hazardous)
- Local **disposal rules** for 340+ Indian cities
- **Environmental impact** — CO₂ and water saved
- A **conversational Q&A** so you can ask follow-up questions

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 📷 Image upload & drag-drop | Upload any photo or drag it onto the page |
| 🤖 Real AI classification | Claude Vision model classifies in ~2 seconds |
| 💬 Ask a question | Chat with AI about the classified item |
| 📍 Location-aware rules | 12 Indian cities with local disposal rules |
| 📊 Impact dashboard | Track CO₂ saved, streak, category breakdown |
| 🕒 Scan history | Searchable, filterable, exportable as CSV |
| 📤 Share results | Web Share API with clipboard fallback |
| 📱 Mobile responsive | Works on all screen sizes with hamburger nav |

---

## 🚀 Getting Started

### Option 1 — GitHub Pages (recommended, zero setup)

1. Fork this repository
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Your site will be live at `https://your-username.github.io/wastewise`

> ⚠️ The Anthropic API is called directly from the browser. See [API Key Setup](#-api-key-setup) below.

### Option 2 — Run locally

```bash
git clone https://github.com/your-username/wastewise.git
cd wastewise
# Just open index.html in your browser — no build step needed
open index.html
```

---

## 🔑 API Key Setup

WasteWise calls the Anthropic API from the browser. To use your own key:

1. Get a free API key at [console.anthropic.com](https://console.anthropic.com)
2. Open `index.html` and search for `api.anthropic.com`
3. The fetch headers currently rely on the claude.ai proxy — if running standalone, add your key:

```js
headers: {
  'Content-Type': 'application/json',
  'x-api-key': 'YOUR_KEY_HERE',          // add this line
  'anthropic-version': '2023-06-01',      // add this line
  'anthropic-dangerous-direct-browser-access': 'true'  // required for browser calls
}
```

> 💡 For production, move the API call to a backend to keep your key secure.

---

## 🗂️ Project Structure

```
wastewise/
├── index.html        # Entire app — HTML + CSS + JS in one file
├── README.md         # This file
├── LICENSE           # MIT License
└── .gitignore        # Standard ignores
```

The app is intentionally a **single HTML file** — easy to deploy anywhere, no build tools, no dependencies except Chart.js (loaded from CDN) and Google Fonts.

---

## 🧠 How the AI Works

```
User uploads photo
       ↓
Base64 encode image
       ↓
POST to Anthropic /v1/messages
  - Model: claude-sonnet-4-20250514
  - Vision: image + text prompt
  - System: waste classification JSON schema
       ↓
Parse JSON response
  { name, type, bin, desc, explain, icon, co2, water, conf }
       ↓
Render result card
```

For the Q&A feature, the classified item context is passed as a system prompt so Claude can answer follow-up questions accurately.

---

## 📱 Pages

| Page | Route | Description |
|------|-------|-------------|
| Home | `#landing` | Hero, how-it-works, categories, testimonials |
| Scan | `#scan` | Upload zone, example chips, AI result panel |
| Dashboard | `#dashboard` | Metrics, Chart.js bar + donut, streak, tips, badges |
| History | `#history` | Searchable, filterable list with CSV export |

---

## 🛠️ Tech Stack

- **Frontend:** Vanilla HTML5, CSS3, JavaScript (ES2020+)
- **AI:** Anthropic Claude Sonnet (vision + text)
- **Charts:** Chart.js 4.4.1
- **Fonts:** Google Fonts (Instrument Serif + DM Sans)
- **Hosting:** GitHub Pages

---

## 🤝 Contributing

Pull requests are welcome! Here are some ideas for contributions:

- [ ] Add more Indian cities to the location database
- [ ] Add more example waste item chips
- [ ] Dark mode toggle
- [ ] Offline PWA support with Service Worker
- [ ] Backend proxy to secure API key
- [ ] Multi-language support (Hindi, Tamil, Telugu…)

---

## 📄 License

MIT License — free to use, modify, and distribute. See [LICENSE](LICENSE).

---

## 🙏 Credits

Built with [Claude AI](https://anthropic.com) by Anthropic · Charts by [Chart.js](https://chartjs.org) · Fonts by [Google Fonts](https://fonts.google.com)

---

<p align="center">Built for a cleaner planet 🌍</p>
