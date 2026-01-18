#  VERİTABANI ENTEGRASYONU TAMAMLANDI

## Yapılan Değişiklikler:

### 1 Oluşturulan Dosyalar:
-  `VeritabaniYoneticisi.cs` - Veritabanı yönetimi sınıfı
-  `VeritabaniYoneticisi_COMPLETE.cs` - SQLite paketi yüklendikten sonra kullanılacak tam versiyon

### 2 Form1.cs'te Yapılan Değişiklikler:
-  Veritabanı değişkenleri eklendi (`veriTabani`, `mevcutOyuncuAdi`)
-  Constructor'da veritabanı başlatıldı
-  Oyun bitti metodu güncellendi - veritabanına kayıt yapılıyor
-  Yeni metodlar eklendi:
  - `GosterOyunBittiDialog()` - Oyun sonu penceresini gösterir
  - `GosterEnYuksekSkorlar()` - En yüksek 10 skoru listeler

### 3 OyunSkoru Sınıfı:
```csharp
public class OyunSkoru
{
    public string OyuncuAdi { get; set; }
    public int BasariliDalgalar { get; set; }
    public int KazanılanAltin { get; set; }
    public int KaleTCanı { get; set; }
    public DateTime TarihSaat { get; set; }
}
```

---

 NÜ GET PAKETINI KURMA (ÖNEMLİ!):

Projeyi çalıştırabilmek için **System.Data.SQLite** paketini kurmalısınız.

### Visual Studio'da:
1. **Araçlar   NuGet Paket Yöneticisi   Paket Yöneticisi Konsolu**
2. Şu komutu yazın:
```
Install-Package System.Data.SQLite
```

### Veya Package.config aracılığıyla:
```xml
<package id="System.Data.SQLite" version="1.0.118.0" targetFramework="net48" />
```

---

##    Paketi Kurulduktan Sonra:

1. `Form1.cs` en üstüne şu satırı ekleyin:
```csharp
using System.Data.SQLite;
```

2. `VeritabaniYoneticisi.cs` dosyasını `VeritabaniYoneticisi_COMPLETE.cs` ile değiştirin

3. Projeyi yeniden derleyin (Build All)

---

##    Oyun Kullanımı:

1. Oyunu başlatın
2. Oyun oynayın ve kale yıkılana kadar devam edin
3. Kale yıkıldığında:
   - Skor otomatik olarak veritabanına kaydedilir
   - "En Yüksek Skorları görmek ister misiniz " sorusu sorulur
   - **Evet** seçeneğini tıklayın
   - Kaydedilmiş tüm skorları görün

---

##    Veritabanı Tablosu:

```sql
CREATE TABLE OyunSkorlari (
    ID INTEGER PRIMARY KEY AUTOINCREMENT,
    OyuncuAdi TEXT NOT NULL,
    BasariliDalgalar INTEGER NOT NULL,
    KazanılanAltin INTEGER NOT NULL,
    KaleTCanı INTEGER NOT NULL,
    TarihSaat DATETIME DEFAULT CURRENT_TIMESTAMP
)
```

**Dosya:** `TowerDefense.db` (otomatik oluşturulur)

---

##   Özellikler:

  Oyun sonunda skorları otomatik kaydet
  En yüksek 10 skoru sıralı olarak göster
  Oyuncu adı, dalga, altın ve tarih/saat bilgisini sakla
  SQL Injection koruması (parametreli sorgular)
  Hata yönetimi ile güvenli veritabanı işlemleri

---

##    Sorun Giderme:

**Eğer derleme hatası alırsanız:**
1. Visual Studio'yu kapatın
2. Proje klasörüne git:
   - `bin` klasörünü sil
   - `obj` klasörünü sil
3. Visual Studio'yu yeniden aç
4. Build All yap

**Paket kurma hatası:**
- PowerShell'i Yönetici olarak çalıştırın
- Paket kaynağını kontrol edin: https://www.nuget.org

---

**Hazırsınız! Şimdi NuGet paketini kurarak başlayabilirsiniz.   **
