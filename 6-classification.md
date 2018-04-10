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
1. Zmodyfikuj teksty orzeczeń tak by zawierały wyłącznie treść pojawiającą się po nagłówku "Uzasadnienie". Jesli nie ma
   uzasadnienia, pomiń dane orzeczenie.
1. Z treści uzasadnień usuń wszystkie wyrazy, które nie są słowami (w szczególności liczby, znaki przestankowe, itp.)
   oraz 20 słów, które najczęściej występują w tekstach orzeczeń (wykorzystaj dane z wcześniejszych zadań).
1. Podziel zbiory z punktu 2 w taki sposób, aby 3/4 tekstów zostało użytych jako dane uczące, a 1/4 jako dane testowe.
   Zwróć uwagę na to, żeby zachowany był rozkład prawdopodobieństwa grup tematycznych, tzn. jeśli sprawy cywilne
   stanowią 10% wszystkich spraw, to powinny one stanowić 10% danych uczących oraz 10% danych testowych.
1. Dla każdej grupy wytrenuj dwa klasyfikatory binarne wykorzystując algorytm Support Vector Machines (SVM) oraz wagowanie TF•IDF:
   1. Pierwszy klasyfikator jako cechy ma wykorzystywać tekstowe (odmienione) formy słów.
   1. Drugi klasyfikator jako cechy ma wykorzstywać podstawowe formy słów (wykorzystaj dane z poprzedniego
      laboratorium).
1. Przedstaw wyniki klasyfikacji dla każdego zbioru tekstów z uwzględnieniem rozmiaru zbioru (liczby słów występujących
   w zbiorze) oraz wariantów algorytmu (formy tekstowe vs. formy podstawowe). Wyniki mają obejmować miary Precision,
   Recall oraz F1.
1. Przedstaw również zbiorcze wyniki klasyfikacji z uwzględnieniem miar micro- oraz macro-average.

## Przydatne informacje

1. Kasyfikacja tekstu z użyciem algorytmu SVM opisana jest w tutorialu 
   [Davida Batisty](http://www.davidsbatista.net/blog/2017/04/01/document_classification/).
