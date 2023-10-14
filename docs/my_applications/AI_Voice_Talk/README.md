# AI Voice Talk

## Summary

You can voice chat with an AI you set up yourself.

- [App Store](https://apps.apple.com/us/app/ai-voice-talk/id6449139482)
- [Google Play]() coming soon...

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

#### Room Creation, Update, Deletion

<img src="https://github.com/RYO1223/resume/assets/70420716/72d5dac5-106f-432f-8cac-f4b5723f4a19" width="30%" />


Create a room for each AI.

You can set AI's settings below:
- name
- speaking language
- gender
- personality
- speaking rate
- relationship with you
- situations in which you meet.

#### Talk with AI

<img src="https://github.com/RYO1223/resume/assets/70420716/f0062a37-98cb-417b-b15c-64403a678729" width="30%" /><img src="https://github.com/RYO1223/resume/assets/70420716/486673ba-cd74-4fec-bfb2-0a6829a565be" width="30%" />

1. speak to AI.
2. the audio is sent to the backend server.
3. in the backend server, the audio is sent to GCP Speak-to-Text, and the server receives text.
4. the text is sent to ChatGPT, along with the AI's settings, and the  server receives the AI's response.
5. the response is sent to GCP Text-to-Speach, and the server receives the response audio.
6. the server sends response audio to the client.

### Multiple Device Support

Since Revenuecat manages billing by referencing the FirebaseAuthentication uid,
If the same account is used on a different device, it will be determined that the subscription has been subscribed to.

---

## Secutity

- By passing through Cloudflare's reverse proxy, the IP address of the backend server is hidden. This prevents attacks on the domain.
- OAuth authentication lowers the risk of passwords and other information being compromised.

## Server Monitioring

- Server load monitoring and health checks by Zabbix.
