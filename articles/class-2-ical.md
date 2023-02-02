---
title: "大学とかの時間割を簡単にカレンダーアプリで表示出来るようにするアプリを作った"
emoji: "🗓️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: \["nextjs", "typescript", "tauri"]
published: false
---

# 作ったもの

https://class2ical.mochi33.comjjjjjjjj

<https://github.com/mochi-sann/class2ical/releases> からダウンロードすればデスクトップアプリとしても使えます(mac でしか動作確認してないけど Windows や Linux でもちゃんと動くはず)

# どんなものなのか？

![webアプリの画像](https://storage.googleapis.com/zenn-user-upload/719562a1ce52-20230117.png)

時間割表に授業とかを入力して、ダウンロードボタンを押すと iClander 形式でファイル雨がダウンロードされるのでそのファイルを Apple カレンダーや、Google カレンダーにインポートするとカレンダーの表示されます。

# 動機

大学の生徒用サイトにアクセスして授業を確認するのが面倒くさいから、Google カレンダーや Apple カレンダーに時間割を表示できるようにしたかったから。

# 技術の話

- フロントエンドフレームワーウ Next.js
  - フロントエンドで完結しているので Next.js の Static HTML Export をして CloudFlare pages にデプロイしています
- デスクトップアプリフレームワーク Tauri
  - このアプリはデスクトップアプリにする必要性はあまりありませんでしたが、Tauri を使ってみたかったので使ってみました。Electron よりもかなりアプリの容量が小さくなって、良さそうな感じでした。
- .ics ファイルの出力 [ical-generator](https://github.com/sebbo2002/ical-generator)
  - このライブラリーを発見したのがこのこのアプリを作り始めたきっかけです。ドキュメントサイトや、型がしっかりしていて開発しやすくてよかったです。
- テストライブラリ Vitest
  - 下にも書きましたが、Jest より早いという評判を見たので入れてみました。結果 Jest よりもとても早く、テスト結果を見な関数を修正したり、テストを作るのがすごくやりやすかったです。
- 日付・時間の管理 dayjs
  - 日付や時間の管理に使いました。開發初期にタイムゾーンの設定がうまく出来て無かったため、授業の時刻がちゃんと設定できず、原因を探すのに苦労しました。
- フォームライブラリ React Hook Form
  - React のフォームライブラリではこれが一番慣れているのでこれを採用しました

web サイトでは nextjs の Static HTML Export をして CloudFlare Pages にデプロイしています。

デスクトップアプリでは、nextjs の Static HTML Export したものを Tauri 上で動かしています。Electron と比べて Tuari はアプリサイズが圧倒的に小さいので良かったです。

## テスト

Unit テストには Vitest を使って実行しています。実行速度が Jest に比べて早く「コードを書く → テストを実行する → コードを書く →...」が早く回せてストレスなく開発ができました。また GitHub Actions で実行しています。![こんな感じで動いています](https://github.com/mochi-sann/class2ical/actions/workflows/ci.yml)
あとは、機能の修正や、追加をするときにテストのエラーを見レバどこのコードを修正すればいいのかがわかりやすいので新機能の開発を安心して行えました。

# 最後に

ぜひ使ってください！！！！！
