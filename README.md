<div align="center">

<img src="https://img.shields.io/badge/version-1.0.0--BETA-blueviolet?style=for-the-badge" />
<img src="https://img.shields.io/badge/minecraft-1.8--1.21-green?style=for-the-badge" />
<img src="https://img.shields.io/badge/Java-8%2B-orange?style=for-the-badge&logo=java" />
<img src="https://img.shields.io/badge/license-MIT-blue?style=for-the-badge" />

<br/><br/>

# 🔒 ProMcSecure

### A powerful HTTP API plugin for Minecraft servers
**Powered by ProMcBot × ProMcSecure**

*Control your Minecraft server through a secure REST API — execute commands, monitor players, track playtime, and more.*

[📥 Download](../../releases/latest) · [📖 Documentation](#-endpoints) · [🐛 Report Bug](../../issues) · [💡 Request Feature](../../issues)

</div>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🌐 **REST API** | Full HTTP API with Bearer token authentication |
| 👤 **Player Tracking** | Online status, ping, world, IP, first join |
| 🏆 **Playtime Leaderboard** | Track and rank players by total playtime |
| 🔑 **Account Detection** | Detect Premium (Microsoft) vs Cracked accounts |
| 🎮 **Client Detection** | Identify the client brand/mod players use |
| 🔐 **AES-256 Encryption** | Bearer token stored encrypted in config |
| ⚡ **Command Execution** | Execute any console command via HTTP |
| 📊 **bStats Metrics** | Anonymous usage statistics |

---

## 📥 Installation

1. Download `ProMcSecure-1.0.0-BETA.jar` from the [Releases](../../releases) page
2. Place it in your server's `/plugins` folder
3. Restart the server — a `config.yml` will be generated automatically
4. Edit `plugins/ProMcSecure/config.yml`:

```yaml
port: 8080
bearer-token: your-secret-token-here   # Auto-encrypted on first start!
require-https: false
```

5. Reload with `/http-commands reload`

> ⚠️ **Security Note:** The bearer token is automatically AES-256 encrypted on first load. Even if someone reads your config file, they cannot use the encrypted value directly.

---

## 🔌 Endpoints

> All endpoints require the `Authorization: Bearer <token>` header.

### `GET /info`
Returns server status and plugin information.

```json
{
  "success": true,
  "playerCount": 5,
  "maxPlayers": 100,
  "serverVersion": "Paper 1.21.3",
  "tps": 20.0,
  "status": "online",
  "plugin_version": "1.0.0-BETA",
  "powered_by": "ProMcBot x ProMcSecure"
}
```

---

### `GET /players`
Returns a list of all online players.

```json
{
  "success": true,
  "players": ["Steve", "Alex", "Notch"]
}
```

---

### `GET /player/{username}`
Returns detailed information about a specific player.

```json
{
  "success": true,
  "username": "Steve",
  "uuid": "...",
  "online": true,
  "world": "world",
  "ping": 42,
  "accountType": "PREMIUM",
  "clientBrand": "vanilla",
  "totalPlaytimeSeconds": 3600,
  "formattedPlaytime": "1h 0m 0s"
}
```

---

### `GET /leaderboard/playtime?limit=10`
Returns the top players ranked by total playtime.

```json
{
  "success": true,
  "leaderboard": [
    { "rank": 1, "username": "Steve", "totalSeconds": 36000, "formatted": "10h 0m 0s", "online": true }
  ]
}
```

---

### `POST /execute`
Executes one or more console commands.

**Request:**
```json
{
  "commands": ["say Hello!", "give Steve diamond 64"],
  "waitForPlayer": "Steve"
}
```

> If `waitForPlayer` is set and they're offline, commands are queued and executed when they join.

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

## 🔐 Security

- **AES-256 Token Encryption** — Your API token is encrypted on first start
- **Bearer Authentication** — All endpoints are protected
- **Code Obfuscation** — Plugin bytecode is obfuscated via ProGuard

---

## 🖥️ Requirements

| Requirement | Version |
|---|---|
| Java | 8 or higher |
| Minecraft Server | Spigot / Paper 1.8+ |

---

## 📜 Changelog

### `v1.0.0-BETA`
- 🚀 Initial public BETA release
- ✅ REST API with Bearer auth
- ✅ Player tracking & playtime system
- ✅ Playtime leaderboard endpoint
- ✅ Premium/Cracked account detection
- ✅ Client brand detection (Optifine, Forge, Fabric, etc.)
- ✅ AES-256 token encryption in config
- ✅ Pending commands queue system

---

<div align="center">

Made with ❤️ by **ProMcBot × ProMcSecure**

⭐ *If this plugin helped you, please star the repository!*

</div>
