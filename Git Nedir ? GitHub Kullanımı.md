**Git nedir ve GitHub Kullanımı** 
================================

Git nasıl ortaya çıktı ?
------------------------

Çok sayıda Linux kernel geliştiricisi proje yönetimi için versiyon kontrol sistemi olan BitKeeper’ ı tercih etmekteydi. BitKeeper zamanının ötesinde, dağıtık bir kaynak kod yönetim sistemi sunmasına rağmen ücretsiz bir yazılım değildi ve kaynak kodu kapalıydı. Bununla birlikte Linux projesine bedelsiz olarak hizmet veriyordu.

Linux gibi bir projenin kapalı kodlu bir kaynak kod yönetim sistemi üzerinden yönetilmesi zamanında epey tartışmalara yol açmıştır.

2005 yılında **Andrew Tridgell** Bitkeeper uygulama protokolünü *reverse-engineering* yoluyla çözmeye çalıştı. Buradaki amacı BitKeeper ile entegre çalışabilecek araçlar üretmekti. **Andrew Tridgell**  BitKeeper protokolünü çözerek kendi istemcisini yazıp BitKeeper sunucusuna onunla bağlanmaya başladı.  Andrew 'in bu çalışması BitKeeper' ın sahibi olan firmanın tepkisini çekti ve Linux projesi için verilen ücretsiz lisansı iptal ederek konuyu hukuki platforma taşıyınca BitKeeper’ ın kullanımından vazgeçildi.

O günlerde **Linus Torvalds**, BitKeeper uygulamasında olduğu gibi dağıtık çalışan ve özellikle performans bakımından hızlı bir versiyon kontrol sistemi istiyordu. Buna cevaben **Linus Torvalds** kolları sıvayıp kafasındaki versiyon kontrol sistemini geliştirmeye başladı. Aradan 2 hafta geçtikten sonra, bugün en çok kullanılan dağıtık kaynak kod yönetim sistemi olan **Git** ortaya çıktı ve Linux kernel kaynak kodları için hizmet vermeye başladı. 

Git Nedir ?
-----------

Git bir versiyon kontrol sistemidir. Peki versiyon kontrol sistemi(VCS) ne işe yarar ?

En temel haliyle VCS;

-   Proje üzerinde yaptığımız değişiklikleri adım adım kaydetmemize,

-   Bu adımlardan herhangi birine geri dönebilmemize

-   Projeyi internet üzerinde oluşturduğumuz uzak depoda saklamamıza

-   Aynı projede farklı kişiler tarafından yapılan değişiklikleri çakışmaları önleyerek birleştirmemize olanak sağlayan bir platformdur.

Git Kurulumu
------------

-   **Windows;** [buradan](https://gitforwindows.org/) kurulumu sağlayabilirler. Kurulum bitince bir shell ekranı gelecektir.

-   **Debian** tabanlı GNU/Linux;

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    apt-get install git-core 
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    komutunu terminal üzerinden çalıştırdıklarında Git sistemlerine kurulacaktır.

-   **macOS;** [buradan](https://sourceforge.net/projects/git-osx-installer/) kurulumu sağlayabilirler.

>   *Klasik console yerine bize daha iyi bir arayüz sunan ve Linux’ te kullanılan bazı kodların Windows ortamında da kullanılmasını sağlayan cmder programonı da kullanabilirsiniz. Dosyayı indirdikten sonra ekstra bir kurulum gerekmeden uygulamayı çalıştırmanız yeterli olacaktır. Ben anlatımıma cmder ile gerçekleştireceğim.*

Kurulum işlemlerimiz bittikten sonra console a

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git --version 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

yazarak kurulumu kontrol edebiliriz.

![version](https://user-images.githubusercontent.com/21074849/37603869-a7ae213c-2ba0-11e8-96f5-c01eedbb1b5f.png)


Proje için Git Reposu oluşturmak
--------------------------------

Uygulamalarımıza başlamadan önce daha anlaşılır olmak adına ortak bir örnek üzerinden gidelim. Masaüstünde Test adlı bir klasör oluşturup içine test.txt dosyası oluşturalım.

Komut ekranımızda reposunu oluşturmak istediğimiz projenin klasörüne gidip aşağıdaki komutu yazalım.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git init
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


![init](https://user-images.githubusercontent.com/21074849/37604217-87b769b4-2ba1-11e8-8278-a4f81a556d54.png)


Bu kod **.git** adında gizli bir klasör oluşturur ve çıktıdan da anlaşılacağı gibi bu klasörün yolunu gösterir. Repo ile ilgili bilgilerin hepsi bu klasörde tutulmaktadır.

Dilerseniz repo kısmında tam ilerlemeden Git i daha iyi anlamak adına **.git** klasörünün içine göz atalım. Sırasıyla aşagıdaki kodları console a yazalım.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
cd .git
tree
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


![tree](https://user-images.githubusercontent.com/21074849/37604382-e99844d2-2ba1-11e8-8242-6c747988bc56.png)

**refs \> heads** te oluşturduğumuz branchlar tutulur. Branch lara daha sonra değineceğiz.

**objects** klasöründe şuan sadece *info* ve *pack* klasörleri var. Fakat ilerleyen zamanlarda biz projemiz üzerinde değişiklik yapıp commit (kaydet) ettiğimizde burada anlamsız dosya isimleri bulunacaktır. Bu klasörler bizim commit yaptığımız değişikliklerin tutulduğu yerlerdir.

Git değişiklikleri bu klasörde obje olarak kaydedip veritabanı tutmaması Git in dağıtık yapıda olmasını kolaylaştırıyor.

Commit işlemleri yaptığımızda **objects** klasörünü tekrar kontrol edeceğiz.

>   *Git değişiklikleri kaydederken SHA1 hash ini kullanır. Bundan dolayı kaydedilen değişiklikler 40 karakterli alfabe ve sayılardan oluşan dosya isimleriyle saklanır.* 

**.git** klasöründen çıkıp proje dizinimize geri gelerek aşağıdaki kodu yazalım.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git status 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bu kod proje dizinimizde en son kayıt yapıldıktan sonra yapılan değişiklikler varsa bize bu değişiklikleri gösterir.

![status](https://user-images.githubusercontent.com/21074849/37604579-5b0ac374-2ba2-11e8-8110-60b30543bb34.png)

Biz şuan dosyamızda hiç değişiklik yapmadığımız için bize *‘hiçbir değişikliğin kaydedilmediğini ve izlenmeyen dosyaların (test.txt)  olduğunu’* söyleyecek. test.txt dosyamız şuan izlenmediği için kırmızı renk olarak gelecek.

Şimdi dosyamızı aşağıdaki kodu yazarak kayıt listesine ekleyelim.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git add .
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Sonuna nokta koymayı unutmayalım. Nokta koyarsak tüm takip edilmeyen dosya ve klasörleri takibe alır.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git add klasor_adi
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

dersek takibe alınmasını istediğimiz klasörü takibe alır sadece.

Şimdi takibe alınna değişiklikleri kaydetme işlemi için aşağıdaki kodu yazalım.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git commit -m "ilk kayıt"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bu kod satırında “ilk kayıt” olarak belirttiğimiz yer commit mesajımızdır. Commit işlemi yaparken o aşamada projede ne yaptığımıza dair bize kısa bilgi veren commit mesajı girmemiz ileride geri dönüp baktığımızda bize yardımcı olur.

Mesela bu committe login işlemleri yaptığımız varsayarak;

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 git commit –m "login işlemleri" 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

şeklinde kaydettik ve daha sonra başka dosyalar üzerinde de değişiklik yapıp commitleme işlemleri yaptım. Sonra fark ettim ki login işlemlerinden sonra projede yanlış ilerlemişim ve login commit ime geri dönerek projemde doğru ilerlemek istiyorum. İşte burada işimize commit mesajı yarayabilir.

Ayrıca 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git commit am "commit  mesajı" 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

komut satırında ek kullandığımız **a** harfi kayıt işlemi yaparken bütün değişikliğe uğramış dosyaları da kayıta ekleyecektir.

![add](https://user-images.githubusercontent.com/21074849/37605013-5c43e08a-2ba3-11e8-806e-fdc8de31c288.png)

Çıktı bize 1 dosyada değişiklik olduğunu ve sıfır ekleme ile silme işlemi olduğunu söyleyecek.


Projeyi Remote Repo(Uzak Depo) ya atmak
---------------------------------------

Şuan projemiz local repoya atıldı fakat remote repoya atılmadı.

Remote repoya atmak için ilk olarak GitHub da kullanıcı hesabı oluşturduktan sonra sağ üst taraftan **New repository** e tıklıyoruz.

![remote](https://user-images.githubusercontent.com/21074849/37605247-d6ca0442-2ba3-11e8-8565-5373c377b4a3.png)

Karşımıza gelen ekranda;

-   **Repository Name** alanına proje ismimizi Test olarak yazıyoruz. Localde oluşturduğumuz proje ile aynı ismi taşımak zorunda değil.

-   **Description** kısmına projeniz hakkında kısa bir açıklama yazabilirsiniz.

-   Projemizi **Public** seçersek herkes projemizi görür ve kullanabilir. Private seçersek sadece bizim projeye eklediğimiz kişiler görebilir ve **Private** özelliği GitHub ta ücretlidir. Private a tıkladığınızda size kart bilgilerinizi sorar zaten. Public seçeneğini seçiyoruz.

-   **‘Initialize this repository witf a README’** kısmını işaretlerseniz size README.md dosyası oluşturur. Buraya da projenizde kullandığınız teknolojileri, kütüphaneleri ya da projenizin kurulumunun nasıl gerçekleşeceği hakkında bilgi verebilirsiniz. Biz bu kısmı işaretlemeyeceğiz.

-   **gitignore**; projede bulunan fakat versiyon kontrolü altına almak istemediğimiz dosya ve klasörleri burada belirterek takipten çıkarabiliriz.

    Örneğin; Python’ da proje yapıyorsunuz. Projede bazı dosyalar ya da dosyalara ait uzantılar vardır bunların takip edilmesini istemiyorsunuz. Add .gitignore’ de Python ı seçerseniz bunları size hazır olarak getirir.

    Burada da şuan bir seçim yapmıyoruz. Ama geniş çaplı projelerde sonradan manuel olarak girmeye uğraşmamınız açısından burada seçim yapmanız yararınıza olur.

-   **licence;** Lisans da depoya koyduğunuz projenin başkaları tarafından kullanılması durumunda sorumlu olacakları lisans şartlarını içerir.

![create](https://user-images.githubusercontent.com/21074849/37605416-33c5bca4-2ba4-11e8-9d8d-66e6bdf4a2b4.png)

Create repository e tıklayarak repomuzu oluşturuyoruz.

![save](https://user-images.githubusercontent.com/21074849/37605528-6d2950c8-2ba4-11e8-8565-64f99165cdcc.png)

Sırasıyla çerçeve içine aldığımız ksımlardan bahsedelim.

İlk çerçevede remote repomuzun url i mevcut. Başka bir bilgisayara kurulum yapmak isteediğimizde bu url i kullanırız.

İkinci çerçeve; biz repoyu oluştururken README.md seçeneğini seçmedik. Burada bu dosyayı sonradan eklemek için izleyeceğimiz yolu anlatıyor.

Üçüncü çerçeve; localdeki projemizi url i kullanarak remote repoya nasıl atacağımızı gösteriyor.

Son çerçeve ise Subversion, Mercurial veya TFS ile takip edilen bir projenizi buraya import edebileceğinizi gösteriyor.

Biz burada üçüncü çerçeveyi uygulayacağız. Burada yazan kodları console a yazalım.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git remote add origin https://github.com/emelkrml/Test.git
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git push -u origin master
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

![remoteadd](https://user-images.githubusercontent.com/21074849/37605858-2cfa92fe-2ba5-11e8-8030-bd70450c04b1.png)

Çıktıdan da anlaşıldığı gibi localdeki projemizi remote repo url i kullanılarak repote repoya kaydedildi.

Hatırlarsanız daha önce git te yapılan değişikliklerin **.git** dosyasında obje olarak tutulduğundan bahsetmiştik. Şimdi Git yapısını daha iyi anlamak için tekrar **.git** dosyasına dönelim.

![treegit](https://user-images.githubusercontent.com/21074849/37606496-a622bf3e-2ba6-11e8-9116-d315677187c7.png)

**refs \> remotes** remote repo da origin de olduğumuzu gösterir.

**objects** dosyasının içine bakarsak **52, 5e, e6** isimlerinde dosyaların oluştuğunu görürüz. Şimdi **52** klasörüne girerek bunu kontrol edelim.

![ls](https://user-images.githubusercontent.com/21074849/37612670-e31233c4-2bb6-11e8-8ec9-e492fd6c4577.png)

**52** klasörünün içinde bulunan dosyaları listelediğimizde 40 karakterden oluşan bir dosya ismi görürüz ve bu dosyanın bu şekilde anlamsız bir isme sahip olması yaptığımız commit işleminin SHA1 şeklinde hashlenerek Git te tutulmasıdır.

Burada dikkat edilmesi gerekne bir diğer hususta bunun GitHub’ ta entegresidir. objects klasöründeki **52** klasörü ve **27723** ile başlayan dosya ismini unutmayalım. GitHub a gidelim ve commit ettiğimiz yerde bulunan isme bakalım.

![github](https://user-images.githubusercontent.com/21074849/37606240-0bfb4ce6-2ba6-11e8-9be6-0e55a8711be5.png)

 “ilk mesaj” commitimize ait obje GitHub’ta da bu şekilde görüntüleniyor.

Benzer şekilde özet bir commit almak için console aşağıdaki kodu yazalım.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git log
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

![log](https://user-images.githubusercontent.com/21074849/37613016-f65cb5de-2bb7-11e8-92f0-4e00fd57b3e0.png)


Görüldüğü gibi oluşan obje klasörümüz(52) ve bunun içinde oluşan dosyamız(2772...) commit işlemimizin nasıl kaydedildiğini gösteriyor.

**HEAD - \> master** diye gösterdiği kısım ise bizim master branch ında olduğumuzu gösteriyor. Ayrıca console a

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git branch 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

yazarakta hangi branch ta olduğumuzu öğrenebiliriz.
