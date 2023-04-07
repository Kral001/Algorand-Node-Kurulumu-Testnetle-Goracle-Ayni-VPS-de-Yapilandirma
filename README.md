# Algorand-Node-Kurulumu-Testnetle-Goracle-Ayni-VPS-de-Yapilandirma

- Öncelikle bir Goracle Node'u kurmak istiyorsanız lütfen aşağıdaki rehbere gidin ve tüm işlemleri eksiksiz yaparak node'unuzu kurun.

https://github.com/Kral001/Goracle-Network-Node-Kurulum-Rehberi

Aşağıdaki işlemler yalnızca Goracle Node'u kurmuş olan ve API'yi purestake olarak değiştirdikten sonra bile aşağıdaki hataları alanlar için oluşturulmuştur. Sık sık buna benzer hatalar alıyorsanız bu işlemleri yapmalısınız.

- Bu Hata: ![100](https://user-images.githubusercontent.com/98269269/230560236-fcbe4bfd-2f83-4c23-80d2-7817f027c201.png)

- Veya Bu Hata: 

2023-04-06T03:17:00.573Z ERROR URLTokenBaseHTTPError: Network request error. Received status 404 (Not Found): failed to retrieve information from the ledger
2023-04-06T03:17:26.123Z ERROR URLTokenBaseHTTPError: Network request error. Received status 404 (Not Found): failed to retrieve information from the ledger

1.BÖLÜM: ALGORAND DÜĞÜMÜNÜ KURUN VE AĞI TESTNET OLARAK DEĞİŞTİRİN

Bunun için ayrı bir vps kullanmıyorsunuz. Algorand düğümü aynı vps içinde kurulacaktır.

1.1.Algorand ve diğer araçları indirin. Bu komutları birer birer çalıştırın:

```
sudo apt-get update
```

```
sudo apt-get install -y gnupg2 curl software-properties-common
```

```
curl -o - https://releases.algorand.com/key.pub | sudo tee /etc/apt/trusted.gpg.d/algorand.asc
```

```
sudo add-apt-repository "deb [arch=amd64] https://releases.algorand.com/deb/ stable main"
```

```
sudo apt-get update
```

```
sudo apt-get install -y algorand-devtools
```

- Yüklemenin başarıyla tamamlandığını doğrulamak için şunu çalıştırın:

```
algod -v
```

- Sonuç şöyle görünmelidir:

![101](https://user-images.githubusercontent.com/98269269/230561139-c6f40559-0e4a-4389-8abe-5d197b333125.png)

1.2.Genesis Dosyasını Testnet Klasöründen Algorand'daki Data Klasörüne Kopyalayarak Ağı Mainnet'ten Testnet'e Geçirin:













