# 🔒 Discord Moderation Bot

A simple Discord bot for **moderation** tasks such as banning, kicking, and timing out members.  
This bot is designed to help administrators and moderators manage their servers easily.

---

## ✨ Features
- **/ban** → Ban a user permanently from the server by ID.
- **/kick** → Kick a user from the server by ID.
- **/timeout** → Timeout (mute) a user for minutes, hours, or days.  
  - If no time is specified, the default timeout is **1 hour**.

---

## ⚙️ Requirements
- Python 3.9+
- Discord.py 2.0+ (`pip install -U discord.py`)

---

## 🚀 Setup
1. Clone or download this repository.
2. Install dependencies:
   ```bash
   pip install -U discord.py
   ```
3. Create a file named `main.py` (or update your existing bot file) and add:
   ```python
   import discord
   from discord.ext import commands
   from moderation import setup_ban_system  # if your commands are in moderation.py

   intents = discord.Intents.default()
   intents.members = True
   intents.guilds = True
   intents.message_content = True

   bot = commands.Bot(command_prefix="!", intents=intents)

   @bot.event
   async def on_ready():
       print(f"✅ Logged in as {bot.user}")
       await bot.tree.sync()

   setup_ban_system(bot)  # load moderation commands

   bot.run("YOUR_BOT_TOKEN")
   ```
4. Replace `YOUR_BOT_TOKEN` with your actual Discord bot token.

---

## 📌 Usage

### 🔨 Ban
Ban a user by ID:
```
/ban user_id:123456789012345678 reason:Spamming
```
The user will be permanently banned from the server.

---

### 👢 Kick
Kick a user by ID:
```
/kick user_id:123456789012345678 reason:Rule violation
```
The user will be removed from the server but can rejoin with an invite.

---

### ⏰ Timeout
Timeout (mute) a user:
```
/timeout user_id:123456789012345678 minutes:30 reason:Spamming
```

Options:
- `minutes` → Timeout in minutes
- `hours` → Timeout in hours
- `days` → Timeout in days

If no duration is specified, the bot will apply a **1-hour timeout by default**.

Example:
```
/timeout user_id:123456789012345678 reason:Bad behavior
```
(Default = 1 hour)

---

## 🛡️ Permissions
- `/ban` → Requires **Administrator** permission
- `/kick` → Requires **Kick Members** permission
- `/timeout` → Requires **Moderate Members** permission

---

## 📜 License
This project is free to use and modify for your own server.
