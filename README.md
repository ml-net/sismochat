# SISMOCHAT

## Simple and Secure Mobile Chat

**SiSMoChat** is an instant messaging App, designed with an eye to children, who on the one hand are digital natives but at the same time are less trained in terms of safety.

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

The ideal solution is a fully decentralized architecture, where every device is free to reach out and interact with each other.

The simplest solution is a completely centralized architecture (a classic `client/server`) where a single server (or a group of them) manages users and messages.

I think a good compromise, perhaps one I can develop with reasonable effort, is described as follows:

- a server (one or more, it doesn't matter at the moment) that owns the list and availability of users (parent and child)
- multiple clients (mobile app or web app) that do the dirty work :smiley: : sending and receiving messages (for child side) and managing child profiles (for parent side)

I would like to start coding the server side as a REST API, with Node.js, to expose an interface for clients to create users and send messages.

The second step will be to create a client that uses these APIs to send and receive messages.

I hope to find someone who wants to help me!!!

# Contribute

The project has officially started, any form of contribution is welcome (improvement suggestions, contributions to the code, graphic proposals for the app and so on).