Yemeksepeti yeni siaprişleri gönderir iken onlara verediğimiz base url sonuna "order/{remoteId}" ekliyor bundan dolayı yemeksepetinin url "order/oder" oldu

Restoran durumunu sorgulama işleminde 404 hatası alırsak Yemeksepeti tarafında **remoteVendors** yani CustomerBranchId yanlış tanımlamışlanmış olabilir.

Restoran kapatma ve açma isteği atabilmesi çalışma saatleri içerisinde olması gerekir. "**Changing state is disabled for this restaurant**"  hatası gelirse bilki çalışma saatleri düzgün değil