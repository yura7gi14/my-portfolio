---
title: "#100日チャレンジ day3"
date: 2025-04-25
draft: false
tags: ["blog", "#100日チャレンジ"]
---

# Day3 簡易ネットワークスキャナ
`#100日チャレンジ`を始めてみました.  
これはDay3の記事です.  
Day2で作ったpingを送信するコードを弄り、複数のIPに対してPingを送信して生きてるIPを判定できるように.  

使用した言語はPython. versionは`Python 3.12.3`  
使用したのは`subprocess`, `ipaddress`

```python
ip_addr = input("ip address:")
net = ipaddress.ip_network(ip_addr)
ips = [str(ip) for ip in net.hosts()]
```
これで送信するIP addressを指定  
宛先のip addressはCLI上で指定可能

```python
for ip in ips:
    print(f"{ip}にping中...")

    response = subprocess.run(
        ["ping", "-c", "1", "-W", "1", ip],
        capture_output=True,
        text=True
    )

    if response.returncode == 0:
        print(f"{ip}は生存している\n")
    else:
        print(f"{ip}は応答なし")
```
これでpingの送信が行われる  
送信されれば`生存している`, 送信されなければ`応答なし`と表示

`subprocess.run`で外部コマンドを呼べる.  
`ping`のところでなんのコマンドを実行するのかを定義.`-c`などはpingで使われるオプションを指定している.  