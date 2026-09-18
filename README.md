# StorySpark — AI Kids' Story Generator

An interactive web application that turns a child's prompt — a character, a
setting, a theme — into a personalised, age-appropriate story, then narrates it
aloud.

Stories are generated with **Google Gemini 2.5 Flash**, checked for
age-appropriateness before they are returned, and voiced through the
**ElevenLabs** API.

---

## Features

- **Story generation** — a custom idea, or "surprise me", turned into a complete
  story with a title, a moral and an age group.
- **Narration** — generated speech so a child who cannot yet read can still
  follow along.
- **Content safety** — prompts and generated text are screened before anything
  reaches the screen.
- **Story library** — stories are persisted and can be reopened by id.
- **Kid-friendly UI** — large type, warm colour, no clutter.

---

## Tech stack

| Layer | What it actually uses |
|---|---|
| Frontend | React 18, TypeScript, Vite, Tailwind CSS, shadcn/ui (Radix primitives) |
| State / routing | TanStack Query, wouter |
| Animation | Framer Motion |
| Backend | Node.js, Express, TypeScript (ES modules) |
| Story generation | Google Gemini 2.5 Flash (`@google/genai`) |
| Text to speech | ElevenLabs API |
| Database | PostgreSQL (Neon serverless) via Drizzle ORM |
| Validation | Zod, shared between client and server |
| Build | Vite (client), esbuild (server) |

> `server/services/openai.ts` is an earlier generation path that is no longer
> wired into the app. `server/routes.ts` calls the Gemini service.

---

## API

| Method | Route | Purpose |
|---|---|---|
| `POST` | `/api/stories/generate` | Generate a story from a prompt |
| `GET` | `/api/stories/:id` | Fetch one story |
| `GET` | `/api/stories` | List recent stories |
| `POST` | `/api/tts/generate` | Narrate a story |

---

## Running it locally

```bash
npm install
npm run db:push     # push the Drizzle schema to your database
npm run dev         # client + server with hot reload
```

Environment variables:

| Variable | Used for |
|---|---|
| `GEMINI_API_KEY` | story generation |
| `ELEVENLABS_API_KEY` | narration |
| `DATABASE_URL` | PostgreSQL connection |

Production build:

```bash
npm run build       # vite build + esbuild server bundle
npm start
```

---

## Author

**Abdul Raheem Goraya** — BS Computer Engineering, GIK Institute (2023–2027).
Working in computer vision, generative AI and AI automation.

- Portfolio — *(add your deployed URL)*
- LinkedIn — https://www.linkedin.com/in/abdul-raheem-goraya-027387368
- GitHub — https://github.com/engineergoraya
