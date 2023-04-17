# Estonian National Bibliography data processing overview

The repository includes the Estonian National Bibliography in a somewhat cleaned and processed form. Raw marc files are available here: http://data.digar.ee/ under Eesti Rahvusbibliograafia -> Eestikeelne Raamat; Muukeelne Raamat.

Admittedly, when doing this, I did not know of a better workflow - e.g. to go from marc to somewhat tidy tables in R, and many of the fields have been converted using brute force methods.

For harmonization, the main information are on authors, publishers, publishing locations. Data for that is in autor_id (main author) + teised_autorid (other authors), they are added together in the .Rmd file and split into coauthors. These author names are linked to a metadata biographic registry at the library (here included just the mapping in person_ids.tsv), whole dataset in Isikud in "Eesti rahvusbibliograafia isikute ja kollektiivide andmed" in data.digar.ee.

I previously did some simple harmonization, limiting myself to only 1800-1940 on publishers, locations, and genres. These names are included. I also linked the authors via VIAF to Wikidata and DNB (German National Bibliography) data and manually to an Estonian local biographic dataset. Some of these datasets also have info on known pseudonyms. This process disambiguates some of the names, but is not terribly efficient, and is implemented quite messily at this point.

So for input into harmonization: the functions harmonize_places(), harmonize_publisher(), and the person_ids.tsv can be files to work with that give some initial results. I'm very sure there are much more cleaner ways to harmonize more of the names, and all things I did, I limited to data from 1800-1940 only - so beyond that, there's nothing done for even the top names.

For manual harmonization, I looked through the top publisher lists, and found places where the names were similar - using alphabetic sequence, and maybe for 1,000 names - though unfortunately I did not document it well and/or I can't find the notes on this. So it gives some coverage of the top, and may be something to validate against, but probably only works on this specific part of the dataset.



## Data files

1. Simple convert to tsv from marc files (long format)
- ERB_eestikeelne_raamat_24_05_2019.tsv
- ERB_muukeelne_raamat_24_05_2019.tsv
2. Selected fields from long format to wide format
- ERB_muuk_works_v_24_05_2019.tsv
- ERB_works_v_24_05_2019.tsv
3. Authorname to personid mappings from NatLib person metadata
- person_ids.tsv

4. Additional data via VIAF. Includes some more pseudonym information, but likely not relevant for bibliographic data.
- linked_data_all.tsv VIAF links between ENB, Wikidata, DNB
- dnb_geo_v4.ttl.tsv - DNB geoinfo long
- total_dnb_relevant.tsv - linked names from DNB
- autorid_ids2.tsv - ISIK local biographic database
- ISIK_basic_sorted_conv_manual_fixed_safecopy_changed.csv - ISIK data
- isik_manual_linking3.csv - ISIK pseudonym lists
- wdata_persons_all_mininfo_order_dbirth.tsv - Wikidata person info
- geo/ - geonames data files

## Data fields in bibliography wide file

1.	RecordNumber - Record id from marc file
2.	c - date field
3.	aeg - date extracted from date field
4.	koht - place of publication. initially raw. harmonize_place replaces this field and creates koht_orig to contain the original data
32.	koht_orig - place of publication original
5.	kirjastus - publishing house. initially raw. harmonize_publisher simply replaces the value here.
6.	title - main title
7.	subtitle - subtitle
8.	autor - an erronous field
9.	autor_id - main author field from marc
10.	autor_name - just the name from main author field
11.	autor_dates - just the dates from main author field
12.	teised_autorid - other authors field from marc
13.	RRid - main permanent id for publication
14.	meta - field for metainformation from marc
15.	meta_eks - eks = eksemplar = number of copies
16.	meta_kop - unsure. related to number of copies or possibly price.
17.	fraktuur - fraktur extracted from meta (not commonly marked)
18.	antiikva - antiqua extracted from meta (not commonly marked)
19.	print - location printed in
20.	keel - language/genre marking from marc; seemed to be mixed
21.	genres - genre marking from marc
22.	links - link to online edition
23.	litsents - license information
24.	aeg2 - better converted timestamp
25.	comptitle - title + subtitle as full composite title
26.	meta_eks2 - number of copies based on meta_eks and meta kop
27.	set - estonian data is kept separate from other languages, so "eesti" or "muukeelne"
28.	keeled2 - usually not used
29.	keeled3 - usually not used
30.	decade - usually not used
31.	langauto - language automatically detected from title
33.	kirjastus_first - first year a publisher is shown

## Data harmonization

- authors: Bibliography has authornames, author_ids are kept in a separate register. Mappings given in person_ids.
- publishers: exact matches and a few partial matches based on checking top publishers and alphabetically similar names.
- publishing locations: manually checked the top locations and alphabetically similar names. and then somewhat fuzzy mapping: 1) order names alphabetically, if sequential names have just one character difference, then map them together (e.g. Tartu, Tartus; Jõgeva, Jõgeval). Repeat this 3 times.
- genres: partial match on the genre names to aggregate types
- birthplaces of authors - a messy path with some manual correctionss
