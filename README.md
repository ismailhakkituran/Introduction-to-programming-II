Pointer Uygulamaları
=====================

### 1. Temel Pointer Tanımı ve Adres Gösterimi

* Değişkenin adresini gösterme
* ```c
  int x = 5; int *px = &x; printf("%p %d", px, *px);
  ```

* `*px = 10;` yaparsak `x` değeri değişir mi?
* Öncesi/sonrası değerleri ekrana yazdırınız.

---

### 2. Pointer değişkeni kullanarak fonksiyondan bir veya daha fazla değer return yapılabilir mi?

void bir fonksiyondan bir `int` değerin karesini global değişken kullanmadan nasıl elde edersiniz? (Gerçekleyiniz 5 dk.)
```c
void kare-al(int *sayi)` ⇒ `*sayi = (*sayi) * (*sayi);` 
```
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
void kare-al(int *sayi) {
    *sayi = (*sayi) * (*sayi);
}

int main() {
    int x = 4;
    printf("Orijinal deger: %d\n", x);

    kare-al(&x);

    printf("Karesi: %d\n", x);
    return 0;
}
```

### 3. Fonksiyondan Birden Fazla Değer Döndürme

* Örnek: `void bolme(int bolunen, int bolen, int *bolum, int *kalan);`
* Kullanıcıdan sayı al, hem bölüm hem kalanı döndür. Pointer konusunu bilmeseydiniz bu problemi nasıl çözerdiniz ? (Aynı fonksiyondan 2 tane değer döndürme problemi)
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

void bolum(int bolunen, int bolen, int *bolum, int *kalan) {
    *bolum = bolunen / bolen;
    *kalan = bolunen % bolen;
}

int main() {
    int bolunen = 17, bolen = 5;
    int bolum, kalan;

    printf("Bolum: %d, Kalan: %d\n", bolum, kalan);

    bolum(bolunen, bolen, &bolum, &kalan);

    printf("Bolum: %d, Kalan: %d\n", bolum, kalan);
    return 0;
}
```

---

### 4. Pointer ile Diziye Erişim

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

### 5. Fonksiyona Dizi Gönderimi ve Ortalama Hesabı

* `void ortalama(int dizi[], int boyut, float *sonuc)`
* Array + pointer + tek değer return
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

void ortalama(int dizi[], int boyut, float *sonuc) {
    int toplam = 0;
    for (int i = 0; i < boyut; i++) {
        toplam += dizi[i];
    }
    *sonuc = (float)toplam / boyut;
}

int main() {
    int sayilar[] = {5, 10, 15, 20};
    float ort;

    ortalama(sayilar, 4, &ort);
    printf("Ortalama: %.2f\n", ort);

    return 0;
}
```

---



### 6. Pointer ve String İşlemleri

C programlama dili temelinde String isminde bir tip yoktur aslında. Bu ihtiyacı da char dizisi ile karşılarız.

* `char *str = "merhaba";` 
* `strlen`, `strcpy`, `strcmp` gibi fonksiyonları kendin pointer ile yaz
* Örnek: `int strlength(char *s)` vs

```c
#include <stdio.h>

int strlength(char *s) {
    int len = 0;
    while (s[len] != '\0') {
        len++;
    }
    return len;
}

int main() {
    char *metin = "merhaba";
    printf("'%s' kelimesinin uzunlugu: %d\n", metin, strlength(metin));

    return 0;
}
```
---


| Başlık                   | Düşünme İçeriği                         |
| ------------------------ | --------------------------------------- |
| `&` ve `*` farkı         | Adres alma ve değer alma                |
| Heap vs Stack            | norml parametre vs referans parametre   |
| Dizi ve Pointer ilişkisi | `p[i]` = `*(p+i)`                       |


