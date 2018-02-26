# Wyrażenia regularne

## 

## Warto wiedzieć

* W niektórych językach programowania można dopasowywać klasy znaków Unicode:
  * `\p{L}` - litery w dowolnym języku (np. a, ą, ć, ü)
  * `\p{Ll}` - mała litera w dowolnym języku
  * `\p{Lu}` - wielka litera w dowolnym języku
* Niestety klasy Unicode nie są obsługiwane w Pythonie, ale są obsługiwane w Rubim.
* Wyrażenia regularne zawierają konstrukcje positive oraz negative lookahead oraz lookbehind. Przykładowo:
  * *positive lookahead* - wyrażenie `(\w+)(?= ma kota)` dopasuje się do łańcucha `Ala ma kota`, ale dopasowanie obejmie tylko słowo
  `Ala`.
  * *negative lookahead* - wyrażenie `(?!<starych )(zł) dopasuje się do łańcucha `10 złotych` ale nie do łańcucha `10
    starych złotych`.
