
<div align="center">

# 🔒 ProMcSecure

<img src="https://img.shields.io/badge/version-1.0.0--BETA-blueviolet?style=for-the-badge" />
<img src="https://img.shields.io/badge/minecraft-1.8--1.21-green?style=for-the-badge" />
<img src="https://img.shields.io/badge/Java-8%2B-orange?style=for-the-badge&logo=java" />
<img src="https://img.shields.io/badge/license-MIT-blue?style=for-the-badge" />

<br/><br/>

### A powerful secure HTTP API plugin for Minecraft servers
**Powered by ProMcBot × ProMcSecure**

*Control your Minecraft server through a highly secure REST API — execute commands, monitor players, track playtime, and more.*

[📥 Download](../../releases/latest) · [🐛 Report Bug](../../issues) · [💡 Request Feature](../../issues)

</div>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🌐 **Secure REST API** | Full HTTP API with Dual-Header Authentication (`Bearer` + `X-Premium-Key`). |
| 👤 **Player Tracking** | Advanced tracking: Online status, ping, world, IP, and first join date. |
| 🏆 **Playtime Leaderboard** | Track and rank players by their total lifetime playtime. |
| 🔑 **Account Detection** | Automatically detect Premium (Microsoft) vs Cracked accounts. |
| 🎮 **Client Detection** | Identify the exact client brand/mod players use (Lunar, Forge, etc.). |
| 🔐 **AES-256 Encryption** | Bearer tokens are deeply encrypted directly in the config file. |
| ⚡ **Command Execution** | Execute any server console command securely via HTTP. |
| 📊 **bStats Metrics** | Lightweight and anonymous usage statistics. |

---

## 📥 Installation

1. Download `ProMcSecure-1.0.0-BETA.jar` from the [Releases](../../releases) page.
2. Place it inside your server's `/plugins` directory.
3. Restart the server — a `config.yml` will be generated automatically.
4. Edit `plugins/ProMcSecure/config.yml` to set your port and token:

---

## ⚙️ Configuration

```yaml
# ProMcSecure Configuration

# Port for the HTTP server
port: 8080

# Bearer token (auto-encrypted with AES-256 on first start)
bearer-token: your-secret-token-here

# Require HTTPS (for reverse proxy with SSL)
require-https: false
```

---


5. Restart the server again. 

> ⚠️ **Security Note:** The bearer token is automatically **AES-256 encrypted** on the first load. Even if someone gains access to your config file, they cannot use the encrypted value!

---

## 🤖 Linking with ProMcBot

Connecting your Minecraft server to **ProMcBot** is incredibly simple and fully automated:

1. Go to your Discord server where **ProMcBot** is invited.
2. Type the slash command: `/setup_server` 
3. A menu will appear. Select the **API Generator / Settings** option.
4. Fill in the required fields in the modal:
   - **API Token**: Paste the exact same `bearer-token` you placed in your `config.yml` (before it encrypted).
   - **API Port**: Enter the exact same `port` you set in your `config.yml`.
5. Click Submit to save.
6. **Done! 🎉** ProMcBot will now securely communicate with your server using advanced dynamic Premium Keys. 

---
> ✨ **Important Note:** ProMcBot offers you a free **Premium trial** as long as you use it to connect to your Minecraft server.
---

## 📊 Example API Responses

*The plugin provides rich JSON data for ProMcBot to render beautiful UI cards. Here is a glimpse of what the responses look like:*

**👤 Player Details Data:**
```json
{
  "success": true,
  "username": "IDmar_",
  "uuid": "00000000-0000-0000-0000-000000000000",
  "online": true,
  "world": "world",
  "ping": 42,
  "accountType": "PREMIUM",
  "clientBrand": "Lunar Client",
  "totalPlaytimeSeconds": 3600,
  "formattedPlaytime": "1h 0m 0s"
}
```

**🏆 Playtime Leaderboard Data:**
```json
{
  "success": true,
  "leaderboard": [
    { "rank": 1, "username": "IDmar_", "totalSeconds": 36000, "formatted": "10h 0m 0s", "online": true },
    { "rank": 2, "username": "Notch", "totalSeconds": 18000, "formatted": "5h 0m 0s", "online": false }
  ]
}
```

## 🔐 Advanced Security

- **AES-256 Token Encryption** — Your API token is instantly encrypted upon starting the server.
- **Dual Header Authentication** — Endpoints are strictly protected by both a `Bearer` token and a dynamic `X-Premium-Key` system managed by ProMcBot.
- **Code Obfuscation** — The plugin's bytecode is heavily obfuscated to prevent reverse engineering.

---

## 🖥️ Requirements

| Requirement | Version |
|---|---|
| Java | 8 or higher |
| Minecraft Server | Spigot / Paper 1.8 - 1.21.x |

---

## 📜 Changelog

### `v1.0.0-BETA`
- 🚀 Initial public BETA release
- ✅ Secure REST API with Dual Authentication integration
- ✅ Player tracking & playtime system
- ✅ Playtime leaderboard engine
- ✅ Premium vs Cracked account detection
- ✅ Client brand detection (Optifine, Forge, Fabric, Lunar, etc.)
- ✅ AES-256 token encryption in config
- ✅ Pending commands queue system

---

<div align="center">

Made with ❤️ by **ProMcBot × ProMcSecure**

⭐ *If this plugin helped you, please star the repository!*

</div>
