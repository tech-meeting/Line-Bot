# 1 準備
- nodeのインストール
- npmのインストール

## 手元のバージョン
npm : 6.9.0
node : 10.16.0

## 準備
```
npm init
npm i @line/bot-sdk express
```

# 2 実装
## コードを書く
(コードのサンプル)[./index.json]

# 3 ngrokでローカルホストを公開
## インストール
https://dashboard.ngrok.com/get-started
ngrokをインストール

## アカウント作成
ngrokのアカウントを作成

## ポート番号の設定
3000にしておく

## 公開
```
const PORT = process.env.PORT || 3000;
```

## デバッグ
管理画面のQRコードを読み込んで使ってみる

# 4 zeitでデプロイ
## インストール
```
npm i -g now
```

## 登録
https://zeit.co/signup

```
now login
```

## 環境変数に移動
```
now secret add channel_secret <channelSecret>
now secret add channel_access_token <channelAccessToken>
```

`now.json` を作る
```
{
  "build": {
    "env": {
      "CHANNEL_SECRET": "@channel_secret",
      "CHANNEL_ACCESS_TOKEN": "@channel_access_token"
    }
  }
}

```

## デプロイ
build scriptを追加する
```
"build": "node index.js",
```
