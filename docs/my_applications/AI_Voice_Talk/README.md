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

- **Language**: Golang/Gin
- **Connection**: WebSocket

### Infrastructure

- Cloudflare: DNS, Reverse Proxy
- RevenueCat
- GCP: Firebase Authentication, Text-to-Speech, Speech-to-Text
- ChatGPT

---

## Function Detail

### Basic Function

1. Room Creation, Update, Deletion

AIの性別や性格、話す速度、自分との関係性や出会うシチュエーションを設定できます。

2. Talk with AI

マイクボタンを押しながら話すと録音されてサーバーに送信されます。
その後、sttによりテキストになり、それを、AIの性格やこれまでの会話と合わせてChatGPTに送信します

1. **音声認識 (STT)**
    - ユーザーの音声データをテキストデータに変換します。

2. **AI対話 (ChatGPT)**
    - 音声認識で得られたテキストをAIが解析し、適切な返答を生成します。

3. **テキストから音声へ (TTS)**
    - AIの返答を音声データに変換して再生します。

### カスタマイズ機能

- AIの性格、性別、話す速度などはユーザーが設定可能です。

### Subscription

- サブスクに加入することで上記の機能がフルに利用できます。

### マルチデバイス対応

- RevenueCatを用いて、ユーザーは同じアカウントで複数の端末でアプリを使用できます。

---

## セキュリティ

- Cloudflareのリバースプロキシを通すことで、セキュリティ対策を強化しています。
- HTTPSリダイレクトも行っています。

---

## 連絡先

- **Email**: [your-email@example.com](mailto:your-email@example.com)
- **GitHub**: [your-github-profile](https://github.com/your-github-profile)

