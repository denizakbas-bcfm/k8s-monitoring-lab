# Kubernetes Synthetic Monitoring & Alerting Pipeline

Bu proje; Minikube üzerinde barındırılan bir web uygulamasına (NGINX), dışarıdan (blackbox) HTTP sağlık kontrolleri uygulayan ve servis kesintilerinde otomatik alarm tetikleyen uçtan uca bir izleme hattıdır.

---

## 🏛️ Mimari Akış

```text
[ NGINX Web Service ] (Hedef / Port 80)
        ▲
        │  (HTTP GET / 200 OK Kontrolü)
        │
[ Blackbox Exporter ] (Prober / Port 9115)
        ▲
        │  (/probe endpoint'inden metrik toplama)
        │
[ Prometheus ] (Zaman Serisi Deposu & Alert Engine)
        │
        └──► [ WebSiteDown Alarmı ] ──► (Pending ── 10s ──► Firing)
# Kubernetes Blackbox & Prometheus Monitoring Lab

Minikube üzerinde çalışan web servisinin Blackbox Exporter ve Prometheus ile sentetik izleme (synthetic monitoring) ve alerting hattı.

## Alarm Kuralı
- **Kural:** `WebSiteDown`
- **Şart:** `probe_success == 0` (for: 10s)
- **Doğrulama:** Web servisi replicas=0 yapıldığında alarmın Pending -> Firing durumuna geçtiği doğrulanmıştır.
