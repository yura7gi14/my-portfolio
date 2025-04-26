---
title: "#100日チャレンジ day4"
date: 2025-04-26
draft: false
tags: ["blog", "#100日チャレンジ"]
---

# Day4 TCPポートスキャナ
`#100日チャレンジ`を始めてみました.  
これはDay4の記事です.  
指定したIPアドレスやドメインの指定した範囲のポートが開いているかをチェックするツールです.   

使用した言語はPython. versionは`Python 3.12.3`  
使用したのは`socket`

```python
target = input("target:")
port_target_start = int(input("target port start:"))
port_target_end = int(input("target port finish:"))
```
これでスキャンするIP addressとポート範囲を指定  


```python
for port in range(port_target_start, port_target_end + 1):
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(0.5)
    result = sock.connect_ex((target, port))

    if result == 0:
        print(f"Port {port} is OPEN")
    else:
        print(f"Port {port} is closed")

    sock.close()
```
TCP通信用のソケットを作成し、指定したIPアドレスとポートに接続を試みます.  
成功したら0を返し、失敗すればエラーコードを返す.  
それに応じたif elseで結果を表示.  

応答の待ち時間の上限を設定している.  