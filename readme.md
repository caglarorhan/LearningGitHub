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

### git --version
Yuklenmis son git versiyonunu verir

### git branch
git icindeki branchlardan o an uzerinde calisilanini gosterir

### git branch <branch_adi>
Bu komutla yeni bir branch yaratilir. Ancak uzerinde bulunulan branch'da kalmaya devam edilir.

### git switch <branch_name> 
Calisma branch olarak belirtilen branch uzerine gecer.
Eger bu komut -c veya -C parametresiyle kullanilirsa , verilen isimle yeni bir branch olusturup onun uzerine gecer.

### git status
Hangi brach uzerinde olundugu, degisiklik olusan dosyalar, bu dosyalarin degisikliklerinin stage uzerine alinip alinmadigi gorulur.

### git log
uzerinde bulunulan branchin commitleri ve gecerli head (en son yapilan commit) hangisi bu gorulur. Bu log icerisinde her commitin hash id si commitin yaninda gorulur. Bu id uzerinde bulunulan brach uzerinde commitler arasinda hareket edilmek istendiginde checkout komutuyla kullanilacaktir

### git checkout <branch_name> 
Bu komutun aliasi git switch <branch_name>'dir. 
Ustunde bulunulan branch'tan baska bir brancha gecmek icin kullanilir.

Eger `git checkout -b <branch_name>` seklinde kullanilirsa verilen isimle yeni bir branch olusturulur ve ona gecilir.

### git checkout <commit_hash_idsi>
id'si (git log ile gorulebilir) verilen commit'in brachindan bagimsiz olarak uzerine gidilir. Bu duruma **detached head state** denilir.
Baska sebeplerle de bu duruma dusulebilir.  
 Bu durumda buradan cikabilirsiniz bir brancha checkout ederek cikilir. git ilgili commiti arsivler.
 Bu durumdayken ek yeni degisiklikeler yapip bunlari commitler ettiyseniz aninda yeni bir branch olusturun. Degisiklikleri commitleyin ve bu branchi ana branch ile veya baska bir branch ile merge edin. Boylece degisiklikler bosa gitmez.


### git branch -d <branch_name> 
Eger branch baska bir branch'a merge edildiyse branchi siler. Merge yoksa dilmez. Bu islemi merge yoksa bile force etmek icin **-d** yerine **-D** kullanilir. Bu durumda branch her halikarda silinir. Bu kullanimda birden fazla branch isimleri bosluklarla eklenerek yazilirsa hepsi birden silinir.

### git add <file_name> 
bir dosyadaki degisiklikleri stage alanina ekler. Eger dosya adi yerine . koyulursa gitin takip ettigi tum dosyalardaki degisiklikleri stage alanina ekler.

### git commit -m "<commit_message>"
Yapilmis degisiklikleri yeni commit olusturup icine ekler ve buna bir mesaj ekler.

### git ls-files 
Stage alanina eklenmis tum dosyalari listeler (git add ile eklenmis)

### git merge <branch_name> 
Adi verilen branch'i uzerinde bulundugumuz branch'a birlestirir.

### git rm <file_name>
Ismi verilen dosyayi siler

### git checkout (--) .
Stage uzerine alinmamis tum degisiklikleri siler (geri alir)

### git restore <file_name> veya .
git checkout -- ile ayni isi yapar. Stage'e alinmamis degisiklikleri siler/geri alir.

### git clean -df 
Takip edilmeyen tum dosyalari siler (df: delete force)

### git reset <file_name> 
### git checkout -- <file_name>
### git restore --staged <file_name> veya .
Hepsi stage alanindaki tum degisiklikleri kaldirir. (add in tersi)

### git reset HEAD~1 
Eger default olarak --soft flag gecerlidir. `git reset --soft HEAD~1` seklinde kullanilirsa commiti siler ama degisiklikleri stage alaninda birakir --hard kullanilirsa commiti siler ve degisiklikleri de stage den kaldirir.

### git stash
Son committen sonra yapilan tum degisiklikleri hafizada bir yere kaydedip (indeksli bir nesnenin icinde) son commit durumune geri doner.

### git stash list
Yapilmis stash leri indeks nolariyla ve degisen dosyalarin ismiyle birlikte listeler

### git stash apply <stash_index_no>
Hafizadaki stashlerden indeks nosu verileni calisma ortamina geri yukler. Eger indeks no girilmemis ise son kaydedilen stashi calisma ortamina geri yukler.
