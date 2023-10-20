This project is an attempt to create an extension of the official CSW and NWL Scrabble lexicons to include words 16-21 letters long. For maximum consistency, it seeks to emulate the methodology that was used in the creation of those lists. Such a list would be suitable for Anagrams and other word games that require adjudication of long words.

### Introduction
Scrabble™ players blessed to have two excellent word lists for competitive play: the _Collins Official Scrabble Words_ (CSW) published by Collins and the _NASPA Word List_ (NWL), published by the North American Scrabble Players Association. Since the longest playable words in Scrabble are 15-letters long, neither of these organizations has attempted to create an official lexicon of words longer than 15 letters in length. Even in Super Scrabble™—which features a 21×21 board—words longer than 15 letters in length are exceedingly rare, so there is little incentive to do so.

There is at least one word game, however, in which such words are (if not altogether common) certainly not a rare occurrence—especially when expert players are involved: the game of [Anagrams](https://www.anagrams.site). If the validity of such a word needs to be adjudicated during gameplay, a standard dictionary must be consulted or an internet search performed. For a computerized Anagrams game this adjudication process must take place automatically. Accordingly, in order to avoid artificially setting the maximum word length at an arbitrarily low 15 letters, a list of longer words must be produced.

The starting point for this word list is the [_Word Judge for Clubs and Tournaments, 2nd Edition_](https://www.amazon.com/Word-Judge-Clubs-Tournaments-Superscrabble/dp/1643676407) (WJ2), compiled by Maliha Mendoza Mahmood. It contains a comprehensive list of words 2-21 letters long designed for the games of Scrabble and Super Scrabble. Although Maliha is sadly no longer with us to describe her methodology in detail, it appears that this work was intended to be as inclusive as possible—or nearly so. It contains all the words in the standard Scrabble source dictionaries as well as many other words from other sources, including dictionaries (including technical ones such as _Taber's Cyclopedic Medical Dictionary_), encyclopedias, and a variety of reference websites. A list of sources (not necessarily complete) can be found in the appendix to the book.

As impressive as this list is—weighing in at over 5 pounds in its print edition—it has a significant shortcoming: It makes no attempt to be consistent with CSW and NWL lexicons, which much more familiar to most Scrabble and Anagrams players. Moreover, it does not include annotations that can be used to separate entries according to their provenance. As a result, the 16 to 21 letter words it contains cannot simply be used as an extension of standard word lists without adding a host of unfamiliar shorter words as well. To simply separate out the long words (16-21 letters) and add them to the standard Scrabble dictionaries would create a lopsided lexicon with disproportionately many 16+ letter words, many of which are obscure and technical—and which have a distinct biochemical flavor due to the inclusion of names of molecular compounds.

To remedy this situation, some kind of return to the original source dictionaries is required. Fortunately it is no longer necessary to scour all of these dictionaries by hand. The Collins English Dictionary, the source dictionary for CSW, and many of the NWL source dictionaries can easily be found online. Also some of these dictionaries have APIs which allow them to be queried programmatically for a reasonable price in a short amount of time. This makes it possible to cross reference each of the 16-21 letter words in Mahmood's comprehensive list and determine if it would be valid according to the methodologies used to assemble the original Scrabble lexicons.

### The CSW 16-21 list
This procedure is not entirely without complications, however. The [Collins API](https://www.collinsdictionary.com/us/collins-api) only verifies the validity of inflections of "root words", i.e. words that have their own separate entry. Inflections of derived forms must be inferred manually. In practice, this means entering the word into the search field at [www.collinsdictionary.com](https://www.collinsdictionary.com) and checking the entry. For example, the Collins API lists APPREHENSIVENESS as a valid word since it is a derived form of APPREHENSIVE; however, the plural APPREHENSIVENESSES must be inferred and added manually. In some cases the correct plural form is not listed and is not easily inferred. For example, terms ending in -ITIS maybe pluralized as -ITISES, as -ITIDES, or as both. In such cases an alternative reference must be consulted. If the word is specifically listed as an uncountable noun then the plural form will generally not be inferred. If a derived form is a verb, then its inflections -ED, -ING, etc will often need to be added manually.

Although the Collins API cannot produce an exhaustive word list on its own, fortunately there are some tools that make the process of completing the word list less taxing: the website's search field has an autocomplete feature which brings up the occasional word that the WJ2 misses. Some of these may be recent additions to the dictionary and are considered as valid for the purpose of constructing the present word list unless they are derived forms of shorter (<15 letter) words that are not in CSW; the goal of the present project is to extend CSW—not to update or correct it. I am, am however, keeping a running tab of words that I find on the website but not in the CSW list.

Other words may belong to the so-called Collins Technical Corpus or be marked as belonging to some specialized word list such as a collection of terms found "in the pharmaceutical industry". These words have been marked as such and will be considered for inclusion or omission according to categories as a whole so as not to have to make decisions on a word-by-word basis—that being the proper function of lexicographers. Words in the Collins Technical Corpus appear in italics in the search field suggestions.

### The NWL 16-21 list
As with the official CSW list of words 2-15 letters in length, the CSW 16-21 list is composed of words from two sources: the Collins English Dictionary and the NWL 16-21 list. The NWL 16-21 list is in turn derived from several source dictionaries. Of these source dictionaries, not all are searchable online and not all of those have accessible APIs. Therefore assembling an exhaustive NWL 16-21 list in the same way that the official NWL 2-15 list was constructed would be a difficult task and would probably require a dedicated ["dictionary committee"](https://scrabbleplayers.org/w/Dictionary_Committee) of volunteers of the type that NASPA employs whenever it updates its word list. 

To date, only the Merriam-Webster Collegiate Dictionary is the only NWL source dictionary that has been used for the construction of the NWL 16-21 list. Fortunately this is probably the most comprehensive of the source dictionaries as well as the most frequently updated. Moreover, it has an [easy-to-use API](https://dictionaryapi.com/) that does not appear to suffer from the problems of inflections described in the CSW section. It is believed that the WJ2 combined with this single API can give an approximate extension of the NWL list up to 21 letters that is reasonably consistent with the official list. Two other source dictionaries, the _Oxford College Dictionary_ and the _Canadian Oxford Dictionary_ appear to have APIs, but it is unknown whether they can be accessed without an expensive commercial license or academic clearance. Anyone who has a physical or electronic copy of a source dictionary lacking such an API is encouraged to contribute words the the NWL list by hand.

### Other considerations
Since the Collins English Dictionary and the Merriam-Webster Collegiate Dictionary are continuously updated, they will contain some words, such as neologisms, that are missing from the WJ2. Such words, if discovered, should also be included in the present word list. Other word lists may be useful for cross-referencing with the APIs.

The 16-21 word lists should be checked to make sure that they do not contain inflections of root words that are not present in the standard Scrabble lists.

The Collins API and the Merriam-Webster API both produce occasional false positives. To my knowledge this only occurs when a word in the Word Judge list appears in one of the source dictionaries, but only with the inclusion of a hyphen or space. For example ALPHAFETOPROTEIN appears as a valid word according to the Collins API, but upon consulting the collinsdictionary.com website we find it only listed as ALPHA-FETOPROTEIN (with a hyphen). It has accordingly been omitted.

### Progress
As a proof of concept, the letter A of the proposed word list has been completed according to the above methodology. The CSW and NWL 16-21 word lists contain 397 and 218 words starting with A, respectively, as showin in the below table. In each list, about half of these have precisely 16 letters, and with each additional letter the number of words drops by about 50%. Comparing these data with the number of 13-, 14-, and 15-letter words in the official CSW and NWL word lists, we see that there is a consistent exponential decline. This suggests that the procedure results in a compatible extension of the lexicons and should be continued.

#### Words beginning with the letter A by lexicon
| Word length | WJ2 |  CSW  | NWL  |
| --------: |--------:| -----:| -----:|
| 13|   |  870|  554|
| 14|   |  596|  364|
| 15|   |  375|  221|
| 16| 485|*201*|*107*|
| 17| 457|*100*| *55*|
| 18| 349| *51*| *23*|
| 19| 249| *25*| *14*|
| 20| 186| *14*| *12*|
| 21| 120|  *6*|  *7*|
|>15|1846|*397*|*218*|

Finally, for the sake of comparison, some words have also been checked manually on [www.merriam-webster.com](https://www.merriam-webster.com). The corpus of words on the latter website is more comprehensive than that of the Merriam-Webster Collegiate Dictionary and similar in size to the CSW list. Other sources will be added in additional columns as necessary in future.
