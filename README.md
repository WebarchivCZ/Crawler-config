# Konfigurační historie sklizní Webarchiv.cz

Toto úložiště používáme ke sledování změn konfigurací našich crawlerů.  
Také zde sledujeme seznamy semínek, která jsme použili pro konkrétní sklizeň.

- [Konfigurační historie sklizní Webarchiv.cz](#konfigurační-historie-sklizní-webarchivcz)
  - [Soubory](#soubory)
    - [Sada semínek pro sklizně](#sada-semínek-pro-sklizně)
    - [Konfigurační soubor crawleru](#konfigurační-soubor-crawleru)
  - [Adresáře](#adresáře)
  - [Zavedené metadatové definice ( Pravidla pro pojmenování záznamu )](#zavedené-metadatové-definice--pravidla-pro-pojmenování-záznamu-)
    - [fileType](#filetype)
    - [directoryType](#directorytype)
    - [dateType](#datetype)
    - [harvestName](#harvestname)
    - [harvestType](#harvesttype)
    - [harvestFreq](#harvestfreq)
  - [Reference](#reference)
  - [Software](#software)
  - [Není zapracováno](#není-zapracováno)
  - [Licence](#licence)

-------

## Soubory

Konvence pojmenování souborů je odvozena z pravidel pro pojmenování záznamů.  
Každý název souboru je pouze kombinací povolených metadatových definic, konkrétně

### Sada semínek pro sklizně

***[[fileType.prefix](#filetype)]-[[dateType.month](#datetype)]-[[harvestType.tag](#harvesttype)]-[[harvestFreq](#harvestfreq)].[[fileType.fileformat](#filetype)]***

```

[seeds]-[2019-06]-[S]-[[1M]_[2M]_[OneShot]_[ArchiveIt]].[txt]

seeds-2019-06-S-1M_2M_OneShot_ArchiveIt.txt

```

### Konfigurační soubor crawleru

***[[fileType.prefix](#filetype)].[[fileType.fileformat](#filetype)]***  
***[[fileType.prefix](#filetype)]-[[harvestType.tag](#harvesttype)]-[[dateType.year](#datetype)].[[fileType.fileformat](#filetype)]***

```
crawler-beans.cxml
crawler-beans-S-2020.cxml
```

## Adresáře

Konvence pojmenování adresářů je odvozena od pravidel pro pojmenování záznamů.  
Každý název adresáře je pouze kombinací zavedených metadatových definic, konkrétně
[harvestType](#harvesttype) a [directoryType.suffix](#directorytype) ,  
spolu s datumovým typem [dateType](#datetype).

***[harvestType]-[directoryType.suffix]***

```
Monthly-crawls/
Topic-crawls/
Shared-config/
```

-------

## Zavedené metadatové definice ( Pravidla pro pojmenování záznamu )

### fileType

| prefix        | mimetype   | fileformat | popis                                            |
| ------------- | ---------- | ---------- | ------------------------------------------------ |
| seeds         | text/plain | txt        | soubor se seznamem semínek vybraných pro sklizeň |
| crawler-beans | text/xml   | cxml       | soubor s konfigurací crawleru                    |

### directoryType

| directoryType | suffix   | popis                                                                    |
| ------------- | -------- | ------------------------------------------------------------------------ |
| config        | -conf    | adresář se sdílenou konfigurací pro všechny crawlery, blacklist, atp.    |
| crawls        | -crawls  | adresář konfigurací crawleru a soubory se semínky specifický typ sklizně |
| reports       | -reports | adresář s logy a reporty o samotne sklizni                               |

### dateType

Definice data a času.

| dateType | format            |
| -------- | ----------------- |
| year     | yyyy              |
| month    | yyyy-MM           |
| day      | yyyy-MM-DD        |
| time     | yyyy-MM-DD@hhmmss |

### harvestName

Abstrahovaný název sklizně (abstrakce viz níže).  
Další informace o metadatovém typu [harvestName #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04harvestnamefull)

### harvestType

Jedná se o kurátorskou definici sklizně, ze které je odvozen seznam semenínek pro sklizeň.  
Další informace o metadatovém typu [harvestType #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04-harvesttype)

| harvestType | tag | popis                                                                                                                 |
| ----------- | --- | --------------------------------------------------------------------------------------------------------------------- |
| Serials     | S   | Každoměsíční sklizeň  (Kombinace výběrových sklizní s různou roční frekvencí )                                        |
| Topics      | T   | Speciální tématická výběrová sklizeň. Tato sklizeň se může opakovat několikrát.                                       |
| Totals      |     | Celoplošná sklizeň národní domény .cz ve spolupráci s cz.nic. Zde bohužel nenajdete semínka ani logy ze sklizní. [^1] |
| Tests       |     | Zkušební a testovací sklizně                                                                                          |
| Requests    |     | Vyžádaná sklizeň ve spolupráci s jinou institucí                                                                      |
| Continuous  |     | Průběžná speciální tématická výběrová sklizeň , sklízí se na denní bázi                                               |

### harvestFreq

Jedná se o kurátorský výběr semínek s definovanou frekvencí opakování sklízení:  
Další informace o metadatovém typu [harvestFreq #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04-harvestsuffixharvestfreq)

| harvestFreq | popis                                                                        |
| ----------- | ---------------------------------------------------------------------------- |
| 1M          | výběr semenínek, která se mají sklízet každý měsíc                           |
| 2M          | výběr semenínek, která se mají sklízet každý druhý měsíc                     |
| 6M          | výběr semenínek, která se mají sklízet každý půlrok                          |
| 12M         | výběr semenínek, která se mají sklízet jednou do roka                        |
| Archive_IT  | výběr nových semenínek, která se mají sklízet jednorázově                    |
| OneShot     | mimosystémově ručně přidaná další semínka, která se mají sklízet jednorázově |

## Reference

[Terminologie vztahující se k archivaci webu](https://www.webarchiv.cz/cs/terminologie)  
[Sklizně ve Webarchivu](https://www.webarchiv.cz/cs/o-webarchivu)  
[Celoplošné sklizně](https://www.webarchiv.cz/cs/celoplosne-sklizne)

## Software

| Software | Version | Language | Official source of code                        | Utilization      |
| -------- | ------- | -------- | ---------------------------------------------- | ---------------- |
| Heritix  | 3.4.0   | Java     | <https://github.com/internetarchive/heritrix3> | crawler          |
| Seeder   |         | Python   | <https://github.com/WebarchivCZ/Seeder.git>    | web curator tool |

## Není zapracováno

- [ ] Vydefinování licence která bude pro repozitář použita
- [ ] Aktualizace a revize konfiguračních souborů crawleru pro všechny typy sklizní
- [ ] Oveření možností pro vytvoření adresáře pro logy a reporty ze sklizní
- [ ] Vytvořit muster formulař pro nahlášení "nevhodného chování" našeho crawleru
  
## Licence

-------
[^1]: Nejsme schopni poskytnout seznam semínek pro celoplošné sklizně, protože by to bylo v rozporu s naší dohodu o poskytování se sdružením [cz.nic](https://nic.cz/)
