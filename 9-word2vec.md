# Word2Vec

Celem zajęć jest zaznajomienie studentów z jednym z najbardziej popularnych algorytmów zamiany słów na wektory wartości
liczbowych (ang. _word embeddings_).

## Zadanie

1. Zapoznaj się z dokumentacją modelu [word2vec w bibliotece Gensim](https://radimrehurek.com/gensim/models/word2vec.html).
1. Z korpusu orzeczeń wyselekcjonuj dane, tak, żeby mieć minimum 1GB tekstu.
1. Oczyść dane usuwając z nich znaczniki HTML oraz usuwając podziały słów na końcach linii.
1. Korzystając z wbudowanego w Gensim [mechanizmu wykrywania wyrażeń wielosegmentowych](https://radimrehurek.com/gensim/models/phrases.html#id2)
   wykryj frazy składające się z maksymalnie 3 słów, korzystając z domyślnych ustawień biblioteki.
1. Dla tak przygotowanego zbioru danych wytrenuj model word2vec o następujących parametrach:
   1. model: CBOW
   1. okno: 5
   1. rozmiar wektora: 300
   1. minimalna liczba występień: 3
1. Zapisz wytrenowany model na dysku.
1. Znajdź 3 najbardziej podobne wyrażenia (słowa i zwroty) dla następujących wyrażeń:
   1. Sąd Najwyższy
   1. Trybunał Konstytucyjny
   1. kodeks cywilny
   1. kpk
   1. sąd rejonowy
   1. szkoda
   1. wypadek
   1. kolizja
   1. szkoda majątkowa
   1. nieszczęście
   1. rozwód
1. Znajdź wypadkową operacji na słowach (5 najbliższych wyników)
   1. Sąd Najwyższy - kpc + konstytucja
   1. pasażer - mężczyzna + kobieta
   1. samochód - droga + rzeka
1. Korzystając z algorytmu [t-SNE](http://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html) 
   przedstaw projekcję wektorów następujących słów na płaszczyznę:
   1. szkoda
   1. strata
   1. uszczerbek
   1. szkoda majątkowa
   1. uszczerbek na zdrowiu
   1. krzywda
   1. niesprawiedliwość
   1. nieszczęście

## Przydatne informacje

1. "Klasyczne" artykuły T. Mikolova i współpracowników: 
   [Distributed Representations of Words and Phrases and their Compositionality](http://papers.nips.cc/paper/5021-distributed-representations-of-words-andphrases)
   oraz [Efficient Estimation of Word Representations in Vector Space](https://arxiv.org/abs/1301.3781) bardzo
   przystępnie opisują sposób tworzenia wektorów w algorytmie word2vec.
1. W algorytmi word2vec występują dwa tryby predykcyjne:
   1. CBOW - na podstawie słów kontekstowych przewidywane jest brakujące słowo,
   1. Skip-gram - na podstawie danego słowa przewidywane są słowa z kontekstu.
1. Algorytm word2vec jest bardzo efektywny - w ciągu jednego dnia może przetworzyć korpusy zawierające miliardy tokenów.
1. Wektorowa reprezentacja uzyskana na podstawie algorytmu word2vec pozwala na wykonywanie operacji algebraicznych:
   w2v("król") - w2v("mężczyzna") + w2v("kobieta") = w2v("królowa")
