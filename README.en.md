# Configuration history of Webarchiv.cz crawls

We use this repository to track changes in heritrix configuration.
We also track seeds we used for harvest.

- [Configuration history of Webarchiv.cz crawls](#configuration-history-of-webarchivcz-crawls)
  - [Files](#files)
    - [File with list of seeds](#file-with-list-of-seeds)
    - [File with configuration of crawler](#file-with-configuration-of-crawler)
  - [Directories](#directories)
  - [Rules for naming records](#rules-for-naming-records)
    - [fileType](#filetype)
    - [directoryType](#directorytype)
    - [dateType](#datetype)
    - [harvestName](#harvestname)
    - [harvestType](#harvesttype)
    - [harvestFreq](#harvestfreq)
  - [Reference](#reference)
  - [Software and software libraries](#software-and-software-libraries)
  - [These are not really implemented](#these-are-not-really-implemented)
  - [License](#license)

-------

Usual files, directories and commits looks like this:

This is what files, directories, and revisions look like:

## Files

The file naming convention is derived from the record naming rules.  
Each file is only a combination of the data type and its value from the metadata specification.

### File with list of seeds

***[[fileType.prefix](#filetype)]-[[dateType.month](#datetype)]-[[harvestType.tag](#harvesttype)]-[[harvestFreq](#harvestfreq)].[[fileType.fileformat](#filetype)]***

```
seeds-2019-06-S-1M_2M_OneShot_ArchiveIt.txt
```

### File with configuration of crawler

***[[fileType.prefix](#filetype)].[[fileType.fileformat](#filetype)]***  
***[[fileType.prefix](#filetype)]-[[harvestType.tag](#harvesttype)]-[[dateType.year](#datetype)].[[fileType.fileformat](#filetype)]***

```
crawler-beans.cxml
crawler-beans-S-2020.cxml
```

## Directories

The directory naming convention is derived from record naming rules.  
Each directory is only a combination of the harvestType and directoryType.

***[[harvestType](#harvesttype)]-[[directoryType.suffix](#directorytype)]***

```
Monthly-crawls/
Topic-crawls/
Shared-config/
```

## Rules for naming records

### fileType

| prefix        | mimetype   | fileformat | description                     |
|---------------|------------|------------|---------------------------------|
| seeds         | text/plain | txt        | file with list of seeds         |
| crawler-beans | text/xml   | cxml       | file with crawler configuration |

### directoryType

| directoryType | suffix   | description                                                                 |
|---------------|----------|-----------------------------------------------------------------------------|
| config        | -conf    | directory with shared configuration for all harvests as blacklist, etc.     |
| crawls        | -crawls  | directory with configuration of crawler and seeds for specifics of harvests |
| reports       | -reports | directory with logs and reports about harvest                               |

### dateType

Definition of recording date and time items.

| dateType | format            |
|----------|-------------------|
| year     | yyyy              |
| month    | yyyy-MM           |
| day      | yyyy-MM-DD        |
| time     | yyyy-MM-DD@hhmmss |

### harvestName

See the metadata specification for more information about [harvestName #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04harvestnamefull)

### harvestType

This is the curatorial definition of the harvest from which the list of seeds for harvest is derived.  
See the metadata specification for more information about [harvestType #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04-harvesttype)

| harvestType | tag | description                                                                                        |
|-------------|-----|----------------------------------------------------------------------------------------------------|
| Serials     | S   | Selective repeating harvest (combination of selected seeds with different annual frequency)        |
| Topics      | T   | Thematic selective harvest. These harvest usually repeats few times.                               |
| Totals      |     | Comprehensive harvest of national domain .cz. We do not store domain crawl configuration here.[^1] |
| Tests       |     | Harvest feasibility tests                                                                          |
| Requests    |     | Requested harvest in cooperation with another institution                                          |
| Continuous  |     | Continuous selective harvest                                                                       |

### harvestFreq

This is curated selection of seeds with defined frequency of repeating crawls:  
See the metadata specification for more information about [harvestFreq #v04](https://github.com/WebarchivCZ/grainery/wiki/Harvest#v04-harvestsuffixharvestfreq)

| harvestFreq | description                                                                                           |
|-------------|-------------------------------------------------------------------------------------------------------|
| 1M          | means selection of seeds to be crawled every month                                                    |
| 2M          | means selection of seeds to be crawled every other month                                              |
| 6M          | means selection of seeds to be crawled twice a year                                                   |
| 12M         | means selection of seeds to be crawled once a year                                                    |
| Archive_IT  | are seeds acquired last month with low frequency as once or twice a year -> to be harvested asap.     |
| OneShot     | are seeds without contracts - which we would like to have in archive, but are not publicly available. |

## Reference

[About Webarchiv Harvests](https://www.webarchiv.cz/en/about)  
[Comprehensive Harvests](https://www.webarchiv.cz/en/harvests)

## Software and software libraries

| Software | Version | Language | Official source of code                        | Utilization      |
|----------|---------|----------|------------------------------------------------|------------------|
| Heritix  | 3.4.0   | Java     | <https://github.com/internetarchive/heritrix3> | crawler          |
| Seeder   |         | Python   | <https://github.com/WebarchivCZ/Seeder.git>    | web curator tool |

## These are not really implemented

- [ ] Definition and settings of the repository license
- [ ] Update crawler config files for all harvest type
- [ ] Create directory for reports of harvests
- [ ] Create abuse report for crawlers
  
## License

-------
[^1]: But we not be able to provide seeds.txt file as it is violates our agreement with seeds provider [NIC.CZ](https://nic.cz/en/)
