# TOPIC MODELING & SENTIMENT ANALYSIS ON MAURICE LEBLANC LUPIN NOVELS

___
## OBJECTIVE
The objective of this project is to analyse Maurice Leblanc, Arsène Lupin story, novels
Maurice Leblanc created a gentleman thief and detective, Arsène Lupin. He wrote more than 20 Arsène Lupin novels  (one of which is a posthumous novel) during the period of 1907- 1941.
My initial objective was to find main topics in his books and to  analyse the main characters


## TOOLS & METHODS
### RAW TEXT LOADING , CLEANING  AND PRE-PROCESSING
The source of the raw texts is [Project Gutenberg](https://www.gutenberg.org/ebooks/search/?query=Maurice+Leblanc&submit_search=Go%21). 
Out of 16 Lupin books in English in Project Gutenberg, I split 10 books into chapters for text analysis. 
The Gutenberg Project book texts include header and footer paragraphs that are not relevant to the book. So we have to remove those parts prior to text pre-processing.
There is no uniform/standard structures/patterns in Project Gutenberg texts. To locate the start and end of the book, we have to find out first what are the first and last elements of the text string to find their index numbers. The same method applies for finding the start and end of each book chapter. 
After removing irrelevant parts of the books and split into chapters, each book was rebundled in a dataframe and saved into csv.files prior to pre-processing.

For the pre-processing I include the following basic tasks:
* word tokenization
* removing accents
* removing punctuations
* removing non alphabetic words
* convert into lowercase
* rejoining the tokenized clean text into a string.

I did not include the stop word cleaning in the preprocessing as it will be included during the topic modeling. 

### TOPIC MODELING

During the first tries of topic modeling using  NMF and the built in 'english' stop-words, varying the number of topic from 2 - 10 and number of top words in the range of 20-30, the resulted topics were too similar to each other and containing a lot of people name.
I then try to customised the stop-words using tagged words; postagging the text and then try to add some categories of tagged words into the stop-words and see the resulting topics.

The final topics were generated using Tdidf and NMF, stop-words include all type of text tagged words except for NN and NNS.

### SENTIMENT ANALYSIS
Basic analysis of sentiment variation/evolution between chapters of each book was carried out.
The books were id following the year of the publication, with book_1 being to the first book published. Sentiment variation/analysis between books was also included. 



## RESULTS & CONCLUSIONS

### Topics

|n-top_word#| Topic No. 01 |Topic No. 02 | Topic No. 03 |Topic No. 04 |Topic No. 05 | Topic No. 06|
|:----------|:-------------|:------------|:-------------|:------------|:------------|:------------|
|0          | man          | island      | hillocks     | emperor     | godstone    | necklace    |
|1          | time         | woman       | caravan      | letters     | radium      | transom     |
|2          | house        | time        | chateau      | man         | man         | cabinet     |
|3          | room         | hand        | men          | coins       | prophet     | poker       |
|4          | nothing      | women       | man          | car         | fairies     | guests      |
|5          | hand         | tunnel      | earrings     | paper       | robe        | room        |
|6          | moment       | nothing     | hand         | room        | centuries   | house       |
|7          | way          | death       | way          | hidingplace | hand        | wife        |
|8          | men          | way         | disc         | book        | power       | shelves     |
|9          | letter       | voice       | children     | time        | miracle     | bohmer      |
|10         | day          | moment      | time         | nothing     | victims     | retaux      |
|11         | life         | bridge      | nothing      | day         | crypts      | anyone      |
|12         | minutes      | cells       | pool         | men         | bohemia     | occasions   |
|13         | death        | motorboat   | envelope     | gallery     | adventure   | letter      |
|14         | words        | passage     | day          | dinstruction| moors       | court       |
|15         | word         | rock        | medals       | highness    | locket      | bridge      |
|16         | morning      | flowers     | moment       | treaty      | island      | apartment   |
|17         | woman        | things      | fact         | hermit      | menhirs     | palermo     |
|18         | thing        | monster     | word         | dot         | legend      | motte       |
|19         | voice        | song        | codicil      | hand        | particle    | schoolmate  |

The topic modeling with Tfidf and NMF, usig stop-words consisting all the words from the text except for NN and NNS tagge words provided the best results.
The main insights from doing the toping modeling is that it is important to customise the stopwords and higher resolution of the text provides better results. In the future I will try to breakdown the chapter into sub-sections. 

### Sentiment Analysis

![Positive Sentiment Overtime](/Users/carlamoestafa/Documents/GitHub/project-4/sentpos_overtime.png)
![Negative Sentiment Overtime](/Users/carlamoestafa/Documents/GitHub/project-4/sentneg_overtime.png)
![Positive Sentiment variation within the books](/Users/carlamoestafa/Documents/GitHub/project-4/sentpos_short.png)
![Negative Sentiment variation within the books](/Users/carlamoestafa/Documents/GitHub/project-4/sentneg_short.png)
![Negative Sentiment variation within the books 10 & 16](/Users/carlamoestafa/Documents/GitHub/project-4/sentneg_10&16.png)

The positive sentiment overtime is quite stable, while negative sentiment is increasing.
Within the books sentiment varies differently depending on the books. Some books are flat, other show variation in positive or negative setiments.


## PROJECT DELIVERABLES:

[PRE-PROCESSING](project_4_preprocessing.ipynb)

[TOPIC MODELING](modeling-final.ipynb)

[SENTIMENT ANALYIS](sentiment.ipynb)

[PROJECT PRESENTATION](project-4.pptx)

