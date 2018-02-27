# Wyrażenia regularne

## Zadanie

Masz do dyspozycji zbiór orzeczeń w formacie:

```
{:id=>205374,
 :courtType=>"CONSTITUTIONAL_TRIBUNAL",
 :courtCases=>[{:caseNumber=>"U 3/86"}],
 :judgmentType=>"SENTENCE",
 :judges=>
  [{:name=>"Andrzej Kabat",
    :function=>nil,
    :specialRoles=>["REPORTING_JUDGE"]},
   {:name=>"Kazimierz Buchała",
    :function=>nil,
    :specialRoles=>["PRESIDING_JUDGE"]},
   {:name=>"Stanisław Pawela", :function=>nil, :specialRoles=>[]}],
 :source=>
  {:code=>"CONSTITUTIONAL_TRIBUNAL",
   :judgmentUrl=>
    "http://otk.trybunal.gov.pl/orzeczenia/teksty/otk/1986/U_03_86.doc",
   :judgmentId=>"c9fd6921a25bf3b0911191e1ad06d1cb",
   :publisher=>nil,
   :reviser=>nil,
   :publicationDate=>""},
 :courtReporters=>["Jerzy Adam Porowski"],
 :decision=>nil,
 :summary=>nil,
 :textContent=>
  "Orzeczenie\n" +
  "z dnia 16 czerwca 1986 r.\n" +
  "/U 3/86 r./\n" +
  "\n" +
  "\n" +
  "Trybunał Konstytucyjny w składzie: \n" +
  "\n" +
  "Przewodniczący: \tSędzia TK Kazimierz Buchała \n" +
  "\n" + ...
 :legalBases=>[],
 :referencedRegulations=>
  [{:journalTitle=>
     "Rozporządzenie Rady Ministrów z dnia 28 października 1983 r. w sprawie określenia liczby punktów sprzedaży napojów alkoholowych.",
    :journalNo=>60,
    :journalYear=>1983,
    :journalEntry=>273,
    :text=>
     "Rozporządzenie Rady Ministrów z dnia 28 października 1983 r. w sprawie określenia liczby punktów sprzedaży napojów alkoholowych (Dz. U. z 1983 r. Nr 60 poz. 273 - § 1, § 2 ust. 2)"},
   {:journalTitle=>
     "Ustawa z dnia 26 października 1982 r. o wychowaniu w trzeźwości i przeciwdziałaniu alkoholizmowi",
    :journalNo=>35,
    :journalYear=>1982,
    :journalEntry=>230,
    :text=>
     "Ustawa z dnia 26 października 1982 r. o wychowaniu w trzeźwości i przeciwdziałaniu alkoholizmowi (Dz. U. z 1982 r. Nr 35 poz. 230 - art. 3 ust. 1, art. 3 ust. 2, art. 12 ust. 1)"},
   {:journalTitle=>
     "Uchwała Sejmu Polskiej Rzeczypospolitej Ludowej z dnia 31 lipca 1985 r. w sprawie szczegółowego trybu postępowania przed Trybunałem Konstytucyjnym.",
    :journalNo=>39,
    :journalYear=>1985,
    :journalEntry=>184,
    :text=>
     "Uchwała Sejmu Polskiej Rzeczypospolitej Ludowej z dnia 31 lipca 1985 r. w sprawie szczegółowego trybu postępowania przed Trybunałem Konstytucyjnym (Dz. U. z 1985 r. Nr 39 poz. 184 - art. 42 ust. 1 pkt 6)"}],
 :keywords=>[],
 :referencedCourtCases=>[],
 :receiptDate=>"",
 :meansOfAppeal=>nil,
 :judgmentResult=>nil,
 :lowerCourtJudgments=>[],
 :dissentingOpinions=>[],
 :judgmentDate=>"1986-06-16"}
```

Zrealizuj następujące zadania:
1. Wydostań wszystkie kwoty pieniężne pojawiające się tekstach orzeczeń określonego roku, znormalizuj je i przedstaw ich
   rozkład w postaci histogramu.
1. Jak w punkcie 1. ale zrób osobny wykres dla wartości do 1 mln zł. oraz powyżej 1 mln zł.
1. Określ liczbę orzeczeń odwołujących się w określonym roku do **artykułu 445 Ustawy z dnia 23 kwietnia 1964 r. - Kodeks cywilny**.
1. Określ liczbę orzeczeń w określonym roku, które zawierają słowo **szkoda** w dowolnej formie fleksyjnej. Wynik ten
   nie może obejmować innych słów, które mają wspólny prefiks ze słowem szkoda, np. *szkodzić*, *szkodzący*, itp.

## Warto wiedzieć

* W niektórych językach programowania można dopasowywać klasy znaków Unicode:
  * `\p{L}` - litery w dowolnym języku (np. a, ą, ć, ü)
  * `\p{Ll}` - mała litera w dowolnym języku
  * `\p{Lu}` - wielka litera w dowolnym języku
* Nie wszystkie silniki dopasowujące wyrażenia regularne działają tak samo. Np. klasy Unicode nie są obsługiwane 
  w Pythonie, ale są obsługiwane w Rubim. Co prawda w Pythonie 3 `\w` dopasuje się do polskich liter, ale nie mamy
  możliwości odróżnienia, czy są to litery wielkie, czy małe.
* Wyrażenia regularne zawierają konstrukcje positive oraz negative lookahead oraz lookbehind. Przykładowo:
  * *positive lookahead* - wyrażenie `(\w+)(?= ma kota)` dopasuje się do łańcucha `Ala ma kota`, ale dopasowanie obejmie tylko słowo
  `Ala`.
  * *negative lookbehind* - wyrażenie `(?!<starych )(zł)` dopasuje się do łańcucha `10 złotych` ale nie do łańcucha `10
    starych złotych`.
* Wyrażenie `\b` dopasowuje się do granicy słowa. Wyrażenie `psu` dopasuje się do słowa `zepsuć`, ale wyrażenie
  `\bpsu\b` dopasuje się wyłącznie do słowa `psu`. Warto zwrócić uwagę, że w Pythonie trzeba wprowadzić podwójny ukośnik
  (`\\bpsu\\b`) lub ozaczenie literalnego napisu (`r'\bpsu\b'`) aby ta sekwencja została poprawnie zinterpretowana.
  (Zastanów się dlaczego tak się dzieje).
* Niektóre języki mają operatory dopasowania do wyrażeń regularnych oraz specjalne literały dla wyrażeń regularny.
  Perl i Ruby  wykorzystują do tego sekwencję `=~` oraz ukośniki.  Dzięki temu możliwe jest tworzenie warunków takich jak `string =~ /\bpsu\b/`.
* Działanie literału `\b` zależne jest jednak od tego jak rozumiane są litery. I tak wyrażenie `\bpsu\b` w Rubim
  zostanie dopasowane do `psu` ale nie do `psuć`, ale w grepie zostanie dopasowane do obu tych przypadków, ponieważ `ć`
  nie jest uznawane za literę.
* Różnice pomiędzy sposobem interpretacji wyrażeń regularnych w różnych językach programowania powodują, że wyrażenia te
  często nie mogą być przenoszone bezpośrednio z jednego języka do innego, bez zmiany ich znaczenia. Należy mieć to na
  uwadze kiedy kopiuje się rozwiązania z Internetu.
