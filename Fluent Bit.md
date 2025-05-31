Log toplayıcı. Topla işler ve iletir.

Her Refresh_Interval dosya boyutunda bir fark var mı kontrolü yapılır. Eğer okunan satırların **offset** değeri tutuluyor ise kaldığı yerden devam eder.

DB parametresi belirtilmezse tail plugin her **Refresh_Interval** döngüsün de tüm log satırlarını baştan okur.

**Inotify_Watcher** değeri **On** yapılırsa loglar gerçek zamanlı olarak yakalanır.

### Match
Filter ya da Output hangi log kayıtlarına uygulancağını belirtir


### 🔹 Kubernetes ile Nasıl Çalışır?

1. Fluent Bit genellikle **DaemonSet** olarak kurulur (her node’da 1 pod).
2. Her node’daki pod, o node’daki container loglarını okur (`/var/log/containers/...`).
3. Logları işler ve istenilen yere gönderir (örneğin: OpenSearch).
### 🔹 Temel Bileşenler

- `[INPUT]` → Log kaynağı (örn. tail ile dosya okuma)
- `[FILTER]` → İşleme (örn. Kubernetes metadata ekleme)
- `[OUTPUT]` → Hedef (örn. OpenSearch)