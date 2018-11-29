# Bellek

D dili bir sistem programlama dili olmasından dolayı bellek yönetimine
müdahele edilmesine izin verir. Fakat elle bellek yönetimi, 
hataya yatkın olduğundan dolayı D dili varsayılan olarak
belleği *çöp toplayıcı(garbage collector)* ile yönetir.

D dilin, C dilinde olduğu gibi `T*` şeklinde işaretçi(pointer) sağlar.

    int a;
    int* b = &a; // b, a'nın adresini tutar
    auto c = &a; // c bir int* ve a'nın adresini tutar

Yığından(heap) bir bellek bloğu `new` ifadesi tahsis edilir. Bu ifade 
yönetilen belleği işaret eden bir işaretçi(pointer) döndürür.

    int* a = new int;

`a` değişkeni tarafından işaret edilen hafıza, program içerisindeki
başka hiçbir değişken tarafından işaret edilmiyorsa, çöp toplayıcı
bu alanı otomatik olarak iade edecektir.

D dilinde işlevlerin 3 farklı güvenlik seviyesi mevcuttur:
`@system`, `@trusted`, and `@safe`.
Aksi belirtilmedikçe, `@system` varsayılandır.
`@safe` tasarımdan dolayı oluşabilecek bellek hatalarını engeller.
`@safe` kod sadece `@safe` veya `@trusted` işlevleri çağırabilir.
Dahası, açık bir şekilde işaretçi(pointer) aritmetiği `@safe` kod
içerisinde yasaktır.

    void main() @safe {
        int a = 5;
        int* p = &a;
        int* c = p + 5; // hata
    }

`@trusted` işlevler, Güvenli D ile alt-seviye dünyası arasında bir köprü
kurmayı sağlayan güvenli işaretlenmiş işlevlerdir.

### Derinlemesine

* [SafeD](https://dlang.org/safed.html)

## {SourceCode}

```d
import std.stdio : writeln;

void safeFun() @safe
{
    writeln("Merhaba Dünya");
    // GC ile yer ayırmak da güvenilir kabul edilir
    int* p = new int;
}

void unsafeFun()
{
    int* p = new int;
    int* fiddling = p + 5;
}

void main()
{
    safeFun();
    unsafeFun();
}
```
