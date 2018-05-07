# Rozpoznawanie jednostek nazewniczych (jednostek identyfikacyjnych, ang. Named Entity Recognition - NER)

Celem zajęć jest zaznajomienie studentów z mechanizmem rozpoznawania jednostek nazewniczych (NER), który jest jednym z
podstawowych narzędzi ekstrakcji informacji.

## Zadanie

1. Zapoznaj się z klasyfikacją jednostek nazewniczych dostępną w dokumencie 
   [Wytyczne KPWr - jednostki identyfikacyjne](http://clarin-pl.eu/pliki/warsztaty/WytyczneKPWr-JednostkiIdentyfikacyjne.pdf).
1. Zapoznaj się z [API serwisu NER](http://nlp.pwr.wroc.pl/redmine/projects/nlprest2/wiki) w systemie [Clarin](http://ws.clarin-pl.eu/ner.shtml).
1. Wybierz 100 pierwszych (sortując wg daty) orzeczeń w danym roku.
1. Rozpoznaj jednostki nazewnicze w dokumentach, korzystając z API Clarin oraz wykorzystując model `n82`. 
1. Przedstaw liczność rozpoznanych klas w postaci dwóch wykresów:
   1. na pierwszy wykresie przedstaw drobnoziarnistą klasyfikację wyrażeń,
   1. na drugim wykresie przedstaw zgrubną klasyfikację wyrażeń.
1. Przedstaw 100 najczęściej rozpoznanych wyrażeń, wraz z podaniem liczby ich wystąpień.
1. Oceń przydatność NERa dla danych jakimi są orzeczenia sądów.

## Przydatne informacje

1. Rozpoznawanie jednostek nazewniczych polega na wykrywaniu w tekście wyrażeń, które posiadają istotną treść - są to
   wyrażenia takie jak nazwy własne czy wyrażenia temporalne. 
1. Wykrywanie jednostek polega na rozpoznaniu początku wyrażenia, końca wyrażenia oraz kategorii semantycznej wyrażenia.
   Klasyfikacja semantyczna w sposób istotny wpływa na jakość wyników - im więcej rozpoznawanych kategorii, tym proces
   ten jest trudniejszy.
1. W kontekście systemów dialogowych jednostki nazewnicze nazywane są również encjami (ang. entities).
1. Najbardziej popularne algorytmy rozpoznawania jednostek nazewniczych bazują na formalizmie 
   [warunkowych pól losowych](https://en.wikipedia.org/wiki/Conditional_random_field) (ang. Conditional Random Fields -
   CRF). Jednak w ostatnim czasie coraz częściej wykorzystuje się algorytmy oparte o 
   [rekurencyjne sieci neuronowe](https://en.wikipedia.org/wiki/Recurrent_neural_network).
1. Do oznaczania jednostek nazewniczych często stosuje się format IOB (_in_, _out_, _beginning_):
   ```
   W            O
   1776         B-TIME
   niemiecki    O
   zoolog       O
   Peter        B-PER
   Simon        I-PER
   Pallas       I-PER
   dokonał      O
   formalnego   O
   ...
   ```
1. Alternatywą względem NERa jest proces _linkowania do bazy wiedzy_ (ang. named entity linking/disambiguation - NED).
   W tym procesie zakłada się istnienie zewnętrznego zasobu zawierającego słownik nazw własnych (które mogą być
   wieloznaczne). W wyniku rozpoznania wyrażenia oraz jegu ujednoznacznienia, możliwe jest nie tylko przypisanie
   właściwej kategorii semantycznej, ale również zdobycie dodatkowych informacji na temat rozpoznanego wyrażenia.
1. Najbardziej popularnymi zasobami wykorzystywanymi do treningu NERów oraz NEDów są Wikipedie ponieważ struktura
   wewnętrznych odnośników Wikipedii dostarcza cennych informacji które można wykorzystać jako cechy w algorytmie
   klasyfikacyjnym, bądź ujednoznaczniającym. 
1. Jako referenycjne bazy wiedzy wykorzystuje się [DBpedię](http://wiki.dbpedia.org/) oraz 
   [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page). 
   Obie bazy wiedzy zawierają szereg ustrukturyzowanych danych pojawiających się w różnych wersjach Wikipedii.
