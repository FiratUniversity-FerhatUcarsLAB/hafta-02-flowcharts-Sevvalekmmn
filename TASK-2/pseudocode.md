BAŞLA

// Kullanıcı Giriş Kontrolü
Kullanıcı_Giriş_Yapmış_Mı?
EĞER EVET ise
    Devam Et
DEĞİLSE
    Giriş_Yap_Veya_Kayıt_Ol

// Ürün Gezinme Döngüsü
TEKRAR
    Ürün_Kategorisi_Göster
    Kullanıcı_Bir_Ürün_Seçti_Mi?
    EĞER EVET ise
        // Sepete Ekleme
        EĞER Stok_Varsa ise
            Sepete_Ekle(Ürün)
        DEĞİLSE
            "Stokta Yok" Mesajı Göster
    Ürün_Gezinmeye_Devam_Edilsin_Mi?
    EĞER HAYIR ise
        ÇIKIŞ
SONA_KADAR

// Sepet Görüntüleme ve Düzenleme
TEKRAR
    Sepeti_Göster
    Kullanıcı_Değişiklik_Yapmak_İstiyor_Mu?
    EĞER EVET ise
        Ürün_Miktarı_Arttır_Azalt_Veya_Sil
    DEĞİLSE
        ÇIKIŞ
SONA_KADAR

// İndirim Kodu Kontrolü
Kullanıcı_Indirim_Kodu_Girdi_Mi?
EĞER EVET ise
    EĞER Kod_Geçerli ise
        İndirimi_Uygula
    DEĞİLSE
        "Geçersiz Kod" Göster

// Minimum 50 TL Kontrolü
EĞER Sepet_Toplam >= 50 TL ise
    Devam Et
DEĞİLSE
    "Minimum 50 TL Alışveriş Gerekli" Göster
    ALIŞVERİŞE GERİ DÖN

// Kargo Ücreti
EĞER Sepet_Toplam >= 200 TL ise
    Kargo_Ücretsiz
DEĞİLSE
    Kargo_Ücreti_Ekle

// Ödeme Yöntemi
Ödeme_Yöntemi_Seç
EĞER Kart ise
    Kart_Ödeme_Al
EĞER Kapıda ise
    Kapıda_Ödeme_Kaydet
EĞER Havale ise
    IBAN_Bilgisi_Göster

// Sipariş Onayı
Sipariş_Onayla
"Teşekkürler! Siparişiniz Alındı" Mesajı Göster

BİTİR
