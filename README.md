# AIMTAS – Enkaz Tespit ve İHA Kontrol Sistemi

Android uygulaması - Afet sonrası arama kurtarma simülasyonu

## Özellikler

- **Java + XML** tabanlı Android uygulaması
- **Simülasyon Modülü**: Gerçek donanım olmadan çalışır
- **İHA Durum Takibi**: Batarya, sinyal, uçuş modu bilgileri
- **Enkaz Tespiti**: Otomatik tespit ve güven oranı gösterimi
- **Bluetooth Simülasyonu**: Bağlantı durumu ve cihaz bilgisi
- **Canlı Log Sistemi**: Gerçek zamanlı mesaj akışı

## Teknik Detaylar

- **Minimum SDK**: Android 8.0 (API 26)
- **Target SDK**: Android 14 (API 34)
- **Dil**: Java
- **UI Framework**: XML (Views)
- **Mimari**: Tek Activity

## Kurulum

### Android Studio'da Açma

1. Android Studio'yu açın
2. `File` > `Open` menüsünden AIMTAS klasörünü seçin
3. Gradle sync işleminin tamamlanmasını bekleyin
4. `Run` > `Run 'app'` ile uygulamayı çalıştırın

### APK Oluşturma

```bash
cd AIMTAS
./gradlew assembleDebug
```

APK dosyası şu konumda oluşur:
```
app/build/outputs/apk/debug/app-debug.apk
```

## Dosya Yapısı

```
AIMTAS/
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/com/aimtas/rescuesystem/
│   │       │   └── MainActivity.java
│   │       ├── res/
│   │       │   ├── layout/
│   │       │   │   └── activity_main.xml
│   │       │   └── values/
│   │       │       ├── strings.xml
│   │       │       └── colors.xml
│   │       └── AndroidManifest.xml
│   └── build.gradle
├── gradle/
│   └── wrapper/
│       └── gradle-wrapper.properties
├── build.gradle
└── settings.gradle
```

## Simülasyon Davranışı

Uygulama açıldığında otomatik olarak:

1. **0-3 saniye**: Sistem başlatılıyor
2. **3-6 saniye**: Bluetooth bağlantısı kuruluyor
3. **6-9 saniye**: İHA'dan veri alınıyor
4. **24-27 saniye**: Enkaz tespit ediliyor
5. **27+ saniye**: Kurtarma ekibi bilgilendiriliyor

### Dinamik Değişimler

- **Batarya**: Her 3 saniyede %1-3 azalır
- **Sinyal Gücü**: Rastgele değişir (ağırlıklı "Güçlü")
- **Log Mesajları**: Her 3 saniyede yeni mesaj eklenir

## İzinler

Aşağıdaki izinler AndroidManifest.xml'de tanımlıdır:

- `BLUETOOTH`
- `BLUETOOTH_ADMIN`
- `BLUETOOTH_CONNECT`
- `BLUETOOTH_SCAN`
- `ACCESS_FINE_LOCATION`
- `ACCESS_COARSE_LOCATION`

**Not**: Uygulama gerçek Bluetooth bağlantısı kullanmaz, sadece simülasyon amaçlıdır.

## Geliştirme Notları

### MainActivity.java
- Handler kullanarak 3 saniyede bir güncelleme
- Random class ile dinamik veri üretimi
- TextView'lere programatik renk atama

### activity_main.xml
- ScrollView içinde LinearLayout yapısı
- CardView ile bölümlere ayrılmış tasarım
- Material Design renk paleti

## Sorun Giderme

### Gradle Sync Hatası
```bash
./gradlew clean
./gradlew build
```

### APK Yüklenemedi
- USB Debugging açık olmalı
- Unknown Sources izni verilmeli

### Uygulama Çöküyor
- Minimum Android 8.0 gereklidir
- Logcat'ten hata mesajını kontrol edin

## Ekran Görüntüleri

Uygulama aşağıdaki bölümleri içerir:

1. **AIMTAS Başlık**: Mavi arka planlı logo ve başlık
2. **İHA Durum Kartı**: Mavi kenarlı, durum bilgileri
3. **Konum & Enkaz Kartı**: Kırmızı kenarlı, tespit bilgileri
4. **Bluetooth Kartı**: Mavi kenarlı, bağlantı durumu
5. **Log Mesajları**: Yeşil kenarlı, kaydırılabilir mesaj alanı

## Lisans

Bu proje eğitim ve simülasyon amaçlı geliştirilmiştir.

## İletişim

Proje: AIMTAS (AI-based Mobile Tracking and Alert System)
Kategori: Afet Yönetimi - Arama Kurtarma
Platform: Android (Java)
