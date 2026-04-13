# HTTP İsteğinin Anatomisi

## 1. HTTP

HTTP (HyperText Transfer Protocol), istemci (client) ile sunucu (server) arasında veri iletişimini sağlayan temel protokoldür. Web tarayıcıları ile sunucular arasındaki tüm veri alışverişi HTTP üzerinden gerçekleşir. HTTP, uygulama katmanında çalışan ve stateless (durumsuz) bir protokoldür. Her istek bağımsız olarak değerlendirilir ve sunucu önceki istekleri hatırlamaz. Bu çalışmada, bir HTTP isteğinin yapısı ve bileşenleri detaylı olarak incelenmiştir.

---

## 2. HTTP İsteğinin Çalışma Mantığı

Bir HTTP isteği şu adımlarla gerçekleşir:

1. Kullanıcı tarayıcıya URL girer
2. Tarayıcı DNS üzerinden IP adresini çözer
3. Sunucuya HTTP isteği gönderilir
4. Sunucu isteği işler
5. HTTP yanıtı (response) döndürülür

![HTTP Diagram](https://www.oreilly.com/api/v2/epubs/urn:orm:book:9781789349863/files/assets/5d678947-2cad-44df-a4a4-5e78fd50fb52.png)


## 3. HTTP İsteğinin Yapısı

Bir HTTP isteği temel olarak üç ana bölümden oluşur:

```
                                          +------------------+
                                          |   HTTP Request   |
                                          +------------------+ 
                                          /        |        \
                                         /         |         \
                                        /          |          \
                             +-------------+  +---------+  +--------+
                             | Request Line|  | Headers |  |  Body  |
                             +-------------+  +---------+  +--------+
```
### 3.1 Request Line (İstek Satırı)

İstek satırı, yapılan isteğin temel bilgilerini içerir:

* HTTP Metodu (GET, POST, PUT ve DELETE)
    * **GET:** Veri almak için kullanılır.
    * **POST:** Sunucuya veri göndermek için kullanılır.
    * **PUT:** Var olan veriyi güncellemek için kullanılır.
    * **DELETE:** Veri silmek için kullanılır.
* İstenen kaynak (URL)
* HTTP Versiyonu

**Örnek:**

```
GET /index.html HTTP/1.1
```

---

### 3.2 Header (Başlıklar)

Header kısmı, istemci hakkında ve istekle ilgili ek bilgileri içerir.

**Örnek Headerlar:**

```
Host: www.bahadirsina.com
User-Agent: Mozilla/5.0
Accept: text/html
Connection: keep-alive
```

Header'lar sayesinde sunucu, istemcinin özelliklerini ve beklentilerini anlayabilir.

---

### 3.3 Body (Gövde)

Body kısmı, genellikle POST ve PUT isteklerinde veri taşımak için kullanılır.

**Örnek:**

```
{
  "username": "bahadir",
  "password": "123456"
}
```

**⚠️ Dikkat:** GET isteklerinde genellikle body bulunmaz.

---

## 4. Örnek HTTP İsteği

```
+--------------------------------------------------+
|                 HTTP REQUEST                     |
+--------------------------------------------------+
|                                                  |      
|              POST /login HTTP/1.1                |       ← Request Line
|                                                  | 
+--------------------------------------------------+
|                                                  |
|          Host: www.bahadirsina.com               |          
|          Content-Type: application/json          |       ← Headers
|          Content-Length: 48                      |
|                                                  |
+--------------------------------------------------+
|                                                  |
|           {                                      |
|             "username": "bahadir",               |       ← Body
|             "password": "123456"                 |
|           }                                      |
+--------------------------------------------------+
```
