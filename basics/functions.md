# İşlevler (Functions)

Her D programının başlangıç noktası olarak `main()` adında bir işlev
her zaman tanımlanır. İşlev bir değer döndürebilir (veya değer dönmeyecekse
`void` olarak tanımlanır.) ve istenildiği kadar argüman alabilir:

    int topla(int lhs, int rhs) {
        return lhs + rhs;
    }

### `auto` dönüş değeri

Eğer dönüş değeri `auto` olarak tanımlandıysa, D dili dönüş değerini
otomatik olarak anlar. Bu nedenle işlev içerisindeki bütün
`return` ifadelerinin dönüş değerlerinin türleri uyumlu olmak zorundadır.

    auto topla(int lhs, int rhs) { // `int` döndürür
        return lhs + rhs;
    }

    auto küçükVeyaEşit(int lhs, int rhs) { // `double` döndürür
        if (lhs <= rhs)
            return 0;
        else
            return 1.0;
    }

### Varsayılan argümanlar

İşlevlerde isteğe bağlı olarak varsayılan argüman tanımlamaya izin verilir.
Bu sayede can sıkan gereksiz tekrarlamalar ortadan kalkar.

    void plot(string msg, string color = "red") {
        ...
    }
    plot("D rocks");
    plot("D rocks", "blue");

Varsayılan argüman tanımlandığında, sonraki bütün tanımlanan argümanların da
varsayılan argüman olarak tanımlanması zorunludur. 

### Yerel işlevler

İşlevler başka bir işlevin içerisinde de tanımlanabilir. Bu sayede yerel
bir şekilde kullanılabilir ve kapsam dışından erişim engellenebilir.
Ve hatta bu yerel işlevler, bulunduğu kapsamdaki nesnelere, değişkenlere erişebilir. 

    void fun() {
        int yerel = 10;
        int iç_işlev() {
            yerel++; // erişim serbest.
        }
        ...

Bazı iç içe işlevler temsilci (delegates) olarak da çağırılır. Temsilciler daha detaylı
bir şekilde daha sonraki [bölümde](basics/delegates) açıklanacaktır.

### Derinlemesine

- [İşlevler](http://ddili.org/ders/d/islevler.html)
- [İşlev Parametreleri](http://ddili.org/ders/d/islev_parametreleri.html)
- [Function specification](https://dlang.org/spec/function.html)

## {SourceCode}

```d
import std.stdio : writeln;
import std.random : uniform;

void rastgeleHesapla()
{
    // 4 farklı matematik işlemi için
    // 4 yerel işlev tanımlıyoruz.
    auto topla(int lhs, int rhs) {
        return lhs + rhs;
    }
    auto çıkart(int lhs, int rhs) {
        return lhs - rhs;
    }
    auto çarp(int lhs, int rhs) {
        return lhs * rhs;
    }
    auto böl(int lhs, int rhs) {
        return lhs / rhs;
    }

    int a = 10;
    int b = 5;

    // uniform BAŞLANGIÇ ve BİTİŞ arasında
    // rastgele bir sayı döndürür. BİTİŞ
    // değeri dahil değildir.
    // Sonuca göre matematik işlemlerinden
    // birini çağırıyoruz.
    switch (uniform(0, 4)) {
        case 0:
            writeln(topla(a, b));
            break;
        case 1:
            writeln(çıkart(a, b));
            break;
        case 2:
            writeln(çarp(a, b));
            break;
        case 3:
            writeln(böl(a, b));
            break;
        default:
            // Erişilemeyen kodu işaretleyen
            // özel kod
            assert(0);
    }
}

void main()
{
    rastgeleHesapla();
    // topla(), çıkart(), çarp() and böl()
    // işlevleri kapsamlarının dışında erişilebilir değil.
    static assert(!__traits(compiles,
                            topla(1, 2)));
}

```
