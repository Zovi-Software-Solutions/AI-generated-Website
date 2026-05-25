# Workflow — From idea to live B2B website without code

> How I (a non-technical founder) built [zovisoftwaresolutions.com](https://zovisoftwaresolutions.com) in ~5 weeks using Claude and Framer.

---

## Who this is for

- Founders or entrepreneurs who want a website but can't afford a developer
- People who tried Webflow or WordPress and got stuck
- Anyone curious about how far AI can take you in web development without code

**My background:** Sales & business development. I know how to sell software. I do not know how to write it.

---

## The tools

| Tool | Purpose | Cost |
|---|---|---|
| Claude (Anthropic) | Every technical decision, every line of code | ~€20/mo |
| Framer Pro | Visual website builder with AI code editor | ~€30/mo |
| Formspree | Contact form → email, no server needed | Free |
| TransIP | Domain registration and DNS | ~€10/yr |
| Google Search Console | SEO, sitemap, indexing | Free |

**Total monthly cost: ~€50.** A developer would have charged €5.000–€15.000 for equivalent work.

---

## Phase 1 — Design decisions (week 1)

Before touching any tool, I had 2–3 sessions with Claude to nail the fundamentals.

**What we decided:**
- Platform: Framer (not Webflow, not WordPress) — because Framer's Workshop AI makes code components possible without coding
- Brand: Navy (#1E3A5F) + gold (#D4AF37) — professional, trustworthy, tech-forward
- Fonts: Fraunces (headings) + Inter (body) — both free on Google Fonts
- Pages: Home · Werkwijze · Leveranciers · Nieuws · Contact · Legal
- Language: Dutch first, English in phase 2

**What Claude produced:** a full design brief, color tokens, typography scale, and component list — all documented in a file I could reference every session.

**Lesson:** Deciding *what* to build before *how* to build it saved weeks of rework.

---

## Phase 2 — Building page by page (weeks 2–4)

### The workflow per component

Every section of the site was built with this exact loop:

```
1. Describe what I want to Claude in plain language
2. Claude writes a Workshop prompt
3. I paste the prompt into Framer Workshop → component is generated
4. I take a screenshot and send it to Claude
5. Claude reviews and writes a corrected prompt if needed
6. Repeat until it looks right
7. Move to the next component
```

This loop took 2–5 iterations per component. Claude reviewed screenshots like a senior developer reviewing a junior's work.

### Build order (homepage)

1. StickyHeader (navigation + logo + CTA button)
2. ZoviHeroSection (hero with shield, headline, buttons)
3. ZoviPijlers (4 value proposition cards)
4. ZoviWerkwijze (4-step process section)
5. ZoviSuppliersSection (5 tabs with vendor categories)
6. ZoviContact (form + direct contact info)
7. ZoviFooterComplete (FAQ accordion + footer columns + legal links)

Then the same for each subpage.

### How Framer Workshop works

Framer has a built-in AI code editor called Workshop. You open a component, type a prompt, and it generates React code. The component appears on your canvas instantly.

The trick: Workshop is good at executing instructions, but bad at understanding vague intent. Claude bridges that gap. Claude writes precise, technical Workshop prompts; Workshop executes them exactly.

```
What I say (plain language) → Claude → Technical Workshop prompt → Framer generates component
```

### Common problems and how Claude solved them

**Problem:** Component was the right shape but wrong width (too narrow on wide screens)
**Fix:** Claude wrote: "set outermost container to width: 100%" in the Workshop prompt

**Problem:** Scrolling stopped working on a page
**Fix:** Claude diagnosed: page frame had wrong layout settings. Step-by-step fix: Layout → Stack → Direction vertical → Distribute: Start → Gap: 0 → Padding: 0

**Problem:** Navigation links didn't work after publishing
**Fix:** Claude wrote Workshop prompt to use `window.location.href` for all nav links (more reliable than Framer's built-in navigation for code components)

**Problem:** Contact form emails went to spam
**Fix:** Add Formspree as contact in Outlook, right-click → mark as not spam. Future emails go to inbox.

---

## Phase 3 — CMS for blog (week 3)

Framer has a built-in CMS. Claude guided me to:

1. Create a "Articles" collection with fields: Title, Slug, Date, Image, Category, Intro, Content
2. Build an article template page (used by all articles)
3. Connect the article list on /nieuws to the CMS collection
4. Create 4 category pages (/nieuws/marktinzicht, /security, /ai, /defence)
5. Add filter tabs linking to each category page
6. Write 4 real articles (Claude helped draft them in the right tone)

**Key insight:** Framer CMS doesn't support dynamic filters via code components. The solution was static category pages — one page per category with a static filter. This is actually better for SEO anyway.

---

## Phase 4 — Going live (week 4)

### DNS setup in TransIP

Claude read screenshots of my TransIP DNS panel and told me exactly what to add, change, and delete:

- Added: `@ A 31.43.160.6` and `@ A 31.43.161.6` (Framer's IP addresses)
- Added: `www CNAME sites.framer.app`
- Kept: MX records (email), SPF, DMARC (these handle my Outlook email — don't delete)
- Deleted: old hosting A records that conflicted

DNS propagated within 2 hours. Site was live on zovisoftwaresolutions.com.

### Google Search Console

1. Go to search.google.com/search-console
2. Add domain property (not URL prefix)
3. Verify via TXT record — Claude told me exactly what to add in TransIP
4. Submit sitemap: `https://zovisoftwaresolutions.com/sitemap.xml` (Framer generates this automatically)

---

## Phase 5 — Polish and animation (week 5)

Once the site was live and functional, we worked on making it exceptional rather than just good.

The hero animation: a shield that assembles itself on page load (outline draws, icons appear one by one, particles float inside, then it shrinks to position and the headline fades in). This was the most complex piece — Claude wrote ~200 lines of SVG and canvas JavaScript. I contributed zero lines. But I gave the creative direction: "The shield should build itself, then the text should appear below."

**Lesson:** AI can execute complex technical work if you give clear creative direction. The division of labor: I decide *what*, Claude decides *how*.

---

## What I learned

### About AI as a development partner

- Claude is better when you show it screenshots than when you describe things in words
- Being explicit about your skill level helps: "I have no technical background, explain this to me like a 5-year-old"
- One change at a time. Testing after every change. This is how real developers work too.
- The context builds up over sessions. The more Claude knows about your project, the better it gets.

### About building without code

- You don't need to understand code to make good decisions about it
- "This looks wrong" is a valid technical specification
- The bottleneck is never the code — it's knowing what you want
- Visual builders (Framer) + AI (Claude) is a genuinely viable production stack in 2025

### About the process

- Design decisions first, building second
- Ship early and improve — the site went live before it was perfect
- Document everything — every session, every decision, every fix. It pays off when you need to go back.

---

## Tips for doing this yourself

1. **Start with Claude, not Framer.** Spend 2–3 sessions deciding what you're building before you open any tool.

2. **Use Framer, not WordPress.** WordPress requires plugins, hosting, security updates. Framer just works. The Workshop AI is the key feature.

3. **Take screenshots obsessively.** Every time something doesn't look right, screenshot it. Send it to Claude. This is faster than any other debugging method.

4. **One component per session.** Don't try to fix everything at once.

5. **Keep a project memory file.** We maintained a `Start-Hier.md` file with every decision, every technical detail, every pending task. At the start of each session, Claude read this file and knew exactly where we left off.

6. **Accept that the first version won't be perfect.** Ship it. Then improve it. A live imperfect site is worth more than a perfect site that never launches.

7. **The mobile version is always second.** Build desktop first, get it right, then fix mobile. Never try to do both at once.

---

## Time investment

| Phase | Sessions | Hours |
|---|---|---|
| Design decisions | 3 | ~6h |
| Building homepage | 4 | ~8h |
| Building subpages | 5 | ~10h |
| CMS + articles | 3 | ~6h |
| Going live + SEO | 2 | ~4h |
| Polish + animation | 3 | ~6h |
| **Total** | **20** | **~40h** |

Not zero effort. But compared to managing a developer, reviewing designs, writing briefs, and handling revisions — this was dramatically faster and cheaper.

---

*Built by Geert Roeterink with Claude (Anthropic) and Framer. May 2026.*
