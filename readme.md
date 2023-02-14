# **My Git Notes**

Git yapisi dosyalar ve dosyalardaki degisiklikleri takip etmek uzerine kuruludur. Boylece versiyonlama ve versiyonlar arasinda seyahat cok kolay hale gelmektedir.

### branch, commit, stage

Branch pek cok degisikligin commit'ler seklinde bulunduruldugu ana dallara verilen isimdir.

Commit ise bir onceki committen sonra yapilan degisikliklerin bir paket halinde taminlandigi durumdur

Stage ise dosyalardaki degisikliklerin commit oncesi tasindigi tanimlanmis bir alandir (sahne gibi dusunulebilir). Bir dosyadaki deisiklikleri stage a aldiginizda o anin bir fotografini cekmis gibi olursunuz. Hemen ardindan dosyada yapilan degisiklikler stage'i etkilemez. Bunun icin yeniden dosyayi stage'e eklemeniz gerekir.

Dosyalarda yapilan degisiklikleri git takip eder (byte by byte).
Bu degisiklikleri stage'e attiktan sonra (bkz. git add komutu) bu sefer tum stage'i gt commit komutu ile branch uzerinde yerini alacak bir commit'e koymaniz gerekir.

### git init
Bulunulan klasorde git yapisini kurar ve git degisiklikleri takibe baslar.

### git branch
git icindeki branchlardan o an uzerinde calisilanini gosterir

### git branch <branch_adi>
Bu komutla yeni bir branch yaratilir. Ancak uzerinde bulunulan branch'da kalmaya devam edilir.

### git status
Hangi brach uzerinde olundugu, degisiklik olusan dosyalar, bu dosyalarin degisikliklerinin stage uzerine alinip alinmadigi gorulur.

### git log
uzerinde bulunulan branchin commitleri ve gecerli head (en son yapilan commit) hangisi bu gorulur. Bu log icerisinde her commitin hash id si commitin yaninda gorulur. Bu id uzerinde bulunulan brach uzerinde commitler arasinda hareket edilmek istendiginde checkout komutuyla kullanilacaktir

### git checkout <branch_name> 
Bu komutun aliasi git switch <branch_name>'dir. 
Ustunde bulunulan branch'tan baska bir brancha gecmek icin kullanilir.

### git checkout <commit_hash_idsi>
id'si (git log ile gorulebilir) verilen commit'in brachindan bagimsiz olarak uzerine gidilir. Bu duruma **detached head state** denilir.
Baska sebeplerle de bu duruma dusulebilir.  
 Bu durumda buradan cikabilirsiniz bir brancha checkout ederek cikilir. git ilgili commiti arsivler.
 Bu durumdayken ek yeni degisiklikeler yapip bunlari commitler ettiyseniz aninda yeni bir branch olusturun. Degisiklikleri commitleyin ve bu branchi ana branch ile veya baska bir branch ile merge edin. Boylece degisiklikler bosa gitmez.

### git branch -d <branch_name> 
Eger branch baska bir branch'a merge edildiyse branchi siler. Merge yoksa dilmez. Bu islemi merge yoksa bile force etmek icin -d yerine -D kullanilir. Bu durumda branch her halikarda silinir. Bu kullanimda birden fazla branch isimleri bosluklarla eklenerek yazilirsa hepsi birden silinir.



