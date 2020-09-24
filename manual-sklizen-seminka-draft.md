# Webarchiv.[[cz](manual-sklizen-seminka.md)] | Manuál pro MANUÁLNÍ přípravu semínek pro sklizně  

- [Webarchiv.[cz] | Manuál pro MANUÁLNÍ přípravu semínek pro sklizně](#webarchivcz--manuál-pro-manuální-přípravu-semínek-pro-sklizně)
  - [Požadavky](#požadavky)
    - [Technické](#technické)
    - [Přístupová oprávnění](#přístupová-oprávnění)
  - [Nejdříve si v terminálu nastavíme požadované proměné do svého prostředí](#nejdříve-si-v-terminálu-nastavíme-požadované-proměné-do-svého-prostředí)
    - [Proměná SEEDER_HOST](#proměná-seeder_host)
    - [Proměná SEEDER_USERNAME](#proměná-seeder_username)
    - [Proměná SEEDER_DATE](#proměná-seeder_date)
    - [Proměná SEEDER CREDENTIALS](#proměná-seeder-credentials)
      - [Nastavení proměné](#nastavení-proměné)
    - [Proměná SEEDER GET LIST](#proměná-seeder-get-list)
      - [Nastavení proměné GET_LIST](#nastavení-proměné-get_list)
      - [Akceptované dotazy](#akceptované-dotazy)
    - [Proměná SEEDER GET URLS](#proměná-seeder-get-urls)
      - [Nastavení proměné GET URLS](#nastavení-proměné-get-urls)
      - [Akceptované hodnoty](#akceptované-hodnoty)
    - [Proměná SEEDER GET HARVEST](#proměná-seeder-get-harvest)
      - [Nastavení proměné GET_HARVEST](#nastavení-proměné-get_harvest)
      - [Akceptované dotazy GET_LIST](#akceptované-dotazy-get_list)
  - [Seeder API - harvests](#seeder-api---harvests)
    - [Semínka ke sklizní dle data a HarvestID](#semínka-ke-sklizní-dle-data-a-harvestid)
    - [Semínka ke sklizní dle data a frekvence jejich sklízení](#semínka-ke-sklizní-dle-data-a-frekvence-jejich-sklízení)
  - [Následně pak již jenom využívat přirozeného prostřédí terminálu](#následně-pak-již-jenom-využívat-přirozeného-prostřédí-terminálu)
  - [Získání semínek připravených ke sklizni](#získání-semínek-připravených-ke-sklizni)
    - [Získaní seznamu připravených sklizní](#získaní-seznamu-připravených-sklizní)
    - [Stažení ze seznamu semínek připravených ke sklizni](#stažení-ze-seznamu-semínek-připravených-ke-sklizni)
  - [Zpracovaní semínek](#zpracovaní-semínek)
    - [Sloučení semínek](#sloučení-semínek)
      - [SORT -unique](#sort--unique)
  - [Reference](#reference)
  - [Není zapracováno](#není-zapracováno)

## Požadavky

### Technické

| Software | Verze |
|----------|-------|
| terminal |       |
| git      |       |
| curl     |       |

### Přístupová oprávnění

Je třeba mít vytvořený přístupový token do aplikace Seeder.  

## Nejdříve si v terminálu nastavíme požadované proměné do svého prostředí

### Proměná SEEDER_HOST

url pro obsah proměné je třeba získat po dohohodě

| Operační systém | terminal   | Nastavení promměné | Obsah proměnné | Nastavení                                |
|-----------------|------------|--------------------|----------------|------------------------------------------|
| Linux           | bash       | SEEDER_HOST        | url_seeder_api |                                          |
| Microsoft       | cmd        | SEEDER_HOST        | url_seeder_api | set SEEDER_HOST=<https://app.webarchiv.cz> |
| Microsoft       | powershell | SEEDER_HOST        | url_seeder_api |                                          |
| Apple           |            | SEEDER_HOST        | url_seeder_api |                                          |

### Proměná SEEDER_USERNAME

Pptřebná práva k provoznímu prostředí

| Operační systém | terminal   | Nastavení promměné | Obsah proměnné | Nastavení                |
|-----------------|------------|--------------------|----------------|--------------------------|
| Linux           | bash       | SEEDER_USERNAME    | username       |                          |
| Microsoft       | cmd        | SEEDER_USERNAME    | username       | set SEEDER_USERNAME=user |
| Microsoft       | powershell | SEEDER_USERNAME    | username       |                          |
| Apple           |            | SEEDER_USERNAME    | username       |                          |

### Proměná SEEDER_DATE

pro datum

| Operační systém | terminal   | Nastavení promměné | Obsah proměnné | Nastavení                      |
|-----------------|------------|--------------------|----------------|--------------------------------|
| Linux           | bash       | SEEDER_DATE        | dateType.day   |                                |
| Microsoft       | cmd        | SEEDER_DATE        | dateType.day   | set SEEDER_DATE=[dateType.day] |
| Microsoft       | powershell | SEEDER_DATE        | dateType.day   |                                |
| Apple           |            | SEEDER_DATE        | dateType.day   |                                |

Nejdříve si v terminálu vytvoříme několik "funkci" pomocí variabilního prostředí

### Proměná SEEDER CREDENTIALS

Výsledná "funkce" by měla zaručit pohodlný dotaz na kurátorský tool které sklizně obsahují semínka.

POST  <SEEDER_HOST>/API/ - U USERNAME /

#### Nastavení proměné

| Operační systém | terminal   | Nastavení promměné     | Obsah proměnné | Nastavení                                                       |
|-----------------|------------|------------------------|----------------|-----------------------------------------------------------------|
| Linux           | bash       | SEEDER_SET_CREDENTIALS | dateType.day   |                                                                 |
| Microsoft       | cmd        | SEEDER_GET_LIST        | dateType.day   | set SEEDER_GET_LIST=%SEEDER_HOST%/seeder/harvests/%SEEDER_DATE% |
| Microsoft       | powershell | SEEDER_GET_SEEDS       | dateType.day   |                                                                 |
| Apple           |            | SEEDER_GET_SEEDS       | dateType.day   |                                                                 |

### Proměná SEEDER GET LIST

Výsledná "funkce" by měla zaručit pohodlný dotaz na kurátorský tool které sklizně obsahují semínka.

GET  <SEEDER_HOST>/harvests/<SEEDER_DATE>/

#### Nastavení proměné GET_LIST

| Operační systém | terminal   | Nastavení promměné | Obsah proměnné | Nastavení                                                       |
|-----------------|------------|--------------------|----------------|-----------------------------------------------------------------|
| Linux           | bash       | SEEDER_GET_HARVEST | dateType.day   |                                                                 |
| Microsoft       | cmd        | SEEDER_GET_LIST    | dateType.day   | set SEEDER_GET_LIST=%SEEDER_HOST%/seeder/harvests/%SEEDER_DATE% |
| Microsoft       | powershell | SEEDER_GET_SEEDS   | dateType.day   |                                                                 |
| Apple           |            | SEEDER_GET_SEEDS   | dateType.day   |                                                                 |

#### Akceptované dotazy

harvest
shortcut_urls

```
SEEDER_GET_LIST/harvest
SEEDER_GET_LIST/shortcut_urls
```

### Proměná SEEDER GET URLS

proměná by ve výsledku měla být používana jako funkce které výsledkem je pohodlný dotaz na wekurátorský tool a stáhnout semínka.

GET  <SEEDER_HOST>/harvests/<SEEDER_DATE>/<fileType.seeds>/-/[<harvestType>]/./<fileType.seed.fileformat>>

#### Nastavení proměné GET URLS

| Operační systém | terminal   | Nastavení promměné | Obsah proměnné | Nastavení                                            |
|-----------------|------------|--------------------|----------------|------------------------------------------------------|
| Linux           | bash       | SEEDER_GET_URLS    | dateType.day   |                                                      |
| Microsoft       | cmd        | SEEDER_GET_URLS    | dateType.day   | set SEEDER_API_DATE=SEEDER_HOST/harvests/SEEDER_DATE |
| Microsoft       | powershell | SEEDER_GET_URLS    | dateType.day   |                                                      |
| Apple           |            | SEEDER_GET_URLS    | dateType.day   |                                                      |

#### Akceptované hodnoty

```
SEEDER_GET_LIST/harvest
SEEDER_GET_LIST/shortcut_urls
```

### Proměná SEEDER GET HARVEST

proměná by ve výsledku měla být zkratkou pro pohodlný dotaz pomocí cURL na wekurátorský tool a umět stáhnout semínka klizně.

#### Nastavení proměné GET_HARVEST

| Operační systém | terminal   | Nastavení promměné | Obsah proměnné | Nastavení                                    |
|-----------------|------------|--------------------|----------------|----------------------------------------------|
| Linux           | bash       | SEEDER_GET_HARVEST |                |                                              |
| Microsoft       | cmd        | SEEDER_GET_HARVEST |                | set SEEDER_GET_HARVEST=SEEDER_HOST/harvests/ |
| Microsoft       | powershell | SEEDER_GET_HARVEST |                |                                              |
| Apple           |            | SEEDER_GET_HARVEST |                |                                              |

#### Akceptované dotazy GET_LIST

```
SEEDER_GET_LIST/harvest
SEEDER_GET_LIST/shortcut_urls
```

## Seeder API - harvests

Seeder poskytuje po ověření na svém api generované seznamy semínínek.
K seznamům zdrojů lze přistupovat ze dvou pohledů.

Níže uvedené jsou adresy URL pro získávání semínek pro konkrétní sklizeňí,
nebo výpis dostupných URL dle frekvence zařazení pro konkrétní den.

Z pohledu sklizně jako zastřešující nebo jako k seznamu semínek dle frekvence jejich sklízení:

### Semínka ke sklizní dle data a HarvestID

|                                          |                       |
|------------------------------------------|-----------------------|
| /seeder/harvests/[dateType.day]/harvests | Seznam URL pro datum  |
| /seeder/harvests/1234/urls               | All seeds for Harvest |

### Semínka ke sklizní dle data a frekvence jejich sklízení

|                                                                    |                                    |
|--------------------------------------------------------------------|------------------------------------|
| /seeder/harvests/[dateType.day]/shortcut_urls                      | Seznam URL pro datum               |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-V1.txt        | Jednou za rok (ročně)              |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-V2.txt        | Dvakrát za rok (půlročně)          |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-V4.txt        | Čtyřikrát za rok (čtvrletně)       |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-V6.txt        | Šestkrát za rok (každé dva měsíce) |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-V12.txt       | Dvanáctkrát za rok (měsíčně)       |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-V52.txt       | Týdně                              |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-V365.txt      | Denně                              |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-OneShot.txt   | Jednorázově                        |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-ArchiveIt.txt | ArchiveIt                          |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-VNC.txt       | VNC: Výběrové custom               |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-Tests.txt     | Tests                              |
| /seeder/harvests/[dateType.day]/seeds-[dateType.day]-Totals.txt    | Totals: Všechna semínka            |

## Následně pak již jenom využívat přirozeného prostřédí terminálu

## Získání semínek připravených ke sklizni

( kurátorksky označená sklizeň s příznakem  ( zamražení semínek v čase ) )

### Získaní seznamu připravených sklizní

```bash
curl SEEDER_GET_LIST/harvests > harvest.txt
```

```
curl SEEDER_GET_LIST/urls_shortcut > urls_shortcut.txt
```

### Stažení ze seznamu semínek připravených ke sklizni

```
curl SEEDER_GET_SEEDS/harvests/   < harvest-[dateType.day].txt
curl SEEDER_GET_SEEDS/harvests/   < urls_shortcut-[dateType.day].txt  
```

## Zpracovaní semínek

### Sloučení semínek

Sloučení semínek se děje pomocí nástrojů příkazové řádky a pomocí programů poskytovaných operačním systémem.

Každý operační systém má svá specifika, možnosti a omezení. Proto pro práci s textem doporučuji využívat unixové nástroje.

Postupně budeme použití pro terminál doplňovat, jinak veškeré ukázky probíhaji v terminálu bash.

#### SORT -unique

| Operační systém | terminal   | Příkaz | Parametry | Run                     |                         |                 |
|-----------------|------------|--------|-----------|-------------------------|-------------------------|-----------------|
| Linux           | bash       | sort   |           |                         |                         |                 |
| Microsoft       | cmd        | sort   |           | ```type file.txt        | sort /unique```         |                 |
| microsoft       | cmd        | sort   |           | ```type file.txt        | powershell -nop "$input | sort -unique``` |
| Microsoft       | powershell | sort   |           | ```Get-Content file.txt | Sort-Object -unique```  |                 |
| Apple           |            | sort   |           |                         |                         |                 |

## Reference

[Seeder API](https://seeder.readthedocs.io/en/latest/api.html)  
[Metadatová specifikace projektu grainery/harvest](https://github.com/WebarchivCZ/grainery/wiki/Harvest)

## Není zapracováno

- [ ] Doplnění jak nákládat s konfiguračním souborem crawler-config
- [ ] Doplnění proměnných pro práci s crawlerem
- [ ] Doplnění jak pracovat přes API s crawlerem
