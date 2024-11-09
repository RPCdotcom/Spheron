# Fizz Setup Guide

![image](https://github.com/user-attachments/assets/0c65e079-47e2-4a10-838f-40268d314861)


Bu rehber, bir Fizz instance'ını Ubuntu sunucusunda yapılandırmak için gerekli kurulum adımlarını içerir. İçerisinde; sistem güncelleme, Docker ve Docker Compose kurulumu, izinlerin ayarlanması, swap dosyası oluşturulması ve Fizz kurulum script'inin çalıştırılması gibi adımlar yer almaktadır.

## Gereksinimler
- Ubuntu sunucusu
- SFTP erişimi (dosya yüklemek için)

## 1. Sistemi Güncelle ve Yükselt

Sistem paketlerini güncellemek ve yükseltmek için aşağıdaki komutu çalıştırın:

```bash
sudo apt update -y && sudo apt upgrade -y
```
## 2. Gerekli paketleri kurun:

```bash
sudo apt install ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev tmux iptables curl nvme-cli git wget make jq libleveldb-dev build-essential pkg-config ncdu tar clang bsdmainutils lsb-release libssl-dev libreadline-dev libffi-dev jq gcc screen unzip lz4 -y
```
## 3. Docker'ı Kur : 

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
docker version
```

## 4. Docker Compose'u Kur : 

```bash
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)
curl -L "https://github.com/docker/compose/releases/download/$VER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

## 4. Docker Kullanıcı İzinleri

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

## Swap Dosyası Oluşturma : 

```bash
sudo fallocate -l 2096M /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

## Fizz Kurulumu
Setup:

Fizz Setup Linki ile sunucu bilgilerinizi girin ve dosyayı indirin. https://fizz.spheron.network/
Bu dosyayı SFTP ile sunucunuza yükleyin.

![image](https://github.com/user-attachments/assets/066e318b-c04e-4422-8592-b3479e3d53bc)


## Çalıştırma Adımları:
Dosyaya çalıştırma izni verin:

```bash
chmod +x ~root/fizzup-v1.1.2.sh
```

## Screen : 

```bash
screen -S fizz
```

## Sunucuya SFTP Olarak Yüklediğin Scripti Çalıştır : 

```bash
sh ~root/fizzup-v1.1.2.sh
```

## Docker Loglarını Görüntüleme : 

```bash
docker-compose -f ~/.spheron/fizz/docker-compose.yml logs -f
```








