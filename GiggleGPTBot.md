# 🤖 GiggleGPTBot - AI Telegram Bot

Smart Telegram bot with AI-powered humor, user statistics, and automated scheduling built on n8n.

## ✨ Features

- **AI Commands**: `/joke`, `/inspire`, `/random` - context-aware responses
- **Smart Mentions**: `@GiggleGPTBot` for personalized replies
- **User Analytics**: `/stats` and `/top` for engagement tracking
- **Auto Scheduling**: Hourly posts for multiple channels
- **Witty Personality**: Elegant humor with cultural references

## 🚀 Quick Setup

1. **Prerequisites**
   - n8n instance
   - PostgreSQL database (Supabase recommended)
   - OpenRouter API key
   - Telegram bot token

2. **Install**
   - Import workflow JSON into n8n
   - Configure credentials (Telegram, PostgreSQL, OpenRouter)
   - Run workflow - database tables auto-created

3. **Configure Bot**
   ```
   /setcommands in @BotFather:
   joke - 😄 Funny joke
   inspire - 💪 Motivation  
   random - 🎲 Random phrase
   stats - 📊 Your statistics
   top - 🏆 Top users
   help - ❓ Help
   ```

## 📋 Commands

| Command | Description |
|---------|-------------|
| `/joke` | AI-generated humor |
| `/inspire` | Motivational quotes |
| `/random` | Surprise content |
| `/stats` | Personal activity stats |
| `/top` | Community leaderboard |
| `@GiggleGPTBot [text]` | Contextual response |

## ⏰ Scheduled Posts

Add automated content:
```sql
INSERT INTO scheduled_posts (chat_id, post_type, scheduled_time) VALUES
(-1001234567890, 'morning_joke', '09:00:00');
```

**Content Types**: `morning_joke`, `daily_motivation`, `random_wisdom`

## 🎯 Use Cases

- **Community Engagement**: Keep channels active with humor
- **Team Communication**: Workplace entertainment and motivation  
- **Content Automation**: Regular posts without manual work
- **Analytics**: Track user activity and engagement

## 🔧 Architecture

```
Telegram → n8n Workflow → PostgreSQL Database
                ↓
            OpenRouter AI → Response Generation
```

**Key Components:**
- Message logging and user statistics
- Command parsing and routing
- AI response generation
- Scheduled content posting

## 📊 Database

Auto-created tables:
- `user_messages` - Chat history
- `user_stats` - Activity tracking
- `scheduled_posts` - Automated content
- `bot_responses` - Response history

## 🚀 Deployment

**Recommended Stack:**
- n8n Cloud or self-hosted
- Supabase (free PostgreSQL)
- OpenRouter (cost-effective AI)

**Cost**: ~$5-15/month depending on usage

## 📄 License

MIT License

---

*Making communities more engaging with AI-powered humor* 🎭
