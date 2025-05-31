Gel Al siparişlerinde [[CustomerAddress]] alanı null geliyor.
OrderMethod ile DeliveryType aynı geliyor ve DeliveryType bilgisi dökümanlarında bulunmuyor. 

UpdateOrder İşlemi

[[GelAl]] siparişlerinde [[ReadyForPickup]] gönderilmelidir. Bunu hazırda gönderdiğinde alınmaya hazır isteği atmış olur

Sipariş durum güncellemesinde hiç bir kontrol yoktur [[GelAl]] siparişi [[Paket Siparişi]] gibi davranılabiliyor. Dikkatli olunmalı

Müşteri siparişi platformun belirlediği süre (siparişi oluşturduktan sonra başlar) içerisinde iptal edebiliyor. Süre dolduktan ekran üzerinden iptal yapamıyor restoranı arayarak iptal etmesi gerekir.
