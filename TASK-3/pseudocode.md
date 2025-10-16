BAŞLA
    Hasta_TC = Girdi("TC No giriniz:")
    
    TEKRAR
        Islem = Girdi("İşlem seçin: 1-Randevu Al, 2-Tahlil Sonucu Gör")
        
        EĞER Islem == 1 O ZAMAN
            // Randevu Modülü
            Poliklinik = Girdi("Poliklinik seçiniz:")
            Doktor = Girdi("Doktor seçiniz:")
            
            TEKRAR
                Saat = Girdi("Uygun saat seçiniz:")
                EĞER Saat uygun mu? EVET
                    Randevu_Onayi = Onay("Randevu onaylansın mı?")
                    GÖNDER SMS("Randevu bilgileri gönderildi")
                    DUR
                HAYIR
                    Mesaj("Lütfen başka bir saat seçin")
            BITIR
            
        HAYIR EĞER Islem == 2 O ZAMAN
            // Tahlil Modülü
            EĞER Tahlil var mı? EVET
                EĞER Sonuç hazır mı? EVET
                    Goster("Tahlil sonucu görüntülendi")
                    Secim = Girdi("PDF indirmek ister misiniz? E/H")
                    EĞER Secim == "E" O ZAMAN
                        PDF_Indir()
                    BITIR
                HAYIR
                    Mesaj("Sonuç henüz hazır değil, bekleyin")
            HAYIR
                Mesaj("Tahlil kaydı bulunamadı")
        BITIR

        Tekrar = Girdi("Başka işlem yapmak ister misiniz? E/H")
    TEKRAR EĞER Tekrar == "E"

BITIR
