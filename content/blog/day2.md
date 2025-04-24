---
title: "#100日チャレンジ day1"
date: 2025-04-24
draft: false
tags: ["blog", "#100日チャレンジ"]
---

# Day2 簡易Pingツール
`#100日チャレンジ`を始めてみました.  
これはDay2の記事です.  
`subprocess`を使用して任意の宛先にPingを送るツールを作りました。    

使用した言語はPython. versionは`Python 3.12.3`  
使用したのは`subprocess` 

```python
target = input()
```
これで宛先を取得  
(例: google.com, 1.1.1.1)

```python
response = subprocess.run(["ping", "-c", "1", target], capture_output=True, text=True)
```
これでpingの送信が行われる

`subprocess.run`で外部コマンドを呼べる.  
`ping`のところでなんのコマンドを実行するのかを定義.`-c`などはpingで使われるオプションを指定している.  