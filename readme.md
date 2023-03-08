# **My Git Notes**

**Master Branch**: uzerinde calisilan ana branch

**Feature Branch** : ana branchdan dallanmis, yeni bir ozelligin gelistirildigi yan branch

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

### git branch -a
git push ve git pull islemlerinde origin uzerindeki (remote) master branch ile etkilesecek ve adina **Remote Tracking Branch** denilen bir ara branch olusur. -a parametresi ile remote uzerinde olusan bu tracking branch da listelenir.

Ornegin `git push` komutunda olusan islemler soyledir: 
 * `git push origin master` komutu verilir
 * localdeki master branchin bir kopyasi remote uzerinde olusturulan `remotes/origin/master` remote tracking branchina aktarilir.
 * Bu remote tracking branch ise remote uzerinde yaratilan `master` branchina kopyalanir.

Ornegin `git pull` komutunda olusan islemler soyledir:
* `git pull origin master` verilir
* remote uzerindeki master branch uzerinde `git fetch` calisir (otomatik)
* remote uzerindeki master branch bilgisi, remote da olusturulan `remotes/origin/master` remote tracking branch uzerine kopyalanir
* `git merge` komutu otomatik calisir 
* `remotes/origin/master` remote tracking branch uzerinden lokaldeki master branch uzerine kopyalanir.

**NOT:** `git fetch remote` remote brachlari locale transfer eder. Ancak pull komutu gibi merge etmez. Pull ve merge komutlarinin ise branch ile birlikte kullanilmasi gerekir. `git pull origin master` gibi.

### git branch -r
Sadece remote branchlar listlenir

### git branch -vv
local branchlar, en son commitleri ve tracking edilenlerin remote uzerinde eslestikleri branchlar listelenir 

### git branch -m <old_branch_name> <new_branch_name>
bir branchin ismini degistirmek icin kullanilir. Ilk isim halihazirdaki branch adi ikincisi ise brancha yeni verilecek isimdir.

## git branch --track <branch_name> origin/<branch_name>
remote ile ayni isimde local tracking branch olusturmaya yarar. Ayni isimde olmalari zorunludur.

### git ls-remote
localde olmayan ama github uzerinde push edilmis veya remote uzerinde olusturulmus branchlari gormek istersek bu komutu kullaniriz. Bu komut push edilmis olsun veya remote uzerinde manuel olusturulmus olsun tum remote branchlari listeler.

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

### git checkout <branch_name>
Uzerinde calisilan branch'tan ismi verilen brancha gecer.
`git switch <branch_name>` ile ayni isi yapar

### git checkout -b <new_branch_name>
Verilen isimle yeni bir branch olusturur ve onun uzerine gecer
`git switch -c <new_branch_name>` ile ayni isi yapar.


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
Son committen sonra yapilan ve stage e atilmamis (add ile stage e eklenmemis) tum degisiklikleri hafizada bir yere kaydedip (indeksli bir nesnenin icinde) son commit durumuna geri doner.

### git stash list
Yapilmis stash leri indeks nolariyla ve degisen dosyalarin ismiyle birlikte listeler. Indeksler tersinedir. Yani son eklenen stash surekli 0. indekstir. Yeni stash eklendikce indeksler kayar.

### git stash apply <stash_index_no>
Hafizadaki stashlerden indeks nosu verileni calisma ortamina geri yukler. Eger indeks no girilmemis ise son kaydedilen stashi calisma ortamina geri yukler.

### git stash push -m "<stash_message>"
Bu komutla stashlere not ekleyebiliriz (commit gibi) boylece `git stash list` komutunda stash icin aciklayici bir not gorunur, secilmesi kolay olur.

### git stash pop <stash_index_no>
Bu komutla stash listesindeki secilen stash calisma ortamina eklenir ve stash listesinden kaldirilir.

### git stash drop <stash_index_no>
Indeks nosu verilen stash listeden kaldirilir/silinir.

### git stash clear
Tum stash verisini siler.

### git reflog
Silinmis degisiklikleri (staged + commit) goruntulenir, hafizada saklanan bu degisiklikler birer hash no ile HEAD olarak temsil edilir. 
Boylece gidilmek istenen HEAD uzerine hash ile `git reset --hard <hash_code>` seklinde gidilebilir. 

### git reset --hard <hash_code>
`git reflog` ile goruntulenen listeden alinacak hash_no ile kullanilip ilgili HEAD uzerine gidilebilir. Boylece o commit geri getirilir.

NOT: Eger bir branch silindiyse ve `git reflog` ile gelen listede gidilmek istenen commit silinmis bir branch uzerindeyse `git checkout <hash_no>` ile bu secilen commit uzerine gidilirse `detached HEAD state` olusur. Bu durumdan cikmak icin: 
* Yeni bir branch olusturulup ona gecilir. `git switch -c <new_branch_name>` 
* Sonra istenirse master branch uzerine gecilip bu yeni branch merge edilebilir.

**NOT:** Local Tracking Branch ve Remote Tracking Branch birbirleriyle ayni isimlerde olmak zorundadir. Local Tracking Branch uzerinden godrudan Remote Tracking Branch'e push, pull yapilabilir. Branch izerindeysek `git push` ve `git pull` dogrudan calisir. 
* Eger bir bracnh'in tracking brach'i yoksa pull ve push kullanirken remote uzerindeki hangi brancha gonderilecegini /cekilecegini belirterek yazmak gerekir.
`git push origin new-feature-branch` gibi.
 
## MERGE

* Fast-Forward Merge
* Non Fast-Forward Merge
  * Recursive
  * Ours
  * Octopus
  * Subtree

### Fast-Forward Merge
Eger master branch da dallanma sonrasi hic yeni commit yoksa feature branch HEAD ine ait tum degisiklikler bu brancha tasinir. Ancak yeni commit yaratilmaz. (`--squash` flag eklenirse yaratilir. bkz asagisi) 

Kullanimi `git merge <feature_branch_name>` seklindedir.

Eger master branch'da (veya calisilan ve uzerine merge yapilan brancha) merge sonraki duruma donmek istersek `git reset --hard HEAD~<head_index_no>` ile donebiliriz. Hangi HEAD e donmek istedigimizi git log ile listeletip oradan secebiliriz. Bu geri alma isleminden feature branch etkilenmez. Uzerindeki commitler aynen kalir.

Eger `--squash` komutu kullanilirsa featured branch degisikliklerinin tamami tek bir HEAD haline getirilip master branch (icine merge edilen branch) uzerine eklenir.

Kullanimi `git merge --squash <feature_branch_name>` seklindedir.



### Recursive Merge
Eger master branchta yeni feature branch uretildikten sonra degisiklikler yapilip uzerine de commit yapildiysa o zaman default olarak merge non forward merge olur ve otomatik recursive merge olarak tanimlanir.

Recursive merge yapildiginda master branch da hali hazirda commitler vardir ve feature branch commitleri ardina eklenir. Burada commitler degisiklik siralarina gore mastera eklenir. Yani feature commitleri ile master commitleri siralarina gore ardisik dizilirler. En sona ise merge edilen feature branch'in son hali commit olarak eklenir (HEAD).

Eger bu sekilde yum commitlerin recursive olarak eklenmeini istemiyorsak `--squash` kullanabiliriz.

Boylece tum feature degisiklikleri masterin stageine eklenir ama commitlerde sadece masterin kendi komitleri gorunur. Bu stage dekiler de commitlenerek mastera eklenebilir.

### git merge --abort
merge sirasinda conflict varsa merge isleminden tamamen vazgecmek icin kullanilir. Conflict secenekleri degerlendirelerek merge islemine devam de edilebilir.

### git rebase <feature_branch>
Bu komutla master branch uzerinde feature branch ayrildiktan sonra yapilmis olan commitler de feature branch uzerine (kendi commitlerinden onceye) eklenir. Master branch ustundeki son commit base commit olur (her iki branch icin de).
Daha sonra master a gecilip feature uzerindeki tum commitler merge edilir (fast-forward merge).
* rebase commitleri tasimaz, yeni commitler yaratir
* kendi reponuz disinda commitleri rebase yapmayin.

Kullanimi:
Eger feature branch'in master'dan dallandigi noktadan sonra master uzerinde yapilan degisiklik commitlerini de feature uzerine almak istersek (geride kalmis olsalarda) 
feature branch uzerinde calisirken

`git rebase master` dedigimizde master uzerinde branch ayrilmasi sonrasi yapilmis yeni commitler feature branch uzerine ve kendi yeni commitlerinin oncesine (base) gelir. Boylece feature branch re-base edilmis olur.

**Commit hash idleri degistigi icin (yeniden yaratildiklarindan) branchlarin tum historysi degisir.** Takim calismalarinda yapilmasi onerilmez. Sadece lokal repoda yapilabilir.

Feature branch  rebase edildikten sonra master brancha gecilip feature branch onun uzerine merge edilir. 
Hangi durumda kullanilir. Feature uzerinde gelistirilen ozellikler master daki yeni gelistirmelere dayaniyorsa/ihtiyac duyuyorsa bu yapilabilir.

### git diff 
iki branch arasindaki farkliliklari gosterir (conflicts) .
Conflict giderilince merge edilebilir.


### git cherry-pick
Bir branchtaki tek bir commiti baska bir brancha merge etmek icin kullanilir. Bu brancha merge edilen commitin idsi degisir (yeni commit yaratildigindan).

**Ornegin:** Master branch'dan bir feature branch ayirdik ve gelistirme yaptik ve commitler yaptik. Sonra feature icinde olmayan ama temel bir duzeltme yapmak zorunda kaldik (masterda eksik kalmasin diye) feature uzerinde duzeltmeyi yapip commit yaptigimizda (duzeltmeye ozel commit) bu commit'in hash idsini aliriz.

Master uzerine geceriz. `git cherry-pick <commit_id>` komustu ile feature uzerindeki duzeltmeyi iceren commiti master uzerine yeni id ile cekeriz. Bu commit masterin yeni HEAD i olur.

## TAG
* Lightweight (temporary) tags: versiyon gibi basit bilgileri icerirler
* Annotated tags: son commitlere verilen full object (veri tasir) taglerdir

### git tag <tag_name> <commit_hash_id>
Tum tagleri gormek icin `git tag` komutunu kullaniyoruz. Belirli bir commite tag vermek icin commitin hash idsini kullanarak `git tag <tag_name> <commit_hash_id>` seklinde tag kaydediyoruz.

tagler uzerinden commitlere gecmek icin (detached head state olusur) `git checkout <tag_name>` seklinde kullanimi da vardir.

Tag silmek icin `git tag -d <tag_name>` komutu kullanilir.

### git show <tag_name>
taglenmis bir commitin bilgilerine tag uzerinden ulasabilmek icin kullanilan komuttur.


### git tag -a <tag_name> -m "<tag_verisi>"
Annotated tag denir. Son commite eklenir. Tag verisi bir aciklama veya eposta, author gibi bilgilerden olusan metindir. `git show <tag_name>` komutu ile goruntulenebilirler. Bu taglerin son commite eklenmesi ve veri tasimasi disinda tum ozellikleri temporary tagler ile aynidir.

## GITHUB

### git remote add origin "<url>"

remote add : uzaktaki bir baglantiyi eklemek demektir

origin: baglantiya verdigimiz isim/nick/alias (bize kalmis, ama gelnek origin seklinde)

url: originin temsil edecegi gercek ve tekil url

### git branch -M main

ana branch olarak hangi isimde bir branch kullanacagimizi belirtiriz. Genellikle main veya master kullanilir.


### git push -u origin main
push: Local degisiklikleri remote repository e atar

-u: upstream

origin main: remote repositorye (kisa adi origin) main branch'ina atar.

Eger default upstream branchdisindaki bir brancha push edilecekse (default olarak) o zaman upstream branch set edilmeli. Su an default main branch olarak gelir. Ornegin sadece
`git push` yazilirsa default upstream hangisiyse ona gonderir.

### git pull
Remote veriyi local repoya ceker.


### git clone
remote repoyu local e kopyalamaya yarar

### git branch --delete --remotes origin/<tracking_branch_name> 
remote uzerindeki ismi verilen tracking branchi silmeye yarar, localde -D ile siliyorduk, remote olunca -D kullanilmaz.

### git push origin --delete <branch_name>
remote uzerindeki ismi verilen nromal branchi silmeye yarar. Remote tracking branch silme ile aradaki farka dikkat!

**NOT:** Remote branch silinirse ona ait remote tracking brach da kendiliginden silinir!

### git push --force origin master
Localde bir head geriye dusulduyse (reset ile vb.) bunu remote a kabul ettirmek icin --force kullanmak zorundayiz.
