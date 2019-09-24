# Tidy Estonian National Bibliography (Eesti Rahvusbibliograafia, ERB) and Texts

Compiled by Peeter Tinits, 2018 (CC-BY-4.0).


This repository presents the code used to process the Estonian National Bibliography entries for a simple bibliographic overview and the linking of these entries with texts collected from DIGAR. 

This is part of greater effort to utilize the Estonian National Bibliography and texts for digital humanities studies, and documents the state at one point in time (Sep 2018). The code aims to ease access to the Bibliography data by transforming it to a [https://vita.had.co.nz/papers/tidy-data.pdf](tidy data) format, with useful information gathered and harmonized by publication.

Note that the scripts are not cleaned and documented thoroughly, as newer, more polished and expanded versions, are anticipated very soon. Ask me for up-to-date results.


## Use

### Preparation 

[http://data.digar.ee/#page6] presents two sets of data files. Download these and place them in appropriate directories.
- [http://data.digar.ee/processed_txt_tsv.zip] - data files of the National Bibliography in different formats. Place them in a folder called `data/`.
- [http://data.digar.ee/processed_pdf_tsv.zip] - the processed corpus files from Digar. Place them in a folder called `corpus/`

Alternatively simply alter the `.Rmd` files to match the locations of these files.

### Running

Simply use the .Rmd files to knit final documents, edit and reuse as needed.


--------------

The code is licensed under the [MIT](https://choosealicense.com/licenses/mit/) license, and is free to use for whatever purpose. If you find this dataset helpful, you can cite this as:

Tinits, Peeter. 2018. Tidy Estonian National Bibliography. (Unpublished.)

An updated and more polished version of the dataset will be completed in the near future. If you have any questions, suggestions, or issues running the code, contact me or post an issue in this repository.

Stable location now at [https://github.com/peeter-t2/tidy_ERB/]
