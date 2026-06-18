---
name: ig-story-carousel
description: "Use when the user asks for IG stories, Instagram stories, story slides, carousels, social slides, or any request to make a story or make a carousel for Instagram. Also use for light, dark, or branded theme variations of Instagram carousel slides. Creates polished 1:1 square carousel slides and stories as HTML widgets with auto-export to PNG."
---

# IG Story Carousel Skill

Create polished, scroll-stopping 1:1 square carousel slides rendered as HTML widgets (9:16 vertical available on request). Every slide should look like something you'd actually post — premium, minimal, modern — AND feel like something worth saving and sharing. Design quality and content virality are equally important. Auto-exports as PNGs for download.

---

## Core Principles

- **Design-first, virality-always.** Every slide is a standalone visual AND a piece of social content engineered to stop scrolls, earn saves, and drive action.
- **1:1 ratio is default.** Always use `aspect-ratio: 1/1` on the slide container, fixed at `width: 340px` centered in the widget. (User can override to 9:16 if needed.)
- **Flat design only.** Solid dark fills + layered geometric shapes for depth. No gradients, no drop shadows, no blur.
- **Font hierarchy matters.** Large bold hook text (22–26px, weight 800), body copy (12–14px, weight 400–500), eyebrow labels (9–10px, uppercase, letter-spacing).
- **Dark palette by default.** Background `#0b0e1a` or similar deep navy/charcoal. Accents for dots, pills, CTAs.
- **Fill the frame.** Whitespace should support clarity — not reduce information value. If a slide feels empty, increase font size or add a content element. Every slide earns its space.
- **All slides in one widget.** Render the full carousel horizontally (flex row, centered, gap 20px, wrapping allowed) in a single widget call. No frame labels required.

---

## Pre-Generation Planning Checkpoint

Before writing any slide, mentally answer these three questions:

1. **What makes slide 1 stoppable?** → Hook must create immediate tension or curiosity.
2. **What makes slide 3 or 4 saveable?** → At least one slide must contain a framework, formula, checklist, or template worth screenshotting.
3. **What makes the last slide action-driving?** → CTA must be platform-aligned — save, share, follow, comment, or DM. Not a generic "link in bio."

---

## Viral Carousel Performance Goals

Every carousel should be optimized for:

- **Scroll-stopping first slide** — tension, pain, or bold claim in the headline
- **Curiosity-driven narrative flow** — each slide earns the next swipe
- **Saveable reference value** — at least one "steal this" slide per carousel
- **Cold-audience readability** — no assumed context, clear and fast on mobile
- **High specificity** — real examples, concrete nouns, practical output
- **Platform-aligned CTA** — save / share / follow / comment / DM

Each slide should answer at least one of:
- Why should I care?
- Why should I keep swiping?
- What can I steal from this immediately?

---

## Copywriting System

### Hook Headlines
Write headlines that create tension, urgency, or curiosity. Avoid generic topic labels.

**Strong patterns:**
- Pain: "Most people use Claude wrong."
- Mistake: "Your prompts aren't bad — they're too vague."
- Contrarian: "Treat prompts like instructions, not wishes."
- Specific: "2 prompt rules most builders ignore."
- Promise: "One framework. Better outputs every time."

**Avoid:**
- Generic labels: "Prompting 101", "AI Tips", "How to use ChatGPT"
- Classroom titles: "Introduction to Prompt Engineering"
- Vague intros: "Today we're going to talk about..."
- Low-tension openers with no hook

### Body Copy Rules
- Short and punchy. Mobile-readable. High signal-to-noise.
- Prefer concrete nouns over abstract language.
- Prefer direct language over "corporate guide" wording.
- One clear takeaway per slide — not a paragraph, not a list of 7 things.
- Examples must be **specific and real**, not generic filler.

**Weak example:** "Write about productivity"
**Strong example:** "Write a 150-word newsletter intro for founders who ship late. Blunt, no fluff, end with a question."

### Transition CTAs (bottom of non-final slides)
Create momentum, not just arrows. Use copy that builds curiosity:
- "Here's the fix →"
- "Rule #1 most people miss →"
- "Now steal this →"
- "This is where it clicks →"
- "The part worth saving →"
- "One more thing →"
- "Save slide 3 →"

### Final Slide CTAs
Choose based on the carousel's primary goal:

| Goal | CTA |
|---|---|
| Follow | "Follow for practical AI workflows" |
| Save | "Save this for your next prompt" |
| Share | "Send this to someone still blaming the AI" |
| Comment | "Comment 'PROMPT' and I'll send part 2" |
| DM | "DM me 'GUIDE' for the full framework" |

Do **not** default to soft external-link language unless the user explicitly wants link clicks.

---

## Viral Copy Patterns

Use these frameworks to structure slide sequences and individual slides:

| Pattern | Structure |
|---|---|
| Pain → Reframe → Fix | Name the problem, reframe why it happens, show the solution |
| Mistake → Why it fails → Better version | Show the bad, explain the failure mode, show the upgrade |
| Bad example → Good example | Side-by-side contrast with explanation |
| Myth → Truth | "Everyone says X. Here's what's actually true." |
| Before → After | Weak version vs strong version |
| Problem → Framework → CTA | Pain slide → saveable slide → action slide |
| Hook → Tension → Insight → Proof → CTA | Full 5-slide arc |

### High-performing first-slide hooks:
- "Most [audience] [do thing] wrong."
- "Your [thing] isn't bad — it's [actual problem]."
- "[Number] [things] most [audience] ignore."
- "Treat [X] like [reframe], not [what they think it is]."
- "Stop [wrong behavior]. Start [right behavior]."

### Cliffhanger transitions between slides:
- End content slides with italicized direction copy: *"Here's the fix →"* or *"Slide 3 is the one worth saving →"*
- Create incomplete loops: introduce a framework, then resolve it on the next slide.

### Save-bait final reference slides:
- "Screenshot this."
- "Save this for your next [task]."
- "Bookmark slide [N] — you'll need it."
- "This is the one worth keeping."

### Comment bait (tasteful):
- "Which of these do you do? Comment below."
- "Tag someone who needs this."
- "Comment '[WORD]' and I'll send [resource]."

---

## Slide Anatomy

Every slide is a `div` with:
```css
width: 340px;
aspect-ratio: 1/1;
background: #0b0e1a;
border-radius: 16px;
overflow: hidden;
position: relative;
display: flex;
flex-direction: column;
justify-content: space-between;
padding: 28px 22px;
box-sizing: border-box;
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

### Three zones (adjusted for 1:1):
1. **Top:** Eyebrow label (brand/topic tag, uppercase, 9–10px, accent color)
2. **Middle (flex: 1):** Headline (22–26px) + supporting content (12–14px)
3. **Bottom:** CTA or next-slide nudge

### Decorative geometry (`position: absolute`, `z-index: 0`):
- Optional: 1 small circle (150–180px, low-opacity fill, positioned at corner)
- Content sits at `z-index: 1`

---

## Content Pattern Library

### Hook slide (Frame 1)
- Bold tension headline (22–26px, weight 800)
- 1–2 line sub-copy explaining the tension (12–14px, muted)
- Italicized swipe nudge: *"Swipe for the fix →"*

### Problem slide — Before/After
- Eyebrow: "The real problem"
- Headline: short, declarative (20–22px)
- Two contrast blocks (stacked):
  - **Weak** block: `background:#1c0f0f; border-left:3px solid #f87171`
  - **Strong** block: `background:#0a1f12; border-left:3px solid #4ade80`
- Body text inside blocks: 12–13px, colored to match block theme

### Framework / Formula slide (Saveable)
- Eyebrow: "Steal this framework"
- Headline: name the framework clearly (20–22px)
- Formula block: `background:#0f1e30; border:1px solid #1e3a5f; border-radius:12px; padding:14px 12px`
- Each item: colored dot (7–8px) + bold label + description (12px, 1.4 line-height)
- Use 4–5 distinct accent colors for multi-part formulas
- CTA: "Save this" pill

### Checklist slide
- Eyebrow: "Run this before you post"
- Headline: "The [topic] checklist" (20–22px)
- 4–6 check items: circle icon (✓ green or ✕ red) + bold label + 1-line description (11–12px)
- CTA: "Save this" pill

### Proof / Stats slide
- Eyebrow: "By the numbers"
- 2–3 stat chips: `background:rgba(255,255,255,0.06); border-radius:8px; padding:10px`
- Each chip: large number (16–18px, bold, accent color) + label (9–10px, muted, uppercase)
- Supporting copy (12–13px, muted)

### CTA / Close slide (Last frame)
- Bold closing statement (22–26px) — restate the core insight
- 1–2 stat chips for social proof (optional)
- Supporting copy (12–13px, muted)
- Full-width pill CTA button (platform-aligned copy)
- Handle line below button

---

## Color System

Default palette (dark navy):
```
Background:    #0b0e1a
Surface:       #0f1e30
Border:        #1e3a5f
Text primary:  #ffffff
Text muted:    #4b6080
Text secondary:#94a3b8
Accent blue:   #3b82f6
Accent purple: #6366f1
Accent teal:   #22d3ee
Accent green:  #4ade80
Accent amber:  #fbbf24
Danger/X:      #f87171
```

CTA buttons: solid accent fill, white text, `border-radius:50px`, `padding:9px 20px`.

Before/After color coding:
- Weak/bad: `background:#1c0f0f; border-left:3px solid #f87171; text color:#fca5a5`
- Strong/good: `background:#0a1f12; border-left:3px solid #4ade80; text color:#86efac`

### Theme variants:
- **Purple dark:** bg `#0d0a1a`, accent `#a855f7`
- **Green dark:** bg `#080f0a`, accent `#4ade80`
- **Warm dark:** bg `#120a00`, accent `#fbbf24`
- **Clean light:** bg `#f8fafc`, text `#0f172a`, accent `#2563eb`

---

## Workflow

1. **Parse the request.** Topic, brand/handle, tone, slide count (default 5 if not specified), aspect ratio (default 1:1), CTA goal (save / share / follow / comment / DM).
2. **Run the planning checkpoint.** Answer the 3 pre-generation questions mentally before writing any copy.
3. **Plan the narrative arc:**
   - 3 slides: Hook → Framework → CTA
   - 4 slides: Hook → Problem → Framework → CTA
   - 5 slides: Hook → Problem → Framework → Proof → CTA
   - 6+ slides: Hook → Problem → Framework → Checklist/Mistakes → Proof → CTA
4. **Assign patterns.** Pick from Content Pattern Library. Ensure at least one slide is a saveable reference.
5. **Write copy first.** Headlines, body, transitions, final CTA — all before touching layout.
6. **Choose theme.** Default dark navy unless user specifies brand colors or light theme.
7. **Build all slides in one widget.** Render horizontally, centered, gap 20px.
8. **Auto-export to PNG.** After widget renders, automatically create high-res HTML and run Playwright export to `/mnt/user-data/outputs/carousel.zip`.

---

## Auto-Export PNG (Playwright — default)

All carousels auto-render and export as PNG files. The workflow is:

1. Build carousel widget for preview (displays in chat immediately)
2. Create `/tmp/slides-{timestamp}.html` at 1080×1920px resolution (1:1 scaled 3.2×)
3. Run Playwright screenshot script to extract each slide as PNG
4. Zip PNGs and present to user in outputs directory

This is automatic — no user action needed unless they specifically want download files.

### Full-res slide HTML rules (slides.html):
Scale 3.2× from widget (340px → 1088px):
- Container: `width:1088px; height:1088px` (fixed, no `aspect-ratio`)
- Font sizes: multiply by ~3.2 (26px → 83px; 13px → 42px)
- Padding: `96px 86px`
- No CSS variables — hardcoded hex throughout
- Each slide is a sibling `<div id="slide-N">`, NOT inside a flex row

### Playwright render script:
```python
import zipfile
import time
from playwright.sync_api import sync_playwright

timestamp = int(time.time())
slides = [
    ("slide-1", "frame-1-hook"),
    ("slide-2", "frame-2-problem"),
    ("slide-3", "frame-3-framework"),
    ("slide-4", "frame-4-proof"),
    ("slide-5", "frame-5-cta"),
]

with sync_playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page(viewport={"width": 1088, "height": 1088})
    page.goto(f"file:///tmp/slides-{timestamp}.html")
    page.wait_for_load_state("networkidle")
    for slide_id, filename in slides:
        page.locator(f"#{slide_id}").screenshot(path=f"/tmp/{filename}.png")
    browser.close()

with zipfile.ZipFile("/mnt/user-data/outputs/carousel.zip", "w") as zf:
    for _, filename in slides:
        zf.write(f"/tmp/{filename}.png", f"{filename}.png")

print(f"✓ Exported {len(slides)} slides to carousel.zip")
```

**Auto-trigger conditions:**
- Always create the high-res HTML file after widget renders
- Always run Playwright export if the slides are substantial (3+ slides, >500 words total)
- Always zip and present to `/mnt/user-data/outputs/`
- Notify user: "Also exported as PNGs for download."

---

## Mode Detection

| Signal | Mode |
|---|---|
| "light theme", "clean", "white", "minimal" | Light theme |
| "9:16" or "vertical" | Vertical story format |
| "1:1" or "square" (default) | Square format |
| uploads an image | Image-reference mode |
| anything else | 1:1 dark navy default |

---

## Light Theme Variant

```
Background:    #f8fafc
Surface:       #f1f5f9
Border:        #e2e8f0
Text primary:  #0f172a
Text muted:    #64748b
Accent:        #2563eb
Danger/X:      #ef4444
```

Light theme before/after:
- Weak: `background:#fef2f2; border-left:3px solid #ef4444; text:#991b1b`
- Strong: `background:#f0fdf4; border-left:3px solid #16a34a; text:#15803d`

Light theme presets:
- **Minimal white + blue:** bg `#ffffff`, accent `#2563eb`
- **Soft cream + amber:** bg `#fffbf0`, accent `#d97706`, text `#1c1917`
- **Sage + green:** bg `#f0fdf4`, accent `#16a34a`, text `#052e16`
- **Lavender + purple:** bg `#faf5ff`, accent `#7c3aed`, text `#2e1065`

---

## Image Upload / Reference Mode

### Intent A — Use as background
- Absolutely positioned `<img>` (`z-index:0`) + dark overlay `rgba(0,0,0,0.52)` at `z-index:1`
- Content at `z-index:2`
- Use solid placeholder fill for preview — tell user to swap for export

### Intent B — Extract brand/style
- Extract dominant colors, vibe (dark/light, minimal/bold)
- Apply as theme palette for all slides
- State extraction explicitly: "I pulled these colors: [list]"

### Intent C — Use content as copy source
- Read content, populate slides from it
- Confirm source copy if ambiguous

---

## Viral Educational Carousel Checklist

Run mentally before outputting:

- [ ] Is slide 1 strong enough to stop a scroll?
- [ ] Is the copy specific, not generic?
- [ ] Does every slide contain one clear takeaway?
- [ ] Is there at least one highly saveable slide?
- [ ] Are examples concrete and real-world?
- [ ] Do transitions pull the reader forward with curiosity?
- [ ] Is the final CTA platform-aligned?
- [ ] Would someone share this?
- [ ] Are font sizes large enough to fill the slide without dead air?
- [ ] Every slide 340px wide, 1:1 ratio (or user-specified)?
- [ ] No gradients on backgrounds?
- [ ] Text readable against background?
- [ ] Decorative elements at z-index:0, content at z-index:1?

---

## Example Trigger Phrases

- "Make me an IG carousel about [topic]"
- "Create story slides for [brand/product]"
- "I need 5 slides teaching [concept]"
- "Make a viral carousel about [topic]"
- "IG stories with CTAs for [funnel stage]"
- "Make a light theme / white background version"
- "Use this image as the background"
- "Pull the brand colors from this logo" [+ image upload]
- "Make slides from these notes" [+ image/doc upload]
