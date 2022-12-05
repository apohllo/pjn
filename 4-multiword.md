# Ekstrakcja wyrażeń wielosegmentowych

Celem zadania jest ekstracja wyrażeń wielosegmentowych, występujących w tekstach prawniczych.

## Zadanie

1. Podziel tekst wszystkich orzeczeń z określonego roku na słowa.
1. Oblicz statystykę występowania bigramów słów, pomijając w tekście wszystkie wyrazy,
   które nie stanowią słów. Liczby powinny być usunięte, ale wyrazy jednoliterowe nie powinny być usuwane. Przykładowo
   dla zdania: "Ala ma kota." statystyka ta wygląda następująco:
   1. "ala ma": 1
   1. "ma kota": 1
1. Korzystając z wzoru na [punktową informację wzajemną](https://en.wikipedia.org/wiki/Pointwise_mutual_information)
   oblicz tę wartość dla wszystkich par słów. Wykorzystaj statystyki unigramów obliczone w [poprzednim zadaniu](3-levenshtein.md).
1. Posortuj bigramy względem malejącej wartości punktowej informacji wzajemnej.
1. Przedstaw 30 pierwszych wyników.
1. Korzystając z wzoru na [statystykę logarytmiczną opartą o rozkład dwumienny (G2)](http://tdunning.blogspot.com/2008/03/surprise-and-coincidence.html)
   sporządź analogiczną listę, jak dla punktowej informacji wzajemnej.
1. Przedstaw 30 pierwszych wyników.
1. Przedyskutuj otrzymane wyniki.

## Przydatne informacje

1. Unigramem nazywamy ciąg składający się z jednego słowa; bigramem - ciąg składający się z dwóch słów; n-gramem - ciąg składający się z n słów.
1. Punktowa informacja wzajemna jest miarą wykorzystywaną do oceny korelacji pomiędzy zjawiskami. 
   Opiera się na założeniu, że zjawiska, których prawdopodobieństwo współwystępowania jest istotnie większe
   od iloczynu prawdopodobieństw wystąpienia każdego ze zjawisk z osobna, są ze sobą silnie skolerowane.
1. Statystyka logarytmiczna oparta o rozkład dwumienny ma bardziej rozbudowane założenia. 
   W skrócie można napisać, że testuje istotność hipotezy, że zjawiska są skorelowane,
   biorąc za podstawę rozkład dwumienny występowania słów w tekście.
1. Metody przedstawione w tym zadaniu mogą być z powodzeniem stosowane również w problemie identyfikacji wyrazów oraz
   zwrotów charakterystycznych dla określonej dziedziny wiedzy.
1. Narzędzie [SRI LM](http://www.speech.sri.com/projects/srilm/) umożliwia efektywne wyliczenia statystyk n-gramów.
   Pozwala również na budowanie modeli językowych w oparciu o tę statystykę.
1. Bardziej zaawansowane algorytmy takie jak np. [AutoPhrase](https://github.com/shangjingbo1226/AutoPhrase) biorą pod
   uwagę znacznie więcej własności wyrażenia: cechy morfosyntaktyczne, konteksty ich występowania oraz wykorzystują dane
   np. z Wikipedii w celu określenia zbioru cech, które identyfikuje poprawne wyrażenia wielosegmentowe.
