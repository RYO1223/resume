# AI Voice Talk

## Summary

自分で設定したAIと音声チャットすることができる

---

## Architecture

![architecture](https://github.com/RYO1223/resume/blob/master/docs/my_applications/AI_Voice_Talk/architecture.jpg?raw=true)

### Frontend

- **Language**: Dart/Flutter

  - **Architecture**: View-Service-Repository
  - **Core Libraries**: Riverpod, go_router

### Backend

- **Language**: Golang

  - **Core Libraries**: Gin, Zap

### Infrastructure

- Cloudflare: DNS, Reverse Proxy
- RevenueCat (Subscription management)
- GCP: Firebase Authentication, Text-to-Speech, Speech-to-Text
- ChatGPT
- Zabbix (Server monitoring)

---

## Function Detail

### Basic Function

1. Room Creation, Update, Deletion

Create a room for each AI.

You can set AI's settings below
- name
- speaking language
- gender
- personality
- speaking rate
- relationship with you
- situations in which you meet.

2. Talk with AI

When you speak while holding down the microphone button, it is recorded and sent to the server.
Then, it is converted to text by GCP Speak-to-Text and sent to ChatGPT, along with the AI's settings and previous conversations.
ChatGPT's reply is converted into voice data by GCP Text-to-Speak and returned to the client.

### Subscription

Subscribing to a subscriber allows full access to the above features.

### Multiple Device

Since Revenuecat manages billing by referencing the FirebaseAuthentication uid,
If the same account is used on a different device, it will be determined that the subscription has been subscribed to.

---

## Secutity

- By passing through Cloudflare's reverse proxy, the IP address of the backend server is hidden. This prevents attacks on the domain.
- OAuth authentication lowers the risk of passwords and other information being compromised.

## Server Monitioring

- Server load monitoring and health checks by Zabbix.
