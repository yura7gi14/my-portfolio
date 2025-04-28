---
title: "#100日チャレンジ day6"
date: 2025-04-28
draft: false
tags: ["blog", "#100日チャレンジ"]
---

# Day6 ドメインIP変換＆逆引きCSV保存ツール
`#100日チャレンジ`を続けています。  
これはDay6の記事です。  
複数のドメインをIPアドレスに変換し、さらに逆引きホスト名も取得して、結果をCSVファイルに保存するツールを作成しました。

使用した言語はPython。versionは`Python 3.12.3`  
使用したライブラリは標準ライブラリの`socket`、`csv`、`sys`です。

```python
input_file = sys.argv[1]
output_file = sys.argv[2]
```

コマンドライン引数から、入力ファイル（ドメインリスト）と出力ファイル（CSV）のファイル名を受け取っています。
```python
with open(input_file, "r") as f:
    domains = f.read().splitlines()
```
入力ファイルを読み込み、1行ずつドメイン名としてリスト化しています。  
```python
for domain in domains:
    try:
        ip = socket.gethostbyname(domain)
        try:
            reverse = socket.gethostbyaddr(ip)[0]
        except socket.herror:
            reverse = "-"
        results.append([domain, ip, reverse, "Success"])
    except socket.gaierror:
        results.append([domain, "-", "-", "Failed"])
```
各ドメインに対してIPアドレス取得を行い、成功すればさらに逆引きホスト名を取得します。  
エラー（存在しないドメインや逆引き失敗など）もきちんと例外処理して、失敗として記録しています。  
```python
with open(output_file, "w", newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["domain", "ip_address", "reverse_lookup", "status"])
    writer.writerows(results)
```
最終的に、変換結果をCSV形式で出力しています。
カラムは「ドメイン名」「IPアドレス」「逆引きホスト名」「ステータス（成功/失敗）」です。  