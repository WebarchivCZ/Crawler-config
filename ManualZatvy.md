<h1>Manuál žatvy</h1>

<h2>1. Check tabulky</h2>
<h2>2. Vygenerovani odpovidajicich seminek</h2>
<h3>Generácia v Sidri</h3>
  <ul><li>1. Choď do "semínkovače"</li>
  <li>2. ctrl+a -označ všetko</li>
  
<h2> Práca v terminály</h2>

</h3>1. nahoď si pracovné prostredie via</h3>
 <pre>screen -r </pre>

</h3>2.</h3> vleze sa do dovnitr k seeds po rokoch, vytvorit vo formate a nazve seeds-2017-02-a pripona sklizne, V - je vyberova, V1M .txt
Spolu so seederom sa vygeneruju prislusne seminka a zavedu sa do suborov
Plus seminka pro <b>cuni</b>  a <b>no contracts</b>>> http://intranet.webarchiv.cz/seeds/no_contracts.php, su s priponou <b>NoContracts (je to V-NC)</b>
Cuni su vo vonkajsom adresari a vedle crawler beans, a pevne zadefinovany odkaz v beansoch

</h3>3. Zlucenie seedov</h3>
Deje sa cez slozku jobs v koreni vsetkych heritrixov a cez jobs do crawler config

Semienka si treba vysortiť na unique a vizuálne ešte raz skontrolovať. Ak by bolo niečo divné,
poslať hneď podnet kurátorom.
<pre>
$ sort 2017/seeds-2017-03-* seeds-CUNI.txt seeds-oneshot.cz > seeds.txt<br>
<br>
$ -u -nique sa dela vo vimu :  sort u a idealne skontrolovat data, veci co zacinaju na http, a rozne slashe na zaciatku upravit, a poznamenta kuratorkam
<br></pre>

<h3>3. Ocheckovat commit na minulom mesiaci</h3>

<pre>$ git status</pre>

<h3>4. Nastavení Crawlerbeans:</h3>

 # Values changing with each crawl
 <pre>
-metadata.jobName=Serials 2017-02-1M_2M_CUNI_ArchiveIt<br>
-metadata.description=Pravidelná sklizeň semínek s měsíční frekvencí, pravidelná sklizeň semínek s dvojměsíční frekvencí, sklizeň webů Karlovy univerzity, archivace semínek s nízkou frekvencí přidaných za minulý
měsíc.<br>
-warcWriter.prefix=Serials-2017-02-1M_2M_CUNI_ArchiveIt<br>
-warcWriter.storePaths=/mnt/archives/archive14/2017/serials/Serials-2017-02-1M_2M_CUNI_ArchiveIt<br>
+metadata.jobName=Serials 2017-03-1M_6M_NoContract_CUNI_ArchiveIt<br>
+metadata.description=Pravidelná sklizeň semínek s měsíční frekvencí, pravidelná sklizeň semínek s půlroční frekvencí, sklizeň semínek bez smlouvy, sklizeň webů Karlovy univerzity, archivace semínek s nízkou frek
vencí přidaných za minulý měsíc.<br>
+warcWriter.prefix=Serials-2017-03-1M_6M_NoContract_CUNI_ArchiveIt<br>
+warcWriter.storePaths=/mnt/archives/archive14/2017/serials/Serials-2017-03-1M_6M_NoContract_CUNI_ArchiveIt<br>
</pre>
<h3>5. Zmeny v CrawlerBeans.xml</h3>
<pre>
$ git add crawler-beans.cxml seeds.txt 2017/seeds-2017-02-*<br>
<br>
skontrolovat co je vybrane:<br>
<br>
$ git status<br>
<br>
a pak to tam odpalkovat s prislusnym oznacenim DOBEHLEJ sklizne<br>
<br>
$ git commit -m 'Serials 2017 02 1M_6M_NoContract_CUNI_ArchiveIt'<br>
<br>
skontrolovat o kolko komitov sme dozadu, overit ci je vsetko spravne, lebo nebezpecie nekonzistence
<br>
$ git push
</pre>

</h2>4. Pustiť sklizeň</h2>
<ul><li>Pustit si lokál GUI instance Heritrixu na https://10.10.0.200:7778/ .</li>
<li>Ocheckovat sklizeň a zrušiť ju ak ešte si frčí: PAUSE, TEARDOWN.</li> </ul>

<pre>Tip: ak si to frčí beztak ďalej, nezostáva, než zhodiť Heritrix komplet. Skontrolovať ale najprv, či idealne warcy su uzavrete - žiadan status open, invalid apod.<br><br>
  Následne znova nahodenie: zájsť do koreňa všetkých heritrixov a pustiť si skripta: ./start3.sh</pre>


Kym dobehne, ocheckovat git, ci seminka boli z dobehnutej sklizne comitnute, potom git staus - co sa v lokalnom zmenili.
odpalit ist cd 2017, aby bola priama cesta k seeds a pak pridat vybrane subory.
