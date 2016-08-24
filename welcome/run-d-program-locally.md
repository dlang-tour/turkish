# D programını çalıştırma

D `dmd` adlı derleyici, `rdmd` adlı script derleyicisi ve 
`dub` adlı paket yöneticisi ile beraber gelir.

### DMD Derleyicisi

*DMD* derleyicisi D dosyalarını derler ve ikili(binary) çıktısı üretir.
Komut satırından *DMD* aşğıdaki gibi çağrılabilir.

    dmd merhaba.d

*DMD* derleyicisinin davranışlarını değiştiren çok fazla komut bulunmaktadır.

Kullanılabilir derleyici komutlarını görebilmek ve bilgi almak için [çevrimiçi belgelere](https://dlang.org/dmd.html#switches) göz atın veya `dmd --help` komutunu çalıştırın.

### `rdmd` ile anında derleme

`rdmd` yardımcı aracı, DMD derleyicisi ile beraber gelir.
Bütün bağımlılıkları derler ve üretilen programı otomatik olarak çalıştırır.

    rdmd merhaba.d

UNIX tabanlı sistemlerde, çalıştırılabilir D dosyanın en başına `#!/usr/bin/env rdmd` satırını ekleyerek script gibi kullanabilirsiniz.

Kullanılabilir komutları görebilmek ve bilgi almak için [çevrimiçi belgelere](https://dlang.org/rdmd.html) göz atın veya `rdmd --help` komutunu çalıştırın.

### Paket yöneticisi `dub`

D'nin standart paket yöneticisi [`dub`](http://code.dlang.org).
`dub`'ı bilgisayarınıza kurduğunuzda, `merhaba` adlı yeni bir aşağıdaki komut ile oluşturulabilir: 

    dub init merhaba

`dub` oluşturulan merhaba adlı klasör içerisinde çalıştırıldığında, bütün bağımlılıkları çözer,
uygulamayı derler ve çalıştırır.

`dub build` komutu uygulamayı çalıştırmadan sadece derler.

Kullanılabilir komutları görebilmek ve bilgi almak için [çevrimiçi belgelere](https://code.dlang.org/docs/commandline) göz atın veya `dub help` komutunu çalıştırın.

Mevcut bütün dub paketleri dub [internet arayüzünden](https://code.dlang.org) görüntülenebilir.