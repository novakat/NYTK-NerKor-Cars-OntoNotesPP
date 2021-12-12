
# NYTK-NerKor+Cars-OntoNotes++

This corpus was derived from [NYTK-NerKor](https://github.com/nytud/NYTK-NerKor), a Hungarian gold standard named entity annotated corpus containing about 1 million tokens. 
It includes a small addition of 12k tokens of text (individual sentences) concerning motor vehicles (cars, buses, motorcycles) from the news archive of [hvg.hu](hvg.hu).
While the annotation in NYTK-NerKor followed the CoNLL2002 labelling standard with just four NE categories (`PER`, `LOC`, `MISC`, `ORG`), this version of the corpus features over 30 entity types, including all entity types used in the [OntoNotes 5.0] English NER annotation.
The new annotation elaborates on subtypes of the `LOC` and `MISC` entity types, and includes annotation for non-names like times and dates, quantities, languages and nationalities or religious or political groups.
The tags are in the `IOB2` format: a `B-` prefix denotes the first item of a NE phrase and an `I-` prefix any non-initial word. Non-entities are marked by an `O` label. 

The new annotation was created by applying zero-shot cross-lingual transfer using three models ([Flair/ner-english-ontonotes-large](https://huggingface.co/flair/ner-english-ontonotes-large), [DeepPavlov/ner_ontonotes_bert_mult](http://docs.deeppavlov.ai/en/master/features/models/ner.html) and [NameTag2 trained on CNEC2](https://ufal.mff.cuni.cz/nametag/2)) the outputs of which were automatically merged with the original annotation and then corrected using regex-based automatic correction patterns and checked manually. Manual correction also concerned certain types of  orthographic/tokenization/segmentation errors.

Note, however, that manual checking of the corpus was not exhaustive, thus annotation in the current version needs further curation to be considered gold standard. Nevertheless, we release this version of the corpus hoping that it proves to be a useful resource for the NLP community.

## Tags derived from the OntoNotes 5.0 annotation

Names are annotated according to the following set of types:
| | | 
|---|---------|
|`PER` | = PERSON People, including fictional |
|`FAC` | = FACILITY Buildings, airports, highways, bridges, etc. |
|`ORG` | = ORGANIZATION Companies, agencies, institutions, etc. |
|`GPE` | Geopolitical entites: countries, cities, states |
|`LOC` | = LOCATION Non-GPE locations, mountain ranges, bodies of water |
|`PROD` | = PRODUCT Vehicles, weapons, foods, etc. (Not services) |
|`EVENT` | Named hurricanes, battles, wars, sports events, etc. |
|`WORK_OF_ART` | Titles of books, songs, etc. |
|`LAW` | Named documents made into laws  |

The following are also annotated in a style similar to names:
| | | 
|---|---------|
| `NORP` | Nationalities or religious or political groups |
| `LANGUAGE` | Any named language |
| `DATE` | Absolute or relative dates or periods |
| `TIME` | Times smaller than a day |
| `PERCENT` | Percentage (including "%") |
| `MONEY` | Monetary values, including unit |
| `QUANTITY` | Measurements, as of weight or distance |
| `ORDINAL` | "first", "second" |
| `CARDINAL` | Numerals that do not fall under another type |

## Additional tags
Further subtypes of names of type `MISC`:
| | |
|-|-|
|`AWARD`| Awards and prizes |
| `CAR` | Cars and trucks |
|`MEDIA`| Media outlets, TV channels, news portals|
|`SMEDIA`| Social media platforms|
|`ORG-GPE` | Geopolitical entities as agents: they would (justly) simply be marked as GPE in the OntoNotes annotation scheme|
|`PROJ`| Projects and initiatives |
|`MISC`| Unresolved subtypes of MISC entities |
|`MISC-ORG`| Organization-like unresolved subtypes of MISC entities |
|`MISC-PER`| Metonymic use of person's names |

Further non-name entities:
| | |
|-|-|
|`DUR` |Time duration
|`ID`| identifier
 
## License and usage

The corpus is available under the license CC-BY-SA 4.0 following the license of the original NYTK-NerKor corpus. If you use this corpus, please cite the papers below. 

## Data

Names of the corpus files reflect the names of corresponding files in the NerKor dataset, however, names of subfolders in NerKor (including reference to the train/dev/test split) are part of the file names in this version. 

See further details about the corpus and the annotation guidelines of the original NerKor dataset in the [NYTK-NerKor](https://github.com/nytud/NYTK-NerKor) repo.

## Data format

The format of data files are [CoNLL-U Plus](https://universaldependencies.org/ext-format.html) with the standard `.conllup` file extension. The first line in each file is: `# global.columns = FORM ONPP:NER`, where:

`FORM`: the token itself;
`ONPP:NER`: OntoNotes++ NE annotation.

Morphological annotation in NerKor was discarded in this version.

## Citation

If you use this resource or any part of its documentation, please cite:

Novák Attila, Novák Borbála. NerKor 1.41e. In: XVIII. Magyar Számítógépes Nyelvészeti Konferencia.

```
@inproceedings{NerKorCarsONPP,
  author    = {Nov{\'a}k Attila and
               Nov{\'a}k Borb{\'a}la,
  title     = {{NerKor} 1.41e},
  booktitle = {XVIII. Magyar Számítógépes Nyelvészeti Konferencia},
  year      = {2022},
}
```

and the publication presenting the original corpus:

Simon, Eszter; Vadász, Noémi. (2021) Introducing NYTK-NerKor, A Gold Standard Hungarian Named Entity Annotated Corpus. In: Ekštein K., Pártl F., Konopík M. (eds) Text, Speech, and Dialogue. TSD 2021. Lecture Notes in Computer Science, vol 12848. Springer, Cham. https://doi.org/10.1007/978-3-030-83527-9_19


```
@inproceedings{DBLP:conf/tsd/SimonV21,
  author    = {Eszter Simon and
               No{\'{e}}mi Vad{\'{a}}sz},
  editor    = {Kamil Ekstein and
               Frantisek P{\'{a}}rtl and
               Miloslav Konop{\'{\i}}k},
  title     = {Introducing {NYTK-NerKor}, A Gold Standard {Hungarian} Named Entity
               Annotated Corpus},
  booktitle = {Text, Speech, and Dialogue - 24th International Conference, {TSD}
               2021, Olomouc, Czech Republic, September 6-9, 2021, Proceedings},
  series    = {Lecture Notes in Computer Science},
  volume    = {12848},
  pages     = {222--234},
  publisher = {Springer},
  year      = {2021},
  doi       = {10.1007/978-3-030-83527-9\_19},
}
```
