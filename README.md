# SISMOCHAT

## Simple and Secure Mobile Chat

**SiSMoChat** is an instant messaging App, designed with an eye to children, who on the one hand are digital natives but at the same time are less trained in terms of safety.

Read the [story behind this project](HISTORY.md).

# The idea

Why not create a messaging app that reaches these goals?

- SIM not needed
- User's safety and privacy guarantee
- Control by a supervisor

Hence the idea behind this project: to create a messaging app that is not linked to the presence of a SIM (but simply to the availability of a network connection), which guarantees the privacy of messages and of the user, in consideration of the delicacy of the target of the same, and above all that it allows a control by a supervisor.

## Children but not only

Replacing **child** with _end user_ and **parent** with _supervisor_ extends the potential of the tool, but at the moment the reference universe is that of `a chat for children controlled by parents`.

# The solution

How can this control be manifested? Leaving aside the obvious possibility of reading messages (this is not the goal and initially it is not foreseen as a function, even if it could still be possible) I imagined the action of adding contacts delegated to the parent's approval: not leaving the freedom to exchange messages with anyone but only with validated (and therefore known) accounts.

Adding (in the first steps) the inhibition of image and URL exchange, the aspects guaranteeing privacy and security are safe; restricting the installation of the App on a single device at a time (for the child profile, at least in a first version), we can complete the recipe with an encryption applied to the messages in order to make them visible in clear text only to the two terminals of the conversation.

We can finish with an obvious availability of Emoji (possibly enriched with other features such as stickers or other) and perhaps the app could be interesting and attractive.

# Technical implementation

The architecture follows a **message relay** pattern: the server holds messages temporarily until the recipient downloads them, then deletes them. The client is the source of truth for message history - no persistent data stays on the server.

Key design choices:
- **E2E encryption** (RSA) - the server cannot read message content
- **Privacy by design** - messages are deleted after download, with a TTL for undelivered ones
- **Parental control** - contacts must be approved by a parent before children can exchange messages
- **Single device** - each child account is paired to one device at a time

## Sub-projects

| Component | Tech | Repo | Status |
|-----------|------|------|--------|
| Server API | Node.js / Express / SQLite | [sismochat_api](https://github.com/ml-net/sismochat_api) | [latest release](https://github.com/ml-net/sismochat_api/releases/latest) |
| Client | TBD | TBD | Planned |

# Project status

- ✅ **API** - Message Relay MVP ([latest release](https://github.com/ml-net/sismochat_api/releases/latest))
- 🔲 Client POC - next milestone

# Contribute

The project has officially started, any form of contribution is welcome (improvement suggestions, contributions to the code, graphic proposals for the app and so on).

Check the sub-projects for open issues and contributing guidelines:
- [sismochat_api - open issues](https://github.com/ml-net/sismochat_api/issues)
- [sismochat_api - CONTRIBUTING.md](https://github.com/ml-net/sismochat_api/blob/main/CONTRIBUTING.md)
