# Onimix Tech — Website

A single-file website (`index.html`) for Onimix Tech. No framework, no build step, no npm install. Everything — HTML, CSS and JavaScript — lives in that one file. Open it in a browser and it works.

---

## 1. Getting Started

1. Unzip `onimix-tech-assets-folder.zip` — this gives you a ready-made `assets/` folder.
2. Place that `assets/` folder in the **same folder** as `index.html`, like this:

```
your-website/
├── index.html
└── assets/
    ├── videos/
    └── images/
```

3. Open `index.html` directly in a browser to preview it. No server or build tool required.
4. When you're happy with it, deploy by uploading the whole `your-website/` folder (index.html + assets) to Vercel, Netlify, GitHub Pages, or any static host.

The site works right now even with empty asset folders — every image and video has a built-in fallback (a placeholder graphic, or an animated background pattern for the hero) so nothing looks broken while you're still gathering your real photos and videos.

---

## 2. Folder Structure Reference

```
assets/
├── videos/
│   ├── hero/hero.mp4            → fullscreen homepage background video
│   ├── about/about.mp4          → About section intro video (play-on-click)
│   ├── services/                → optional ambient video, Services section
│   ├── projects/                → optional ambient video, Projects section
│   └── background/               → optional ambient video, any other section
│
└── images/
    ├── logo/                    → site logo (logo.png) + favicon (favicon.png)
    ├── hero/                    → hero-poster.jpg (shown before hero video loads)
    ├── profile/                 → profile.jpg (About section photo)
    ├── projects/                → featured project screenshots
    ├── birthday-flyer/          → Birthday Flyers portfolio gallery
    ├── wedding/                 → Wedding Designs portfolio gallery
    ├── pos-flyer/                → POS Flyers portfolio gallery
    ├── burial/                  → Burial Designs portfolio gallery
    ├── church/                  → Church Designs portfolio gallery
    ├── business/                → Business Flyers portfolio gallery
    ├── political/                → Political Campaign Designs gallery
    ├── social-media/            → Social Media Designs gallery
    ├── logo-design/              → Logo Designs gallery
    ├── branding/                 → Brand Identity gallery
    ├── banners/                  → Banners gallery
    ├── posters/                  → Posters gallery
    ├── ui-design/                → UI/UX Designs gallery
    ├── mockups/                  → Mockups gallery
    └── others/                   → Others gallery
```

Every one of these is already wired up inside `index.html`. You never need to touch the JavaScript — just add files to the right folder and, where filenames differ, update the `src` path in the HTML (see section 4).

---

## 3. Recommended Media Sizes

| Asset | Recommended spec |
|---|---|
| Logo (`assets/images/logo/logo.png`) | Transparent PNG or SVG, ~160×48px |
| Favicon (`assets/images/logo/favicon.png`) | Square, 512×512px |
| Hero video (`assets/videos/hero/hero.mp4`) | 1920×1080, MP4/H.264, 15–40 second loop, no audio needed (it's muted) |
| Hero poster (`assets/images/hero/hero-poster.jpg`) | 1920×1080 — shown as the first frame before the video loads |
| About video (`assets/videos/about/about.mp4`) | 1280×720, MP4/H.264, audio is fine (it's play-on-click, not autoplay) |
| Profile photo (`assets/images/profile/profile.jpg`) | Portrait, ~800×960px |
| Project screenshots (`assets/images/projects/`) | 1400×900px (16:10) |
| Portfolio gallery images | 1000×1250px (4:5) or 1000×1000px (1:1) |
| Section/background videos | 1920×1080, muted, short and looping, compressed to keep file size small |

**Image formats:** JPG, JPEG, PNG, WEBP, AVIF and SVG all work everywhere on this site.

- For the logo, profile photo, and project screenshots, the code automatically tries every format for you — just name the file to match what's in the comments (e.g. `profile.jpg` *or* `profile.png` *or* `profile.webp` all work without touching any code).
- For portfolio gallery images added via `list.txt` (see below), just write the exact filename including its extension — since you're typing it yourself, any format you list will work.

---

## 4. How to Replace Things

Open `index.html` in any text editor and search (Ctrl/Cmd+F) for these terms — every replaceable spot has a comment block above it explaining exactly what to do:

- `REPLACE COMPANY LOGO HERE`
- `REPLACE HERO VIDEO HERE`
- `REPLACE ABOUT PHOTO HERE`
- `REPLACE ABOUT VIDEO HERE`
- `REPLACE PROJECT SCREENSHOTS HERE`
- `HOW THIS GALLERY MAPS TO YOUR FOLDERS`

**General pattern for any image/video:** find the `src="assets/..."` path in the HTML and either (a) rename your file to match it exactly, or (b) edit the path in the code to match your filename.

### Adding portfolio images (any filename — recommended method)

Every category folder (e.g. `assets/images/wedding/`) contains a `list.txt` file. Open it and add one line per image — **any filename, any format**:

```
my-cousins-wedding-flyer.jpg
invite-card-v2.png
save-the-date.webp|Save the Date — Custom Title
```

The optional `|Custom Title` part sets the caption shown in the lightbox. Leave it off and a title is generated automatically from the filename (dashes/underscores become spaces, capitalized).

1. Drop your actual image file(s) into that same category folder.
2. Add their filenames to `list.txt` (one per line).
3. Save and refresh the site.

That category's sample placeholder images disappear automatically and your real images take their place — filtering, the lightbox, and next/previous navigation all pick them up with zero code edits. If a category's `list.txt` is empty, the sample placeholders just stay visible so the gallery is never empty.

### Adding portfolio images (advanced/alternative method)

You can also hand-edit the HTML directly if you prefer full control: go to `<section id="portfolio">` in `index.html`, copy one `.gallery-item` block, and update its `<img src>`, `alt`, `data-title` and `data-category`. Both methods work side by side.

### Adding an optional background video to a section

The Services and Projects sections each have a commented-out `<video class="section-bg-video">` block. Uncomment it and point the `<source>` at your file in `assets/videos/services/` or `assets/videos/projects/` — the styling (low opacity, full-cover, behind content) is already defined.

---

## 5. What's Already Built

- Fullscreen cinematic hero video with autoplay/muted/loop/inline, dark overlay, and an animated fallback pattern if the video isn't there yet
- About section with a play-on-click intro video
- Services, Naira-priced Graphic Design pricing (6 tiers), Technologies marquee, AI Lab, Featured Projects
- A single filterable Creative Portfolio gallery covering all 15 categories, with a fullscreen lightbox (previous/next buttons, keyboard arrows, mobile swipe, image titles and category labels)
- Testimonials slider, Contact section (WhatsApp, email, Facebook), footer
- Loading animation, scroll-reveal animations, hover glow effects, glassmorphism, parallax hero overlay, mobile menu, back-to-top button, floating WhatsApp button

---

## 6. Notes

- The contact form is presentation-only — it doesn't send anywhere yet. Connect it to a service like Formspree or EmailJS, or your own backend, when you're ready.
- No build tools, package managers, or frameworks are used anywhere. It's plain HTML/CSS/JavaScript, so it will keep working indefinitely with zero maintenance overhead.
- If you ever want to split this single file into separate `.css`/`.js` files for a larger project, everything is already clearly organized in labeled sections (`/* ---------- section name ---------- */`) to make that easy.
