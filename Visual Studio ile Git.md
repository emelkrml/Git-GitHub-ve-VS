**Visual Studio ile Git** 
================================

Öncelikle Visual Studio da ayarlama yapmamıız gerekiyor. Visual Studio da **Tools -> Options -> Source Control -> Plug-in Selection** a geliyoruz.
Buradan **Git** seçeneğini seçip OK diyoruz. 

![vs](https://user-images.githubusercontent.com/21074849/37616497-2e14c22e-2bc1-11e8-8fc5-bec3a9910336.png)

Visual Studio' da **File -> New Project** diyerek bir tane Console Application açalım. 

Üstte **View -> Team Explorer** tıklarsak sağ tarafta Team Explorer sekmesi açılır.

![team](https://user-images.githubusercontent.com/21074849/37617742-10e80d9c-2bc5-11e8-96d0-01a0d14f8d52.png)

Bu sekmede bulunna ;

**New;** ile Git takibi olan yeni bir proje açılabilir.

**Add;** ile Git takibi olan yeni proje eklenebilir.

**Clone;** ile GitHub' tan proje çekebiliriz.


Projeyi oluşturduğumuz dosyayı kontrol edersek **.git, .gitignore ve .gitattributes** dosyalarını görürüz. Bu da oluşturduğumuz proje gti tarafından takip ediliyor demektir.

![vsgit](https://user-images.githubusercontent.com/21074849/37619620-078e8edc-2bcb-11e8-80d0-c1f61b0f0d39.png)

Şimdi projemizde değişiklik yapıp değişiklikleri remote repo ya atalım. Değişiklik yaptığımızda değişiklik yapılan dosyanın yanında kırmızı tik gözükür. Bu bize değişiklik yapıldığını ve bu değişikliğin kaydedilmediğini gösterir.

![vscommit](https://user-images.githubusercontent.com/21074849/37619565-ec160d6a-2bca-11e8-9914-88d6037f97ca.png)

Yaptığımız değişiklikleri kaydetmek için projeye sağ tıklayıp --> commit i seçelim.

![vscommit2](https://user-images.githubusercontent.com/21074849/37619773-80b4fa30-2bcb-11e8-926a-34bc5158b203.png)

 Sol tarafta **Enter a commit message** yazan yere commit mesajımızı girelim. 
 
![vscommes](https://user-images.githubusercontent.com/21074849/37620034-32a5ebc8-2bcc-11e8-8bd8-b621bfaae3e3.png)

**Commit All;** sadece değişiklikleri repomuza kaydeder, GitHub a kaydetmez.

**Commit All and Push** ise değişiklikleri hem repomuza hem GitHub a kaydeder.

**Commit All and Sycn** ise değişiklikleri kaydedip GİtHUb ile de senkronize eder fakat GitHub sitesinde push olmasını açılmasını da ister.

**Commit All and Push** seçeneğini seçip karşımıza gelen ekrana Yes diyelim. Resimde de görüldüğü gibi bizden url isteyecek.

![vsurl](https://user-images.githubusercontent.com/21074849/37620438-43385e34-2bcd-11e8-8267-a3a0cf5f4819.png)

Bunun için GitHub hesabımızda repo açıp url ini kopyalayalım.
 
 
