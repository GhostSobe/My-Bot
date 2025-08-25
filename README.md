# Discord DM Bot v5 - Complete Edition

🤖 **บอทสำหรับส่งข้อความส่วนตัวและจัดการเซิฟเวอร์ด้วย Slash Commands**

Made By : Khaotom

## 🚀 การติดตั้งและใช้งาน

### 1. ติดตั้ง Dependencies
```bash
npm install discord.js
npm install dotenv
npm install @discordjs/voice
npm install @snazzah/davey sodium-native
```

### 2. สร้างบอทใน Discord Developer Portal
- ไปที่ [Discord Developer Portal](https://discord.com/developers/applications)
- กดปุ่ม **"New Application"** และตั้งชื่อบอท
- ไปที่แท็บ **"Bot"** และกดปุ่ม **"Add Bot"**
- คัดลอก **Bot Token** (เก็บไว้เป็นความลับ!)
- เปิดใช้งาน **MESSAGE CONTENT INTENT** ในส่วน Privileged Gateway Intents

### 3. ตั้งค่า Environment Variables
สร้างไฟล์ `.env` ในโฟลเดอร์เดียวกับบอท:
```env
BOT_TOKEN=your_bot_token_here
DISCORD_VOICE_USE_DAVE=false
```

### 4. เชิญบอทเข้าเซิฟเวอร์
- ไปที่แท็บ **"OAuth2"** > **"URL Generator"**
- เลือก **Scopes**: `bot`, `applications.commands`
- เลือก **Bot Permissions**:
  - Send Messages
  - Read Message History
  - View Channels
  - Use Slash Commands
  - Connect (สำหรับ Voice)
  - Speak (สำหรับ Voice)
  - Manage Messages
  - Moderate Members
  - Ban Members
  - Kick Members
  - Manage Channels
  - Manage Roles
  - Manage Nicknames
  - Manage Emojis and Stickers

### 5. รันบอท
```bash
node v5.js
```

## 📋 Slash Commands ที่ใช้ได้

### 📨 **DM Commands**
- `/setup` - ตั้งค่าห้องนี้เป็น Log Channel
- `/send <user> <message>` - ส่งข้อความส่วนตัว
- `/checkdm <user>` - ตรวจสอบว่าส่ง DM ได้หรือไม่
- `/history <user>` - ดูประวัติการติดต่อ

### 🔨 **Moderation Commands**
- `/timeout <user> <duration> [reason]` - Timeout ผู้ใช้ (1m = 1นาที, 1h = 1ชั่วโมง, 1d = 1วัน)
- `/untimeout <user> [reason]` - ยกเลิก timeout
- `/ban <user> [reason]` - แบนผู้ใช้
- `/unban <userid> [reason]` - ยกเลิกแบน (ต้องใช้ User ID)
- `/kick <user> [reason]` - เตะผู้ใช้
- `/setup-muted` - สร้าง Muted role และตั้งค่าสิทธิ์อัตโนมัติ
- `/mute <user> [reason]` - Mute ผู้ใช้ (ปิดไมล์)
- `/unmute <user> [reason]` - Unmute ผู้ใช้ (เปิดไมล์)
- `/clear <amount> [user]` - ลบข้อความ 1-100 ข้อความ

### 🔒 **Channel Management**
- `/lockchannel <lock/unlock> [channel] [reason]` - ล็อค/ปลดล็อคช่องสนทนา
- `/slowmode <seconds> [channel]` - ตั้งค่า slowmode (0-21600 วินาที)

### 🎭 **User Management**
- `/role <user> <role> <add/remove> [reason]` - จัดการ role ของผู้ใช้
- `/nick <user> [nickname]` - เปลี่ยนชื่อเล่น (เว้นว่างเพื่อรีเซ็ต)

### 🔊 **Voice Commands**
- `/joinvoice [channel]` - เข้าร่วมช่องเสียง
- `/leavevoice` - ออกจากช่องเสียง
- `/voicestatus` - ดูสถานะช่องเสียงของบอท

### 🎨 **Fun & Utilities**
- `/copyemoji <emoji> [name]` - คัดลอก emoji จากเซิฟเวอร์อื่น
- `/userinfo <user>` - ดูข้อมูลผู้ใช้อย่างละเอียด
- `/avatar [user]` - ดู avatar ของผู้ใช้
- `/ping` - ตรวจสอบความเร็วตอบสนองของบอท

### 📢 **Announcement Commands**
- `/announce <channel> <message>` - ส่งประกาศ

### 🔧 **System Commands**
- `/status` - ดูสถานะบอท
- `/serverinfo` - ดูข้อมูลเซิฟเวอร์
- `/setstream <url>` - เปลี่ยนลิ้ง streaming URL
- `/reset` - รีเซ็ตการตั้งค่า
- `/help` - แสดงคำสั่งทั้งหมด

## 🛡️ สิทธิ์ที่ต้องการ

| คำสั่ง | สิทธิ์ที่จำเป็น |
|--------|----------------|
| `/setup`, `/reset` | Administrator |
| `/send`, `/announce`, `/userinfo`, `/status`, `/history`, `/checkdm`, `/serverinfo`, `/avatar`, `/voicestatus`, `/clear` | Manage Messages |
| `/timeout`, `/untimeout`, `/mute`, `/unmute` | Moderate Members |
| `/ban`, `/unban` | Ban Members |
| `/kick` | Kick Members |
| `/joinvoice`, `/leavevoice` | Connect |
| `/lockchannel`, `/slowmode` | Manage Channels |
| `/role`, `/setup-muted` | Manage Roles |
| `/nick` | Manage Nicknames |
| `/copyemoji` | Manage Emojis and Stickers |
| `/setstream` | Administrator |

## ✨ ฟีเจอร์ใหม่ใน v5

### 🎯 **Advanced Moderation**
- ระบบ Mute/Unmute ด้วย role-based system
- การจัดการข้อความแบบ bulk delete
- ระบบล็อคช่องสนทนาและ slowmode

### 🎨 **Server Customization**
- คัดลอก emoji จากเซิฟเวอร์อื่น
- จัดการ role และ nickname
- เปลี่ยน streaming URL แบบ real-time

### 🔊 **Enhanced Voice Support**
- บอทสามารถเข้าร่วมช่องเสียงเพื่อแสดงว่ายังทำงานอยู่
- ตรวจสอบสถานะการเชื่อมต่อได้ง่าย
- จัดการการเชื่อมต่อแบบ graceful shutdown

### 🎯 **Dynamic Status**
- บอทจะเปลี่ยนสถานะอัตโนมัติทุก 15 วินาที
- รองรับการเปลี่ยน streaming URL แบบ real-time
- แสดง activity ที่หลากหลาย

### 🚦 **Enhanced Error Handling**
- ข้อความ error ที่ละเอียดและเป็นภาษาไทย
- จัดการกับ Discord API error codes อย่างเหมาะสม
- ป้องกันการดับของบอทเมื่อเกิด error

### 📊 **Comprehensive Server Info**
- ข้อมูลเซิฟเวอร์ที่ครบถ้วนพร้อม statistics
- แสดงข้อมูล boost level, features, และ member counts
- UI ที่สวยงามด้วย embeds

## 🎁 ข้อดีของ Slash Commands

✅ **UI ที่สะดวก** - มี autocomplete และ parameter hints  
✅ **ตรวจสอบพารามิเตอร์อัตโนมัติ** - ลดข้อผิดพลาดในการใช้งาน  
✅ **ระบบสิทธิ์ที่ชัดเจน** - Discord จัดการสิทธิ์ให้อัตโนมัติ  
✅ **ไม่มี prefix conflicts** - ไม่ปะทะกับบอทอื่น  
✅ **UX ที่ดีกว่า** - ผู้ใช้ไม่ต้องจำคำสั่ง  

## ⚡ ตัวอย่างการใช้งาน

```
/setup                              - ตั้งค่าห้องปัจจุบันเป็น log channel
/send @user สวัสดีครับ                - ส่ง DM ไปหาผู้ใช้
/timeout @user 30m ส่งสแปม            - timeout ผู้ใช้ 30 นาที
/mute @user ใช้คำหยาบ                 - mute ผู้ใช้ด้วย role system
/clear 10                           - ลบข้อความ 10 ข้อความล่าสุด
/lockchannel lock #general          - ล็อคช่อง general
/role @user @Member add             - เพิ่ม role Member ให้ผู้ใช้
/copyemoji <:custom:123456789>      - คัดลอก emoji จากเซิฟเวอร์อื่น
/setstream https://youtube.com/...   - เปลี่ยนลิ้ง streaming
/joinvoice General                  - เข้าร่วมช่องเสียง General
/announce #general ประกาศสำคัญ        - ส่งประกาศในช่อง general
```

## 🔧 การแก้ปัญหา

### ❌ **บอทไม่ตอบสนอง**
- ตรวจสอบว่า Token ถูกต้อง
- เช็คว่าเปิด MESSAGE CONTENT INTENT แล้ว
- ดูใน console ว่ามี error อะไร

### ❌ **ไม่เห็น Slash Commands**
- รอ 1-2 นาทีให้ Discord อัพเดท
- ลอง restart Discord client
- เช็คว่าบอทมีสิทธิ์ `applications.commands`

### ❌ **Voice Commands ไม่ทำงาน**
- ตรวจสอบว่าติดตั้ง `@snazzah/davey` แล้ว
- เช็คว่าบอทมีสิทธิ์ Connect และ Speak
- ดูว่าตั้ง `DISCORD_VOICE_USE_DAVE=false` ใน .env แล้วหรือไม่

### ❌ **DAVE Protocol Error**
```bash
npm install @snazzah/davey sodium-native
```
หรือตั้งค่า:
```env
DISCORD_VOICE_USE_DAVE=false
```

### ❌ **Mute/Role Commands ไม่ทำงาน**
- รันคำสั่ง `/setup-muted` ก่อนใช้งาน mute
- ตรวจสอบว่าบอทมีสิทธิ์ Manage Roles
- ตรวจสอบว่า role ของบอทสูงกว่า role ที่จะจัดการ

## 📁 โครงสร้างไฟล์

```
bot-project/
├── index.js               # ไฟล์บอทหลัก (เวอร์ชั่นล่าสุด)
├── .env                   # environment variables
├── bot_config.json        # การตั้งค่าที่บันทึกอัตโนมัติ
├── package.json           # dependencies
└── README.md              # คู่มือนี้
```

## 🔒 ความปลอดภัย

⚠️ **อย่าแชร์ Bot Token ให้ใคร!**  
⚠️ **เก็บไฟล์ `.env` เป็นความลับ**  
⚠️ **อย่า commit Bot Token ลง Git**  
⚠️ **ตรวจสอบสิทธิ์ก่อนให้บอทเข้าเซิฟเวอร์**

## 💾 การสำรองข้อมูล

บอทจะสร้างไฟล์ `bot_config.json` อัตโนมัติเพื่อเก็บการตั้งค่า:
- Log Channel ของแต่ละเซิฟเวอร์
- Streaming URL ที่กำหนดเอง
- ข้อมูลผู้ติดตั้ง
- เวลาที่ติดตั้ง

## 🆕 Version 5 Changelog

### ✅ เพิ่ม Advanced Moderation
- `/setup-muted` - สร้าง Muted role อัตโนมัติ
- `/mute`, `/unmute` - ระบบ mute แบบ role-based
- `/clear` - ลบข้อความแบบ bulk delete
- `/lockchannel` - ล็อค/ปลดล็อคช่องสนทนา
- `/slowmode` - ตั้งค่า slowmode

### ✅ เพิ่ม Server Management
- `/role` - จัดการ role ของผู้ใช้
- `/nick` - เปลี่ยนชื่อเล่น
- `/copyemoji` - คัดลอก emoji จากเซิฟเวอร์อื่น
- `/setstream` - เปลี่ยน streaming URL

### ✅ ปรับปรุง UI/UX
- Embed ที่สวยงามและมีข้อมูลครบถ้วน
- Error messages ที่ละเอียดและเป็นภาษาไทย
- Permission checking ที่ดีขึ้น

### ✅ เพิ่ม Voice Features
- Voice Channel Support ที่เสถียรขึ้น
- Connection management ที่ดีขึ้น
- Voice status monitoring

### ✅ ปรับปรุง Performance
- Optimized command handling
- Better memory management
- Graceful shutdown process

---

## 📞 ติดต่อและสนับสนุน

หากมีปัญหาหรือข้อเสนอแนะ กรุณาติดต่อ **Khaotom** ผู้พัฒนา

🔗 **Discord Community:** discord.gg/yt-rocket

**Happy Botting! 🎉**
