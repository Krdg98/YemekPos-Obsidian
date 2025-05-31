Prometheus pull yapısı gereği verileri belirlenen bir noktadan çeker. PushGateWay ona çevirileri çekebileceği bir havuz sonar ve dışarıdan gelen veriler bu havuzda toplanır proemtheus lazım olduğunda bu havuzdan verileri toplar.

---
### Kullanım Senaryoları:

- **Kısa Ömürlü İşler**: Batch işler gibi kısa süre çalışan uygulamalar, metriklerini doğrudan Prometheus'a sunamaz. Bu durumda metrikler Pushgateway'e gönderilir.
- **Manuel Metrik Gönderme**: Örneğin, bir script ile metrik üretip bunu Prometheus'a iletmek istediğinizde Pushgateway kullanılabilir.
- **Dağıtık Sistemler**: Metriklerin merkezi bir noktadan toplanması gerektiğinde.

### Nasıl Çalışır?

1. Pushgateway, genellikle bir HTTP sunucusu olarak çalışır (varsayılan port: 9091).
2. Metrikler, aşağıdaki gibi bir HTTP POST isteğiyle Pushgateway'e gönderilir:
```
echo "some_metric 42" | curl --data-binary @- http://pushgateway:9091/metrics/job/some_job
```
