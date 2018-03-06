# Lematyzacja i wyszukiwanie pełnotekstowe

## Zadania

1. Zainstaluj ElasticSearch (ES)
1. Zainstaluj w ES plugin do obsługi języka polskiego https://github.com/allegro/elasticsearch-analysis-morfologik 
1. Zdefiniuj w ES analizator zawierający następujące elementy (tekst w języku polskim):
   1. standardowy tokenizer
   1. filtr lematyzujący oparty o morfologika
1. Zdefiniuj w ES indeks do przechowywania orzeczeń sądów zawierający następujące elementy:
   1. treść orzeczenia - typu: tekst w języku polskim
   1. datę orzeczenia - typu: data
   1. sygnaturę orzeczenia - typu: słowo kluczowe
   1. imiona i nazwiska sędziów wydających orzeczenie - typu: tablica
1. Załaduj dane z wybranego roku do ESa
1. Znajdź liczbę orzeczeń, w których występuje słowo **szkoda**.
1. Znajdź liczbę orzeczeń, w których występuje fraza **trwały uszczerbek na zdrowiu**, dokładnie w tej kolejności ale w
   dowolnej formie fleksyjnej.
1. Jak wyżej, ale z uwzględnieniem możliwości wystąpienia maksymalnie 2 dodatkowych słów pomiędzy dowolnymi elementami
   frazy.
1. Określ 3 sędziów, którzy wydali największą liczbę orzeczeń w danym roku, wraz z liczbą wydanych orzeczeń.
1. Przedstaw histogram liczby orzeczeń w zależności od miesiąca.

## Przydatne infromacje

1. Silniki Full Text Search (FTS) są wyspecjalizowane w przechowywaniu oraz wyszukiwaniu danych tekstowych.
1. Dwa najpopularniejsze FTSy to SOLR oraz ElasticSearch (ES).
1. Niektóre bazy danych posiadają rozwiązania podobne do FTSów, ale ze względu na mniej elestyczną budowę 
   oraz większą optymalizację dostępu do danych strukturalnych, trudniej jest je dostosować do wybranego języka.
1. Zarówno dla SOLRa jak i ES istnieją pluginy wspierające język polski, np. https://github.com/allegro/elasticsearch-analysis-morfologik 
1. Działanie FTSów oparte jest o tzw. odrócony indeks - po załadowaniu dokumentu, jest on dzielony na tokeny (niezależne
   elementy tekstu - w przybliżeniu słowa), które następnie są przetwarzane przez filtry. Tak przetworzone tokeny
   trafiają do indeksu, którego kluczami są tokeny, a wartościami - miejsca ich wystąpień w dokumentach.
1. Minimalna konfiguracja FTSa wymaga określenia dwóch własności: zasad podziału tekstu na tokeny oraz łańcucha
   przekształceń (filtrów), którym poddawane są tokeny. 
1. FTSy posiadają zazwyczaj wiele wbudowanych tokenizerów - mogą np. uwzględniać takie elementy jak znaczniki HTML,
   które będą traktowane w sposób szczególny.   
1. Wśród popularnych tokenizerów można wymienić: _standard tokenizer_ (oparty o zasady podziału na słowa według
   algorytmu Unicode), _whitespace tokenizer_ (oparty o podział tekstu w miejsach występowania białych znaków), czy
   _url/email tokenizer_ (który działa podobnie do _standard tokenizera_ ale dodatkowo rozpoznaje adresy URL i e-mail
   jako kompletne tokeny). 
1. Niektóre znaki (np. przecinki, kropki) mogą być usuwane już na etapie podziału tekstu na tokeny.
1. Wśród popularnych filtrów można wymienić: zamianę na małe litery, zastępowanie liter ze znakami diakrytycznymi (np.
   litery ą) ich odpowiednikami z alfabetu łacińskiego (ą -> a), filtrowanie słów z tak zawnej stop-listy (listy
   najpopularniejszych słów, takich jak _i_, _a_, _w_, itp.) oraz **lematyzatory**.
1. Lematyzacja polega na sprowadzeniu słowa do jego formy podstawowej, np. dla formy _psu_ jest to forma _pies_
   (dla rzeczownika formą podstawową jest forma mianownik liczby pojedynczej - o ile występuje). 
1. W języku występuje wiele form wieloznacznych - przykładowo forma _goli_ może mieć następujące formy podstawowe:
   _gol_, _golić_, _goły_. 
1. Czytając tekst człowiek może bez problemu wskazać formę podstawową. Dla komputera stanowi to jednak duże wyzwanie, a
   algorytmy lematyzacyjne uwzględniające kontekst nie są trywialne. Dlatego w FTSach problem ten rozwiązywany jest
   pragmatycznie - dla każdej formy w tekście jej wystąpienie jest przyporządkowywane do **wszystkich** form
   podstawowych, z którymi jest ona kompatybilna. Ponieważ ten sam proces realizowany jest w trakcie wyszukiwania,
   użycie innej formy tekstowej niż forma występująca w tekście, powoduje dopasowanie jednej formy do drugiej,
   poprzez wspólną formę podstawową. Np. jeśli w dokumencie jest zdanie: _W trakcie meczu padły 2 **gole**_, a zapytanie ma
   postać: _Ile **goli** padło w meczu?_, to algorytm lematyzacji powiąże oba dokumenty, dzięki istnieniu wspólnej formy
   podstawowej _**gol**_.
