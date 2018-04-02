**Visual Studio ile Git** 
================================

Öncelikle Visual Studio da ayarlama yapmamıız gerekiyor. Visual Studio da **Tools -> Options -> Source Control -> Plug-in Selection** a geliyoruz.
Buradan **Git** seçeneğini seçip OK diyoruz. 

![vs](https://user-images.githubusercontent.com/21074849/37616497-2e14c22e-2bc1-11e8-8fc5-bec3a9910336.png)

Visual Studio' da **File -> New Project** diyerek bir tane ***Console Application*** açalım. 

Üstte **View -> Team Explorer** tıklarsak sağ tarafta Team Explorer sekmesi açılır.

![team](https://user-images.githubusercontent.com/21074849/37617742-10e80d9c-2bc5-11e8-96d0-01a0d14f8d52.png)

Bu sekmede bulunna ;

**New;** ile Git takibi olan yeni bir proje açılabilir.

**Add;** ile Git takibi olan yeni proje eklenebilir.

**Clone;** ile GitHub' tan proje çekebiliriz.


Projeyi oluşturduğumuz dosyayı kontrol edersek **.git, .gitignore ve .gitattributes** dosyalarını görürüz. Bu da oluşturduğumuz proje git tarafından takip ediliyor demektir.

![vsgit](https://user-images.githubusercontent.com/21074849/37619620-078e8edc-2bcb-11e8-80d0-c1f61b0f0d39.png)

Şimdi projemizde değişiklik yapıp değişiklikleri remote repo ya atalım. Değişiklik yaptığımızda değişiklik yapılan dosyanın yanında kırmızı tik gözükür. Bu bize değişiklik yapıldığını ve bu değişikliğin kaydedilmediğini gösterir.

![vscommit](https://user-images.githubusercontent.com/21074849/37619565-ec160d6a-2bca-11e8-9914-88d6037f97ca.png)

Yaptığımız değişiklikleri kaydetmek için projeye sağ tıklayıp --> commit i seçelim.

![g0](https://user-images.githubusercontent.com/21074849/38192098-0e093a88-3674-11e8-8163-6cea581538d6.png)

 Sol tarafta **Enter a commit message** yazan yere commit mesajımızı girelim. 
 
![g1](https://user-images.githubusercontent.com/21074849/38192099-0e39a95c-3674-11e8-841a-e00535a389b7.png)

**Commit All;** sadece değişiklikleri repomuza kaydeder, GitHub a kaydetmez.

**Commit All and Push** ise değişiklikleri hem repomuza hem GitHub a kaydeder.

**Commit All and Sycn** ise değişiklikleri kaydedip GİtHUb ile de senkronize eder fakat GitHub sitesinde push olmasını açılmasını da ister.

**Commit All and Push** seçeneğini seçip karşımıza gelen ekrana Yes diyelim. Resimde de görüldüğü gibi bizden url isteyecek.

![vsurl](https://user-images.githubusercontent.com/21074849/37620438-43385e34-2bcd-11e8-8267-a3a0cf5f4819.png)

Bunun için GitHub hesabımızda GitProject adında repo açıp url ini buraya kopyalayalım ve Publish diyelim. GitHub sayfasını yenilediğimizde projenin glmiş olduğunu görürüz.

![g2](https://user-images.githubusercontent.com/21074849/38192336-17a616fa-3675-11e8-97fe-2b1635d5032a.png)
 
 Buraya kadar oluşturulan bir projeyi ve bu projede yapılan değişiklikleri GitHub hesabına atma işlemi gerçekleştirildi.
 
 Aynı şekilde ***Program.cs*** dosyasında değişiklik yapıp solution a sağ tıklayıp ***Commit*** diyelim. Commit mesajımıız yazıp ***Commit All and Push*** dediğimizde bu sefer url istemeden direkt GitHub reposuna gönderir.
 
  Changes alanında ise hangi dosyalarda değişiklik olduğunu gösterir. Eğer bu kısımda değişiklikleri geri almak istenirse ilgili dosyaya sağ tıklanıp ***Undo Changes...*** denir.
  
  Aynı işlem solution a sağ tıklayıp ***Undo*** diyerekte yapılabilir.
 
![g3](https://user-images.githubusercontent.com/21074849/38192914-0d9597fa-3678-11e8-8f43-1d2766720d72.png)
 
 GitHub sayfasını yenileyelim. Yapılan değişiklik commit mesajında gözükecek. 
 
 ![g4](https://user-images.githubusercontent.com/21074849/38192724-fc0e813c-3676-11e8-9cef-513e089d3919.png)
 
 Team Explorer - Home' da bulunan özelleikleri inceleyelim.
 
 ![g5](https://user-images.githubusercontent.com/21074849/38193190-6f4574ce-3679-11e8-8c4d-c3e9316121d3.png)

***Changes;*** yapılan değişiklikleri gösterir.

***Branches;*** oluşturulan brancların ve hangi branc ta olduğumuzu gösterir.
 
***Syn;*** projeyi senkronize etmemizi sağlar ya da yeni proje açıkdıysa ***Sync -> Push*** diyerek projeyi remote repo ye gönderir. 
 
 ***Setting;*** seçeneğinden ise GitHub hesabımızla ilgili değişiklikler yapılabilir.
 
 >   ***NOT:*** Projede gerçekleştirilen değişiklik geçmişini görüntülemek için solution ya da ilgili dosyaya tıklayarak ***View Story...*** diyerek görüntüleyebiliriz.
 
***GitProject.sln*** a tıklayıp yukarısında bulunan ***New*** e tıklarsak solution a yeni proje ekleyebiliriz.
***Open*** diyerek varolan projeyi açabiliriz.

**Branch**
--------------------------------
Projede gerçekleştirilen işlemlere göre dallanmalar olabilir. Bu dallanmalar proje yönetiminde iş akışını ve yönetimini kolaylaştırır. Ayrıca gerçekleştirilen dallanmalar ana projede bozulmayı engeller. 

Web sitesi yapacağımızı düşünelim. Sitede gerçekleştirecek işlemleri branch sayesinde küçük iş parçacıklarına bölerek büyük yapı oluştururuz. İş parçacıkları projeyi daha kontrollü bir şekilde büyütmemizi sağlar.

Web sitesinde menü, footer ve sosyal medya şeklinde 3 tane ayrı branch açtığımızı düşünelim. Bu 3 branch ı ayrı ayrı bitirdikçe ana projeye yani master a commit ederiz. Herhangi bir branchta sorun yaşadığımızda tekrar brancha dönüp değişiklik gerçekleştiririz. Mesela web sitesinde sosyal medya branch ını bitirip commitledim. Fakat daha sonra web sitesinde böyle bir özellik istemediğimize karar verdik. Direkt commitlenmiş sosyal medya branch ını silerek ana projeden sosyal medyayı çıkarmış oluruz. 

Şimdi uygulamalı olarak Visual Studio branch açalım.

Sağ allta bulunna ***master*** yazısına tıklayıp ***New Branch*** diyelim. Yukarıda gelen alana branch ismi girerek ***master*** dalını seçelim ve ***Create Branch*** diyelim.

>   master dalı dışında bu kısımda daha sonra oluşturduğumuz branchlarda bulunabilir. O branch lardan birini seçerek onlar üzerinde de dallanabiliriz.

![g6](https://user-images.githubusercontent.com/21074849/38194429-20f10d68-3680-11e8-958d-e736399302cd.png)

Sonra sağ alta bakarsak oluşturduğumuz ***TestBranch*** gelir.

![g7](https://user-images.githubusercontent.com/21074849/38194610-3421ffae-3681-11e8-9fff-159fea2ceb98.png)

Şimdi branch üzerinde değişiklik yapıp commit leyelim. Projeceye ***BranchClass*** isminde class ekleyelim. Solution a sağ tıklayıp Commit diyelim.

![g8](https://user-images.githubusercontent.com/21074849/38195407-038c13ca-3686-11e8-8281-a3eb4f4555a7.png)

>   Commit yaparken hangi branch ta olduğumuza dikkat edelim !!!

***Commit All and Push*** dedikten sonra GitHub sayfasına gelip yenileyelim. Karşımıza aşağıdakine benzer görüntü gelecektir.

![g9](https://user-images.githubusercontent.com/21074849/38195408-03aa6f82-3686-11e8-98b6-185d68097aad.png)

Burada branch ı çekip projeye eklememizi için onay istiyor. ***Compare & Pull Request*** diyerek işlemi onaylayalım. 

![g10](https://user-images.githubusercontent.com/21074849/38195410-03c87cd4-3686-11e8-95ef-af5b5296f870.png)

***Able to merge*** proje de çakışma olmadıpğını ve ana projeye tamamen branch ı sorunsuz bağlayabileceğimizi elirtiyor.

>   Bazı durumlarda projede ekip şeklinde çalışıldığında branchlarda çakışma gerçekleşebilir. Mesela oluşturduğumuz ***BranchClass***
içerisinde aynı anda 2 kişi değişiklik yapıp commitlediğinde çakışma meydana gelir. Git hangi değişikliği commitleyeceğine karar veremez. Bu gibi durumlarda ***Able to merge*** yerine çakışma olduğunu belirten bir hata gelir ekrana.

Branch a tercihe göre açıklama ekleyebiliriz. Eklemeden geçelim.

![g11](https://user-images.githubusercontent.com/21074849/38195411-03e7b694-3686-11e8-8664-b0dd8b493572.png)

Pull işlemi başarılı bir şekilde gerçekleştikten sonra branch ı merge ederek ana projeye dahil ederiz.

![g12](https://user-images.githubusercontent.com/21074849/38195412-0406a734-3686-11e8-8b18-9ecbf5e6b16a.png)

Branch başarılı şekilde merge edilerek kapatıldı.

![g13](https://user-images.githubusercontent.com/21074849/38195413-042480ce-3686-11e8-956e-a2503083576b.png)

 GitHub sayfasını yenilendiğinde branch ın geldiğini ve 2 branches yazıldığını göreceğiz.

İlk branch projeyi GitHub a atmamız, ikinci branch ise ***TestBranch*** atmamız.


