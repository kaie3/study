# ネットワーク

## [Liunx で LAN 上のデバイスを探索する](https://oppekepe.org/5609)

Nmap を使用する
デバイスの探索には -sP オプションを使います。\
このオプションでは hostname や MAC アドレスを取得できるほか，\
MAC アドレスの割り当てリストから特定したベンダ名も表示してくれます（MAC アドレスの自己申告に依存します）。\
IP アドレスレンジが 192.168.1.0/24 の場合は以下のようにします（ip addr 等で確認できます）。

```script
sudo apt install nmap #install
sudo nmap -sP 192.168.1.0/24
```

[プロフェッショナルIPv6](https://professionalipv6.booth.pm/items/913273)
