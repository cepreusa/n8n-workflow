# GiggleGPTBot — Witty Telegram Bot with AI & Postgres

## 📝 Overview

GiggleGPTBot is a witty Telegram bot built with **n8n**, **OpenRouter**, and **Postgres**.
It delivers short jokes, motivational one-liners, and playful roasts, responds to mentions, and posts scheduled witty content.
The workflow also tracks user activity and provides lightweight statistics and leaderboards.

---

## ✨ Features

* 🤖 **AI-powered humor engine** — replies with jokes, motivation, random witty lines, or sarcastic roasts.
* 💬 **Command support** — `/joke`, `/inspire`, `/random`, `/roast`, `/help`, `/stats`, `/top`.
* 🎯 **Mention detection** — replies when users tag `@GiggleGPTBot`.
* ⏰ **Scheduled posts** — morning jokes, daily motivation, and random wisdom at configured times.
* 📊 **User analytics** — counts messages, commands, reactions, and generates leaderboards.
* 🗄️ **Postgres persistence** — robust schema with tables for messages, responses, stats, and schedules.

---

## 🛠️ How It Works

1. **Triggers**

   * `Telegram Trigger` — receives all messages and commands from a chat.
   * `Schedule Trigger` — runs hourly to check for planned posts.

2. **Processing**

   * `Switch` routes commands (`/joke`, `/inspire`, `/random`, `/roast`, `/help`, `/stats`, `/top`).
   * `Chat history` fetches the latest context.
   * `Mention Analysis` determines if the bot was mentioned.
   * `Generating an information response` builds replies for `/help`, `/stats`, `/top`.
   * AI nodes (`AI response to command`, `AI response to mention`, `AI post generation`) craft witty content via **OpenRouter**.

3. **Persistence**

   * `Init Database` ensures tables exist (`user_messages`, `bot_responses`, `bot_commands`, `message_reactions`, `scheduled_posts`, `user_stats`).
   * Logging nodes update stats and store every bot/user interaction.

4. **Delivery**

   * Replies are sent back via `Telegram Send` nodes (`Send AI response`, `Send info reply`, `Reply to Mention`, `Submit scheduled post`).

---

## ⚙️ Setup Instructions

1. **Create a Telegram Bot** with [@BotFather](https://t.me/BotFather) and get your API token.
2. **Add credentials** in n8n:

   * `Telegram API` (your bot token)
   * `OpenRouter` (API key from [openrouter.ai](https://openrouter.ai/))
   * `Postgres` (use your DB, Supabase works well).
3. **Run the `Init Database` node once** to create all required tables.
4. **(Optional) Seed schedule** with the `Adding a schedule` node — it inserts:

   * Morning joke at 06:00
   * Daily motivation at 09:00
   * Random wisdom at 17:00
     (Adjust `chat_id` to your group/channel ID.)
5. **Activate workflow** and connect Telegram Webhook or Polling.

---

## 📊 Database Schema

* **user\_messages** — stores user chat messages.
* **bot\_responses** — saves bot replies.
* **bot\_commands** — logs command usage.
* **message\_reactions** — tracks reactions.
* **scheduled\_posts** — holds scheduled jokes/wisdom/motivation.
* **user\_stats** — aggregates per-user message/command counts and activity.

---

## 🔑 Example Commands

* `/joke` → witty one-liner with light irony.
* `/inspire` → short motivational phrase.
* `/random` → unexpected witty remark.
* `/roast` → sarcastic roast (no offensive targeting).
* `/stats` → shows your personal stats.
* `/top` → displays leaderboard.
* `/help` → lists available commands.
* `@GiggleGPTBot` + message → bot replies in context.

---

## 🚀 Customization Ideas

* Add new command categories (`/quote`, `/fact`, `/news`).
* Expand analytics with reaction counts or streaks.
* Localize prompts into multiple languages.
* Adjust CRON schedules for posts.

---

## ✅ Requirements

* Telegram Bot token
* OpenRouter API key
* Postgres database

---

📦 Import this workflow, configure credentials, run the DB initializer — and your witty AI-powered Telegram companion is ready!
