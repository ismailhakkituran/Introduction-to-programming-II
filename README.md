# Operatör Önceliklerini Kısaca Hatırlayalım

## 1. Klasik Aritmetik İşlem Önceliğini Hatırlayalım.
```c
#include <stdio.h>

int main() {
    int a = 4, b = 3, c;
    c = a + b * 2;

    printf("c = %d\n", c);
    return 0;
}
```

## 2. Atama Operatörü vs. Artırma İşlemi : Hangisi önce çalışır?
a, b ve c' nin değerleri ne olur?
```c
#include <stdio.h>

int main() {
    int a = 5;
    int b = a++;
    int c = ++a;
    printf("a = %d, b = %d, c = %d\n", a, b, c);
    return 0;
}
```

## 3. Dört İşlem Önceliği vs. Artırma İşlemi : Hangisi önce çalışır?
x ve y' nin değerleri ne olur?
```c
#include <stdio.h>

int main() {
    int x = 3;
    int y = 2 * x++ + 1;
    printf("x = %d, y = %d\n", x, y);
    return 0;
}
```

## 4. Atama Operatörü vs. Artırma İşlemi : Hangisi önce çalışır?
Fonksiyon return ettiğinde dönülen değere ekleme yapılma önceliği nasıl olur?
```c
#include <stdio.h>

int getFive() {
    return 5;
}

int main() {
    int val = 2;
    int result = getFive() + val++;
    printf("result = %d, val = %d\n", result, val);
    return 0;
}
```

## 5. Bir Başka Karışık Örnek
```c
#include <stdio.h>

int main() {
    int a = 1;
    int b = (a++ + ++a) * 2; // a++ = 1, ++a = 3 → b = (1+3)*2 = 8, a = 3

    printf("a = %d, b = %d\n", a, b);
    return 0;
}
```
CEVAP.5:  a++ = 1, ++a = 3 → b = (1+3)*2 = 8, a = 3


#### Konuyu değiştirelim...

## 6. Ekrana 5614 adet 'A' karakteri yazan bir uygulama yapınız.
Bu uygulama bellekten yer tahsisi olarak sadece ```i``` değişkeni kadar yer istiyor. (1 integer ne kadar yer kaplar?)

```c
#include <stdio.h>

int main() {
    for (int i = 0; i < 5614; i++) {
        printf("A");
    }
    return 0;
}
```

Uygulama derledikten sonra 2 farklı şekilde çalıştıralım:
#### 1. Ekrana yazdıralım
```shell
gcc -o main main.c
./main
```

#### 2. stdout (Standart Çıkışı) bir dosyaya yönlendirerek dosyaya yazdıralım.
```shell
gcc -o main main.c
./main > dosyam.txt #uzantının bir önemi yok
```

#### Dosyanın büyüklüğüne ls komutu ile bakalım
```shell
ls -al
```

#### veya
```shell
ls -al dosyam.txt
```
#### Diskte ne kadar yer kaplıyor ?

Şimdi bu dosyayı stdin' i yönlendirerek bir diziye aktarınız ve program çalışmakta iken kapladığı alan nedir?


```c
#include <stdio.h>

int main() {
    char buffer[5164];
    int i;

    for (i = 0; i < 5164; i++) {
        int c = getchar();
        if (c == EOF) {
            break;
        }
        buffer[i] = (char)c;
    }

    printf("Okunan karakter sayısı: %d\n", i);

    return 0;
}
```

Çalıştıralım
```shell
gcc -o main main.c
./main < dosyam.txt #bir önceki programda oluşturduğumuz dosya
```

Hep açık kalacak bu uygulamayı kapatmak için koşan process' i cut (kesme) etmemiz gerekiyor
```shell
Ctrl + C
```

#### Uygulamanın bellekte kapladığı alanı nasıl öğreniriz ?

Windows işletim sisteminde "Görev Yöneticisi" uygulamasının Linux/Unix sistemlerde terminalde çalışan karşılığı olan uygulama nedir?

**Cevap** ```top``` komutu
```shell
top
```
veya
```shell
top | grep main
```

Hangi sütun bellekte kapladığı alanı verir ve neden tutarsızlık var araştırınız.
