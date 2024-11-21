## Fizz Node v1.1.4 Güncellemesi

### 21/11/2024 Tarihinde Gelen Fizz Node Güncellemesi : 

### Link : https://fizz.spheron.network/ Üzerinden Sunucumuz için güncel script'i indirelim.

![image](https://github.com/user-attachments/assets/22fa6005-2381-4a70-9e83-3cb7868c58db)

### İndirdikten sonra SFTP ile dosyayı sunucumuza aktaralım : 

- Termius kullanıyorsanız dosyayı root dizinin altına sürüklemeniz yeterli olacaktır. Doğru dosyayı sürüklediğinizden emin olun. Eski script olmasın :)

![image](https://github.com/user-attachments/assets/ce27da95-b803-47f2-8be2-08e2a56dde6d)

## Yetki Verelim : 

```bash
chmod +x fizzup-v1.1.1.sh
```
## Script'i Çalıştıralım : 

```bash
bash fizzup-v1.1.1.sh
```

### Kendisi eski çalışanı kapatacak - yeni containeri oluşturup başlatacaktır. Sonrasında Loglar gelecektir.

![image](https://github.com/user-attachments/assets/f9084449-e8da-4269-a2d3-7ed1c1468cdb)

- CTRL C ile çıkabilirsiniz - herhangi bir sakınca yoktur. Çalışmayı durdurmaz.

### Dilerseniz ara ara yeniden logları kontrol etmek için : 

```bash
docker-compose -f ~/.spheron/fizz/docker-compose.yml logs -f
```
