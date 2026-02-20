<div align="center">

# 🌌 Lumina AI — Multi-Modal AI Generation Platform

[![Next.js](https://img.shields.io/badge/Next.js%2013-000000?style=for-the-badge&logo=next.js&logoColor=white)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://typescriptlang.org)
[![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com)
[![Replicate](https://img.shields.io/badge/Replicate-000000?style=for-the-badge&logo=replicate&logoColor=white)](https://replicate.com)
[![Clerk](https://img.shields.io/badge/Clerk-6C47FF?style=for-the-badge&logo=clerk&logoColor=white)](https://clerk.dev)
[![Stripe](https://img.shields.io/badge/Stripe-635BFF?style=for-the-badge&logo=stripe&logoColor=white)](https://stripe.com)
[![Live Demo](https://img.shields.io/badge/Live%20Demo-luminaai.tech-FF6B6B?style=for-the-badge&logo=vercel&logoColor=white)](https://luminaai.tech)

> **5-in-1 Multi-Modal AI SaaS** — One platform for AI conversation, image generation, code generation, music creation, and video generation — with a token credit system and Stripe billing.

</div>

---

## ✨ AI Tools Included

| Tool | Model | Description |
|------|-------|-------------|
| 💬 **AI Conversation** | GPT-4 | Intelligent chat with context memory |
| 🎨 **Image Generation** | DALL-E 3 | Text-to-image with style controls |
| 💻 **Code Generation** | GPT-4 Code | Multi-language code generation & explanation |
| 🎵 **Music Generation** | Replicate (MusicGen) | Text-to-music with genre controls |
| 🎬 **Video Generation** | Replicate (Zeroscope) | Text-to-video clips |

---

## 🏗️ Architecture

```
User Request → Clerk Auth → Credit Check → AI API (OpenAI/Replicate) → Response
     ↓
Credit System: MySQL (Prisma) → Usage tracking → Stripe for top-ups
     ↓
Frontend: Next.js 13 App Router → Shadcn/UI → Tailwind CSS
```

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | Next.js 13 (App Router), TypeScript, Tailwind CSS, Shadcn/UI |
| **AI - Text/Code** | OpenAI GPT-4 (gpt-4, gpt-3.5-turbo) |
| **AI - Image** | OpenAI DALL-E 3 |
| **AI - Audio/Video** | Replicate API (MusicGen, Zeroscope V2) |
| **Auth** | Clerk (social login, email, JWT) |
| **Database** | MySQL + Prisma ORM |
| **Payments** | Stripe + Webhooks |
| **Rate Limiting** | Custom credit token system |
| **Deployment** | Vercel |

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/Asim-Shahani/Lumina_AI.git
cd Lumina_AI

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Fill in all required keys (see below)

# Set up the database
npx prisma db push

# Run the development server
npm run dev
```

## 🔑 Environment Variables

```env
# Clerk Auth
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/dashboard
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/dashboard

# OpenAI
OPENAI_API_KEY=

# Replicate
REPLICATE_API_TOKEN=

# Database
DATABASE_URL=

# Stripe
STRIPE_API_KEY=
STRIPE_WEBHOOK_SECRET=
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

## 💡 Key Implementation Details

### Credit Token System
- New users receive **10 free API calls** across all tools
- Each generation consumes **1 credit token**
- Pro subscription unlocks **unlimited generations**
- Credits tracked in MySQL via Prisma, checked on every API call

### Multi-Model Integration
The platform uses a **unified API gateway pattern**:
- `/api/conversation` → OpenAI Chat Completions
- `/api/image` → DALL-E 3 via OpenAI Images API
- `/api/code` → OpenAI with system prompt for code specialist role
- `/api/music` → Replicate MusicGen
- `/api/video` → Replicate Zeroscope V2

### Stripe Integration
- **Pro Plan**: $20/month unlimited access
- Webhooks handle: `checkout.session.completed`, `invoice.payment_succeeded`, `customer.subscription.deleted`
- Automatic user tier upgrade/downgrade on webhook events

## 🌐 Live Demo

Visit **[luminaai.tech](https://luminaai.tech)** to see all 5 AI tools in action.

---

<div align="center">

Built with ❤️ by [Asim Shahani](https://github.com/Asim-Shahani) | AI Engineer

⭐ Star this repo if you find it helpful!

</div>
