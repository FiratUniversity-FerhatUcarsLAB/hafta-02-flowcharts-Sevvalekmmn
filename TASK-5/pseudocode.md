Başla
    Eğer Sistem_Aktif_mi = EVET ise
        Döngü Başla (Sürekli)
            Sensör_Verisi = Sensör_Oku()
            
            Eğer Hareket_Sensörü = Tespit_Etti ise
                Kamera_Aktive_Et()
            Bitir Eğer

            Eğer Kapı_Pencere_Sensörü = Açık ise
                Kamera_Aktive_Et()
            Bitir Eğer

            Eğer Ev_Sahibi_Evde_mi = HAYIR ise
                Alarm_Seviyesi = Belirle_Alarm_Seviyesi(Sensör_Verisi)
                Bildirim_Gonder(Alarm_Seviyesi, SMS)
                Bildirim_Gonder(Alarm_Seviyesi, App)
                Bildirim_Gonder(Alarm_Seviyesi, Email)
            Bitir Eğer

            Bekle(Belirli_Süre)
            
            Eğer Alarm_Sıfırla_mı = EVET ise
                Alarmı_Sıfırla()
            Bitir Eğer

        Döngü Bitir
    Aksi_Halde
        Sistem_Kapalı_Mesajı()
    Bitir Eğer
Bitir

