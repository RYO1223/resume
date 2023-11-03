# AI Voice Talk

## 概要

自分で作成したAIとボイスチャットができるアプリです。

- [App Store](https://apps.apple.com/us/app/ai-voice-talk/id6449139482)
- [Google Play]() - Coming Soon...

---

## アーキテクチャ

![architecture](https://github.com/RYO1223/resume/blob/master/docs/my_applications/AI_Voice_Talk/architecture.jpg?raw=true)

### フロントエンド

- **言語**: Dart/Flutter
- **アーキテクチャ**: View-Service-Repository
- **コアライブラリ**: Riverpod, go_router

### バックエンド

- **言語**: Golang
- **コアライブラリ**: Gin, Zap

### インフラ

- Cloudflare: DNS, Reverse Proxy
- RevenueCat for subscription management
- GCP: Firebase Authentication, Text-to-Speech, Speech-to-Text
- ChatGPT
- Zabbix for server monitoring

---

## 機能詳細

### 基本機能

#### ルーム作成・更新・削除

それぞれのAIごとにルームを作成します。各AIは以下のものを設定できます:

- 名前
- 話す言語
- 性別
- 性格
- 話す速度
- あなたとの関係性
- AIと出会った状況

<img src="https://github.com/RYO1223/resume/assets/70420716/72d5dac5-106f-432f-8cac-f4b5723f4a19" width="30%" />

#### AIと話す

1. **ボイス録音:** あなたが話したことを録音します。
2. **音声データの送信:** バックエンドサーバーに録音データを送信します。
3. **Speach-to-Text 変換:** GCPのSpeak-to-Textを使用して、音声をテキストに変換します。
4. **AIの返答生成:** テキスト、AIの設定、これまでの会話をChatGPTに送信して、AIの返答を生成します。
5. **Text-to-Speach 変換:** GCPのText-to-Speachを使用して、テキストを音声に変換します。
6. **クライアントに送信:** 生成した音声データをクライアントに送信して、再生します。

<img src="https://github.com/RYO1223/resume/assets/70420716/f0062a37-98cb-417b-b15c-64403a678729" width="30%" /><img src="https://github.com/RYO1223/resume/assets/70420716/486673ba-cd74-4fec-bfb2-0a6829a565be" width="30%" />

### マルチデバイスサポート

Firebase AuthenticationとRevenueCatを使用して、同じアカウントでログインしている端末全てで課金機能を使用することができます。

---

## AI 

AIから正しい返答（この場合は設定した人格の返答のみ。説明は必要ないので生成されないようにする。）を生成するためにプロンプトエンジニアリングと呼ばれる手法を使用しています。

もし適切なプロンプトを使用しなければ、このようになります。

> プロンプト
>
> ```
> 空が
> ```
> 
> 出力:
>
> ```
> 青い
> 晴れた日には空は青く、曇った日には空は灰色や白色になることがあります。
> ```
>
> https://www.promptingguide.ai/introduction/basics#basic-prompts

### [Few-Shotプロンプティング](https://www.promptingguide.ai/jp/techniques/fewshot)


ルームを作成してすぐは過去の会話がないため、上記で示したように適切な返答が得られない可能性が高いです。
そのため、ルームを作成するときは常に挨拶から始まるようにしています。

それに加え、AIが必ず設定した言語で返答するように、挨拶はその言語でするようにしています。
会話が続くに連れて適切な応答をする可能性が高まります。

## セキュリティ

- ドメインへの攻撃を防ぐために、Cloudflareのreverse proxyを使用して、バックエンドのIPアドレスを隠しています。
- パスワードやその他の個人情報の漏洩リスクを減らすためにOAuth認証を使用しています。

## サーバーモニタリング

Zabbixを使用して、サーバーのヘルスチェック、パフォーマンスアラームを設定しています。
