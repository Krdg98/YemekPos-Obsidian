
- Zaman serisi alarak metriclerin tutulmasını sağlar. 
-  Bir **/metrics** en pointine ihtiyacı vardır ve buradan metricleri pull eder.
- [[PushGateWay(Prometheus)]] ile daha optimize kullanılabilir.
- Label kısmı uzatılabilir lakin label alanındaki değişiklik ne kadar fazla ise prometheus tüketimi o kadar artırıyor. 
```
  private static readonly Counter OrderCounter = Metrics
    .CreateCounter("orderhub_order_total", "Sipariş kayıt sayısı",
        new CounterConfiguration
        {
            LabelNames = new[] { "platform", "config_id", "order_status", "process_status" }
        });
```
 
Eğer `platform`, `order_status`, `process_status` da kombinasyona girerse:  
**1000 x 5 x 2 x 2 = 20.000** farklı zaman serisi olabilir!
Bu, Prometheus’un RAM ve performansına doğrudan etki eder.

---
# Pushgatewat

Prometheus pull yapısı ile metricleri çeker ve ilgili enpointen verileri alır. Pushgateway ise metricleri kendisine **Post** ile gelen metricleri tutuar ve Prometheus **Pull** ile ona gelen metricleri alır. Özetle metric havuz görevi görür.

---

# Counter 
İlgili metric sadece artar. Sıfırlanmaz.
### Kullanım Amaçları:

- Toplam API çağrısı sayısı
- Hata/başarı sayısı
- Kafka'ya yazılan toplam mesaj adedi
- Sisteme gelen toplam sipariş sayısı

```
private static readonly Counter RequestCounter = Metrics
    .CreateCounter("api_requests_total", "Toplam API istek sayısı");

RequestCounter.Inc(); // 1 artır
RequestCounter.Inc(3); // 3 artır

```

# Gauge
Artabilen ve azalabilen anlık veri tutan yapı 

### Kullanım Amaçları:

- Bellek kullanımı (RAM)
- İşlemdeki kullanıcı sayısı
- Kuyruktaki mesaj sayısı
- CPU sıcaklığı gibi sistem metrikleri

```
private static readonly Gauge QueueGauge = Metrics
    .CreateGauge("queue_message_count", "Kuyruktaki mesaj sayısı");

QueueGauge.Set(5); // Anlık değeri 5 yap
QueueGauge.Inc();  // 1 artır
QueueGauge.Dec();  // 1 azalt

```

---

# scrape_interval

- Hedef(/metrics) endpointi kaç saniyede bir metrik toplayacağını temsil eder

# scrape_timeout

- Hedef(/metrics) enpointinden veriyi almak için bekleyeceği max. süre

# evaluation_interval

- Prometheus bir kural varsa bu kuralın kaç saniyede bir kontrol edeceğini belirler 

---
