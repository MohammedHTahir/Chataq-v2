# Chataq-v2

A full-featured AI-powered UI generation app built with Next.js and React. Chataq-v2 lets you describe any interface in plain language and watch it get built in real time — with authentication, chat history, and multi-user support out of the box.

<p align="center">
    <img src="./screenshot.png" alt="Chataq-v2 Screenshot" width="800" />
</p>

## Features

### Core
- **AI-Powered Generation** — Describe any UI or app in plain text and get working code instantly
- **Real-time Preview** — Split-screen interface with chat on one side and a live preview on the other
- **Streaming Responses** — Toggle streaming mode for real-time token-by-token output
- **Conversation History** — Full chat history maintained throughout each session
- **Prompt Suggestions** — Built-in starter prompts to help you get going quickly
- **Full Task Support** — Handles all task types including thinking, web search, repo search, diagnostics, file reading, code generation, and design inspiration

### Auth & Multi-user
- **Anonymous Access** — Start building immediately, no sign-up required (3 generations/day)
- **Guest Accounts** — Register for a persistent session (5 generations/day)
- **Full Accounts** — Permanent account with higher limits (50 generations/day)
- **Secure Auth** — Email/password auth via NextAuth.js with bcrypt password hashing
- **Multi-tenant Architecture** — Each user only sees their own chats and projects
- **Rate Limiting** — Per-user daily limits with automatic resets

## Tech Stack

- **Framework** — Next.js 16 (App Router, Turbopack)
- **Auth** — NextAuth.js v5
- **Database** — PostgreSQL via Drizzle ORM
- **Styling** — Tailwind CSS v4
- **Language** — TypeScript

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/MohammedHTahir/Chataq-v2.git
cd Chataq-v2
```

### 2. Install dependencies

```bash
pnpm install
```

### 3. Set up environment variables

Create a `.env` file in the root:

```bash
# Generate with: openssl rand -base64 32
AUTH_SECRET=your-auth-secret-here

# PostgreSQL connection string
POSTGRES_URL=postgresql://user:password@localhost:5432/chataq

# Your AI API key
AI_API_KEY=your_api_key_here
```

### 4. Set up the database

```bash
pnpm db:migrate
```

### 5. Run the dev server

```bash
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Database Commands

| Command | Description |
|---|---|
| `pnpm db:generate` | Generate migration files from schema changes |
| `pnpm db:migrate` | Apply pending migrations |
| `pnpm db:studio` | Open Drizzle Studio |
| `pnpm db:push` | Push schema directly (dev only) |

## Deploy to Vercel

The fastest way to deploy Chataq-v2 is with Vercel + Neon Postgres:

1. Push this repo to GitHub
2. Import it in [vercel.com/new](https://vercel.com/new)
3. Add your environment variables (`AUTH_SECRET`, `POSTGRES_URL`, `AI_API_KEY`)
4. Deploy

## Project Structure

```
chataq-v2/
├── app/
│   ├── (auth)/          # Login & register pages
│   ├── api/             # API routes (chat, projects, auth)
│   ├── chats/           # Chat history pages
│   ├── layout.tsx
│   └── page.tsx         # Main UI
├── components/
│   ├── ai-elements/     # AI UI components
│   ├── chat/            # Chat interface components
│   ├── home/            # Homepage components
│   └── shared/          # Shared components (header, etc.)
├── lib/
│   └── db/              # Drizzle schema & migrations
└── hooks/
    └── use-chat.ts      # Chat state & streaming logic
```

## User Limits

| User Type | Daily Limit | Persistence |
|---|---|---|
| Anonymous | 3 chats | None |
| Guest | 5 chats | Session only |
| Registered | 50 chats | Permanent |

## License

MIT
