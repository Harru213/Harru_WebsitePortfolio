# Harru — Portfolio

Single-page portfolio for Harry "Harru" Rocero, AI Graphic Designer & Video Editor.
Next.js (App Router) + TypeScript + Tailwind CSS v4 + framer-motion + Lenis.

## Run it (VS Code terminal)

```bash
npm install
npm run dev
```

Open http://localhost:3000

## Add your files to /public (exact names)

```
public/
├── me/
│   ├── portrait-bw.jpg          ← grayscale, back/side view
│   └── portrait-color.jpg       ← color portrait
├── icons/
│   ├── play-3d.png              ← 3D hero icon (transparent PNG)
│   └── sparkle-3d.png
├── works/
│   └── work-01.jpg … work-24.jpg
├── videos/
│   ├── video-01.mp4 … video-06.mp4               ← 9:16, H.264, 2–4 MB each
│   └── video-01-poster.jpg … video-06-poster.jpg ← first frame
└── logos/
    higgsfield.svg  kling.svg  google-flow.svg  openart.svg  midjourney.svg  nano-banana.svg
    chatgpt.svg  elevenlabs.svg  premiere-pro.svg  after-effects.svg  photoshop.svg  capcut.svg
```

Missing files never break the page: they show a cream placeholder tile until you add them.

## Edit content

All text, works (titles, categories, tools), videos, tools, socials and email live in **`lib/data.ts`**.

## Project structure

```
app/
├── layout.tsx            Archivo font, meta tags, smooth scroll, grain overlay
├── page.tsx              Section order
└── globals.css           Color tokens, grain, marquee, 3D helpers
components/
├── providers/smooth-scroll.tsx   Lenis + scrollTo() for nav links
├── ui/                   shadcn/ui: button, input, textarea, label, dialog, badge, tooltip
├── motion/               BlurIn, FadeUp, WordReveal, Marquee
├── shared/               SafeImage (fallbacks), LogoTile/ToolLogo, SectionLabel, SocialIcon
└── sections/
    ├── nav.tsx           Floating pill menu
    ├── hero.tsx          Title + floating 3D icons
    ├── about.tsx         Sticky section with flipping portrait
    ├── flip-card.tsx     The 3D portrait card
    ├── statement.tsx     Word-by-word scroll reveal
    ├── apart.tsx         What Sets Me Apart
    ├── portfolio/        The Book: index, book-spread, page-leaf, book-page, lightbox
    ├── videos/           Reel Stack: index, reel-card
    ├── tools.tsx         Marquee + logo grid
    ├── contact.tsx       Form with validation
    └── footer.tsx        Links + giant wordmark
hooks/use-media-query.ts  useIsMobile, usePrefersReducedMotion
lib/
├── data.ts               ALL content
├── motion.ts             Easing + spring tokens
└── utils.ts              cn(), pad()
```

## Notes

- The contact form validates and shows a success message, but it does not send email yet.
  Connect it to Formspree, Resend or a server action in `components/sections/contact.tsx` (`onSubmit`).
- Replace the placeholder email (`hello@harru.com`) and the `#` social links in `lib/data.ts`.
- `prefers-reduced-motion` is respected: no flips or marquee, the book becomes a paginated grid,
  and the videos become a normal list with play buttons.
