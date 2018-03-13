# Korekta tekstu i odległość Levenshteina

## Zadania

1. Podziel tekst wszystkich orzeczeń z określonego roku na słowa.
1. Oblicz i utrwal listę frekwencyjną słów (liczbę wystąpień posortowaną względem malejącej liczby wystąpień słów).
   Przykładowo, jeśli korpus zawiera zdanie "Ala Ala, kot", to lista frekwencyjna dla tego korupusu jest następująca:
   1. Ala: 2
   1. kot: 1
1. Z listy frekwencyjnej usuń pozycje, które nie stanowią słów (np. są to pojedyncze litery występujące w
   zanonimizowanej wersji nazw własnych). Usuń również wszystkie wartości, które nie są zapisane literami (w
   szczególności liczby).
1. W skali logarytmicznej przedstaw wykres, w którym na osi X są pozycje na liście frekwencyjnej, a na osi Y liczba
   wystąpień słowa zajmującego określoną pozycję.
1. Korzystając z pliku [polimorfologik.zip](https://github.com/morfologik/polimorfologik/releases/download/2.1/polimorfologik-2.1.zip) 
   znajdź wszystkie słowa, które nie znajdują się w tym słowniku.
1. Przedstaw 30 przykładowych słów, które nie należą do słownika.
1. Korzystając z algorytmu korekty słów oraz listy frekwencyjnej, określ najbardziej prawdopodobną korektę
   słów, które nie występują w słowniku.

## Przydatne informacje

1. Odległość edycyjna, zwana również odległością Levenshteina to miara określona dla dowolnej pary łańcuchów znaków.
   Miara ta określa minilaną ilość operacji dodania, usunięcia oraz zamiany znaków jest niezbędnych aby zamienić łańcuch _a_ w
   łańcuch _b_. Miara ta jest symetryczna, dlatego kolejność łańcuchów nie ma znaczenia.
1. Implementacja algorytmu obliczającego odległość Levenshteina jest najczęściej realizowana w formie algorytmu
   dynamicznego, który wykorzystuje wcześniejsze wyniki, w celu przyspieszenia obliczeń - 
   zob. [artykuł w Wikipedii](https://en.wikipedia.org/wiki/Levenshtein_distance).
1. W przypadku korekty błędnych słów miara Levenshtaina może służyć do wyboru zbioru słów, które mają najmniejszą
   odległość od danego, błędnego słowa w sensie odległości Levenshteina. Jeśli zbiór ten składa się z wielu elementów,
   nie wystarcza jednak do wybrania najbardziej prawdopodobnej korekty. Można to zrobić korzystając ze statystyki
   wystąpień słów i wybrać słowo, które wśród słów o tej samej odległości, jest najbardziej prawdopodobne.
1. Zwykle algorytm korekty nie wykorzystuje bezpośredniej implementacji algorytmu dla odległości Levenshteina. Zamiast
   tego na podstawie błędnego słowa generowane są wszystkie słowa o odległości 1, potem 2, itd. aż znaleziona zostanie
   słowo, które może stanowić korektę danego słowa - zob. [artykuł P. Norviga na ten temat](https://norvig.com/spell-correct.html).
