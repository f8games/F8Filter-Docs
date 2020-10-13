# Charicon Kullanım rehberi

Charicon oyun içerisindeki karakterlere, karakter isminin yanında o karaktere özel verebileceğiniz icon sistemidir.

### İstemci(Client) tarafı;
![RefRankCrest](../images/chariconclientside.png)

**RefRankCrest.txt dosyası media.pk2 dosyanızda "server_dep/silkroad/textdata/refrackcrest.txt" yolunda bulunmaktadır.**

>Kırmızı ile belirtilen alan, "<span style="color:red">Service</span>" kolonudur. Bu alandan eklediğimiz icon'u aktif veya deaktif edebiliriz.
>
>Yeşil ile belirtilen alan, "<span style="color:green">Dosya yolu</span>" kolonudur. Bu alandan media.pk2 dosyanıza eklemiş olduğunuz dosyanın(iconun) yolunu gösterebilirsiniz.
>
>Mavi ile belirtilen alan, "<span style="color:blue">ID</span>" kolonudur. Bu alandan iconunuza bir ID tanımlayabilirsiniz. Tanımladığınız bu ID'yi veritabanı tarafında kullanacaksınız.

### Veritabanı tarafı;
![CharIcon](../images/charicondbside.png)


> <span style="color:red">CharID</span>: Kullanıcının karakterinin veritabanındaki sanal kimliği.
> 
> <span style="color:red">RankCrest</span>: Kullanıcıya vereceğiniz iconun ID'si. 


**Örnek bir SQL kodu ile "<span style="color:red">F8FilterTEST</span>" isimli kullanıcı'ya RankCrest textimizdeki 1 numaralı icon'u verelim;**

~~~~Mssql
[USE F8Filter]
update _Char set RankCrest = '1' where CharID = (select CharID from SRO_VT_SHARD.._Char(NOLOCK) where charname16 = 'F8FilterTEST') --Eğer shard veritabanı adınız SRO_VT_SHARD değilse query'i kendi shard veritabanı adınız ile çalıştırmalısınız.
~~~~

**NOT:** <span style="color:red">Bir karakter aynı anda en fazla 1 charicon'a sahip olabilir.</span>

**NOT2:** <span style="color:red">Ekleyeceğiniz iconlar 16x16 boyutuna sahip olmalıdır.</span>