# AI Voice Talk

## 概要

このアプリは、STT（音声認識）、ChatGPT（AI対話）、TTS（テキストから音声へ）の技術を活用して、ユーザーの音声データからAIの返答を音声データとして再生します。

---

## アーキテクチャ

![architecture](https://github.com/RYO1223/resume/blob/master/docs/my_applications/AI_Voice_Talk/architecture.jpg?raw=true)

### フロントエンド

- **技術スタック**: Flutter
- **通信**: WebSocket

### バックエンド

- **技術スタック**: Golang
- **通信**: WebSocket

### インフラストラクチャ

- **DNS**: Cloudflare
- **セキュリティ**: Cloudflareのリバースプロキシ
- **課金**: RevenueCat

---

## 機能詳細

### 基本機能

1. **音声認識 (STT)**
    - ユーザーの音声データをテキストデータに変換します。

2. **AI対話 (ChatGPT)**
    - 音声認識で得られたテキストをAIが解析し、適切な返答を生成します。

3. **テキストから音声へ (TTS)**
    - AIの返答を音声データに変換して再生します。

### カスタマイズ機能

- AIの性格、性別、話す速度などはユーザーが設定可能です。

### サブスクリプション

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

