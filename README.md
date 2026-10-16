# LLM Tabanlı Dinamik Guardrail Mimarisi

Kurumsal yapay zekâ sistemlerinde **Prompt Injection** ve **hassas veri sızıntısı** saldırılarını engellemek amacıyla geliştirilmiş, Python tabanlı, iki aşamalı bir Guardrail mimarisi.

Bu proje, İstanbul Aydın Üniversitesi Yönetim Bilişim Sistemleri lisans bitirme tezi (60 sayfa) kapsamında geliştirilen Proof of Concept çalışmasıdır.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![OWASP](https://img.shields.io/badge/OWASP-LLM%20Top%2010-black)

---

## Sonuçlar

| Metrik | Değer |
|---|---|
| Test senaryosu sayısı | 100 |
| Doğruluk (Accuracy) | %92 |
| F1 skoru | %91,83 |
| Ortalama ek gecikme | ~15 ms |

Güvenlik katmanı yalnızca 15 ms ek gecikme oluşturduğu için gerçek zamanlı kullanıma uygundur.

---

## Problem

Kurumsal chatbot ve LLM entegrasyonları iki temel riskle karşı karşıyadır. Bu proje, OWASP LLM Top 10 kapsamındaki şu iki riske odaklanır:

- **Prompt Injection:** Kullanıcının, modelin sistem talimatlarını atlatmasına ya da değiştirmesine yönelik girdiler göndermesi.
- **Sensitive Information Disclosure:** Modelin yanıtında hassas ya da gizli bilgilerin sızması.

---

## Mimari

Sistem, modelin iki ucuna yerleştirilen iki katmandan oluşur:

```
Kullanıcı Girdisi
       │
       ▼
┌─────────────────┐
│  Input Guardrail │  → Prompt Injection girişimlerini tespit eder ve engeller
└─────────────────┘
       │ (güvenli girdi)
       ▼
┌─────────────────┐
│       LLM        │
└─────────────────┘
       │
       ▼
┌──────────────────┐
│  Output Guardrail │  → Hassas veri sızıntısını tespit eder ve engeller
└──────────────────┘
       │ (güvenli yanıt)
       ▼
  Kullanıcıya Yanıt
```

**Input katmanı:** Gelen isteği modele ulaşmadan önce analiz eder.
**Output katmanı:** Modelin ürettiği yanıtı kullanıcıya iletmeden önce kontrol eder.



## Sınırlılıklar

- Değerlendirme 100 senaryoluk bir test setiyle yapılmıştır; daha geniş ve çeşitli veri setleriyle doğrulanması gerekir.
- Bu çalışma bir Proof of Concept'tir, doğrudan production kullanımı için tasarlanmamıştır.
- Guardrail katmanları tek başına yeterli bir savunma değildir; çok katmanlı bir güvenlik yaklaşımının parçası olarak düşünülmelidir.

---

## Kullanılan Teknolojiler

Python · OWASP LLM Top 10 · Prompt Injection Analizi · Guardrail Tasarımı

---

## İletişim

**Anıl Özgül**
[LinkedIn](https://www.linkedin.com/in/an%C4%B1l-%C3%B6zg%C3%BCl-a51075337/) · [GitHub](https://github.com/anilozgul) · anilozgul2003@gmail.com
