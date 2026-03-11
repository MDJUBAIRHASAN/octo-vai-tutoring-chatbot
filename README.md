# Octo vAI — AI Tutoring Chatbot for SSC/HSC Students

An AI-powered tutoring chatbot for SSC/HSC students in Bangladesh, built with **React**, **Tailwind CSS v4**, **NVIDIA NIM API** (`meta/llama-3.1-70b-instruct`), and **Supabase Edge Functions**.

## ✨ Features

- 🎓 **Class level selector** — SSC (Class 9–10) or HSC (Class 11–12)
- 📚 **Subject selector** — Math, Physics, Chemistry
- 🌐 **Web Search toggle** — powered by Tavily API for real-time search
- 🖼️ **Visual Lesson mode** — generates sandboxed HTML/CSS lessons in an iframe
- 💬 **Session memory** — full conversation context for follow-up questions
- 🌙 **Dark mode** — full dark/light theme with `localStorage` persistence
- 📱 **Responsive layout** — mobile-first with collapsible sidebar
- 👍 **Feedback buttons** — thumbs up/down on AI replies
- ⏹️ **Stop button** — abort in-flight AI requests via `AbortController`

## 🗂️ Project Structure

```
src/
  app/
    App.tsx                    # Root component
    api.ts                     # NVIDIA NIM API client + Tavily web search
    types.ts                   # TypeScript types (Chat, Message, ClassLevel, Subject)
    context/
      ThemeContext.tsx          # Dark mode React context
    components/
      Sidebar.tsx               # Chat history sidebar (minimizable)
      ChatArea.tsx              # Main chat view with sticky header
      WelcomeScreen.tsx         # Welcome/quick-action cards
      MessageBubble.tsx         # User & AI message bubbles with feedback
      InputArea.tsx             # Textarea + controls row
      MarkdownRenderer.tsx      # Custom markdown → HTML renderer
  imports/
    svg-zj1e0602ub.ts          # SVG path data
  styles/
    fonts.css                  # Google Fonts (Inter)
    index.css                  # Entry CSS
    tailwind.css               # Tailwind v4 setup
    theme.css                  # CSS design tokens
supabase/
  functions/
    server/
      index.tsx                # Hono web server — /nvidia-chat & /web-search routes
utils/
  supabase/
    info.tsx                   # Supabase project ID & anon key (auto-generated)
```

## 🚀 Setup & Running

### Prerequisites

- Node.js ≥ 18
- pnpm (recommended) or npm
- A [Supabase](https://supabase.com/) project
- An [NVIDIA NIM API key](https://build.nvidia.com/) set as `NVIDIA_API_KEY` in Supabase secrets
- A [Tavily API key](https://tavily.com/) set as `TAVILY_API_KEY` in Supabase secrets

### Install dependencies

```bash
pnpm install
```

### Configure Supabase secrets

In your Supabase project dashboard → Edge Functions → Secrets, add:

```
NVIDIA_API_KEY=nvapi-xxxxxxxxxxxxxxxxxxxx
TAVILY_API_KEY=tvly-xxxxxxxxxxxxxxxxxxxx
```

### Update Supabase info

Edit `utils/supabase/info.tsx` with your own Supabase project ID and anon key.

### Run locally

```bash
pnpm dev
```

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 18, TypeScript, Tailwind CSS v4 |
| AI Model | NVIDIA NIM `meta/llama-3.1-70b-instruct` |
| Backend proxy | Supabase Edge Functions (Deno + Hono) |
| Web Search | Tavily Search API |
| Icons | lucide-react |
| Build tool | Vite 6 |

## 📄 License

MIT
