# kelime-sayıcı  Metin dosyasındaki kelimelerin frekanslarını hesaplayan kodlar
# Dosyayı okuyup kelimeleri sayacak bir fonksiyon
def kelime_sayacı(dosya_adı):
    kelime_sözlüğü = {}

    try:
        # Metin dosyasını aç
        with open(dosya_adı, 'r', encoding='utf-8') as dosya:
            metin = dosya.read()

            # Metni küçük harfe çevir ve noktalama işaretlerini temizle
            metin = metin.lower()
            metin = metin.replace('.', '').replace(',', '').replace('!', '').replace('?', '')

            # Metni boşluklardan ayır ve her kelimenin frekansını say
            kelimeler = metin.split()
            for kelime in kelimeler:
                if kelime in kelime_sözlüğü:
                    kelime_sözlüğü[kelime] += 1
                else:
                    kelime_sözlüğü[kelime] = 1

        return kelime_sözlüğü

    except FileNotFoundError:
        print("Belirtilen dosya bulunamadı.")
        return None

# Kelime frekanslarını görüntüle
def frekansları_görüntüle(kelime_sözlüğü):
    if kelime_sözlüğü:
        for kelime, frekans in kelime_sözlüğü.items():
            print(f"{kelime}: {frekans}")
    else:
        print("Kelime sözlüğü boş.")

if __name__ == "__main__":
    dosya_adı = "metin.txt"  # Kelime frekanslarını hesaplamak istediğiniz metin dosyasının adını girin
    kelime_sözlüğü = kelime_sayacı(dosya_adı)

    if kelime_sözlüğü:
        print(f"{dosya_adı} dosyasındaki kelime frekansları:")
        frekansları_görüntüle(kelime_sözlüğü)

