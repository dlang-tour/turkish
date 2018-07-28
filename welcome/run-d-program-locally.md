# D programlarını çalıştırmak

D derleyicisi `dmd`, kodlarınızı betik-gibi çalıştıran `rdmd` ve
paket yöneticisi `dub` ile gelir. 

### DMD Derleyicisi

*DMD* derleyicisi D dosya veya dosyalarını derleyerek kendi
başına çalışabilen (binary) bir dosya oluşturur.
Terminal aracılığıyla *DMD* dosya adıyla beraber çağırılabilir.

    dmd merhaba.d

DMD derleyicisinin davranışını değiştirmenizi sağlayan bir çok seçenek vardır.
Mevcut seçeneklere göz atmak için
[Online Documentation](https://dlang.org/dmd.html#switches) adresine bakabilir veya
`dmd --help` komutunu çalıştırabilirsiniz.

### `rdmd` ile Anında Derleme

Yardımcı araç `rdmd`, DMD derleyicisi ile beraber gelir,
Bütün bağımlılıkların otomatik olarak derlendiğinden emin olur ve
otomatik olarak uygulamayı çalıştırır.

    rdmd merhaba.d

UNIX benzeri sistemlerde Shebang satırı `#!/usr/bin/env rdmd`
çalıştırılacak D kodunun en üst satırına eklenerek betik-gibi çalışması sağlanabilir.


[Online Documentation](https://dlang.org/rdmd.html) adresine bakabilir veya
`rdmd --help` komutunu çalıştırabilirsiniz.

### `dub` Paket Yöneticisi

`dub` D dilinin standart paket yöneticisidir. `dub` yerel bir şekilde kurulmuştur.
Komut satırından `merhaba` adında yeni proje oluşturmak için: 

    dub init merhaba

`dub` komutunu bu klasör içerisinde çalıştırmak bütün bağımlılıkları yükleyecek ve
uygulamayı derleyip çalıştıracaktır.

`dub build` komutu programı derleyecektir.

Mevcut komut ve özellikleri görmek için [Online Documentation](https://code.dlang.org/docs/commandline)
adresine bakabilir veya `dub help` komutunu çalıştırabilirsiniz.

Bütün mevcut dub paketlerine [dub internet arayüzü](https://code.dlang.org) üzerinden göz atabilirsiniz.
