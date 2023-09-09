# Bilgisayarınızda D programlarını çalıştırmak

D derleyicisi `dmd`, kodlarınızı betik gibi çalıştıran `rdmd` ve paket yöneticisi `dub` ile gelir.

### DMD Derleyicisi

*DMD* derleyicisi D dosyalarını derleyerek çalıştırılabilen (binary) bir dosya oluşturur. *DMD* terminalde dosya adıyla beraber çağırılabilir:

    dmd merhaba.d

DMD derleyicisinin davranışını değiştirmenizi sağlayan bir çok seçenek vardır. Mevcut seçeneklere göz atmak için [çevrimiçi dokümentasyon](https://dlang.org/dmd.html#switches)a bakabilir veya `dmd --help` komutunu çalıştırabilirsiniz.

### `rdmd` ile Anında Derleme

Yardımcı araç `rdmd`, DMD derleyicisi ile beraber gelir, Bütün bağımlılıkların derlendiğinden emin olur ve kodu otomatik olarak çalıştırır.

    rdmd merhaba.d

UNIX benzeri sistemlerde shebang satırı `#!/usr/bin/env rdmd` çalıştırılacak D kodunun en üst satırına eklenerek betik gibi çalışması sağlanabilir.


Detaylı bilgi için [kullanım kılavuzu](https://dlang.org/rdmd.html)na bakabilir veya `rdmd --help` komutunu çalıştırabilirsiniz.

### `dub` Paket Yöneticisi

`dub` D dilinin standart paket yöneticisidir. Eğer `dub` bilgisayarınızda kuruluysa `merhaba` adında yeni bir projeyi komut satırından oluşturabilirsiniz:

    dub init merhaba

`dub` komutunu bu klasör içerisinde çalıştırmak bütün bağımlılıkları yükleyecek ve uygulamayı derleyip çalıştıracaktır. `dub build` komutu ise programı sadece derleyecektir.

Mevcut komut ve özellikleri görmek için [kullanım kılavuzu](https://code.dlang.org/docs/commandline)na bakabilir veya `dub help` komutunu çalıştırabilirsiniz.

Bütün mevcut dub paketlerine https://code.dlang.org sayfasından göz atabilirsiniz.
