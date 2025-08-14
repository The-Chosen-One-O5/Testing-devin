# 🚂 Railway Deployment Guide for Telegram Scheduler Bot

## Prerequisites
- GitHub account
- Railway account (free at railway.app)
- Your Telegram bot token

## Step-by-Step Deployment

### 1. Prepare Your Repository

Your repository now includes all necessary files:
- ✅ `railway.toml` - Railway configuration
- ✅ `Procfile` - Alternative process definition
- ✅ `.gitignore` - Excludes sensitive files
- ✅ `requirements.txt` - Python dependencies
- ✅ All bot source code

### 2. Commit and Push to GitHub

```bash
# Add all files (excluding those in .gitignore)
git add .

# Commit changes
git commit -m "Add Railway deployment configuration"

# Push to GitHub
git push origin main
```

### 3. Deploy to Railway

1. **Sign up for Railway**
   - Go to [railway.app](https://railway.app)
   - Sign up with your GitHub account

2. **Create New Project**
   - Click "New Project"
   - Select "Deploy from GitHub repo"
   - Choose your bot repository

3. **Configure Environment Variables**
   - In Railway dashboard, go to your project
   - Click on "Variables" tab
   - Add these environment variables:
     ```
     BOT_TOKEN=your_telegram_bot_token_here
     DATABASE_PATH=bot_data.db
     DEFAULT_TIMEZONE=UTC
     LOG_LEVEL=INFO
     ```

4. **Deploy**
   - Railway will automatically detect Python and install dependencies
   - The bot will start using the `railway.toml` configuration
   - Monitor the deployment in the "Deployments" tab

### 4. Verify Deployment

1. **Check Logs**
   - In Railway dashboard, click on "Logs"
   - Look for: "Starting Telegram Scheduler Bot..."
   - Ensure no errors appear

2. **Test Bot**
   - Add your bot to a Telegram group
   - Send `/start` command
   - Try setting a schedule: `/setschedule 14:30 Test message`

### 5. Environment Variables Explained

| Variable | Description | Example |
|----------|-------------|---------|
| `BOT_TOKEN` | Your Telegram bot token from BotFather | `123456789:ABCdef...` |
| `DATABASE_PATH` | SQLite database file path | `bot_data.db` |
| `DEFAULT_TIMEZONE` | Default timezone for groups | `UTC` |
| `LOG_LEVEL` | Logging verbosity | `INFO` |

### 6. Monitoring and Maintenance

**Railway Dashboard Features:**
- **Logs**: Real-time application logs
- **Metrics**: CPU, memory, and network usage
- **Deployments**: History of all deployments
- **Settings**: Environment variables and configuration

**Important Notes:**
- Railway free tier includes $5/month in credits
- Typical bot usage: $1-3/month
- Database persists between deployments
- Automatic deployments on git push

### 7. Troubleshooting

**Common Issues:**

1. **Bot not responding**
   ```
   Check logs for "BOT_TOKEN not found" error
   Verify environment variables are set correctly
   ```

2. **Database errors**
   ```
   Ensure DATABASE_PATH is set to "bot_data.db"
   Check file permissions in logs
   ```

3. **Timezone issues**
   ```
   Verify DEFAULT_TIMEZONE is valid (e.g., "UTC", "America/New_York")
   Check group timezone settings with /status command
   ```

4. **Memory/CPU limits**
   ```
   Monitor usage in Railway dashboard
   Upgrade plan if needed
   ```

### 8. Updating Your Bot

1. Make changes to your code locally
2. Test changes: `python test_bot.py`
3. Commit and push to GitHub
4. Railway automatically redeploys

### 9. Backup Strategy

**Database Backup:**
- Railway provides persistent storage
- Consider periodic manual backups
- Download database file from Railway dashboard if needed

**Code Backup:**
- GitHub serves as your code backup
- Tag important releases: `git tag v1.0.0`

### 10. Scaling and Costs

**Free Tier Limits:**
- $5/month in credits
- Sufficient for small to medium bots
- Monitor usage in dashboard

**Upgrade Options:**
- Pro plan: $20/month
- Unlimited usage
- Priority support

## Alternative Platforms

If Railway doesn't work for you:

1. **Render** - Free tier with 750 hours/month
2. **Fly.io** - Free allowances for small apps
3. **Heroku** - Paid plans available
4. **DigitalOcean App Platform** - $5/month minimum

## Support

- Railway Documentation: [docs.railway.app](https://docs.railway.app)
- Railway Discord: Community support
- Bot Issues: Check logs and test locally first

---

**Your bot is now ready for 24/7 operation! 🚀**

Happy scheduling! 🤖✨