# Wyrażenia regularne

## 

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
  * *negative lookbehind* - wyrażenie `(?!<starych )(zł) dopasuje się do łańcucha `10 złotych` ale nie do łańcucha `10
    starych złotych`.
* Wyrażenie `\b` dopasowuje się do granicy słowa. Wyrażenie `psu` dopasuje się do słowa `zepsuć`, ale wyrażenie
  `\bpsu\b` dopasuje się wyłącznie do słowa `psu`. Warto zwrócić uwagę, że w Pythonie trzeba wprowadzić podwójny ukośnik
  (`\\bpsu\\b`) lub ozaczenie literalnego napisu (`r\bpsu\b`) aby ta sekwencja została poprawnie zinterpretowana.
  (Zastanów się dlaczego tak się dzieje).
* Niektóre języki mają specjalne literały dla wyrażeń regularny -- np. Perl i Ruby wykorzystują do tego ukośniki oraz
  operatory dopasowania do wyrażeń regularnych. Dzięki temu możliwe jest tworzenie warunków takich jak `string =~
  /\bpsu\b/`.
