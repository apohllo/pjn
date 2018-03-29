# Tagowanie morfosyntaktyczne

Celem zadania jest zapoznanie się z rolą taggera morfosyntaktycznego w przetwarzaniu języków naturalnych.

## Zadanie

1. Pobierz [obraz Dockera](https://hub.docker.com/r/apohllo/krnnt/) zawierający następujące narzędzia:
   1. Morfeusz - słownik morfosyntaktyczny
   1. Corpus2 - narzędzie dostępu do korpusów
   1. Toki - tokenizer dla j. polskiego
   1. Maca - konwerter tagsetów, analizator morfosyntaktyczny
   1. krnnt - tagger dla języka polskiego
1. Korzystając z zainstalowanego taggera otaguj morfosyntaktycznie i zlematyzuj wszystkie orzeczenia z wybranego roku.
1. Na podstawie otagowanych orzeczeń oblicz statystykę bigramów o następujących własnościach:
   1. słowo w formie zlematyzowanej, pisane małymi literami
   1. tag zawierający wyłącznie kategorię morfosyntaktyczną słowa (czyli w uproszczeniu informację o tym, czy jest to
      rzeczownik, czasownik, przymiotnik, itp.)
1. Przykładowo dla zdania "Ala ma kota" otagowanego jako
   ```
   Ala	none
           Ala	subst:sg:nom:f	disamb
   ma	space
           mieć	fin:sg:ter:imperf	disamb
   kota	space
           kot	subst:sg:acc:m2	disamb
   .	none
           .	interp	disamb
   ```
   algorytm powinien zarejestrować następujące pary: `ala:subst mieć:fin` oraz `mieć:fin kot:subst`.
1. Oblicz statystykę logarytmiczna opartą o rozkład dwumienny dla tego zbioru.
1. Przedstaw 30 pierwszych wyników, w których na pierwszy miejscu występuję rzeczownik, a na drugim miejscu rzeczownik
   lub przymiotnik.

## Przydatne informacje

1. Konfiguracja narzędzi do analizy morfosyntaktycznej (Maca i in.) opisana jest na [stronie Politechniki
   Wrocławskiej](http://nlp.pwr.wroc.pl/redmine/projects/libpltagger/wiki/InstallOnUbuntu11).
1. Instalacja biblioteki KRNNT opisana jest [na githubie](https://github.com/kwrobel-nlp/krnnt).
1. Analizator morfosyntaktyczny jest narzędziem, które dla słów w tekście generuje możliwe interpretacje form bazowych
   oraz wartości kategorii gramatycznych. Przykładowo dla słowa "ma" może on wygnerować następujące interpretacje:
   ``` 
    ma	space
            mieć	fin:sg:ter:imperf
            mój  	adj:sg:nom:f:pos
            mój  	adj:sg:voc:f:pos
   ```
   Pierwsza interpretacja wskazuje, że słowo to jest *czasownikiem, w trzeciej osobie liczby pojedynczej*, druga
   interpretacja wskazuje, że słowo to jest *przymiotnikiem (bardziej poprawnie zaimkiem dzierżawczym) rodzaju
   żeńskiego, w stopniu równym, w mianowniku liczby pojedynczej*, a ostatnia analogicznie, ale w *wołaczu*.
1. Pełny wykaz tagów używanych przez Morfeusza można znaleźć na stronie [NKJP](http://nkjp.pl/poliqarp/help/ense2.html).
1. Tagger morfosyntaktyczny jest narzędziem, które w sposób automatyczny ustala wartości kategorii gramatycznych dla
   słów w tekście oraz najczęściej dokonuje również lematyzacji słów. Przykładowo, w zdaniu "Ala ma kota" tagger
   powinien uznać, że słowo "ma" posiada formę podstawową "mieć" i jest czasownikiem zgodnie z opisem z p. 1.
1. Dzięki taggerowi uzyskujemy szczegółowy opis morfosyntaktyczny słów w tekście, co umożliwia np.
   wybór słów określonego typu (np. czasowników) lub posiadających określoną wartość innej cechy
   morfologicznej (np. rzeczowniki w *mianowniku*), budowanie bardziej złożonych narzędzi (np. parsera j.
   polskiego), wykorzystanie cech morfosyntaktycznych w alogorytmach uczenia maszynowego, itp.
