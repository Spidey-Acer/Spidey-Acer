# 🎬 HeyGen Hero-Intro — Production Guide

Everything you need to generate the 40-second avatar intro that sits at the top of your GitHub profile. Copy the prompts verbatim. Total render time on HeyGen: ~5–10 min.

> **Why a video on a GitHub profile?** Almost nobody does it. A talking avatar that opens with *"I'm Peter — I ship production AI software"* makes you unmissable to recruiters, collaborators, and clients skimming 40 profiles a day. GitHub can't autoplay video, so we export a **short looping GIF/thumbnail** that links to the full video (YouTube/Loom). The README is already wired for it.

---

## 0. The fastest path (HeyGen "Say it with video" agent)

On `app.heygen.com/home`, paste this into the **"Ask for a video…"** prompt bar and hit Submit (Auto-pilot mode):

```
Create a 40-second vertical-friendly talking-head intro video for a software
founder's GitHub profile. Use a professional male avatar seated in a modern
dark home-office with subtle violet/cyan rim lighting. Confident, warm,
fast-paced delivery. Add lower-third captions in a clean sans-serif, and cut
to short screen-recording B-roll of code and a farm-tech dashboard between
lines. Brand colors: deep navy #0B0E1A background, electric violet #7C3AED and
cyan #06B6D4 accents. Read this script exactly:

[PASTE THE SCRIPT FROM SECTION 2 HERE]
```

If Auto-pilot's avatar/voice aren't right, use the manual controls below — they give you exact control.

---

## 1. Avatar & Voice setup

### Avatar (pick ONE)
- **Best (personal brand):** *Create Your Avatar* → **Instant Avatar** from a 2-minute webcam clip of yourself. This is YOUR face — 10× more credible than a stock avatar for a founder. Record in good light, plain/dark background, look at the lens, speak naturally.
- **Fast fallback:** A stock **HeyGen avatar** — filter for *male, business-casual, seated, warm*. Avoid the over-polished corporate ones; pick one that reads "builder," not "salesman."

### Voice (pick ONE)
- **Best:** *Clone Your Voice* — 2 min of clean audio → your real voice on the avatar. Unbeatable authenticity.
- **Fallback:** HeyGen voice → filter **English (Kenyan/African or neutral international), male, warm, mid-pace**. Set **Speed: 1.05×**, **Pause: natural**. Avoid robotic "news anchor" presets.

---

## 2. The Script (≈105 words · ~40s at natural pace)

> Read exactly. Beats marked `//` are for B-roll cuts, not spoken.

```
Hey — I'm Peter Kibet. People call me Spidey.

// [cut: terminal typing]
I'm a solo founder shipping production AI software out of Nairobi.

I build MkulimaOS — a farm-management platform running live farms in Kenya —
// [cut: farm dashboard]
and I co-founded Verify, a health-practitioner verification hub.

// [cut: Claude Community Kenya site]
I'm also Anthropic's Claude Community Ambassador for Kenya, growing East
Africa's first Claude developer community.

// [cut: back to avatar]
My rule is simple: don't just plan it — ship it.

If you're building something real, or you need someone who does —
let's talk. Scroll down, or find me below.
```

### Alt 25-second cut (if you want it tighter)
```
I'm Peter Kibet — Spidey. A solo founder shipping production AI software from
Nairobi. I build MkulimaOS for real Kenyan farms, co-founded the Verify health
platform, and I'm Anthropic's Claude Ambassador for Kenya. My rule: don't just
plan it — ship it. If you're building something real, let's talk.
```

---

## 3. Scene-by-scene B-roll (upload these as clips/screenshots in HeyGen's timeline)

| Time | Spoken line | On-screen B-roll |
|------|-------------|------------------|
| 0–5s | "Hey — I'm Peter Kibet…" | Avatar full-frame, name lower-third: **Peter Kibet · @Spidey-Acer** |
| 5–12s | "solo founder shipping…" | Screen-rec of a terminal / VS Code with real code scrolling |
| 12–20s | "I build MkulimaOS…" | Screen-rec of `app.mulinga.farm` dashboard |
| 20–27s | "co-founded Verify…" | Verify hub UI / practitioner search |
| 27–34s | "Claude Community Ambassador…" | `claudekenya.org` homepage + a community photo |
| 34–40s | "don't just plan it — ship it… let's talk" | Back to avatar, CTA lower-third: **github.com/Spidey-Acer · peterkibet.co.ke** |

> Grab B-roll fast: screen-record each site with the OS recorder (Win+Alt+R) for 8–10s each. No polish needed — HeyGen crops and captions.

---

## 4. Brand system (set in HeyGen "Brand Kit")

- **Background / base:** `#0B0E1A` (deep navy)
- **Accent 1:** `#7C3AED` (electric violet)
- **Accent 2:** `#06B6D4` (cyan)
- **Text on dark:** `#F8FAFC`
- **Caption font:** a clean geometric sans (Inter / Poppins / HeyGen's "Sans" default)
- **Lower-third style:** left-aligned, violet→cyan underline bar, white text
- **Logo:** drop your Spidey Labs mark bottom-right at ~60% opacity if you have one

---

## 5. Export → GIF → embed (do this after render)

1. **Download** the final MP4 from HeyGen (1080p).
2. **Host the full video** on YouTube (unlisted or public) or Loom. Copy the link.
3. **Make the looping GIF thumbnail** (the clickable preview in the README):
   ```bash
   # 6-second, 900px-wide, optimized loop from the first 6s
   ffmpeg -ss 0 -t 6 -i intro.mp4 -vf "fps=12,scale=900:-1:flags=lanczos" -loop 0 assets/intro-preview.gif
   ```
   *(You have ffmpeg locally — this keeps the GIF under ~4 MB so GitHub loads it fast.)*
4. In `README.md`, the intro block is already scaffolded — just:
   - replace `assets/intro-preview.gif` if you named it differently, and
   - set the `href` to your hosted video URL.
5. Commit both `assets/intro-preview.gif` and `intro.mp4` is **not** needed (keep the MP4 out of git — host it, link it).

---

## 6. Quality checklist before you ship the video

- [ ] First 3 seconds hook without sound (captions carry it — most GitHub visitors are muted)
- [ ] Your name + role visible in the first lower-third
- [ ] B-roll shows **real** products (Mulinga dashboard, Verify, claudekenya.org) — no stock filler
- [ ] Ends on a clear CTA + your links
- [ ] GIF preview < 4 MB and loops cleanly
- [ ] Full video link works in an incognito window (unlisted ≠ private)

> **Honesty gate:** every claim in the script is true and shipping today. Keep it that way — no "AI-powered blockchain" inflation. Your real story is already strong.
