# UHC

A competitive **UHC (Ultra Hardcore)** plugin for Minecraft 1.8.8 with optimized chunk loading, Redis/MongoDB support, GUI menus, and advanced matchmaking systems.

---

## **Features**

- Optimized chunk loading system 
- Redis integration for multi-server data sync  
- MongoDB support for player stats and leaderboards  
- GUI menus for matchmaking, teams, and server status  
- Custom scenarios 
- ELO-based ranking system with hologram display  

---

## **💻 API Usage for www.veltra.lol**

The plugin exposes a REST API to fetch UHC match data.

### **1. Get all available UHC matches**

```http
GET /api/matches
```

| Parameter  | Type      | Description                  |
| :--------  | :-------  | :--------------------------- |
| `apiKey`   | string    | **Required** API key         |
| `listed`   | boolean   | **Required** include listed matches |

**Example Response:**
```json
[
  {
    "matchID": "abc123",
    "status": "running",
    "players": 12,
    "border": 1000,
    "scenario": "CutClean"
  }
]
```

---

### **2. Get a specific UHC match**

```http
GET /api/matches/${matchID}
```

| Parameter  | Type   | Description                     |
| :--------  | :----  | :------------------------------ |
| `matchID`  | string | **Required** Match ID (from uhc.gg) |

**Example Response:**
```json
{
  "matchID": "abc123",
  "status": "running",
  "players": [
    {"name": "Player1", "elo": 1200},
    {"name": "Player2", "elo": 1250}
  ],
  "border": 1000,
  "scenario": "CutClean",
  "startTime": "2025-08-26T15:00:00Z"
}
```

---

## **⚙️ Installation**

1. Copy the plugin `.jar` to your server `plugins/` folder.  
2. Restart the server to generate configuration files.  
3. Configure `config.yml` for Redis and MongoDB connection.  
4. Optionally, adjust default game settings (border, scenarios, timers).  

---

## **📄 Example `config.yml`**

```yaml
redis:
  host: "127.0.0.1"
  port: 6379

mongodb:
  host: "127.0.0.1"
  port: 27017
  database: "uhc"

game:
  defaultBorder: 1000
  meetupTime: 1200
  scenario: "CutClean"
```

---

## **📄 Commands**

| Command | Description |
| ------- | ----------- |
| `/uhc start` | Start the UHC match |
| `/uhc stop`  | Stop the current match |
| `/uhc join`  | Join the meetup |
| `/uhc leave` | Leave the meetup |
| `/uhc manage`| Open management GUI (maps, chests, scenarios) |
| `/leaderboard <kit>` | Show kit-based leaderboard |

---

## **📜 License**

MIT License – free to use, modify, and distribute.

---

## **💬 Support**

- For issues or feature requests, please open a **GitHub Issue**.  
- Join our **Discord server** for live support and discussion.

