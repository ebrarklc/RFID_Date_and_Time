# RFID RTC Writer ⏱🔐

Bu proje, bir **MFRC522 RFID okuyucu** ile bir **DS3231 RTC (Real-Time Clock)** modülünü birlikte kullanarak, bir RFID karta anlık tarih ve saat bilgisini yazmayı amaçlar.

## 🛠 Kullanılan Bileşenler

- Arduino Mega 2560
- MFRC522 RFID Okuyucu
- DS3231 RTC Modülü
- MIFARE 1K RFID Kart
- Jumper Kablolar

## 🧠 Fonksiyonlar

- DS3231 üzerinden **gerçek zamanlı tarih ve saat** alınır.
- RFID karta **"ddMMyyHHmm"** formatında zaman bilgisi yazılır.
  - Örnek: `1501251359` → 15 Ocak 2025, 13:59

## ⚡️ Devre Bağlantıları

### RFID (MFRC522)

| RFID Pin | Arduino Mega Pin |
|----------|------------------|
| SDA      | 53               |
| SCK      | 52               |
| MOSI     | 51               |
| MISO     | 50               |
| RST      | 49               |
| GND      | GND              |
| VCC      | 3.3V             |

### RTC (DS3231)

| RTC Pin | Arduino Mega Pin |
|---------|------------------|
| VCC     | 5V               |
| GND     | GND              |
| SDA     | A4               |
| SCL     | A5               |

## 📥 Gerekli Kütüphaneler

Arduino IDE üzerinden aşağıdaki kütüphaneleri yükleyin:

- `MFRC522` (Miguel Balboa tarafından)
- `RTClib` (Adafruit tarafından)

## 🚀 Kullanım

1. RTC saatini ayarlamak için kodu ilk kez yüklediğinizde:
    ```cpp
    rtc.adjust(DateTime(F(__DATE__), F(__TIME__)));
    ```
    kısmı sistem saatine göre RTC’yi ayarlar.

2. Kartı yaklaştırdığınızda terminalde aşağıdaki gibi bir çıktı görürsünüz:
    ```
    ⏰ 1501251359
   

