# 🎯 Render Deployment Guide - FREE UNLIMITED Hosting

## ✅ Why Render is Perfect for Your Bot

- **✅ TRULY FREE**: 750 hours/month (enough for 24/7 with monthly restart)
- **✅ No Credit Card Required**: Unlike Heroku
- **✅ Always-On Option**: With simple keep-alive setup
- **✅ GitHub Integration**: Automatic deployments
- **✅ Free Database**: PostgreSQL included
- **✅ Easy Setup**: Web interface deployment

## 🚀 Step-by-Step Deployment

### Step 1: Prepare Your Repository (Already Done!)

Your bot now includes:
- ✅ Flask web server to prevent sleeping
- ✅ `render.yaml` configuration file
- ✅ Updated `requirements.txt` with Flask
- ✅ Environment variable support

### Step 2: Deploy to Render

1. **Sign Up for Render**
   - Go to [render.com](https://render.com)
   - Sign up with your GitHub account (FREE - no credit card needed)

2. **Create New Web Service**
   - Click "New +" → "Web Service"
   - Connect your GitHub repository
   - Select your bot repository

3. **Configure Service**
   - **Name**: `telegram-scheduler-bot`
   - **Environment**: `Python 3`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `python bot.py`
   - **Instance Type**: `Free` (0.1 CPU, 512 MB RAM)

4. **Set Environment Variables**
   In the "Environment" tab, add:
   ```
   BOT_TOKEN=your_telegram_bot_token_here
   DATABASE_PATH=bot_data.db
   DEFAULT_TIMEZONE=UTC
   LOG_LEVEL=INFO
   PORT=10000
   ```

5. **Deploy**
   - Click "Create Web Service"
   - Render will automatically build and deploy your bot
   - Wait for deployment to complete (usually 2-3 minutes)

### Step 3: Get Your Bot Token

If you don't have a bot token:
1. Message `@BotFather` on Telegram
2. Send `/newbot`
3. Follow prompts to create your bot
4. Copy the token and add it to Render environment variables

### Step 4: Set Up Keep-Alive (Prevent Sleeping)

**Option A: UptimeRobot (Recommended)**
1. Sign up at [uptimerobot.com](https://uptimerobot.com) (FREE)
2. Add new monitor:
   - **Type**: HTTP(s)
   - **URL**: Your Render app URL (e.g., `https://telegram-scheduler-bot.onrender.com`)
   - **Interval**: 5 minutes
3. This will ping your bot every 5 minutes to keep it awake

**Option B: Cron-job.org**
1. Sign up at [cron-job.org](https://cron-job.org) (FREE)
2. Create new cron job:
   - **URL**: Your Render app URL + `/ping`
   - **Interval**: Every 5 minutes

### Step 5: Test Your Deployment

1. **Check Logs**
   - In Render dashboard, go to "Logs" tab
   - Look for: "Starting Telegram Scheduler Bot..."
   - Ensure no errors appear

2. **Test Web Server**
   - Visit your Render app URL
   - Should see: "🤖 Telegram Scheduler Bot is running!"

3. **Test Bot**
   - Add your bot to a Telegram group
   - Send `/start` command
   - Try: `/setschedule 14:30 Test message`

## 🔧 Configuration Details

### Environment Variables

| Variable | Required | Description | Example |
|----------|----------|-------------|---------|
| `BOT_TOKEN` | ✅ | Telegram bot token | `123456789:ABCdef...` |
| `DATABASE_PATH` | ✅ | SQLite database path | `bot_data.db` |
| `DEFAULT_TIMEZONE` | ✅ | Default timezone | `UTC` |
| `LOG_LEVEL` | ✅ | Logging level | `INFO` |
| `PORT` | ✅ | Web server port | `10000` |

### Web Endpoints

Your bot exposes these endpoints:
- `/` - Status page
- `/health` - Health check (JSON)
- `/ping` - Simple ping response

## 📊 Free Tier Limits

- **Hours**: 750 hours/month (31 days × 24 hours = 744 hours)
- **CPU**: 0.1 CPU units
- **Memory**: 512 MB RAM
- **Bandwidth**: 100 GB/month
- **Build Time**: 500 minutes/month

## 🛠️ Troubleshooting

### Common Issues:

1. **Bot not responding**
   ```
   Check Render logs for errors
   Verify BOT_TOKEN is correct
   Ensure bot has permissions in group
   ```

2. **Service sleeping**
   ```
   Set up UptimeRobot monitoring
   Check ping frequency (every 5 minutes)
   Verify web server is running on correct port
   ```

3. **Database errors**
   ```
   Check DATABASE_PATH environment variable
   Ensure file permissions are correct
   Look for SQLite lock errors in logs
   ```

4. **Build failures**
   ```
   Check requirements.txt syntax
   Verify Python version compatibility
   Look at build logs for specific errors
   ```

### Debug Commands:

Check if web server is working:
```bash
curl https://your-app-name.onrender.com/health
```

## 🔄 Updating Your Bot

1. Make changes to your code locally
2. Test: `python test_bot.py`
3. Commit and push to GitHub
4. Render automatically redeploys

## 💾 Database Backup

**Important**: Render's free tier has ephemeral storage
- Database resets on each deployment
- For persistent data, consider upgrading to paid plan
- Or use external database (PostgreSQL free tier)

## 📈 Monitoring

### Render Dashboard:
- **Logs**: Real-time application logs
- **Metrics**: CPU, memory usage
- **Events**: Deployment history
- **Settings**: Environment variables

### UptimeRobot Dashboard:
- **Uptime**: Service availability
- **Response Time**: Performance metrics
- **Alerts**: Email notifications for downtime

## 🎉 Success Checklist

Your deployment is successful when:
- ✅ Render shows "Live" status
- ✅ Web endpoint returns bot status
- ✅ Bot responds to `/start` in Telegram
- ✅ Scheduled messages work correctly
- ✅ UptimeRobot shows 100% uptime

## 💰 Cost Breakdown

**Render Free Tier**: $0/month
- 750 hours (enough for 24/7 with monthly restart)
- 512 MB RAM, 0.1 CPU
- 100 GB bandwidth

**UptimeRobot**: $0/month
- 50 monitors
- 5-minute intervals
- Email alerts

**Total Cost**: **$0/month** 🎉

## 🆘 Support

- **Render Docs**: [render.com/docs](https://render.com/docs)
- **Render Community**: [community.render.com](https://community.render.com)
- **Telegram Bot API**: [core.telegram.org/bots](https://core.telegram.org/bots)

---

## 🚀 Ready to Deploy!

Your Telegram Scheduler Bot is now fully configured for FREE unlimited hosting on Render!

**Next Steps:**
1. Sign up for Render
2. Deploy your repository
3. Set environment variables
4. Set up UptimeRobot monitoring
5. Test your bot

**Happy Scheduling! 🤖✨**