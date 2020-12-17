
# Lexicon-based Sentiment Analysis for Economic and Financial Applications

This package allows Python users to leverage on cutting-hedge NLP
techniques to easily run sentiment analysis on economic text.
Given a list of texts as input and a list of tokens of interest (ToI),
the algorithm analyses the texts and compute the economic sentiment associated
each ToI. Two key features characterize this approach. First, it is
*fine-grained*, since words are assigned a polarity score that ranges in
\[-1,1\] based on a dictionary. Second, it is *aspect-based*, since the
algorithm selects the chunk of text that relates to the ToI based on a
set of semantic rules and calculates the sentiment only on that text,
rather than the full article.

The package includes some additional of features, like automatic
negation handling, tense detection, location filtering and excluding
some words from the sentiment computation. The algorithm only supports English
language, as it relies on the *en\_core\_web\_lg* language model from
the `spaCy` Python module.

## Installation

Make sure to install the following libraries:

``` bash
pip install utm lxml numpy fastavro h5py spacy nltk matplotlib joblib toolz textblob gensim pandas
```

``` py
pip install git+https://github.com/hanzhichao2000/pysentiment
pip install sentence_splitter wordcloud ruamel-yaml  pycosat
```

Set up NLTK:

``` bash
python -m nltk.downloader all
python -m nltk.downloader wordnet
python -m nltk.downloader omw
python -m nltk.downloader sentiwordnet
```

Finally get spacy models:

``` bash
python -m spacy download en_core_web_lg
python -m spacy download en_core_web_md
python -m spacy download en_core_web_sm
python -m spacy download it_core_news_sm
python -m spacy download de_core_news_sm
python -m spacy download fr_core_news_sm
python -m spacy download fr_core_news_md
python -m spacy download es_core_news_sm
python -m spacy download es_core_news_md
python -m spacy download nl_core_news_sm
```

## Example

Let’s assume that you want to compute the sentiment associated to two
tokens of interest, namely *unemployment* and *economy*, given the two
following sentences.

``` bash
text = ['Unemployment is rising at high speed', 'The economy is slowing down and unemployment is booming']
include = ['unemployment', 'economy']

get_sentiment(text = text, include = include)
>   Doc_id Text                       Chunk              Sentiment Tense Include  
>       1 Unemployment is rising at… Unemployment is r…    -0.899 pres… unemploy…
>       2 The economy is slowing do… economy is slowing    -0.3   pres… economy  
>       2 The economy is slowing do… unemployment is b…    -0.8   pres… unemploy…
```

The output of the function `get_sentiment` is a list, containing two
objects:

  - “sentiment” containing the average sentiment computed for
    each text;

  - “sentiment\_by\_chunk” containing the sentiment computed
    for each chunk detected in the texts.

The first element of the output list provides the overall average
sentiment score of each text, while the second provides the detailed
score of each chunk of text that relates to one of the ToI.




## Citation:

If you use this package, we encourage you to add the following references to the related papers:

<!-- ## References: -->

	- Barbaglia L., Consoli S., Manzan S. (2021).
    Fine-grained, aspect-based sentiment analysis on economic and financial lexicon. Available at arXiv:
    
  - Barbaglia L., Consoli S., Manzan S. (September 23, 2020).
    Forecasting with Economic News. Available at SSRN:
    <https://ssrn.com/abstract=3698121>

  - Barbaglia L., Consoli S., Manzan S. (2020). Monitoring the Business
    Cycle with Fine-Grained, Aspect-Based Sentiment Extraction from
    News. In: Bitetta V., Bordino I., Ferretti A., Gullo F., Pascolutti
    S., Ponti G. (eds) Mining Data for Financial Applications. MIDAS
    2019. Lecture Notes in Computer Science, vol 11985. Springer.


