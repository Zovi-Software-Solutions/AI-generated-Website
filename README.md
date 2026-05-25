# Zovi Software Solutions — Website built with AI, zero code

> **A professional B2B website built entirely without writing a single line of code — using Claude (Anthropic) and Framer.**

🌐 **Live site:** [zovisoftwaresolutions.com](https://zovisoftwaresolutions.com)

---

## 🧠 The story

I'm Geert Roeterink, co-founder of Zovi Software Solutions. We help businesses source software licenses from the right vendors across Europe. My background is in sales and business development — not software development.

When it came time to build our website, I had two options:
1. Hire a developer for €5.000–€15.000 and wait weeks
2. Try to build it myself with AI

I chose option 2. What followed was a series of daily sessions with **Claude (Anthropic)** and **Framer**, where Claude guided me step by step — writing code I didn't understand, explaining decisions in plain language, and adapting to my feedback in real time.

The result: a fully functional, professional B2B website with CMS, contact forms, SEO configuration, DNS setup, animated components, and 5 complete pages — built in under 5 weeks.

---

## ✨ What got built

| Feature | How |
|---|---|
| 5 full pages (Home, Werkwijze, Leveranciers, Nieuws, Contact) | Claude wrote Workshop prompts → Framer generated React components |
| Animated hero with SVG shield assembly | Claude wrote canvas + SVG animation code |
| CMS for blog articles (4 live, filterable by category) | Framer CMS + Claude-designed card templates |
| Contact form → email | Formspree integration |
| Cookie, Privacy & Terms pages | Claude wrote full Dutch legal text |
| Live on custom domain | DNS configured in TransIP via Claude's instructions |
| Google Search Console | Verified + sitemap submitted |
| Mobile responsive | CSS media queries written by Claude via Workshop |

---

## 🛠️ Tech stack

```
Framer Pro        — visual website builder with React code component support
Claude (Sonnet)   — Anthropic's AI, used for every technical decision
Formspree         — contact form backend (no server needed)
TransIP           — domain registrar and DNS management
Google Search Console — SEO indexing and sitemap submission
```

No framework setup. No terminal. No package.json. No Git commits during development.

---

## 🤝 How Claude and Framer work together

Framer has a feature called **Workshop** — an AI code editor built into the designer. You type a prompt, it generates a React component, and you drag it onto your canvas.

The magic: **Claude wrote the Workshop prompts.**

Instead of me guessing what to ask Framer's AI, Claude understood my design intent, translated it into precise technical instructions, and handed me a prompt ready to paste. Claude also reviewed screenshots of the result, spotted problems, and wrote corrected prompts.

```
Me (Geert)         Claude (Anthropic)        Framer Workshop
    |                     |                        |
    |-- "I want a hero -->|                        |
    |   with animation"   |                        |
    |                     |-- Writes prompt ------>|
    |                     |                        |-- Generates React
    |                     |                        |   component
    |<-- Screenshot ------+------------------------+
    |                     |
    |                     |-- Reviews + fixes ----->|
    |                     |                        |-- Updated component
```

Claude acted as my **technical co-founder** — the one who spoke code, while I spoke business.

---

## 📁 Repository structure

```
/
├── README.md          ← you are here
├── prompts.md         ← the actual AI prompts used
├── workflow.md        ← step-by-step process: idea → live website
└── index.html         ← static HTML reference version
```

---

## 🚀 Key results

- **~5 weeks** from idea to live website
- **€0** in developer costs
- **5 pages** fully designed and functional
- **4 articles** live in CMS
- **100% built** through natural language conversation with Claude

---

## 💡 What others can learn

You do not need to learn React, CSS, or JavaScript to build a professional website in 2025. What you need:

1. A clear idea of what you want to build
2. The ability to describe it in plain language
3. Patience to test, screenshot, and iterate
4. A good AI partner (Claude) + a visual builder (Framer)

The most important skill turned out to be **giving good feedback** — not writing code.

---

## 📬 Contact

**Geert Roeterink** — Co-founder, Zovi Software Solutions
📧 [info@zovisoftwaresolutions.com](mailto:info@zovisoftwaresolutions.com)
🌐 [zovisoftwaresolutions.com](https://zovisoftwaresolutions.com)
💼 [LinkedIn](https://linkedin.com/in/geertroeterink)

---

## 🙏 Credits

- **Claude (Anthropic)** — [claude.ai](https://claude.ai) — the AI that wrote every line of code
- **Framer** — [framer.com](https://framer.com) — the visual builder that made it deployable
- **Formspree** — [formspree.io](https://formspree.io) — contact form handling
- **TransIP** — [transip.nl](https://transip.nl) — domain and DNS

---

*This repository exists to show that the barrier to building on the web has fundamentally changed. If I can build this, you can too.*
