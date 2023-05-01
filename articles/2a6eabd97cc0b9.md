---
title: "slコマンドとlsコマンドを合体させた「sls」の紹介"
emoji: "🚂"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["deno", "typescipt", "cli", "terminal"]
published: true
---

Deno の勉強でコマンドを作りました

https://github.com/mochi-sann/sls

[![asciicast](https://asciinema.org/a/bs7b3eiVOz8ciOFIcr4O51o3M.svg)](https://asciinema.org/a/bs7b3eiVOz8ciOFIcr4O51o3M)

こんな感じで sl が流れてきて、後ろを引いている貨車の中にファイルの一覧が入っています。

# インストール

```bash
deno install --allow-run --allow-read --name sls https://deno.land/x/sls/cli.ts
```

# 使い方

ファイルの一覧を調べたいフォルダに移動して実行するだけです

```bash
sls
```

## コマンドのオプションなど

```bash
❯ sls --help

  Usage:   sls [dir]
  Version: v1.1.1

  Description:

    show filelist with sl

  Options:

    -h, --help                 - Show this help.
    -V, --version              - Show the version number for this program.
    -s, --speed      <number>  - set Sl speed                               (Default: 30)
    -r, --reverse              - reverse Sl
    -l, --loop                 - loop sl
    --startFromLeft            - sl start from Left
```

# まとめ

いい感じに蒸気とかが動くように頑張りました
