---
title: "#100日チャレンジ day1"
date: 2025-04-23
draft: false
tags: ["blog", "#100日チャレンジ"]
---

# Day1 IP情報の表示ツール
`#100日チャレンジ`を始めてみました.  
これはDay1の記事です.  

使用した言語はPython. versionは`Python 3.12.3`  
モジュールとしてsocketを使用している.  

```python
hostname = socket.gethostname()
```
これでホスト名を取得し, 

```python
ip_address = socket.gethostbyname(hostname)
```
これでIP情報を取得.

`gethostname`でシステムの標準のホスト名を取得.  
`gethostbyname`でインターネットに出るためのルータに接続しているインターフェースのローカルIPアドレスを取得.  