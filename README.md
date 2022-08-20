# Book-Classification--Classification-Is-All-You-Need

# Gutenberg Project Overview
**Project Gutenberg is a library of over 60,000 free eBooks**

![Gutenberg](https://drive.google.com/uc?export=view&id=1bOd8Hiv-sU8Skj1gYR-2cxLUEBIretyZ)

In this project we selected some books from Gutenburg library from different categories and then select random paragraphs from then and labeled this paragraphs by the book name for ground truth.
After creating the dataset we used many transformation algorithms to embed the text to numbers for modeling process like (Fast-text,BERT ,TF_IDF,BOW,Skip gram ,Glove ,LDA ,Word2Vec ,Doc2Vec)
<br> After this we tried many clustering algorithms like(K-means,Expected-maximization(EM),Hierarchical,) and chose the champion one which achieved the kappa and silhouette score.


**Recommended to use GPU to run much faster.
But it works well with the CPU also.**
- GPU takes around 40 min, while CPU may take hours.

# Project Methodology

![Gutenberg](https://drive.google.com/uc?export=view&id=1-YX8_vqTOSjudFe5AiovLCDzA6SEOhLm)

# Project Main Steps


- [Data Exploration](#1)
- [Data Preprocessing](#2)
- [Word Embedding](#3)
  - [BOW](#4)
  - [TF-IDF](#5)
  - [Doc2Vec](#6)
  - [Bert Embedding](#7)
  - [Glove](#8)
  - [Fast text](#9)
  - [Word2Vec](#10)
  - [LDA (Linear Discriminant Analysis)](#11)
- [Word embedding dictionary](#12)
- [Training](#13)
- [BERT classifier](#14)
- [Validation](#15)
- [Error analysis](#16)
  - [Reduce the samples' word number](#17)
  - [Word Counts](#18)
- [Grid Search](#19)
- [Conclusion](#20)

# <a name="1">Data Exploration</a>
**By discovering the books’ content as shown below:**
> Moby Dick by Herman Melville 1851]\r\n\r\n\r\nETYMOLOGY.\r\n\r\n(Supplied by a Late Consumptive Usher to a Grammar School)\r\n\r\nThe pale Usher--threadbare in coat, heart, body, and brain; I see him\r\nnow.  He was ever dusting his old lexicons and grammars, with a queer\r\nhandkerchief, mockingly embellished with all the gay flags of all the\r\nknown nations of the world.  He loved to dust his old grammars; it\r\nsomehow mildly reminded him of his mortality.\r\n\r\n"While you take in hand to school others, and to teach them by what\r\nname a whale-fish is to be called in our tongue leaving out, through\r\nignorance, the letter H, which almost alone maketh the signification\r\nof the word, you deliver that which is not true." --HACKLUYT\r\n\r\n"WHALE. ... Sw. and Dan. HVAL.  This animal is named from roundness\r\nor rolling; for in Dan. HVALT is arched or vaulted." --WEBSTER\'S\r\nDICTIONARY\r\n\r\n"WHALE. ... It is more immediately from the Dut. and Ger. WALLEN;\r\nA.S. WALW-IAN, to roll, to wallow." --RICHARDSON\'S DICTIONARY\r\n\r

- Many problems have been found in books' content, so we should deal with them.

# <a name="2">Data Preprocessing</a>
**Clean the content of the books by:**
- Removing the word capitalization, unwanted characters, white spaces, and stop words.
- Replacing some patterns.
- Applying lemmatization and tokenization.

**The data after cleaning process**
> delight steelkilt strain oar stiff pull harpooneer get fast spear hand radney sprang bow always furious man seem boat bandage cry beach whale topmost back nothing loath bowsman haul blinding foam blent two whiteness together till sudden boat struck sunken ledge keel spill stand mate instant fell whale slippery back boat right dash aside swell radney toss sea flank whale struck spray instant dimly see veil wildly seek remove eye moby dick whale rush round sudden maelstrom seize swimmer jaw rear high plunge headlong go meantime first tap boat bottom lakeman slacken line drop astern whirlpool calmly look thought thought

**Dataset Building**
![image](/Image/Screenshot_1.png)
- Create a data frame containing 2 columns and 1000 rows representing the books' samples (Sample) and the book name (Label)

**Note:** Before starting to transform words. We split the data into training and testing, to prevent data leakage.

