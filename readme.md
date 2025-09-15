# 🤖 Discord Bot - Complete Documentatie

## 📋 Inhoudsopgave
1. [Bot Overzicht](#bot-overzicht)
2. [Installatie & Setup](#installatie--setup)
3. [Startup Proces](#startup-proces)
4. [Commands Overzicht](#commands-overzicht)
5. [DevMode Systeem](#devmode-systeem)
6. [Rate Limiting & Performance](#rate-limiting--performance)
7. [Failure Protocols](#failure-protocols)
8. [Troubleshooting](#troubleshooting)
9. [Configuratie](#configuratie)
10. [Bestandsstructuur](#bestandsstructuur)
11. [Security & Permissions](#security--permissions)
12. [Maintenance & Updates](#maintenance--updates)

---

## 🎯 Bot Overzicht

### **Hoofdfuncties:**
- **Music Bot**: Spotify/YouTube integratie met playlists
- **Coinflip & Blackjack**: Gambling systeem met economy
- **XP & Levels**: Gebruiker progressie systeem  
- **Moderation**: Kick, ban, jail, warn systemen
- **Custom Commands**: Jury kan eigen commands toevoegen
- **DevMode**: Uitgebreide debugging en management tools
- **Admin Requests**: Jury voting systeem voor belangrijke beslissingen

### **Bot Specificaties:**
- **Framework**: Discord.py 2.0+
- **Python**: 3.10+ vereist
- **Database**: JSON file-based storage
- **Hosting**: Local/Server deployment
- **Uptime**: 24/7 operational capability

---

## 🚀 Installatie & Setup

### **1. Vereisten:**
```bash
Python 3.10+
pip install discord.py
pip install psutil
pip install nest_asyncio (optional)
```

### **2. Configuratie Files:**
Zorg dat de volgende bestanden bestaan:

**main.json** - Hoofd configuratie:
```json
{
    "DISCORD_TOKEN_1": "your_primary_token_here",
    "DISCORD_TOKEN_2": "your_backup_token_here", 
    "JURY_IDS": [123456789, 987654321],
    "SIGNUP_ANNOUNCE_CHANNEL_ID": 1234567890,
    "FEEDBACK_CHANNEL_ID": 1234567890,
    "START_CHANNEL_ID": 1234567890,
    "DRIVE_LINK": "https://drive.google.com/...",
    "SUGGESTIONS_CHANNEL_ID": 1234567890
}
```

**Andere Required Files:**
- `userdb.json` - User database
- `coins.json` - Economy data
- `levels_data.json` - XP/Level data
- `blackjack_stats.json` - Gambling statistics
- `custom_commands.json` - Custom commands
- `moderation_log.json` - Moderation logs

### **3. Bot Opstarten:**
```bash
python bot.py
```

**Startup Keuzes:**
1. **Token Selectie** (1 of 2)
2. **Mode Selectie**:
   - Y = 🧪 TESTMODE (DMs alleen naar 1101881866480525432)
   - N = 🚀 PRODUCTIE (DMs naar alle jury leden)

---

## 🔄 Startup Proces

### **Startup Flow:**
1. **bot.py** - Token & mode keuze + loading animaties
2. **main.py** - Discord connection + cog loading
3. **on_ready()** - Startup DMs naar jury + status display

### **Loading Animaties:**
- ⚙️ Configuratie laden
- 📦 Dependencies controleren  
- 🐍 Python versie valideren
- 🌐 Discord connectie voorbereiden
- 🎉 Bot online celebratie

### **Startup DM naar Jury:**
Alle jury leden krijgen automatisch een DM bij bot startup met:
- Timestamp van start
- Server informatie
- Uptime tracking
- Contact informatie voor problemen

---

## 📜 Commands Overzicht

### **🎵 Music Commands:**
- `!join` - Bot joins voice channel
- `!play <url>` - Play Spotify/YouTube
- `!leave` - Disconnect from voice
- `!add <url>` - Add song to playlist
- `!playlist` - Show current playlist

### **🎰 Gambling Commands:**
- `!flip <amount>` - Coinflip betting
- `!cfstats` - Coinflip statistics
- `!blackjack <bet>` - Blackjack game
- `!bjstats` - Blackjack statistics  
- `!balance` - Check coin balance
- `!baltop` - Leaderboard

### **📊 XP & Levels:**
- `!progress` - Your XP progress
- `!xpleaderboard` - XP leaderboard
- `!dailyxp` - Claim daily XP
- `!level @user` - Check user level

### **🔨 Moderation (Jury Only):**
- `!kick @user [reason]` - Kick user
- `!ban @user [reason]` - Ban user  
- `!jail @user <minutes> [reason]` - Temporary jail
- `!warn @user [reason]` - Warn user
- `!clear <amount>` - Delete messages
- `!notes @user` - View/manage user notes

### **🛠️ Management Commands:**
- `!devmode` - Toggle DevMode (Jury only)
- `!admin <request>` - Submit admin request
- `!customcmd add <name> <response>` - Add custom command
- `!help` - Show help menu
- `!info` - Bot information
- `!ping` - Check bot latency

---

## 🔧 DevMode Systeem

### **DevMode Activatie:**
- Command: `!devmode`
- Alleen voor jury leden
- Creëert privé management kanaal

### **DevMode Features:**

#### **🎛️ Control Panel:**
- ⚡ **Stress Test** - Webhook-based performance testing
- 🔧 **Cog Management** - Load/unload bot modules
- 📊 **Statistics** - Bot usage analytics
- 🗃️ **Database** - View/manage data files
- 🔄 **Restart Bot** - Safe bot restart
- ⚙️ **Config Reload** - Refresh configuration
- 🗑️ **Cleanup** - Remove old files/channels
- 📝 **Logs** - View detailed logs
- 📋 **Copy Keys** - Copy important data to clipboard
- 🚪 **Exit DevMode** - Deactivate DevMode

#### **📊 Stress Test Details:**
- **Scenario 1**: Coinflip Rush (180 commands)
- **Scenario 2**: XP Event Surge (150 commands)  
- **Scenario 3**: Raid Simulation (33 commands)
- **Scenario 4**: Blackjack Tournament (90 commands)
- **Scenario 5**: Help Spam (160 commands)
- **Total**: ~613 commands via 10 webhooks

### **DevMode Logging:**
- Alle events worden gelogd naar console (alleen tijdens DevMode)
- Discord embed logs in DevMode kanaal
- Command execution tracking
- Error monitoring

---

## ⚡ Rate Limiting & Performance

### **Discord Rate Limits:**
⚠️ **Kritieke Limieten:**

#### **Message Rate Limits:**
- **Per Channel**: 5 messages per 5 seconds
- **Per Guild**: 10.000 messages per 10 minutes  
- **DM Rate**: 1 message per second
- **Webhook Rate**: 5 messages per second per webhook

#### **API Rate Limits:**
- **REST API**: 50 requests per second
- **Gateway**: 120 events per minute
- **Slash Commands**: 3000 per application per day

#### **Webhook Limits:**
- **Per Channel**: Maximum 15 webhooks
- **Total**: 1000 webhooks per application

### **Bot Performance Optimizations:**

#### **Message Batching:**
```python
# ✅ GOED - Batch messages
messages = ["Message 1", "Message 2", "Message 3"]
embed = discord.Embed(description="\n".join(messages))
await channel.send(embed=embed)

# ❌ SLECHT - Spam messages
for msg in messages:
    await channel.send(msg)  # Rate limit risk!
```

#### **Async Operations:**
```python
# ✅ GOED - Concurrent operations
tasks = [send_dm(user) for user in users]
await asyncio.gather(*tasks, return_exceptions=True)

# ❌ SLECHT - Sequential operations  
for user in users:
    await send_dm(user)  # Slow!
```

#### **Error Handling:**
```python
try:
    await channel.send(message)
except discord.HTTPException as e:
    if e.status == 429:  # Rate limited
        await asyncio.sleep(e.retry_after)
        await channel.send(message)
```

### **Performance Monitoring:**
- Stress test meet commands/second
- Memory usage tracking via psutil
- Response time monitoring
- Error rate tracking

---

## 🚨 Failure Protocols

### **Bot Crash Recovery:**

#### **1. Automatic Restart (Signal Handler):**
```python
# SIGTERM/SIGINT handling in main.py
async def shutdown_handler():
    # Send shutdown DMs to jury
    # Cleanup resources
    # Graceful shutdown
```

#### **2. Crash Detection:**
- Process monitoring via systemd/pm2
- Health check endpoints
- Watchdog timers
- Auto-restart on failure

#### **3. Data Recovery:**
```bash
# Backup strategy
cp userdb.json userdb.json.backup
cp coins.json coins.json.backup
cp levels_data.json levels_data.backup
```

### **Network Failure Recovery:**

#### **Discord Gateway Reconnection:**
- Automatic reconnection via discord.py
- Exponential backoff on failures
- Status monitoring in DevMode

#### **API Failure Handling:**
```python
@bot.event
async def on_error(event, *args, **kwargs):
    # Log error to DevMode
    # Send notification to jury
    # Attempt graceful recovery
```

### **Database Corruption Recovery:**

#### **JSON File Validation:**
```python
def validate_json_file(filepath):
    try:
        with open(filepath, 'r') as f:
            json.load(f)
        return True
    except:
        # Restore from backup
        restore_backup(filepath)
        return False
```

#### **Backup Strategy:**
- Hourly automated backups
- Version control for config files
- Corruption detection on startup
- Rollback procedures

### **Memory Leak Prevention:**
```python
# Periodic cleanup
async def cleanup_task():
    while True:
        await asyncio.sleep(3600)  # Every hour
        gc.collect()  # Force garbage collection
        # Clean old cache entries
        # Monitor memory usage
```

---

## 🔍 Troubleshooting

### **Common Issues:**

#### **1. Bot Won't Start:**
```bash
# Check Python version
python --version  # Must be 3.10+

# Check dependencies
pip list | grep discord

# Check file permissions
ls -la *.json

# Validate JSON syntax
python -m json.tool main.json
```

#### **2. Commands Not Working:**
- Verify bot has required permissions
- Check command cooldowns
- Validate user permissions (jury/admin)
- Review error logs in console

#### **3. Database Issues:**
```python
# Reset database (DANGER!)
python -c "import json; json.dump({}, open('userdb.json', 'w'))"

# Validate database integrity
python -c "
import json
try:
    with open('userdb.json') as f:
        data = json.load(f)
    print('✅ Database valid')
except:
    print('❌ Database corrupted')
"
```

#### **4. Memory Issues:**
```python
# Check memory usage
import psutil
print(f"Memory: {psutil.virtual_memory().percent}%")

# Memory cleanup
import gc
gc.collect()
```

#### **5. Permission Errors:**
- Check bot role hierarchy
- Verify channel permissions
- Review jury ID list in config
- Check Discord developer portal settings

### **Debug Mode Activation:**
```python
# Enable debug logging
import logging
logging.basicConfig(level=logging.DEBUG)
```

### **Emergency Procedures:**

#### **Force Shutdown:**
```bash
# Kill bot process
pkill -f "python bot.py"

# Or via PID
ps aux | grep bot.py
kill -9 <PID>
```

#### **Config Reset:**
```bash
# Backup current config
cp main.json main.json.emergency

# Reset to defaults (create new main.json)
```

#### **Complete Reset:**
```bash
# WARNING: This deletes ALL data!
rm userdb.json coins.json levels_data.json
python bot.py  # Will recreate empty databases
```

---

## ⚙️ Configuratie

### **main.json Parameters:**

#### **Required Settings:**
```json
{
    "DISCORD_TOKEN_1": "Primary bot token",
    "DISCORD_TOKEN_2": "Backup bot token", 
    "JURY_IDS": [1234567890, 9876543210],
    "SIGNUP_ANNOUNCE_CHANNEL_ID": 1234567890,
    "FEEDBACK_CHANNEL_ID": 1234567890,
    "START_CHANNEL_ID": 1234567890,
    "DRIVE_LINK": "https://drive.google.com/drive/...",
    "SUGGESTIONS_CHANNEL_ID": 1234567890
}
```

#### **Optional Settings:**
```json
{
    "DEBUG_MODE": false,
    "MAX_COIN_BET": 1000,
    "DAILY_XP_AMOUNT": 50,
    "LEVEL_XP_MULTIPLIER": 100,
    "BLACKJACK_HOUSE_EDGE": 0.02
}
```

### **Environment Variables:**
- `BOT_TOKEN_CHOICE` - "1" or "2" (set by bot.py)
- `BOT_TESTMODE` - "Y" or "N" (set by bot.py)

### **File Permissions:**
```bash
chmod 600 *.json    # Config files - read/write owner only
chmod 755 *.py      # Python files - executable
chmod 644 *.md      # Documentation - readable
```

---

## 📁 Bestandsstructuur

```
bot-project/
├── 🐍 Core Files
│   ├── bot.py              # Startup script with loading bars
│   ├── main.py             # Main bot logic & events
│   └── requirements.txt    # Python dependencies
│
├── 🔧 Bot Modules (Cogs)
│   ├── devmode.py          # DevMode system & stress testing
│   ├── general.py          # General commands & admin requests
│   ├── moderate.py         # Moderation commands
│   ├── levels.py           # XP & leveling system
│   ├── coinflip.py         # Coinflip gambling
│   ├── blackjack.py        # Blackjack gambling
│   ├── music.py            # Music bot functionality
│   ├── reactionrole.py     # Reaction role system
│   ├── customcommands.py   # Custom command system
│   ├── echo.py             # Echo/repeat commands
│   └── songwars.py         # Song competition system
│
├── 🗄️ Database Files
│   ├── main.json           # Main configuration
│   ├── userdb.json         # User database
│   ├── coins.json          # Economy/currency data
│   ├── levels_data.json    # XP/levels data  
│   ├── blackjack_stats.json # Gambling statistics
│   ├── custom_commands.json # Custom commands data
│   ├── moderation_log.json  # Moderation actions log
│   ├── moderation_history.json # Historical mod data
│   ├── moderator_notes.json # User notes by mods
│   ├── jailed_roles.json   # Jail system data
│   └── reaction_role_msg_id.json # Reaction roles
│
├── 🔐 Security Files  
│   ├── admin_dashboard_private.pem # Private key
│   ├── admin_dashboard_public.pem  # Public key
│   ├── admin_api_auth.py          # API authentication
│   └── generate_admin_keys.py     # Key generation
│
├── 🌐 Web Dashboard
│   └── admin_dashboard.py         # Web interface
│
├── 📚 Documentation
│   ├── BOT_DOCUMENTATION.md       # This file
│   ├── COMMANDS.md                # Command reference
│   └── CHANGELOG.md               # Version history
│
└── 🗂️ Cache & Logs
    └── __pycache__/               # Python bytecode cache
```

### **File Size Guidelines:**
- **Config files**: < 10 KB each
- **Database files**: < 1 MB each (monitor growth)
- **Log files**: Rotate when > 10 MB
- **Cache files**: Auto-cleanup older than 7 days

---

## 🔒 Security & Permissions

### **Discord Permissions Required:**

#### **Bot Permissions:**
```
REQUIRED:
✅ Send Messages
✅ Read Message History  
✅ Use External Emojis
✅ Add Reactions
✅ Manage Messages (for moderation)
✅ Manage Roles (for jail system)
✅ Kick Members (for moderation)
✅ Ban Members (for moderation)
✅ Connect (for music)
✅ Speak (for music)
✅ Manage Webhooks (for stress testing)

OPTIONAL:
🔶 Administrator (for full functionality)
```

#### **Channel Permissions:**
```json
{
    "DevMode Channel": {
        "view_channel": "jury_only",
        "send_messages": "bot_only",
        "manage_webhooks": "bot_only"
    },
    "General Channels": {
        "view_channel": "everyone", 
        "send_messages": "everyone",
        "use_slash_commands": "everyone"
    }
}
```

### **API Security:**

#### **Token Management:**
- Store tokens in `main.json` (never commit to git)
- Use environment variables for production
- Rotate tokens regularly (monthly)
- Monitor token usage in Discord developer portal

#### **Rate Limit Protection:**
```python
# Built-in rate limit handling
@commands.cooldown(1, 5, commands.BucketType.user)
async def expensive_command(ctx):
    # Command logic here
    pass
```

#### **Input Validation:**
```python
# Sanitize user input
import re

def sanitize_input(text):
    # Remove dangerous characters
    return re.sub(r'[<>@#&]', '', text)[:100]
```

### **Data Protection:**

#### **Sensitive Data Encryption:**
```python
# For storing sensitive user data
from cryptography.fernet import Fernet

key = Fernet.generate_key()
cipher = Fernet(key)

encrypted_data = cipher.encrypt(b"sensitive_data")
decrypted_data = cipher.decrypt(encrypted_data)
```

#### **Backup Encryption:**
```bash
# Encrypt backups
gpg --symmetric --cipher-algo AES256 userdb.json
# Creates userdb.json.gpg

# Decrypt when needed
gpg --decrypt userdb.json.gpg > userdb.json
```

---

## 🔄 Maintenance & Updates

### **Regular Maintenance Tasks:**

#### **Daily:**
- Monitor bot status (uptime, errors)
- Check memory usage
- Review error logs
- Verify backup integrity

#### **Weekly:**
- Database cleanup (old entries)
- Log file rotation
- Performance analysis
- Security audit

#### **Monthly:**
- Update dependencies
- Rotate access tokens
- Full system backup
- Performance optimization review

### **Update Procedure:**

#### **1. Pre-Update Checklist:**
```bash
# Create full backup
cp -r bot-project/ bot-project-backup-$(date +%Y%m%d)/

# Test configuration
python -c "import json; json.load(open('main.json'))"

# Check disk space
df -h

# Verify Python version
python --version
```

#### **2. Update Dependencies:**
```bash
# Update Python packages
pip install --upgrade discord.py
pip install --upgrade -r requirements.txt

# Check for breaking changes
python bot.py --dry-run  # If implemented
```

#### **3. Deploy Update:**
```bash
# Graceful shutdown
kill -TERM $(pgrep -f "python bot.py")

# Deploy new code
git pull origin main  # If using git

# Start bot
python bot.py
```

#### **4. Post-Update Verification:**
- Bot starts successfully
- All commands work
- Database integrity maintained
- Performance metrics normal
- Error logs clean

### **Rollback Procedure:**
```bash
# If update fails, rollback
pkill -f "python bot.py"
rm -rf bot-project/
mv bot-project-backup-YYYYMMDD/ bot-project/
cd bot-project/
python bot.py
```

### **Performance Monitoring:**

#### **Key Metrics:**
- **Response Time**: < 2 seconds per command
- **Memory Usage**: < 500 MB RAM
- **CPU Usage**: < 30% average
- **Error Rate**: < 1% of commands
- **Uptime**: > 99.5%

#### **Monitoring Tools:**
```python
# Built-in monitoring via DevMode
# Stress test results
# Memory usage tracking
# Command execution statistics
```

#### **Alerting:**
- High memory usage (> 80%)
- High error rate (> 5%)
- Bot offline > 5 minutes
- Database corruption detected

---

## 📞 Support & Emergency Contacts

### **Emergency Procedures:**
1. **Bot Down**: Check process, restart if needed
2. **Database Corruption**: Restore from backup
3. **High Resource Usage**: DevMode → Restart Bot
4. **Security Breach**: Rotate tokens, audit logs
5. **Discord API Issues**: Monitor Discord status page

### **Contact Information:**
- **Primary Admin**: astro16 (Discord)
- **Technical Issues**: Use `!admin` command
- **Emergency**: Direct DM to jury members

### **Useful Resources:**
- **Discord.py Documentation**: https://discordpy.readthedocs.io/
- **Discord Developer Portal**: https://discord.com/developers/
- **Discord API Status**: https://discordstatus.com/
- **Python Documentation**: https://docs.python.org/

---

## 📝 Change Log

### **Version History:**
- **v1.0**: Initial bot creation
- **v1.1**: Added DevMode system
- **v1.2**: Webhook stress testing
- **v1.3**: Testmode functionality
- **v1.4**: Loading animations & improved UX
- **v1.5**: Comprehensive documentation (this file)

### **Known Issues:**
- Emoji encoding in some terminal environments
- Rate limiting during high-volume stress tests
- Memory growth during extended uptime (>7 days)

### **Planned Features:**
- Web dashboard improvements
- Advanced analytics
- Automated backup system
- Multi-server support

---

*📅 Last Updated: September 15, 2025*  
*🔄 Next Review: October 15, 2025*

**⚠️ Important**: This documentation should be reviewed and updated monthly to ensure accuracy and completeness.
