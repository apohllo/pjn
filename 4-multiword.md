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

1. Bigramem nazywamy ciąg składający się z dwóch słów.
1. Unigramem nazywamy ciąg składający się z jednego słowa.
1. n-gramem nazywamy ciąg składający się z n słów.
1. Punktowa informacja wzajemna jest miarą wykorzystywaną do oceny korelacji pomiędzy zjawiskami. 
   Zbudowana jest na założeniu, że zjawiska, których prawdopodobieństwo współwystępowania jest istotnie większe
   od iloczynu prawdopodobieństw każdego ze zjawisk z osobna, to znaczy, że są one silnie skolerowane.
1. Statystyka logarytmiczna oparta o rozkład dwumienny (nie znalazłem niestety oficjalnego tłumaczenia ang. *log
   likelihood ratio*) ma bardziej rozbudowane założenia. W skrócie można napisać, że mierzy ona odchylenie pomiędzy
   współwystępowaniem, a wystepowanie na osobności, biorąc za podstawę rozkład dwumienny.
1. Metody przedstawione w tym zadaniu mogą być z powodzeniem stosowane również w problemie identyfikacji wyrazów oraz
   zwrotów charakterystycznych dla określonej dziedziny wiedzy.
