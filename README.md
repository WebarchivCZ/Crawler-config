Configuration history of Webarchiv.cz crawls.
==============

We use this repository to track changes in Heritrix configuration. We also track seeds we used for earch crawl. Usual commits looks like this "Type_of_Crawl Year Month Seed_type"  

#### Seed_type 
This is curated selection of seeds with defined frequency of repeating crawls:
1M means selection of seeds to be crawled every month  
2M means selection of seeds to be crawled every other month  
6M means selection of seeds to be crawled twice a year  
12M means selection of seeds to be crawled once a year   
Archive_IT are seeds acquired last month with low frequency as once or twice a year -> to be harvested asap.  
No_contract are seeds without contracts - which we would like to have in archive, but are not publicly available.

####Type_of_crawl
Serials - are repeating crawls every month. They are accompanied with Seed_type.
Topic - is special harvest. These harvest usually repeats few times. As Seed_type we increment Seed_type starting wih 00.. 
CZ - this is whole domain crawl of .cz. We do not keep whole domain crawl configuration here, but it will probably change. But we will not be able to provide seeds.txt file as it is violates our agreement with seeds provider nic.cz


####Shared-conf directory 
It contains text files shared among all crawls. There are sites we promised not crawl or do not want crawl for whatever reasons.  

####These are not really implemented
Article-crawls are usually single page + few hops away topical crawls.  
Continuous-crawls should be used to experiment with RSS based crawling etc. Not done yet.  
