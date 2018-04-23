# Klasyfikacja tekstu

Celem zadania jest zapoznanie się z wybranymi metodami klasyfikacji tekstu.

## Zadanie

1. Dla wybranego roku wybierz orzeczenia, które zostały wydane przez sądy powszechne (`courtType: COMMON`) lub Sąd
   Najwyższy (`courtType: SUPREME`).
1. Podziel wybrane orzeczenie według sygnatury (pierwsza wartość w polu `courtCases` -> wartość klucza `caseNumber`) na następujące grupy:
   1. `A?C.*` - sprawy cywilne
   1. `A?U.*` - sprawy z zakresu ubezpieczenia społecznego
   1. `A?K.*` - sprawy karne
   1. `G.*` - sprawy gospodarcze
   1. `A?P.*` - sprawy w zakresie prawa pracy
   1. `R.*` - sprawy w zakresie prawa rodzinnego
   1. `W.*` - sprawy o wykroczenia
   1. `Am.*` - sprawy w zakresie prawa konkurencji
1. Zmodyfikuj teksty orzeczeń tak by zawierały wyłącznie treść pojawiającą się po nagłówku "Uzasadnienie". Jeśli nie ma
   uzasadnienia, pomiń dane orzeczenie.
1. Z treści uzasadnień usuń wszystkie wyrazy, które nie są słowami (w szczególności liczby, znaki przestankowe, itp.)
   oraz 20 słów, które najczęściej występują w tekstach orzeczeń (wykorzystaj dane z wcześniejszych zadań).
1. Podziel zbiory z punktu 2 w taki sposób, aby 3/4 tekstów zostało użytych jako dane uczące, a 1/4 jako dane testowe.
   Zwróć uwagę na to, żeby zachowany był rozkład prawdopodobieństwa grup tematycznych, tzn. jeśli sprawy cywilne
   stanowią 10% wszystkich spraw, to powinny one stanowić 10% danych uczących oraz 10% danych testowych.
1. Dla każdej grupy wytrenuj dwa klasyfikatory binarne wykorzystując algorytm Support Vector Machines (SVM) oraz wagowanie TF•IDF:
   1. Pierwszy klasyfikator jako cechy ma wykorzystywać tekstowe (odmienione) formy słów.
   1. Drugi klasyfikator jako cechy ma wykorzystywać podstawowe formy słów (wykorzystaj dane z poprzedniego
      laboratorium).
1. Przedstaw wyniki klasyfikacji dla każdego zbioru tekstów z uwzględnieniem rozmiaru zbioru (liczby słów występujących
   w zbiorze) oraz wariantów algorytmu (formy tekstowe vs. formy podstawowe). Wyniki mają obejmować miary Precision,
   Recall oraz F1.
1. Przedstaw również zbiorcze wyniki klasyfikacji z uwzględnieniem miar micro- oraz macro-average.

## Przydatne informacje

1. Klasyfikacja tekstu z użyciem algorytmu SVM opisana jest w tutorialu 
   [Davida Batisty](http://www.davidsbatista.net/blog/2017/04/01/document_classification/).
1. Do klasyfikacji tekstów wykorzystywane jest podejście [bag-of-words](https://en.wikipedia.org/wiki/Bag-of-words_model), 
   (BoW) tzn. kolejność słów w tekście nie jest znacząca,
   istotne jest zaś to jak często dane słowo pojawia się w danym tekście. Ponadto każde słowo - niezależnie od jego
   znaczenia - traktowana jest jako osobna składowa wektora. Dlatego w podejściu tym słowa o podobnym znaczeniu, lecz
   odmiennej pisowni, traktowane są tak samo jak słowa, które nie mają podobnego znaczenia. Jest to zasadnicze
   ograniczenie tego podejścia.
1. Istotą metody BoW jest konstrukcja wektora, w którym każdemu słowu odpowiada jedna składowa. Przez ,,słowo'' można
   rozumieć np. formę tekstową lub formę podstawową. W tym drugim przypadku (dla j. polskiego) wektor będzie
   znacznie mniejszy, gdyż wiele różnych form tekstowych będzie reprezentowanych przez jedną składową wektora. Niemiej
   jednak rozmiar wektora jest bardzo duży - zwykle posiada on kilkadziesiąt do kilkuset tysięcy składowych. Aby
   ograniczyć rozmiar wektora można pominąć słowa, które występują rzadziej niż _n_ razy (np. rzadziej niż 5 razy).
1. Algorytm [Support Vector Machines](https://en.wikipedia.org/wiki/Support_vector_machine) (SVM) 
   jest algorytmem uczenia maszynowego stosowanym do klasyfikacji binarnej,
   którego charakterystyczną cechą jest znajdowanie (w najprostszym przypadku) hiperpłaszczyzny wraz z maksymalnym
   marginesem najlepiej separującej dwa zbiory danych. Po znalezieniu tej hiperpłaszczyzny klasyfikacja odbywa się
   poprze określenie, po której stronie hiperpłaszczyzny znajduje się dany egzemplarz.
1. SVM może być stosowany również w przypadku, gdy obszary nie są separowalne, poprzez zastosowanie tzw. 
   [kerneli](https://en.wikipedia.org/wiki/Kernel_method) - przekształceń, które zastępują surowe wartości cech
   klasyfikacyjnych, wartościami funkcji, dla której są one argumentami. Jednakże w przypadku klasyfikacji tekstów,
   najczęściej stosuje się liniowe klasyfikatory SVM.
1. [Wagowanie TF•IDF](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) polega na modyfikacji wag przypisywanych składowym wektora. 
   Wartość wagi danej składowej rośnie wraz ze wzrostem liczby wystąpień danego słowa (_term frequency_ TF) w
   klasyfikowanym dokumencie, a maleje wraz ze wzrostem liczby wystąpień danego słowa w dokumentach korpusu (_inverted
   document frequency_ IDF).
1. Miary [Precision](https://en.wikipedia.org/wiki/Precision_and_recall) (pl. _czułość_), 
   [Recall](https://en.wikipedia.org/wiki/Precision_and_recall) (pl. _swoistość_) oraz 
   [F1](https://en.wikipedia.org/wiki/F1_score) (średnia harmoniczna _czułości_ i _swoistości_) są wykorzystywane w
   algorytmach klasyfikujących do weryfikacji poprawności klasyfikacji. Pierwsza miara wskazuje procent poprawnych
   odpowiedzi testu, w przypadku wykrycia cechy badanej, a druga miara wskazuje procent poprawnych odpowiedzi testu, w
   przypadku braku wykrycia tej cechy. Trzecia miara najczęściej jest wykorzystywana do porównywania różnych algorytmów, 
   ponieważ zwykle można zwiększać swoistość kosztem czułości i vice versa, modyfikując hiper-parametry algorytmu.
1. Miary [micro-average](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_fscore_support.html#sklearn.metrics.precision_recall_fscore_support) 
   oraz macro-average są wykorzystywane do porównywania algorytmów klasyfikujących, w których występuje wiele klas
   obiektów. Pierwsza miara ignoruje przynależność klasyfikowanych przykładów do klasy i traktuje je jako należące do
   jednej klasy, dzieląc je na przykłady pozytywne bądź negatywnych. Natomiast druga miara jest średnią arytmetyczną
   wartości Pr, Rc oraz F1 uzyskanych dla poszczególnych klas.
