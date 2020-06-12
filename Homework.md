**6 Haziran Ödevleri**

**Git Flow**

Git flow, yazılım geliştirmenin her aşamasını kolayca yönetmek için farklı
dallarla çalışır, yazılımınızın “sürüm” kavramına sahip olması durumunda
kullanılması önerilir, çünkü bu kavramın eksik olduğu Continuous Delivery veya
Continuous Deployment ortamında çalışırken en iyi karar değildir. Bu akışın bir
başka iyi yanı, ekiple birlikte çalışırken ve bir veya daha fazla geliştiricinin
aynı özellik için işbirliği yapması gerektiğinde mükemmel uyum sağlamasıdır.

**Merge Pull Request**

\- Create Merge Commit, tüm commitleri historyde tutar ve master branch'a taşır.
Squash and Merge, tüm commitleri tek bir committe gruplandırır. Rebase and
Merge, History'deki tüm commitleri master branch’in önüne ekler.

\- Merge Commit ve Squash and merge son işlemde ekstra commit ekler, rebase and
merge ise eklemez.

[AspNet Boilerplate - Web Application Framework](https://aspnetboilerplate.com/)

ASP.NET Boilerplate, özellikle yeni modern web uygulamaları için tasarlanmış
genel amaçlı bir uygulama çerçevesidir. Tanıdık araçlar kullanır ve size bir
SOLID geliştirme deneyimi sunmak için etraflarındaki en iyi uygulamaları
uygular.

**7 Haziran Ödevleri**

**Razor Pages**

Razor Pages, mvc (model view controller)'a göre daha kolay uygulama geliştirmeyi
sağlayan bir platformdur. Frontend çatılarda kullanılan yaklaşım olan model view
view model (mvvm) yapısına benzeşen two way binding özelliğini desteklemektedir.

** C\# Json Serialize/Deserialize**

**Serialization**, nesnelerin çalışma zamanındaki (runtime) durumlarını alıp
geçici veya kalıcı olarak bir kaynağa (*file,memory, database, socket,
buffer* vb.) saklamak/transfer etmek için belirli bir forma dönüştürülüp yazma
işlemidir. **Deserialization**, bir kaynakta (*file,memory, database, socket,
buffer* vb.) bulunan serileştirilmiş (serialize) belirli bir formdaki
nesnelerin, ihtiyaç olduğunda çalışma zamanındaki durumunu elde etme işlemidir.

**MVP vs MVC vs MVU**

MVP Pattern’i MVC’den evrilmiş bir patterndir, sadece bağımlılıklar değişir ve
Controller’ın yerine Prenseter (ki bu durumda kendisine hala Controller
denebiliyor) gelir. Inputları direkt View karşılar, modern programlama
ortamlarının mantığına daha uygundur. View Presenter’ını biliyor, Presenter ise
View’i bir interface aracılığıyla biliyor aralarında bir abstraction var. Ayrıca
MVC’nin aksine View ile Presenter arasında 1–1 ilişki var. Presenter Model’i
manipule ediyor, Model’in değişikleri Presenter’a notify etme durumu birazcık
tartışmalı, etmeyedebilir, Presenter ilgili değişikliği yapıp, View’i kendisi
güncelleyebilir. Zaten buradaki en büyük fark MVC’nin aksine Presenter’ın View’i
bir interface aracılığıyla kendisinin güncellemesi, View burada Presenter’a
interface aracılığıyla istediği bilgiyi açabilir, ister Textbox’ın Text’i olsun
ister Buton’ın Enabled’ı olsun. Presenter View’in nasıl bir View, Web mi?
Windows mu? olduğuyla ilgilenmiyor, sadece data akışıyla ilgili ne yapması
gerektiğini, View’den gelen etkileşimleri nasıl karşılaması gerektiğini ve
View’de nasıl değişikler yapması gerektğini biliyor. Yani Prensenter’ımız burada
karar mekanizaması rölünü üstleniyor.

MVC, Model, View, Controller’dır. Controller kullanıcıdan gelen inputları
karşılar, ayrıca UI ile ilgili bütün akışı yönetir ve kararları verir.
Controller View hakkında hiç birşey bilmez ama View Controller’ı bilir.
Görüldüğü üzere Controller ile View arasında 1-n bir ilişki var yani bir
Controller birden fazla View tarafından kullanılabilir. Controller kullanıcıdan
gelen inputlar doğrultusunda Model üzerinde değişikleri yapar, Model değiştiğini
View’e notify eder yani View ile Model arasında Observer ilişkisi var. View,
Model’e register olur, görüldüğü üzere bir model’e birden fazla View register
olabilir. Aralarında ki observer ilişkisi sayesinde, Model’deki herangi bir
değişiklik ona register olmuş bütün View’lere yansır.

Şeması birazcık MVP’yi andırıyor fakat buradaki fark, Presentation Model hem
View ile ilgili stateleri tutuyor hemde View hakkında hiç birşey bilmiyor.
Aslında PM View’in state ve davranışlarıyla ilgili bilgiyi kendi üzerine alıyor
ve Business Layer ile arasındaki kordinasyonu sağlıyor ve View’e karar vermeyle
ilgili çok az şey bırakıyor. View yine stateleri tutuyor aslında. Fakat MVP’nin
aksine Presentation Model View ile ilgili hiç bir bilgiye ihtiyaç duymuyor, bu
yüzden ki View ile PM arasında 1-n bir ilişki var, bir PM birden fazla View’de
kullanılabiliyor, bu kısmıyla MVC’ye benziyor, fakat MVC’nin aksine View
üzerinde ki manipulasyonlar PM üzerinden gerçekleşiyor. Aslında şöylede
bakabiliriz, PM ile View arasında yine bir observer ilişkisi var, .Net’e
kullanım şekillerinden biride **INotifyPropertyChanged** interface’inden
türeyip, .Net’in binding alt yapısını kullanması. Zaten özünde yaptığı iş
DataBinding. Kendi propertylerini View’in propertyleriyle senkronize ediyor,
aynı zamanda state’lerede karar veriyor, mesela şu şu TextBox dolduğunda şu
Buton enabled olsun gibi. Tabi herzaman enabled olucak bir kontrol’un state’ini
PM’de tutmak anlamsız. Yukarıda da bahsettiğim gibi MVVM PM ile aynı prensip
üzerine kurulu ama WPF ve Silverlight’da ki XAML ve Binding alt yapısına
optimize bir şekilde düzenlenmiş olması. Yukarda da bahsettiğim gibi PM’in tek
dez avantajı elde uygun bir binding mekanizması yoksa çok fazla bu iş ile ilgili
kod yazılması. Windows Forms’un bir binding alt yapısı var ama WPF’in Binding
alt yapısı çok üstün, çok yetenekli. En basidinden WPF’de herangi bir UI
Elementinin (bkz : XAML) herangi bir propertysini bir .NET nesnesinin property
ve ya methoduna bind edebiliyorsunuz ayrıca bir karar mekanizmasına sahip
Command alt yapısıda var.
