# Algorand-Node-Kurulumu-Testnetle-Goracle-Ayni-VPS-de-Yapilandirma

- Öncelikle bir Goracle Node'u kurmak istiyorsanız lütfen aşağıdaki rehbere gidin ve tüm işlemleri eksiksiz yaparak node'unuzu kurun.

https://github.com/Kral001/Goracle-Network-Node-Kurulum-Rehberi

Aşağıdaki işlemler yalnızca Goracle Node'u kurmuş olan ve API'yi purestake olarak değiştirdikten sonra bile aşağıdaki hataları alanlar için oluşturulmuştur. Sık sık buna benzer hatalar alıyorsanız bu işlemleri yapmalısınız.

- Bu Hata: 

![100](https://user-images.githubusercontent.com/98269269/230560236-fcbe4bfd-2f83-4c23-80d2-7817f027c201.png)

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

```
cd /var/lib/algorand/genesis/testnet
```

```
sudo cp genesis.json /var/lib/algorand/
```

```
cd
```

- Şimdi ağ anahtarının tamamlanıp tamamlanmadığını test etmek için:

Node'u başlatalım:

```
sudo systemctl start algorand
```

- Node'un durumunu kontrol edelim:

```
goal node status -d /var/lib/algorand/
```

Sonuç şöyle görünmelidir:

![102](https://user-images.githubusercontent.com/98269269/230562038-0bc32766-25bb-479f-a69d-059957fc983f.png)

Genesis Kimliğini gözlemleyebilirsiniz: testnet-v1.0

1.3. Şimdi Goracle yapılandırmasına koymamız gereken belirteci kopyalayın

```
cd /var/lib/algorand/
```

```
vim algod.token
```

- Sonuç şöyle görünmelidir:

![103](https://user-images.githubusercontent.com/98269269/230562461-417f26f9-f0c1-4bdd-8ab8-69212f28f607.png)

- Ekranda gördüğünüz bu jeton kodunu kopyalayın ve saklayın.

- Vim'i kapatın ve ana Dizine geri dönmek için cd yazın.

1.4. Düğümünüzü hızlı bir şekilde senkronize etmek için aşağıdaki komutu kullanabilirsiniz:

- Bu bağlantıya tıklayın ve ekrandaki kodu kopyalayın.

https://algorand-catchpoints.s3.us-east-2.amazonaws.com/channel/testnet/latest.catchpoint

- Kopyaladığınız kodu aşağıda gördüğünüz BURAYAYAPIŞTIRIN yazan yere yapıştırın.

```
goal node catchup BURAYAYAPIŞTIRIN -d /var/lib/algorand/
```




























