# Listem – Yapılacaklar ve Alışveriş Uygulaması

Türkçe, mobil öncelikli, pastel lila/beyaz/açık gri tasarımlı, tamamen çalışan bir uygulama.

## Ekranlar
- **Ana Sayfa (/)**: Bugünün tarihi (ör. "23 Ekim 2026, Cuma"), saate göre karşılama ("Günaydın", "İyi akşamlar"), günün sözü, tamamlanan görevler için dairesel ilerleme halkası, bugünün görevleri özeti, alışveriş listesi özeti, Takvim ve Geçmiş'e hızlı geçiş kartları.
- **Yapılacaklar (/yapilacaklar)**: Görev ekle / düzenle / sil, tamamlandı işaretle, öncelik (Düşük / Orta / Yüksek, renkli etiket), tarih ve saat seçimi, "Ertele" (yarına taşır, ertelendi olarak kaydedilir). Filtre: Tümü / Bugün / Yaklaşan / Tamamlanan. Kaydırarak silme yerine net düğmeler.
- **Alışveriş (/alisveris)**: Ürün ekle, miktar ve birim (adet, kg, litre, paket), kategori (Meyve-Sebze, Süt Ürünleri, Et, Temizlik, Atıştırmalık, Diğer — ikonlu), alındı işaretle, kategoriye göre gruplu liste, "Alınanları temizle".
- **Takvim (/takvim)**: Aylık takvim, görevi olan günlerde nokta; gün seçince o günün görevleri.
- **Geçmiş (/gecmis)**: Tamamlanan ve ertelenen görevler sekmeli, tarihe göre gruplu.
- **Profil (/profil)**: İsim ve avatar düzenleme (karşılamada kullanılır), istatistikler (toplam/tamamlanan görev, alınan ürün), Takvim ve Geçmiş bağlantıları, tüm verileri sıfırlama.

Alt menü: Ana Sayfa, Yapılacaklar, Alışveriş, Profil. Ortada/sağ altta yüzen "+" düğmesi; ekleme ve düzenleme alttan açılan panelde.

## Boş durumlar
Her liste için özel çizim, sıcak bir mesaj ("Henüz görevin yok, ilk görevini ekleyelim!") ve ekleme düğmesi.

## Tasarım
- Renkler: pastel lila ana renk, beyaz kartlar, açık gri zemin; öncelikler için yumuşak pembe/şeftali/nane tonları.
- Yazı tipi: Plus Jakarta Sans (Türkçe karakter desteği tam).
- Büyük yuvarlatılmış kartlar, yumuşak gölgeler, lucide ikonları.
- Akıcı animasyonlar: işaretleme, liste ekleme/silme, sekme geçişleri, ilerleme halkası.
- Masaüstünde telefon genişliğinde ortalanmış görünüm; mobilde tam ekran.

## Veri saklama
Tüm veriler cihazda kalıcı saklanır; uygulama kapatılıp açılınca kaybolmaz. Hesap/giriş gerekmez. (İleride cihazlar arası senkronizasyon istenirse Lovable Cloud ile giriş eklenebilir.)

## Teknik detaylar
- Ayrı sayfa dosyaları: index, yapilacaklar, alisveris, takvim, gecmis, profil; ortak alt menü kök düzende.
- Durum yönetimi: zustand + persist (localStorage), hidrasyon sonrası okunur (SSR uyumsuzluğunu önlemek için).
- Tarih: date-fns + `tr` yerel ayarı; shadcn Calendar (Türkçe), saat seçici.
- Animasyon: framer-motion.
- Her sayfaya Türkçe başlık/açıklama meta verisi; `<html lang="tr">`.
- Öncelik sıralaması, erteleme ve ilerleme yüzdesi hesapları için küçük birim testleri.
