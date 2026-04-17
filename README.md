# 🍬 Candy Blast — Match-3 Puzzle Game

A fully-featured **Candy Crush-style match-3 puzzle game** built with React (web) and Expo (mobile). Blast candies, chain combos, unlock special powers, and compete globally on the leaderboard!

---

## 🎮 Live Demo

> **Web Version:** [Play Candy Blast](https://candyblast.replit.app/candy-web/)
> **Mobile:** Scan QR in Expo Go (see below)

---

## ✨ Features

### Gameplay
- **8×8 grid** with 6 candy types
- **20 progressive levels** — from *First Bite* (500 pts) to *Ultimate Blast* (60K pts)
- **Special candies** created by matching 4+ in a row:
  - 🔵 **Striped** (4-match) — clears entire row or column
  - 💚 **Wrapped** (L/T-shape) — 5×5 area blast
  - 🌈 **Rainbow** (5-match) — clears all candies of one color
- **Combo chains** — consecutive matches multiply your score by up to 5×
- **Floating score numbers** pop up on every match
- **Shuffle detection** — board auto-shuffles if no moves left
- **Pause / Resume** mid-game

### Progression
- 20 levels with unique names, badge emojis, and increasing targets
- Star rating system (1–3 stars) based on moves efficiency
- Unlock the next level on completion
- Local high score saved in browser (`localStorage`)

### Leaderboard
- **Global leaderboard** powered by PostgreSQL
- Submit your name and score after any game
- Top 20 players ranked with 🥇🥈🥉 medals
- Shows level reached and time ago

### Monetization (Ads)
- Google AdSense integration ready
- Ad placements: Home screen, Level Complete, Game Over
- Easy plug-in — just add your Publisher ID (see setup below)

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Web Frontend | React 19, Vite 7, TypeScript |
| Mobile | Expo (React Native), Expo Router |
| Animations | Framer Motion (web), React Native Reanimated (mobile) |
| Styling | Tailwind CSS v4, CSS custom properties |
| Backend | Express.js (Node), TypeScript |
| Database | PostgreSQL + Drizzle ORM |
| Monorepo | pnpm workspaces |

---

## 📁 Project Structure

```
candy-blast/
├── artifacts/
│   ├── candy-web/          # React + Vite web game
│   │   ├── src/
│   │   │   ├── components/ # UI components (GameBoard, CandyCell, Leaderboard…)
│   │   │   ├── context/    # GameContext (state management)
│   │   │   ├── lib/        # gameEngine.ts, gameConfig.ts, api.ts
│   │   │   └── App.tsx
│   │   └── vite.config.ts
│   ├── candy-crush/        # Expo mobile app
│   │   ├── app/            # Expo Router screens
│   │   ├── components/     # Native components
│   │   └── context/        # Mobile game context
│   └── api-server/         # Express REST API
│       └── src/
│           ├── routes/     # leaderboard.ts, health.ts
│           └── lib/        # db.ts
└── lib/
    └── db/                 # Drizzle schema + migrations
        └── src/schema/     # leaderboard.ts
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js 20+
- pnpm 9+
- PostgreSQL (or use Replit's built-in DB)

### Installation

```bash
# Clone the repo
git clone https://github.com/yourusername/candy-blast.git
cd candy-blast

# Install all dependencies
pnpm install
```

### Environment Variables

Create a `.env` file in the root (or set these in your hosting platform):

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/candyblast

# Optional: Google AdSense
VITE_ADSENSE_CLIENT_ID=ca-pub-XXXXXXXXXXXXXXXX
```

### Database Setup

```bash
# Push schema to database
pnpm --filter @workspace/db run push
```

### Run Locally

```bash
# Start the API server (port 8080)
pnpm --filter @workspace/api-server run dev

# Start the web game (port 23820 → /candy-web/)
pnpm --filter @workspace/candy-web run dev

# Start the mobile app
pnpm --filter @workspace/candy-crush run dev
```

---

## 📱 Mobile App (Expo)

1. Install **Expo Go** on your phone ([iOS](https://apps.apple.com/app/expo-go/id982107779) / [Android](https://play.google.com/store/apps/details?id=host.exp.exponent))
2. Run `pnpm --filter @workspace/candy-crush run dev`
3. Scan the QR code shown in the terminal

---

## 🏆 Leaderboard API

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/leaderboard` | Fetch top 20 scores |
| `POST` | `/api/leaderboard` | Submit a new score |

### POST `/api/leaderboard`

```json
{
  "playerName": "CandyKing",
  "score": 15000,
  "level": 7
}
```

---

## 💰 Ads Setup (Google AdSense)

1. Create a [Google AdSense](https://adsense.google.com) account
2. Add your site and get your **Publisher ID** (`ca-pub-XXXXXXXXXXXXXXXX`)
3. Set the env variable: `VITE_ADSENSE_CLIENT_ID=ca-pub-XXXXXXXXXXXXXXXX`
4. Uncomment the AdSense script in `artifacts/candy-web/index.html`
5. Replace slot IDs in the `<AdBanner slot="...">` components with your real ad unit IDs from the AdSense dashboard

**Ad Placements:**
- Home screen — horizontal banner at bottom
- Level Complete screen — rectangle between stats and next level
- Game Over screen — rectangle above tips

**Alternative Ad Networks:** Media.net, PropellerAds, AdMaven

---

## 🎨 Candy Theme

| Token | Value | Usage |
|---|---|---|
| Background | `#0d0020 → #1a0533 → #2d0f50` | Deep purple gradient |
| Primary | `#FF6B6B` | Buttons, combos |
| Accent | `#FFD700` | Stars, high score |
| Purple | `#9B59B6` | Progress, borders |

---

## 🗺️ Roadmap

- [ ] Power-ups (extra moves, color bomb)
- [ ] Daily challenge mode
- [ ] Sound effects & music
- [ ] Friend challenges via share link
- [ ] In-app purchases (extra moves)
- [ ] Persistent level progress per player

---

## 📄 License

MIT © 2026 — Feel free to fork, modify, and ship your own candy game!

---

<p align="center">Made with 🍬 and lots of sugar</p>
