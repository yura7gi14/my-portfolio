---
title: "Day6 - ドメインIP変換＆逆引きCSV保存ツール"
date: 2025-04-28
description: "複数のドメインをIPアドレスに変換＋逆引きして結果をCSVに保存するCLIツール"
tags: ["Python", "ネットワーク", "ツール"]
tech: ["Python 3.12", "socket", "csv"]
github: "https://github.com/yura7gi14/Day/tree/main/day6"
draft: false
---

Python の標準ライブラリ `socket` と `csv` を使って、  
複数ドメインをIPアドレスに変換し、逆引きホスト名も取得して、結果をCSVに保存するCLIツールを作成しました。

### 使用技術
- Python 3.12
- socket
- csv

### 機能概要
- 入力ファイル（ドメインリスト）からドメイン名を読み込み
- 各ドメインについてIPアドレスを取得
- IPアドレスから逆引きホスト名も取得
- 成功/失敗のステータスを付与
- すべての結果をCSVファイルに保存

### GitHubリポジトリ
👉 [Day6 - ドメインIP変換＆逆引きCSV保存ツール](https://github.com/yura7gi14/Day/tree/main/day6)
