# Yıldız-Üçgen (Star-Delta) Otomatik Motor Başlatıcı Panosu

Bu depo, yüksek güçlü 3 fazlı asenkron motorların kalkış akımını düşürmek amacıyla kullanılan **Yıldız-Üçgen (Star-Delta) Otomatik Kumanda Devresi**'nin QElectroTech şemasını, simülasyon aşamalarını ve profesyonel pafta çıktısını barındırır.

---

## 🚀 Proje Hakkında
Büyük güçlü asenkron motorlar doğrudan (şebekeye direkt) başlatıldıklarında nominal akımlarının 5 ila 7 katı kadar yüksek kalkış akımı çekerler. Bu proje; motorun ilk kalkış anında **Yıldız ($\text{Y}$)** konfigürasyonunda çalıştırılarak kalkış akımının düşürülmesini, ayarlanan süre sonunda ise otomatik olarak **Üçgen ($\Delta$)** konfigürasyonuna geçerek tam güçte çalışmasını sağlayan endüstriyel kumanda panosu tasarımını kapsar.

---

## ⚙️ Çalışma Mantığı ve Adım Adım Çalışma Senaryosu

1. **Başlatma ve Yıldız Konfigürasyonu ($\text{Y}$ Kalkış):**
   * Operatör `START` butonuna bastığında **Ana Kontaktör (K1)** ve **Yıldız Kontaktörü (K3)** aynı anda devreye girer.
   * Motor sargılarına faz-nötr gerilimi ($V_L / \sqrt{3}$) uygulanır. Böylece motor kalkış akımı ve momenti düşürülerek şebeke üzerindeki olumsuz yüklenme önlenir.
   * Ana kontaktör enerjilendiği an **Zaman Rölesi (ZR)** saymaya başlar.

2. **Geçiş Süreci ve Zaman Rölesi Tetiklenmesi:**
   * Zaman rölesi ayarlanan bekleme süresini (örneğin 3–5 saniye) tamamladığında, Yıldız kontaktörünün (`K3`) hattındaki kapalı kontağını açar.
   * **Yıldız Kontaktörü (`K3`) devreden çıkar.**

3. **Üçgen Konfigürasyonuna Geçiş ($\Delta$ Çalışma):**
   * Yıldız kontaktörü tamamen devreden çıktıktan hemen sonra zaman rölesi Üçgen kontaktörünün (`K2`) hattındaki kontağını kapatır.
   * **Üçgen Kontaktörü (`K2`) devreye girer** ve kendini mühürler.
   * Motor sargılarına tam şebeke gerilimi ($V_L$) uygulanır ve motor nominal devrinde, tam güçte çalışmaya devam eder.

4. **Elektriksel Kilitleme (Interlock Safety):**
   * Yıldız (`K3`) ve Üçgen (`K2`) kontaktörlerinin aynı anda devreye girip fazlar arası kısa devre oluşturmasını önlemek için iki kontaktör arasında **Elektriksel Kilitleme (Interlock)** kullanılmıştır.

5. **Güvenlik ve Koruma Elemanları:**
   * Aşırı yük veya mekanik zorlanma durumunda **Termik Aşırı Akım Rölesi (FR)** kumanda devresini keser.
   * `STOP` veya `ACİL STOP` butonuna basıldığında tüm sistem anında durur.

---

## 🛠️ Kullanılan Bileşenler ve Donanım
* **Güç Devresi Elemanları:**
  * 3 Fazlı Ana Otomatik Sigorta / Devre Kesici (3P MCB / C10)
  * Ana Kontaktör (`K1`)
  * Üçgen Kontaktörü (`K2`)
  * Yıldız Kontaktörü (`K3`)
  * Termik Aşırı Akım Rölesi (`FR`)
  * 3 Fazlı Asenkron Motor (U1-V1-W1 / U2-V2-W2 klemensli)
* **Kumanda Devresi Elemanları:**
  * Kumanda Koruma Sigortası (1P / 2P MCB)
  * Acil Durum Stop Butonu (NC)
  * Stop Butonu ve Start Butonu
  * Yıldız-Üçgen Zaman Rölesi (`ZR`)

---

## 📐 Teknik Özellikler ve Tasarım Kriterleri
* **Kalkış Akımı Yönetimi:** Kalkış akımını direkt başlatmaya göre $1/3$ oranına indirger.
* **Güvenlik Interlock Mimarisi:** Yıldız ve Üçgen kontaktörleri arasında elektriksel kilitleme ile tam emniyet sağlanmıştır.
* **Pafta Standardı:** QElectroTech ile endüstriyel IEC standartlarına uygun koordinatlı çizim, antet (title block) ve PDF export entegrasyonu gerçekleştirilmiştir.

---

## 📂 Dosya Yapısı
* `Yildiz_Ucgen_Kumanda.qet` — QElectroTech kaynak proje dosyası (Düzenlenebilir).
* `Yildiz_Ucgen_Kumanda_Semasi.pdf` — Profesyonel PDF pafta çıktısı.

---

## 📊 Görsel Simülasyon ve Devre Şemaları

### 🎥 Otomasyon Panel Simülasyonu
<p align="center">
  <img width="100%" alt="Yıldız Üçgen Simülasyonu" src="https://github.com/user-attachments/assets/1769b8a4-a559-4781-a8e4-d44d150e4901" />
</p>

---

### ⚡ QElectroTech Devre Şemaları & Pafta Çıktısı

<p align="center">
  <img width="100%" alt="Devre Şeması 1" src="https://github.com/user-attachments/assets/fe84412a-1c87-4eb9-9867-6c0f4cdef08d" />
</p>

<p align="center">
  <img width="100%" alt="Devre Şeması 2" src="https://github.com/user-attachments/assets/d75071ca-2ca3-4b87-a612-0fdddf116b8f" />
</p>

<p align="center">
  <img width="100%" alt="Devre Şeması 3" src="https://github.com/user-attachments/assets/4fd1224a-c205-45bb-b06b-5a7d94e5fc90" />
</p>

<p align="center">
  <img width="100%" alt="Devre Şeması 4" src="https://github.com/user-attachments/assets/2bd1221d-cd24-43f6-a86a-a115c441f37a" />
</p>

