Project Name: Fizz Setup Guide
Bu depo, bir Fizz instance'ını Ubuntu sunucusunda yapılandırmak için gerekli kurulum talimatlarını ve script'leri içerir. Bu rehber; sistem güncellemeyi, Docker ve Docker Compose kurulumunu, gerekli izinleri ayarlamayı, swap dosyası oluşturmayı ve Fizz kurulum script'ini çalıştırmayı kapsar.

Gereksinimler
Ubuntu sunucusu
Dosya yüklemek için SFTP erişimi
Sistemi Güncelle ve Yükselt
Sistem paketlerini güncellemek ve yükseltmek için aşağıdaki komutu çalıştırın:

bash
Kodu kopyala
sudo apt update -y && sudo apt upgrade -y
Gerekli paketleri kurun:

bash
Kodu kopyala
sudo apt install ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev tmux iptables curl nvme-cli git wget make jq libleveldb-dev build-essential pkg-config ncdu tar clang bsdmainutils lsb-release libssl-dev libreadline-dev libffi-dev jq gcc screen unzip lz4 -y
Docker'ı Kur
Docker deposunu ayarlayın ve Docker'ı kurun:

bash
Kodu kopyala
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
docker version
Docker Compose'u Kur
Docker Compose'u kurun:

bash
Kodu kopyala
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)
curl -L "https://github.com/docker/compose/releases/download/$VER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose --version
Kullanıcı İçin Docker İzinleri
Kullanıcınıza Docker izinleri ekleyin:

bash
Kodu kopyala
sudo groupadd docker
sudo usermod -aG docker $USER
Swap Dosyası Oluşturma
Bellek yönetimini iyileştirmek için 4GB'lık bir swap dosyası oluşturun:

bash
Kodu kopyala
sudo fallocate -l 4096M /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
Fizz'i SFTP ile Kur
Fizz Network adresinden kurulum dosyasını indirin.
SFTP kullanarak bu dosyayı sunucunuza yükleyin.
Kurulumu Çalıştırma
Script'i çalıştırılabilir hale getirin:

bash
Kodu kopyala
chmod +x /root/fizzup.sh
Bir ekran oturumu başlatın:

bash
Kodu kopyala
screen -S fizz
Kurulum script'ini çalıştırın:

bash
Kodu kopyala
sh /root/fizzup.sh
Docker Loglarını Görüntüleme
Docker loglarını izlemek için aşağıdaki komutu kullanın:

bash
Kodu kopyala
docker compose -f ~/.spheron/fizz/docker-compose.yml logs -f
