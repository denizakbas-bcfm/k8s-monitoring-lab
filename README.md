# Kubernetes Blackbox & Prometheus Monitoring Lab

Minikube üzerinde çalışan web servisinin Blackbox Exporter ve Prometheus ile sentetik izleme (synthetic monitoring) ve alerting hattı.

## Alarm Kuralı
- **Kural:** `WebSiteDown`
- **Şart:** `probe_success == 0` (for: 10s)
- **Doğrulama:** Web servisi replicas=0 yapıldığında alarmın Pending -> Firing durumuna geçtiği doğrulanmıştır.
