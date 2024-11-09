# Fizz Setup Guide

Bu rehber, bir Fizz instance'ını Ubuntu sunucusunda yapılandırmak için gerekli kurulum adımlarını içerir. İçerisinde; sistem güncelleme, Docker ve Docker Compose kurulumu, izinlerin ayarlanması, swap dosyası oluşturulması ve Fizz kurulum script'inin çalıştırılması gibi adımlar yer almaktadır.

## Gereksinimler
- Ubuntu sunucusu
- SFTP erişimi (dosya yüklemek için)

## 1. Sistemi Güncelle ve Yükselt

Sistem paketlerini güncellemek ve yükseltmek için aşağıdaki komutu çalıştırın:

```bash
sudo apt update -y && sudo apt upgrade -y
```
