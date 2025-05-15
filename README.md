Pointer Uygulamaları
=====================

### 1. Temel Pointer Tanımı ve Adres Gösterimi

* Değişkenin adresini gösterme
* `int x = 5; int *px = &x; printf("%p %d", px, *px);`

* `*px = 10;` yaparsak `x` değeri değişir mi?
* Öncesi/sonrası değerleri ekrana yazdırınız.

---

### 3. Pointer değişkeni kullanarak fonksiyondan bir veya daha fazla değer return yapılabilir mi?

void bir fonksiyondan bir `int` değerin karesini global değişken kullanmadan nasıl elde edersiniz? 
* `void kareAl(int *sayi)` ⇒ `*sayi = (*sayi) * (*sayi);` (Gerçekleyiniz 5 dk.)
\
\
\
\
\
\
\
\
CEVAP:
```c
void kareAl(int *sayi) {
    *sayi = (*sayi) * (*sayi);
}

int main() {
    int x = 4;
    printf("Orijinal deger: %d\n", x);

    kareAl(&x);

    printf("Karesi: %d\n", x);
    return 0;
}
```

### 4. Fonksiyonla Birden Fazla Değer Döndürme

* Örnek: `void bolumKalan(int bolunen, int bolen, int *bolum, int *kalan);`
* Kullanıcıdan sayı al, hem bölüm hem kalan döndür. Pointer konusunu bilmeseydiniz bu problemi nasıl çözerdiniz ? (Aynı fonksiyondan 2 tane değer döndürme problemi)
(Düşünme 5 dk.)

\
\
\
\
\
\
CEVAP:

Array kullanımı
`int bolme-islemi[2]={  0 , 0 }` 1. elemana bölüm değerini, 2 elemana kalan değerini koyup, diziyi return ediniz.


YENİ SORU:
Peki bu 2 değerin tipi birbirinden farklı olsaydı? (Örneğin noktalı bir sayı ve bir karakter değişkeni)
Bu 2 değer bir dizinin elemanı olamaz...
(Düşünme 5 dk.)
\
\
\
\
\
\
CEVAP:
Pointer kullanarak fonksiyona değişkeni değil, değişkenin adresini göndermek.

```c
#include <stdio.h>

void bolumKalan(int bolunen, int bolen, int *bolum, int *kalan) {
    *bolum = bolunen / bolen;
    *kalan = bolunen % bolen;
}

int main() {
    int bolunen = 17, bolen = 5;
    int bolum, kalan;

    bolumKalan(bolunen, bolen, &bolum, &kalan);

    printf("Bolum: %d, Kalan: %d\n", bolum, kalan);
    return 0;
}
```

---

### 5. Pointer ile Diziye Erişim

* `int dizi[] = {1,2,3}; int *p = dizi;`
* `*(p + i)` ile dizi elemanlarını yazdır
(Kodlama 5 dk.)
\
\
\
\
\
\
CEVAP:

```c
#include <stdio.h>

int main() {
    int dizi[] = {10, 20, 30, 40};
    int *p = dizi;

    for (int i = 0; i < 4; i++) {
        printf("dizi[%d] = %d, *(p+%d) = %d\n", i, dizi[i], i, *(p + i));
    }

    return 0;
}
```
---

### 6. Fonksiyona Dizi Gönderimi ve Ortalama Hesabı *(10 dk)*

* `void ortalama(int dizi[], int boyut, float *sonuc)`
* Array + pointer + tek değer return

---

### 7. Pointer ile Dinamik Bellek Yönetimi (malloc/free) *(10 dk)*

* `int *dizi = malloc(n * sizeof(int));`
* Kullanıcıdan kaç eleman alınacağını sor, değerleri oku, ortalamasını hesapla

---

### 8. Pointer ve String İşlemleri *(10 dk)*

* `char *str = "merhaba";`
* `strlen`, `strcpy`, `strcmp` gibi fonksiyonları kendin pointer ile yaz
* Örnek: `int strlength(char *s)` vs

---

### 9. Struct ve Pointer (Bonus: C'de Object-like yapı) *(10 dk)*

* `struct Ogrenci { char ad[20]; int yas; };`
* Pointer ile struct alanlarına erişim (`ogrPtr->ad`)

---

## Bonus (Zaman Kalırsa):

* **Pointer to Pointer** (`int **pp`)
* **Function Pointers** (`int (*f)(int, int)`)

---

## Sunum veya Uygulama için Hazır Başlıklar

| Başlık                   | İçerik                            |
| ------------------------ | --------------------------------- |
| `&` ve `*` farkı         | Adres alma ve değer alma          |
| Heap vs Stack            | malloc nerede çalışır?            |
| Dizi ve Pointer ilişkisi | `p[i]` = `*(p+i)`                 |
| Bellek sızıntısı         | malloc + free unutulursa ne olur? |


