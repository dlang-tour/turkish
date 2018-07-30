# İşlevler (Functions)

Her d programının başlangıç noktası olarak `main()` adında bir işlev
her zaman tanımlanır. Bir işlev bir değer döndürebilir (veya değer dönmeyecekse
`void` olarak tanımlanır.) ve istenildiği kadar argüman alabilir:

    int topla(int lhs, int rhs) {
        return lhs + rhs;
    }

### `auto` dönüş değeri

Eğer dönüş değeri `auto` olarak tanımlandıysa, D dili dönüş değerini
otomatik olarak anlar. Bu nedenle farklı `return` ifadeleri uyumlu türde
değerler döndürmek zorundadır.

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

İşlevlerde isteğe bağlı olarak varsayılan argüman tanımlamaya izin verir.
Bu sayede can sıkan gereksiz tekrarlamaları ortadan kaldırır.

    void plot(string msg, string color = "red") {
        ...
    }
    plot("D rocks");
    plot("D rocks", "blue");

Varsayılan argüman tanımlandığında, sonraki bütün tanımlanan argümanların da
varsayılan argüman olarak tanımlanması beklenir. 

### Yerel işlevler

İşlevler başka bir işlevin içerisinde de tanımlanabilir. Bu sayede yerel
bir şekilde kullanılabilir ve kapsam dışından erişim sağlanamaz.
Ve hatta bu işlevler bulunduğu kapsamdaki değişkenlere erişebilir. 

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

void randomCalculator()
{
    // Define 4 local functions for
    // 4 different mathematical operations
    auto add(int lhs, int rhs) {
        return lhs + rhs;
    }
    auto sub(int lhs, int rhs) {
        return lhs - rhs;
    }
    auto mul(int lhs, int rhs) {
        return lhs * rhs;
    }
    auto div(int lhs, int rhs) {
        return lhs / rhs;
    }

    int a = 10;
    int b = 5;

    // uniform generates a number between START
    // and END, whereas END is NOT inclusive.
    // Depending on the result we call one of
    // the math operations.
    switch (uniform(0, 4)) {
        case 0:
            writeln(add(a, b));
            break;
        case 1:
            writeln(sub(a, b));
            break;
        case 2:
            writeln(mul(a, b));
            break;
        case 3:
            writeln(div(a, b));
            break;
        default:
            // special code which marks
            // UNREACHABLE code
            assert(0);
    }
}

void main()
{
    randomCalculator();
    // add(), sub(), mul() and div()
    // are NOT visible outside of their scope
    static assert(!__traits(compiles,
                            add(1, 2)));
}

```
