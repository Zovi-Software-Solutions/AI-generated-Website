# AI Prompts — Building zovisoftwaresolutions.com

> These are the actual prompts used to build the Zovi website. Some are prompts I gave to Claude directly. Others are prompts Claude wrote for me to paste into Framer Workshop.

---

## 1. Framer Workshop prompts (paste into Framer's AI code editor)

These prompts were written by Claude and pasted into Framer Workshop to generate React components.

### StickyHeader — mobile hamburger menu

```
Make this header fully mobile responsive. On screens 768px and below:
- Set outermost container width to 100%
- Hide all navigation links and the "Uw aanvraag" button
- Show a hamburger icon (☰) on the right side in white, font-size 24px
- Clicking hamburger toggles a vertical dropdown menu below the header
- Dropdown: full width, background #1E3A5F, all nav links stacked vertically
- Each nav link: white, 16px, padding 16px 24px, links to same URLs as desktop
- Desktop layout above 768px stays exactly as is
```

**Why it works:** Specific breakpoint (768px), exact colors from the brand guide, explicit behavior (toggle), and a clear instruction to preserve desktop layout. No ambiguity.

---

### ZoviPijlers — 4 columns to 2×2 grid on mobile

```
Make this section fully mobile responsive. On screens 768px and below:
- Set outermost container to width: 100%, padding: 40px 24px
- Change the 4-column grid to 2 columns (2x2 grid)
- Each card: full width within its grid cell, center-aligned content
- Icon size: 40px, title: 16px bold, description: 14px
- Gap between cards: 24px
- Desktop layout above 768px stays exactly as is
```

**Why it works:** Describes the grid transformation explicitly, sets font sizes to prevent layout collapse, keeps desktop untouched.

---

### ContactForm — 2 columns to 1 column on mobile

```
Make this contact form section fully mobile responsive. On screens 768px and below:
- Set outermost container to width: 100%, padding: 40px 24px
- Stack the two-column layout (form + contact info) into a single column
- Form fields: full width (100%), stacked vertically
- Each input: width 100%, font-size 16px (prevents iOS zoom)
- "Direct contact" section appears below the form, not beside it
- Desktop layout above 768px stays exactly as is
```

**Why it works:** The `font-size: 16px` on inputs is a real trick — iOS Safari zooms in on inputs with smaller font sizes. Naming that explicitly prevents a common mobile bug.

---

### ZoviHeroAnimated — cinematic shield assembly

```
Build a React hero section component called ZoviHeroAnimated for Zovi Software Solutions 
with a cinematic intro animation. Full width, min-height 560px, dark navy gradient 
background (#06101F → #0E1F3D → #06101F).

SHIELD SVG: viewBox="0 0 150 200". 
Outer path: M 0,10 L 150,10 L 150,120 Q 150,185 75,200 Q 0,185 0,120 Z
Dividers: horizontal line y=107, vertical line x=75.
Gold gradient: #F0D080 → #D4B168 → #A8895A.

PHASE 1 (0–3.1s): Shield at scale(1), 210×280px, centered in hero.
Draw shield outline with stroke-dashoffset animation (dasharray:700, 1.3s ease).
Use 3 layered paths for glow: stroke-width 14 opacity 0.06 / stroke-width 7 opacity 0.13 / stroke-width 3 full.
Then horizontal divider (dasharray:155, 0.5s at t=1.05s), vertical (dasharray:195, t=1.25s).
Then fade in 4 icon groups (0.55s each):
- t=1.65s Top-left Radar: 3 concentric circles cx=38 cy=58 r=8/14/20, sweep line to (50,44), blip dot r=3.2 at (49,45), center dot
- t=2.0s Top-right Eye: lens path M89,58 C94,43 130,43 135,58 C130,73 94,73 89,58Z, iris r=10, pupil r=4, highlight r=2.2 at (117,53)
- t=2.35s Bottom-left Lock: rect x=27 y=140 w=24 h=18 rx=2, arch M31,140 v-6 a8,8 0 0 1 16,0 v6, keyhole dot r=3 at (39,149)
- t=2.7s Bottom-right Neural: nodes at (110,133)/(95,146)/(125,146)/(110,161), connecting lines, pulse rings at (110,133)
Canvas layer (210×280px, absolute, behind SVG): 38 particles inside shield boundary, 
gold/white, connect with lines when within 50px. Fade in at t=1.4s.

PHASE 2 (t=3.1s): Transition: top→34px, transform→translate(-50%,0) scale(0.52). 
Duration 0.9s cubic-bezier(0.4,0,0.2,1).

PHASE 3 (t=3.7s): Fade in text block (absolute, top:196px, centered):
- Eyebrow: "SOFTWARE LEVERANCIER IN EUROPA" #D4B168, 10px, letter-spacing 3px
- H1: "Stuur de aanvraag naar Zovi, wij pakken het op." white 36px bold
- Subtitle: white 58% opacity, 14px, max-width 520px
- Buttons: gold filled "Uw aanvraag" + outlined white "Zo werken wij"
Animation plays once on mount. Export as default.
```

**Why it works:** Divides the animation into named phases, gives exact coordinates from the real SVG file, specifies timing down to the millisecond, and explains the canvas clipping approach. Framer's AI needs this level of precision for complex animations.

---

## 2. Prompts to Claude (conversational)

These are the types of prompts I gave Claude directly in conversation.

### Starting a new component

```
I want to build [component name]. It should look like [description]. 
The colors are navy (#1E3A5F) and gold (#D4AF37). 
Write me the Workshop prompt to paste into Framer.
```

### Fixing something that doesn't look right

```
[screenshot] 
This doesn't look right. The [element] is [problem]. 
Can you write a fixed Workshop prompt?
```

**Why it works:** Screenshots are more valuable than descriptions. Showing Claude the exact problem is faster than describing it. Claude can read images.

### Mobile fix pattern

```
On my phone, [section] looks like [description of problem]. 
Everything is zoomed out and too small to read. 
Write me a Workshop prompt to fix only the mobile version — desktop must stay exactly as is.
```

### DNS / technical setup

```
I'm in TransIP DNS management. I need to point my domain to Framer. 
Here are two screenshots of my current DNS settings. 
Tell me exactly what to add, change, and delete.
```

**Why it works:** Claude can read screenshots of DNS panels. Asking for exact changes (add/change/delete) prevents mistakes.

---

## 3. Prompt patterns that work well with Claude

### The "screenshot + fix" pattern
Show a screenshot, describe what's wrong, ask for a specific fix. This is faster than any other approach.

### The "preserve desktop" clause
Always add "desktop layout above 768px stays exactly as is" when working on mobile. Without it, fixes tend to break desktop.

### The "exact colors" rule
Always include hex codes. "Navy" or "gold" are ambiguous. `#1E3A5F` and `#D4AF37` are not.

### The "component by component" approach
Fix one component per session. Testing after each change makes it easy to know what broke what.

### The "tell me what to do, step by step" request
```
Tell me exactly what to click, step by step. 
I have no technical background. One step at a time.
```
Claude adjusts its instructions to your level when you make your level explicit.

---

## 4. What NOT to do

❌ **Vague prompts:** "Make it look better" → Claude has no reference for "better"

❌ **Too many changes at once:** "Fix the header, footer, contact form and mobile" → impossible to test

❌ **Skipping screenshots:** Describing visuals is slower and less accurate than showing them

❌ **Not testing after each change:** A working component might break when you fix another one next to it

---

*These prompts are specific to Zovi's design system. Adapt hex codes, font sizes, and component names to your own project.*
