# AI Chat Interface

A modern, responsive AI chat interface built with Next.js, React, and Tailwind CSS.
It renders a polished conversational UI — agent/user message bubbles, avatars,
timestamps, and per-message actions (copy, download, thumbs up/down) — styled
with shadcn/ui primitives and Lucide icons.

> Demo app: the conversation shown is a static demo exchange. Wire your own
> backend (OpenAI, Anthropic, NVIDIA NIM, or any LLM API) into the
> `ChatInterface` component to make it fully interactive.

## Features

- 💬 Clean chat UI with distinct agent and user message bubbles
- 👤 Agent avatar + username/timestamp headers per message
- ⚡ Message actions: copy to clipboard, download, thumbs up/down feedback
- 🖱️ Smooth auto-scrolling message area (`ScrollArea`)
- 🎨 Dark-mode ready theming via `next-themes`
- 📱 Responsive layout (flex column, max-width message bubbles)
- 🧩 Reusable UI primitives (Button, Textarea, ScrollArea, ThemeProvider)
- ♿ Accessible Radix UI foundations with keyboard support

## Tech Stack

- **Framework:** Next.js 15 (App Router, React 19, TypeScript)
- **Styling:** Tailwind CSS + `tailwindcss-animate`, shadcn/ui components
- **UI primitives:** Radix UI (dialog, dropdown, scroll-area, tabs, toast, …)
- **Icons:** Lucide React
- **Fonts:** Geist (`geist` package)
- **Analytics:** Vercel Analytics
- **Forms/extras:** React Hook Form, date-fns, cmdk, embla-carousel, recharts

## Quick Start

```bash
# Install dependencies (pnpm or npm)
pnpm install
# or: npm install

# Run the dev server
pnpm dev
# or: npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Build for production

```bash
pnpm build
pnpm start
```

### Static export (Cloudflare Pages / GitHub Pages)

The app has no API routes or server-only features, so it can be fully
statically exported. Add `output: "export"` to `next.config.mjs` and build:

```bash
next build   # writes static files to ./out
```

Deploy the `out/` directory to Cloudflare Pages (or push it to the
`gh-pages` branch for GitHub Pages).

## Project Structure

```
.
├── app/
│   ├── layout.tsx        # Root layout (theme provider, analytics, metadata)
│   ├── page.tsx          # Home page -> renders ChatInterface
│   └── globals.css       # Tailwind + global styles
├── chat-interface.tsx    # Main chat UI component (messages, input, actions)
├── layout.tsx            # Alternate/legacy root layout
├── page.tsx              # Alternate/legacy page
├── components/
│   ├── theme-provider.tsx
│   └── ui/               # shadcn/ui primitives (button, textarea, scroll-area, …)
├── lib/
│   └── utils.ts          # cn() class-merge helper
├── styles/
│   └── globals.css       # Additional global styles
├── public/               # Static assets & placeholder images
├── next.config.mjs       # Next.js config (images unoptimized)
├── tailwind.config.ts    # Tailwind theme config
└── components.json       # shadcn/ui config
```

## Environment Variables

None required — the app runs fully client-side with demo data.

To connect a real AI backend, add your key as an env var (e.g. in `.env.local`):

```bash
OPENAI_API_KEY=sk-...      # or ANTHROPIC_API_KEY=..., etc.
```

Then replace the demo `messages` state in `chat-interface.tsx` with calls to
your API route or LLM provider SDK.

## Deployment Notes

- **Vercel:** push to GitHub and import the repo — zero config (`next build`
  / `next start` defaults).
- **Cloudflare Pages:** enable static export (`output: "export"`) and set the
  build command to `next build` with output directory `out`.
- **GitHub Pages:** same static-export build, deploy the `out/` folder from
  the `gh-pages` branch.
- `next.config.mjs` already sets `images.unoptimized: true`, which is required
  for static-export image support.

## License

MIT — free to use, modify, and share.

---

Built by Girish Lade — https://ladestack.in
