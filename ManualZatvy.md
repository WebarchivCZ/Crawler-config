<h1>Manuál žatvy</h1>

<h2>1. Check tabuľky</h2>
1. zistenie sklizní, ktoré treba odpáliť.
<br>
<h2>2. Vygenerovanie odpovedajúcich semienok</h2>
<h3>Generácia v Sidri</h3>
  <ul><li>1. Choď do "semínkovače"</li>
  <li>2. ctrl+a -označ všetko</li></ul>
<br>
<h2>3. Práca v terminály</h2>
<br>
<h3>1. nahoď si pracovné prostredie via</h3>
 <pre>screen -r </pre>
<br>
<h3>2. Utvorenie seeds-YYYY-MM-varianty-varianty.txt</h3>
Vleze sa do dovnútra k seeds, rozložené po rokoch. Vytvoriť vo formáte a názve <b> seeds-2017-02-a pripona sklizne</b>, V - je výberova, V1M .txt
Spolu so seederom sa vygenerujú príslušné semienka a zavedú sa do príslušných súborov.
<pre>
ŠPECIALITKA: Plus semienka pre <b>cuni</b> a <b>no contracts</b>>> http://intranet.webarchiv.cz/seeds/no_contracts.php, su s príponou <b>NoContracts (je to V-NC)</b>
Cuni su vo vonkajšom adresári a vedľa - crawler beans. Pevne zadefinovaný odkaz na nich v beans.cxml</pre>
<br>
<h3>3. Zlúčenie seedov</h3>
Deje sa cez zložku <b>jobs</b> v koreni všetkých heritrixov a via jobs do crawler config.
<br>
Semienka si treba vysortiť na unique a vizuálne ešte raz skontrolovať. Ak by bolo niečo divné,
poslať hneď podnet kurátorom, že čo ako to majú u seba.

<pre>
$ sort 2017/seeds-2017-03-* seeds-CUNI.txt seeds-oneshot.cz > seeds.txt<br>
<br>
$ -u -nique sa dela vo vimu :  sort u a idealne skontrolovat data, veci co zacinaju na http, a rozne slashe na zaciatku upravit, a poznamenta kuratorkam
<br></pre>
<br>
<h3>4. Ocheckovat commit na minulom mesiaci</h3>

<pre>$ git status</pre>
<br>
<h3>5. Nastavenie Crawlerbeans.cxml:</h3>

  Values changing with each crawl:

 <pre>
-metadata.jobName=Serials 2017-02-1M_2M_CUNI_ArchiveIt<br>
-metadata.description=Pravidelná sklizeň semínek s měsíční frekvencí, pravidelná sklizeň semínek s dvojměsíční frekvencí, sklizeň webů Karlovy univerzity, archivace semínek s nízkou frekvencí přidaných za minulý
měsíc.<br>
-warcWriter.prefix=Serials-2017-02-1M_2M_CUNI_ArchiveIt<br>
-warcWriter.storePaths=/mnt/archives/archive14/2017/serials/Serials<b>-</b>2017-02-1M_2M_CUNI_ArchiveIt<br>
+metadata.jobName=Serials[<b>medzera</b>]2017-03-1M_6M_NoContract_CUNI_ArchiveIt<br>
+metadata.description=Pravidelná sklizeň semínek s měsíční frekvencí, pravidelná sklizeň semínek s půlroční frekvencí, sklizeň semínek bez smlouvy, sklizeň webů Karlovy univerzity, archivace semínek s nízkou frek
vencí přidaných za minulý měsíc.<br>
+warcWriter.prefix=Serials<b>-</b>2017-03-1M_6M_NoContract_CUNI_ArchiveIt<br>
+warcWriter.storePaths=/mnt/archives/archive14/2017/serials/Serials<b>-</b>2017-03-1M_6M_NoContract_CUNI_ArchiveIt<br>
</pre> <br>
<h3>5. Kontrola zmien a push na github</h3>
<pre>
pridanie súborov do gitu:<br>
$ git add crawler-beans.cxml seeds.txt 2017/seeds-2017-02-*<br>
<br>
skontrolovať, čo je vybrané:<br>
$ git status
<br>
a pak to tam odpálkovať s príslušným označením DOBEHLEJ sklizne - tá súčasná [3] sa zálohuje až dobehne<br>
$ git commit -m 'Serials 2017[<b>medzera</b>]02[<b>medzera</b>]1M_6M_NoContract_CUNI_ArchiveIt'<br>
<br>
Skontrolovať o kolko komitov sme dozadu, overiť, či je všetko správne, lebo hrozí nebezpečie inkonzistencie<br>
$ git push
</pre>
<br>
<h2>4. Odštartovať novú sklizeň</h2>
<ul><li>Pustiť si lokál GUI inštanciu Heritrixu na https://10.10.0.200:7778/ .</li>
<li>Ocheckovat sklizeň a zrušiť ju ak ešte si frčí: PAUSE, TEARDOWN.</li>

<pre>Tip: ak si to frčí beztak ďalej, nezostáva, než zhodiť Heritrix komplet. Skontrolovať ale najprv, či idealne warcy su uzavrete - žiadan status open, invalid apod.<br><br>
  Následne znova nahodenie: zájsť do koreňa všetkých heritrixov a pustiť si skripta: ./start3.sh</pre>
</ul>
<ul>
<li>Kým dobehne, ocheckovat git, či semienka boli z dobehnutej sklizne commitnute, potom git staus - čo sa v lokálnom zmenili.
odpáliť cestou: cd 2017, aby bola priama cesta k seeds a pak pridať vybrané súbory.</li></ul>
