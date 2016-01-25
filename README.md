Configuration history of Webarchiv.cz crawls.
==============

We use this repository to track changes in Heritrix configuration. We also track seeds we used for earch crawl. Usual commits looks like this "Type_of_Crawl Year Month Type_of_seed"

Ie. Serial is usual monthly crawl, Type_of_seed: 1M means seeds crawled every month, 2M seeds crawled every other month, 6M seeds crawled twice a year, 12M is crawled once a year, Archive_IT are seeds acquired last month with low frequency as once or twice a year -> to be harvested asap, No_contract are seeds without contracts - which we would like to have in archive, but are not publicly available.

Type of crawl Topic means it is special harvest. These harvest usually repeats, so we start with 00

Shared-conf are text files shared among all crawls. There are sites we promised not crawl or do not want crawl for whatever reasons.  

We do not keep whole domain crawl configuration here, but it will probably change. But we will no be able provide seeds.txt file as it is violates our agreement with seeds provider nic.cz

These are not really implemented
Article-crawls are usually single page + few hops away topical crawls.  
Continuous-crawls should be used to experiment with RSS based crawling etc. Not done yet.  
