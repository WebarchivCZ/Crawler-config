# Webarchiv.[[en](README.en.md)] | Konfigurační historie sklizní

Toto úložiště používáme ke sledování změn konfigurací našich crawlerů.  
Také zde verzujeme seznamy semínek, která jsme použili pro konkrétní sklizeň.

- [Webarchiv.[en] | Konfigurační historie sklizní](#webarchiven--konfigurační-historie-sklizní)
  - [Soubory](#soubory)
    - [Sada semínek pro sklizně](#sada-semínek-pro-sklizně)
    - [Konfigurační soubor crawleru](#konfigurační-soubor-crawleru)
  - [Adresáře](#adresáře)
  - [Specifikované místní metadatové typy pouze pro potřeby repozitáře](#specifikované-místní-metadatové-typy-pouze-pro-potřeby-repozitáře)
    - [fileType](#filetype)
    - [directoryType](#directorytype)
    - [dateType](#datetype)
  - [Specifikované metadatové typy v grainery/harvest a grainery/data](#specifikované-metadatové-typy-v-graineryharvest-a-grainerydata)
    - [harvestName](#harvestname)
    - [harvestType](#harvesttype)
    - [harvestFreq](#harvestfreq)
  - [Reference](#reference)
  - [Software](#software)
  - [Není zapracováno](#není-zapracováno)
  - [Licence](#licence)

-------

## Soubory

Konvence pojmenování souborů vychazí z metadatové specifikace v projektu grainnery vztahujících se ke sklizním.  
Každý název souboru je tvořen pouze kombinací takto definovaných metadatových typů.

### Sada semínek pro sklizně

Aktuální varianta

***[[fileType.prefix](#filetype)]-[[dateType.month](#datetype)]-[[harvestType.tag](#harvesttype)]-[[harvestFreq](#harvestfreq)].[[fileType.fileformat](#filetype)]***

```

[seeds]-[2019-06]-[S]-[[1M]_[2M]_[OneShot]_[ArchiveIt]].[txt]

seeds-2019-06-S-1M_2M_OneShot_ArchiveIt.txt

```

### Konfigurační soubor crawleru

Aktuální varianta

***[[fileType.prefix](#filetype)].[[fileType.fileformat](#filetype)]***  
***[[fileType.prefix](#filetype)]-[[harvestType.tag](#harvesttype)]-[[dateType.year](#datetype)].[[fileType.fileformat](#filetype)]***

```
crawler-beans.cxml
crawler-beans-S-2020.cxml
```

## Adresáře

Konvence pojmenování adresáře vychazí z metadatové specifikace v projektu grainnery vztahujících se ke sklizním.  
Každý název adresáře je tvořen pouze kombinací takto definovaných metadatových typů.

[harvestType](#harvesttype) a [directoryType.suffix](#directorytype) ,  
spolu s datumovým typem jako volným typem [dateType](#datetype).

***[harvestType]-[directoryType.suffix]***

```
Monthly-crawls/
Topic-crawls/
Shared-config/
```

-------

## Specifikované místní metadatové typy pouze pro potřeby repozitáře

### fileType

| prefix        | mimetype   | fileformat | popis                                            |
|---------------|------------|------------|--------------------------------------------------|
| seeds         | text/plain | txt        | soubor se seznamem semínek vybraných pro sklizeň |
| crawler-beans | text/xml   | cxml       | soubor s konfigurací crawleru                    |

### directoryType

| suffix  | popis                                                                         |
|---------|-------------------------------------------------------------------------------|
| config  | adresář se sdílenou konfigurací pro všechny crawlery, blacklist, sheets, atp. |
| crawls  | adresář konfigurací crawleru a soubory se semínky specifický typ sklizně      |
| reports | adresář s logy a reporty o samotne sklizni                                    |

### dateType

Definice data a času.

| dateType | format            |
|----------|-------------------|
| year     | yyyy              |
| month    | yyyy-MM           |
| day      | yyyy-MM-DD        |
| time     | yyyy-MM-DD@hhmmss |

## Specifikované metadatové typy v grainery/harvest a grainery/data

Pokud není zdůrazněno jinak vše platí pro sekci grainery/harvest

### harvestName

Abstrahovaný název sklizně (abstrakce viz níže).  
Další informace o metadatovém typu [harvestName #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04harvestnamefull)

### harvestType

Jedná se o kurátorskou definici sklizně, ze které je odvozen seznam semínek odpovídajících zaměření sklizně.  
Další informace o metadatovém typu [harvestType #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04-harvesttype)

| harvestType | tag | popis                                                                                                                                    |
|-------------|-----|------------------------------------------------------------------------------------------------------------------------------------------|
| Serials     | S   | Každoměsíční sklizeň  (Kombinace výběrových sklizní s různou roční frekvencí )                                                           |
| Topics      | T   | Speciální tématická výběrová sklizeň. Tato sklizeň se může opakovat několikrát.                                                          |
| Totals      |     | Celoplošná sklizeň národní domény .cz ve spolupráci s [CZ.NIC](https://nic.cz/). Zde bohužel nenajdete semínka ani logy ze sklizní. [^1] |
| Tests       |     | Zkušební a testovací sklizně                                                                                                             |
| Requests    |     | Vyžádaná sklizeň ve spolupráci s jinou institucí                                                                                         |
| Continuous  |     | Průběžná speciální tématická výběrová sklizeň , sklízí se na denní bázi,                                                                 |

### harvestFreq

Jedná se o kurátorský výběr semínek s definovanou frekvencí opakováného sklízení:  
Další informace o metadatovém typu [harvestFreq #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04-harvestsuffixharvestfreq)

| harvestFreq | popis                                                                        |
|-------------|------------------------------------------------------------------------------|
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
[Metadatová specifikace projektu grainery/harvest](https://github.com/WebarchivCZ/grainery/wiki/Harvest)

## Software

| Software | Version | Language | Official source of code                        | Utilization      |
|----------|---------|----------|------------------------------------------------|------------------|
| Heritix  | 3.4.0   | Java     | <https://github.com/internetarchive/heritrix3> | crawler          |
| Seeder   |         | Python   | <https://github.com/WebarchivCZ/Seeder.git>    | web curator tool |

## Není zapracováno

- [ ] Vydefinování licence která bude pro repozitář použita
- [ ] Aktualizace a revize konfiguračních souborů crawleru pro všechny typy sklizní
- [ ] Oveření možností pro vytvoření adresáře pro logy a reporty ze sklizní
- [ ] Vytvořit muster formulař pro nahlášení "nevhodného chování" našeho crawleru
  
## Licence

-------
[^1]: Bylo by to v rozporu s naší dohodu o manipulaci s domenovým datasetem poskytovkáných sdružením [CZ.NIC](https://nic.cz/)  
      Proto nemůžeme zveřejnit seznam semínek pro celoplošné sklizně a samozřejmě ani výstupy logu.
