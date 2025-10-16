BAŞLA

  bakiye ← 5000            // Varsayılan bakiye

  TEKRARLA

    kalan_hak ← 3

    // PIN DOĞRULAMA
    DÖNGÜ kalan_hak > 0 İKEN
        YAZ "Lütfen PIN kodunuzu girin:"
        OKU girilen_pin

        EĞER girilen_pin = 1234 İSE
            YAZ "PIN doğrulandı."
            ÇIK PIN_DOGRULAMA
        DEĞİLSE
            kalan_hak ← kalan_hak - 1
            YAZ "Hatalı PIN. Kalan deneme hakkınız: ", kalan_hak
        SON
    SON_DÖNGÜ

    EĞER kalan_hak = 0 İSE
        YAZ "3 kez hatalı PIN girildi. Kart bloke edildi."
        ÇIK SISTEMDEN
    SON

    // PARA ÇEKME İŞLEMİ
    DÖNGÜ TRUE
        YAZ "Çekmek istediğiniz tutarı girin:"
        OKU tutar

        EĞER tutar ≤ 0 İSE
            YAZ "Geçersiz tutar! Pozitif bir değer girin."
        DEĞİLSE EĞER tutar MOD 10 ≠ 0 İSE
            YAZ "Tutar 10 TL ve katları olmalıdır."
        DEĞİLSE EĞER tutar > bakiye İSE
            YAZ "Yetersiz bakiye. Mevcut bakiye: ", bakiye
        DEĞİLSE
            bakiye ← bakiye - tutar
            YAZ tutar, " TL çekildi. Kalan bakiye: ", bakiye
            ÇIK PARA_CEKME
        SON
    SON_DÖNGÜ

