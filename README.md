# Tidy Estonian National Bibliography (ENB)

Compiled by Peeter Tinits, 2018-2023 (CC-BY-4.0).

## Overview

Tidy ENB adapts, harmonizes and enriches the data in Estonian National Bibliography to support analyses of its data. It has converted the marc21 file into a custom wide data file that includes the key information per publication with one book per row. The names of the publishers, the associated placenames have been harmonized and the genres of the publications have been standardized with a focus on the period 1800-1940. The information on authors associated with the publications has been enriched with the data available from the German National Bibliography and Wikidata via the VIAF links in the system.

## Data

The dataset relies on the data files provided by the National Library of Estonia 1) [Estonian books](https://data.digar.ee/erb/ERB_eestikeelne_raamat.zip), 2) [Books in other languages](https://data.digar.ee/erb/ERB_muukeelne_raamat.zip) as well as [Persons in ENB](https://data.digar.ee/erb/person.zip). They are complemented with information from VIAF, German National Bibliography, Wikidata and GEONAMES. 

## Processing

The processing scripts are given in the code folder. The processing also relies on the package [ENBtools](https://github.com/peeter-t2/harmonize_ENB) made to simplify data conversiotn and harmonization. It also relies on the [textcat](https://cran.r-project.org/web/packages/textcat/index.html) package to augment the language information already in the bibliography. 

## Geo-coding

Individuals have been associated with their location of birth based on the associated metadata in linked databases and placename information. In adding geotags, the data from Wikidata geolocations was preferred, followed by the locations given in DNB, followed by the placenames given in DNB that were combined with GEONAMES data. For publisher locations, geotags were added from GEONAMES data based on the harmonized locations. The automatic geo-tagging can be mistaken and the results are hoped to be improved in the future.

## Reports

Overviews of the key characteristics of the data are provided in the reports/ folder, code to reproduce them in the code/ folder.

--------------

The code is licensed under the [MIT](https://choosealicense.com/licenses/mit/) license, and is free to use for whatever purpose. 

The dataset has been developed for the publication: Tinits, Peeter 2023. Stratified Historical Corpus of Estonian 1800–1940. Eesti Rakenduslingvistika Ühingu Aastaraamat 19, 175-194. doi:10.5128/ERYa19.11 which you may cite if you find it helpful.

An updated and more polished version of the dataset will be completed in the near future. If you have any questions, suggestions, or issues running the code, contact me or post an issue in this repository.

Stable location now at [https://github.com/peeter-t2/tidy_ENB/](https://github.com/peeter-t2/tidy_ENB/).
