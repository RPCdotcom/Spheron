## Fizz Node v1.1.7 Güncellemesi

### 8/12/2024 Tarihinde Gelen Fizz Node Güncellemesi : 

### Link : https://fizz.spheron.network/ Üzerinden Sunucumuz için güncel script'i indirelim.

![image](https://github.com/user-attachments/assets/22fa6005-2381-4a70-9e83-3cb7868c58db)

### İndirdikten sonra SFTP ile dosyayı sunucumuza aktaralım : 

- Termius kullanıyorsanız dosyayı root dizinin altına sürüklemeniz yeterli olacaktır. Doğru dosyayı sürüklediğinizden emin olun. Eski script olmasın :)

![image](https://github.com/user-attachments/assets/37294168-c5b3-4522-9e13-09b380fe4414)

## Yetki Verelim : 

```bash
chmod +x fizzup-v1.1.2.sh
```
## Script'i Çalıştıralım : 

```bash
bash fizzup-v1.1.2.sh
```

#### Kendisi eski çalışanı kapatacak - yeni containeri oluşturup başlatacaktır. Sonrasında Loglar gelecektir.

![image](https://github.com/user-attachments/assets/f9084449-e8da-4269-a2d3-7ed1c1468cdb)

- CTRL C ile çıkabilirsiniz - herhangi bir sakınca yoktur. Çalışmayı durdurmaz.

### Dilerseniz ara ara yeniden logları kontrol etmek için : 

```bash
docker-compose -f ~/.spheron/fizz/docker-compose.yml logs -f
```
#### Paneliniz üzerinden Kontrol Edebilirsiniz. Artık Güncel bir şekilde devam edecektir.

![image](https://github.com/user-attachments/assets/f35de96f-12dc-4233-981b-6149d644a836)
