# AI Voice Talk

## Summary

Voice chat with an AI of your own creation.

- [App Store](https://apps.apple.com/us/app/ai-voice-talk/id6449139482)
- [Google Play]() - Coming Soon...

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
- RevenueCat for subscription management
- GCP: Firebase Authentication, Text-to-Speech, Speech-to-Text
- ChatGPT
- Zabbix for server monitoring

---

## Function Detail

### Basic Function

#### Room Creation, Update, Deletion

Create a personalized room for each AI companion. Customize your AI's settings:

- name
- speaking language
- gender
- personality
- speaking rate
- relationship with you
- situations in which you meet.

<img src="https://github.com/RYO1223/resume/assets/70420716/72d5dac5-106f-432f-8cac-f4b5723f4a19" width="30%" />

#### Talk with AI

1. **Record Voice:** Captures your spoken voice for AI interaction.
2. **Transmit Spoken Audio:** Forward audio to the backend server. 
3. **Speach-to-Text Conversin:** Use GCP Speak-to-Text to convert from audio to text.
4. **Response Generation:** Send text, AI's settings, and previous conversation history to ChatGPT for the AI's response.
5. **Text-to-Speach Conversion:** Utilize GCP Text-to-Speach for response audio.
6. **Client Audio Feedback:** Delivers the generated response audio back to the client for playback.

<img src="https://github.com/RYO1223/resume/assets/70420716/f0062a37-98cb-417b-b15c-64403a678729" width="30%" /><img src="https://github.com/RYO1223/resume/assets/70420716/486673ba-cd74-4fec-bfb2-0a6829a565be" width="30%" />

### Multiple Device Support

RevenueCat manages subscriptions via Firebase Authentication uid, which you can use across devices for the same account.

---

## AI 

In order to obtain an appropriate response (in this case, only the AI's response; no explanation is needed), a technique called prompt engineering must be used appropriately.

If you don't use the proper prompts, your response will look like this.

> Prompt
> 
> ```
> The sky is
> ```
> 
> Output:
> 
> ```
> blue
> 
> The sky is blue on a clear day. On a cloudy day, the sky may be gray or white.
> ```
>
> https://www.promptingguide.ai/introduction/basics#basic-prompts

### [few-shot prompting](https://www.promptingguide.ai/techniques/fewshot)

Whenever You create a new room, you always start with a greeting automatically because the beginning of the conversation is unlikely to be responded to correctly by the AI.

It also begins with a greeting in the language set for the room. This increases the likelihood that the AI will respond in that language.
The "few-shot" increases as the conversation continues, increasing the likelihood of a correct response.

## Secutity

- Cloudflare's reverse proxy hides the backend server's IP address, preventing domain-based attacks.
- OAuth authentication enhances security, reducing the risk of password and data exposure.

## Server Monitoring

I maintain server health and performance through continuous monitoring and health checks using Zabbix.
