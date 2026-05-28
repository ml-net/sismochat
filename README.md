# SiSMoChat

**Simple and Secure Mobile Chat**

A messaging app designed for children — no SIM required, end-to-end encrypted, parent-controlled.

> *"Dad, do you remember that app to send messages to my friends? You haven't done it anymore?"*

Read the [full story](HISTORY.md) behind this project. 🇮🇹 [Leggila in italiano](HISTORY.it.md).

---

## What is SiSMoChat?

SiSMoChat is an instant messaging platform where:

- 🔒 **Messages are end-to-end encrypted** — the server cannot read them
- 👨‍👩‍👧 **Parents control contacts** — children can only message approved connections
- 📱 **No SIM needed** — works on any device with WiFi
- 🛡️ **Privacy by design** — messages are relayed, not stored permanently
- 📲 **Installable as an app** — PWA, works on any device

Replace *child* with *end user* and *parent* with *supervisor*, and the tool extends beyond families — but the primary goal is **a safe chat for children, controlled by parents**.

---

## Architecture

```
┌─────────────┐        ┌────────────┐        ┌─────────────┐
│   Client A  │◄──────►│ API Server │◄──────►│   Client B  │
│   (PWA)     │ HTTPS  │  (Relay)   │ HTTPS  │   (PWA)     │
└─────────────┘  +WS   └────────────┘  +WS   └─────────────┘
```

- **Server** = temporary message relay (not a persistent store)
- **Client** = source of truth for messages (local storage)
- **Encryption** = RSA key pairs per device, server sees only ciphertext
- **Notifications** = WebSocket (real-time) + Web Push (background)

---

## Components

| Component | Tech | Repo | Status |
|-----------|------|------|--------|
| Server API | Node.js, Express, SQLite | [sismochat_api](https://github.com/ml-net/sismochat_api) | ✅ [v0.10.0](https://github.com/ml-net/sismochat_api/releases/latest) |
| Client | Vue 3, Vite, Tailwind, PWA | [sismochat_client](https://github.com/ml-net/sismochat_client) | 🚧 In development |
| Client POC | Vanilla JS (archived) | [sismochat_web](https://github.com/ml-net/sismochat_web) | 📦 Archived |

---

## Features

### ✅ Server (released)
- Parent/child account management
- Contact discovery and connection approval
- Text, emoji, sticker, and audio (PTT) messaging
- E2E encryption (RSA)
- Multi-device support with key management
- Client-seeded state recovery (DB-less resilience)
- Web Push notifications
- Rate limiting and security hardening

### 🚧 Client (in progress)
- Vue 3 + Tailwind + PrimeVue
- PWA (installable, offline-capable)
- Service Worker with push notifications
- Internationalization (IT/EN)

### 📋 Planned
- Authentication UI
- Parent dashboard
- Chat interface with E2E encryption
- Capacitor wrapper for app stores (future)

---

## Project Status

The API is **feature-complete and deployed**. The client is in active development — milestone v0.1.0 (project foundation) is nearly complete.

**API Documentation:** https://sismochat-api.onrender.com/doc

---

## Contributing

Contributions are welcome! Check the sub-projects for open issues and guidelines:

- **API** — [open issues](https://github.com/ml-net/sismochat_api/issues) · [CONTRIBUTING.md](https://github.com/ml-net/sismochat_api/blob/main/CONTRIBUTING.md)
- **Client** — [open issues](https://github.com/ml-net/sismochat_client/issues) · [CONTRIBUTING.md](https://github.com/ml-net/sismochat_client/blob/main/CONTRIBUTING.md)

---

## License

Both server and client are licensed under [GNU AGPL v3.0](https://www.gnu.org/licenses/agpl-3.0.html).
