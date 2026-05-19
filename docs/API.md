# API Reference

## Base URL

```
http://localhost:3000/api
```

## Endpoints

### Health Check

Get server health status.

**Request:**
```
GET /health
```

**Response:**
```json
{
  "status": "ok",
  "timestamp": "2026-05-19T10:30:00Z",
  "version": "1.0.0"
}
```

---

### Get All Games

Retrieve a list of available games.

**Request:**
```
GET /games
```

**Response:**
```json
{
  "games": [
    {
      "id": 1,
      "title": "Adventure Quest",
      "description": "Epic adventure",
      "thumbnail": "url_to_image"
    }
  ],
  "total": 1
}
```

---

### Get Game Details

Get specific game information.

**Request:**
```
GET /games/:gameId
```

**Parameters:**
- `gameId` (string): Game identifier

**Response:**
```json
{
  "gameId": "1",
  "title": "Adventure Quest",
  "description": "Epic adventure game",
  "thumbnail": "url_to_image",
  "players": 150,
  "rating": 4.5
}
```

---

### Play Game

Start a new game session.

**Request:**
```
POST /games/:gameId/play
```

**Parameters:**
- `gameId` (string): Game identifier

**Response:**
```json
{
  "sessionId": "session_1_1234567890",
  "gameId": "1",
  "status": "starting"
}
```

---

### Get Game State

Get current game session state.

**Request:**
```
GET /games/:gameId/state
```

**Response:**
```json
{
  "gameId": "1",
  "state": "running",
  "players": 5,
  "uptime": 3600,
  "fps": 60
}
```

---

### Pause Game

Pause the current game session.

**Request:**
```
POST /games/:gameId/pause
```

**Response:**
```json
{
  "status": "paused",
  "gameId": "1"
}
```

---

### Resume Game

Resume the paused game.

**Request:**
```
POST /games/:gameId/resume
```

**Response:**
```json
{
  "status": "running",
  "gameId": "1"
}
```

---

### Stop Game

Stop the current game session.

**Request:**
```
POST /games/:gameId/stop
```

**Response:**
```json
{
  "status": "stopped",
  "gameId": "1"
}
```

---

## Error Responses

All errors return appropriate HTTP status codes:

```json
{
  "error": "Error message",
  "path": "/api/endpoint",
  "timestamp": "2026-05-19T10:30:00Z"
}
```

### Common Status Codes

- `200`: Success
- `400`: Bad Request
- `404`: Not Found
- `500`: Internal Server Error

## Rate Limiting

Currently no rate limiting. This may be added in future versions.

## Authentication

Currently no authentication required. Authentication support will be added in future versions.
