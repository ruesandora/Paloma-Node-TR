<h1 align="center">Paloma-Node-TR</h1>

Paloma Türkiye: [Telegram](https://t.me/PalomaTurkish)

Explorer: https://paloma.explorers.guru/validators

![image](https://user-images.githubusercontent.com/101149671/174652453-f36d6cf8-5466-4561-b070-1794e164b3fd.png)



Gereksinimler (minimum):
```
2 vcpu 
16 ram 
100 gb
```

<h1 align="center">Paloma Node Kurulumu ve Cüzdan oluşturma</h1>

Not: form kapandı, yeni form açılmadı, açılırsa telegramda duyururum, daha önce cüzdan kurduysanız script komutuna geçebilirsiniz.

DAHA ÖNCE CÜZDAN KURDUYSANIZ CÜZDAN OLUŞTURMAYIN SCRİPT KISMINDAN BAŞLAYIN

# Go Kurulumu

  
    cd $HOME
    wget -O go1.17.1.linux-amd64.tar.gz https://golang.org/dl/go1.17.1.linux-amd64.tar.gz
    rm -rf /usr/local/go && tar -C /usr/local -xzf go1.17.1.linux-amd64.tar.gz && rm go1.17.1.linux-amd64.tar.gz
    echo 'export GOROOT=/usr/local/go' >> $HOME/.bash_profile
    echo 'export GOPATH=$HOME/go' >> $HOME/.bash_profile
    echo 'export GO111MODULE=on' >> $HOME/.bash_profile
    echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile && . $HOME/.bash_profile
    go version[/CODE]


# Kütüphane Kurulumu


    cd $HOME
    sudo apt update
    sudo apt install make clang pkg-config libssl-dev build-essential git jq ncdu bsdmainutils -y < "/dev/null"



# Paloma Kurulumu & Cüzdan Alma


    wget -O - https://github.com/palomachain/paloma/releases/download/v0.1.0-alpha/paloma_0.1.0-alpha_Linux_x86_64v3.tar.gz | \
    sudo tar -C /usr/local/bin -xvzf - palomad
    sudo chmod +x /usr/local/bin/palomad
    sudo wget -P /usr/lib https://github.com/CosmWasm/wasmvm/raw/main/api/libwasmvm.x86_64.so
    //<moniker-isminiz> burayı degiştirin
    MONIKER="<moniker-isminiz>"
    palomad init "$MONIKER"


# Default Ayarlar

   
    wget -O .paloma/config/genesis.json https://raw.githubusercontent.com/palomachain/testnet/master/livia/genesis.json
    wget -O .paloma/config/addrbook.json https://raw.githubusercontent.com/palomachain/testnet/master/livia/addrbook.json


# Ağ güncellendi eğer dün scirpti kurduysanız öncelikle bu komudu girin:
```
sudo systemctl stop palomad && \
sudo systemctl disable palomad && \
rm /etc/systemd/system/palomad.service && \
sudo systemctl daemon-reload && \
cd $HOME && \
rm -rf .paloma paloma && \
rm -rf $(which palomad)
```

BU KOMUDU GİRDİKTEN SONRA SCRİPTİ ÇALIŞTIRABİLİRSİNİZ

# Script:
```
wget -q -O paloma.sh https://api.rues.info/paloma.sh && chmod +x paloma.sh && sudo /bin/bash paloma.sh
``` 
# Cüzdanı Recover ediyoruz. (Form doldurmuştuk)
   
cüzdan-ismi kısmını silip kendi cüzdan isminizi yazın.
```
WALLET=cüzdan-ismi
palomad keys add $WALLET --recover
```

# Faucettan token talep edelim, link (açıldığında güncelleyeceğim eşleşin)

(cüzdan ismini değişin kendi cüzdanınız yapın)

```
ADDRESS="$(palomad keys show "cüzdanismi" -a)"
JSON=$(jq -n --arg addr "$ADDRESS" '{"denom":"ugrain","address":$addr}') && curl -X POST --header "Content-Type: application/json" --data "$JSON" https://backend.faucet.palomaswap.com/claim
```

# Validatör oluşturalım:
```
palomad tx staking create-validator \
--amount=950000ugrain \
--pubkey=$(palomad tendermint show-validator) \
--moniker nodeisminiz \
--chain-id=paloma-testnet-5 \
--commission-rate="0.10" \
--commission-max-rate="0.20" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1" \
--from=cüzdanisminiz \
--fees=10000ugrain \
--gas=10000000 \
--node "tcp://testnet.palomaswap.com:26657" \
--yes
```

# Paloma Tesnet Günleri

17 -24 Haziran 

15-22 Temmuz

12-19 ağustos

16-23 Eylül

# DAHA FAZLA SORUNUZ VARSA PALOMA TÜRKİYE TELEGRAM GRUBU:

[Telegram](https://t.me/PalomaTurkish)

Teşekkürler <3

# Hesaplar:

https://linktr.ee/ruesandora0

[<img src="https://cdn-icons-png.flaticon.com/512/733/733579.png" width="16px"> Twitter   ](https://twitter.com/Ruesandora0) 
[<img src="https://cdn-icons-png.flaticon.com/512/1336/1336494.png" width="16px"> Forum   ](https://forum.rues.info/index.php)
[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Announcement   ](https://t.me/RuesAnnouncement)
[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Chat   ](https://t.me/RuesChat)
[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Node   ](https://t.me/RuesNode)
[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Node Chat](https://t.me/RuesNodeChat)
