<h1 align="center">Paloma-Node-TR</h1>

![paloma](https://user-images.githubusercontent.com/101149671/173926483-33d00bf3-861e-4e30-9339-e04360cbd16b.png)


Merhaba Dostlarım, bu yazı da Paloma Ağı için Cüzdan Oluşturup. Kayıt yapacaz..
Paloma Projesi Türkçe Kaynaklar


Öncelikle Kayıt Linki : https://docs.google.com/forms/d/e/1FAIpQLSdSviH22JzZ70wcKd1FTevPOiab7g4fyDA3WphKVpYlKBiqkQ/viewform



# Gerekenler

Paloma Cüzdanı 

Ethereum Cüzdanı 

1 Adet Sunucu



<h1 align="center">Paloma Node Kurulumu ve Cüzdan oluşturma</h1>


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

    
# Cüzdan Oluşturma
   
    // <moniker-ismi> SİLİP İSMİNİZİ GİRİN
    VALIDATOR=<moniker-ismi>
    palomad keys add "$VALIDATOR"[/CODE][CODE][/CODE]


Cüzdanınızı kaydedin ve Testnete başvurun.. 
Yazar :[@muuustafasari](https://twitter.com/muuustafasari) 

# DAHA FAZLA SORUNUZ VARSA PALOMA TÜRKİYE TELEGRAM GRUBU:

[Telegram](https://t.me/PalomaTurkish)

Teşekkürler <3


# Hesaplar:

[<img src="https://cdn-icons-png.flaticon.com/512/733/733579.png" width="16px"> Twitter   ](https://twitter.com/Ruesandora0) 
[<img src="https://cdn-icons-png.flaticon.com/512/1336/1336494.png" width="16px"> Forum   ](https://forum.rues.info/index.php)
[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Announcement   ](https://t.me/RuesAnnouncement)
[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Chat   ](https://t.me/RuesChat)
[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Node   ](https://t.me/RuesNode)
[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Node Chat](https://t.me/RuesNodeChat)

