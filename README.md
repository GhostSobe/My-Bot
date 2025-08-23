# Discord DM Bot v2 - Enhanced Edition

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
- คัดลอกลิงก์และเชิญบอทเข้าเซิฟเวอร์

### 5. รันบอท
```bash
node .
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

### 🔊 **Voice Commands** (ใหม่!)
- `/joinvoice [channel]` - เข้าร่วมช่องเสียง (เพื่อแสดงว่าบอทยังทำงาน)
- `/leavevoice` - ออกจากช่องเสียง
- `/voicestatus` - ดูสถานะช่องเสียงของบอท

### 📢 **Utility Commands**
- `/announce <channel> <message>` - ส่งประกาศ
- `/userinfo <user>` - ดูข้อมูลผู้ใช้อย่างละเอียด
- `/serverinfo` - ดูข้อมูลเซิฟเวอร์
- `/avatar [user]` - ดู avatar ของผู้ใช้
- `/ping` - ตรวจสอบความเร็วตอบสนองของบอท
- `/status` - ดูสถานะบอทและเซิฟเวอร์
- `/reset` - รีเซ็ตการตั้งค่าเซิฟเวอร์
- `/help` - แสดงคำสั่งทั้งหมด

## 🛡️ สิทธิ์ที่ต้องการ

| คำสั่ง | สิทธิ์ที่จำเป็น |
|--------|----------------|
| `/setup`, `/reset` | Administrator |
| `/send`, `/announce`, `/userinfo`, `/status`, `/history`, `/checkdm`, `/serverinfo`, `/avatar`, `/voicestatus` | Manage Messages |
| `/timeout`, `/untimeout` | Moderate Members |
| `/ban`, `/unban` | Ban Members |
| `/kick` | Kick Members |
| `/joinvoice`, `/leavevoice` | Connect |

## ✨ ฟีเจอร์ใหม่

### 🔊 **Voice Channel Support**
- บอทสามารถเข้าร่วมช่องเสียงเพื่อแสดงว่ายังทำงานอยู่
- ตรวจสอบสถานะการเชื่อมต่อได้ง่าย
- จัดการการเชื่อมต่อแบบ graceful shutdown

### 🎯 **Dynamic Status**
- บอทจะเปลี่ยนสถานะอัตโนมัติทุก 30 วินาที
- แสดงจำนวนเซิฟเวอร์ที่บอทกำลังให้บริการ

### 🚦 **Enhanced Error Handling**
- ข้อความ error ที่ละเอียดและเป็นภาษาไทย
- จัดการกับ Discord API error codes อย่างเหมาะสม
- ป้องกันการดับของบอทเมื่อเกิด error

### 📊 **Improved Commands**
- `/ping` - แสดงความเร็วตอบสนอง API และ Response Time
- `/serverinfo` - ข้อมูลเซิฟเวอร์ที่ครบถ้วนมากขึ้น
- `/avatar` - ดู avatar ความละเอียดสูง

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
/joinvoice General                  - เข้าร่วมช่องเสียง General
/announce #general ประกาศสำคัญ        - ส่งประกาศในช่อง general
/userinfo @user                     - ดูข้อมูลของผู้ใช้
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

## 📁 โครงสร้างไฟล์

```
bot-project/
├── index.js               # ไฟล์บอทหลัก
├── .env                   # environment variables
├── bot_config.json        # การตั้งค่าที่บันทึกอัตโนมัติ
├── package.json           # dependencies
└── README.md              # คู่มือนี้
```

## 🔒 ความปลอดภัย

⚠️ **อย่าแชร์ Bot Token ให้ใคร!**  
⚠️ **เก็บไฟล์ `.env` เป็นความลับ**  
⚠️ **อย่า commit Bot Token ลง Git**  

## 💾 การสำรองข้อมูล

บอทจะสร้างไฟล์ `bot_config.json` อัตโนมัติเพื่อเก็บการตั้งค่า:
- Log Channel ของแต่ละเซิฟเวอร์
- ข้อมูลผู้ติดตั้ง
- เวลาที่ติดตั้ง

## 🆕 Version 2 Changelog

- ✅ เพิ่ม Voice Channel Commands
- ✅ Dynamic Bot Status  
- ✅ Enhanced Error Handling
- ✅ Improved Status Command
- ✅ New Utility Commands (ping, serverinfo, avatar)
- ✅ Better Permission Management
- ✅ Graceful Shutdown Process
- ✅ DAVE Protocol Compatibility

---

## 📞 ติดต่อและสนับสนุน

หากมีปัญหาหรือข้อเสนอแนะ กรุณาติดต่อ **Khaotom** ผู้พัฒนา


**Happy Botting! 🎉**
