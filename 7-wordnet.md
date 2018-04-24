# Słowosieć (WordNet)

Celem zajęć jest zaznajomienie studentów ze Słowosiecią (WordNetem) - popularnym słownikiem zawierającym opis
semantyczny słów.

## Zadanie 

1. Zapoznaj się z [API Słowosieci](http://api.slowosiec.clarin-pl.eu/docs/index.html)
1. Zapoznaj się z [relacjami Słowosieci](http://nlp.pwr.wroc.pl/narzedzia-i-zasoby/narzedzia/disaster/25-wiedza/81-relacje-w-slowosieci)
1. Znajdź wszystkie znaczenia **rzeczownika** _szkoda_ oraz wymień ich synonimy (jeśli posiadają).
1. Znajdź domknięcie przechodnie relacji **hiperonimi** dla pierwszego znaczenia wyrażenia _wypadek drogowy_ i przedstaw
   je w postaci grafu skierowanego.
1. Znajdź bezpośrednie **hiponimy** rzeczownika _wypadek<sub>1</sub>_.
1. Znajdź **hiponimy drugiego rzędu** dla rzeczownika _wypadek<sub>1</sub>_.
1. Przedstaw w postaci grafu skierowanego (z etykietami dla krawędzi) relacje semantyczne pomiędzy następującymi grupami leksemów:
   1. szkoda<sub>2</sub>, strata<sub>1</sub>, uszczerbek<sub>1</sub>, szkoda majątkowa<sub>1</sub>, 
      uszczerbek na zdrowiu<sub>1</sub>, krzywda<sub>1</sub>, niesprawiedliwość<sub>1</sub>, nieszczęście<sub>2</sub>.
   1. wypadek<sub>1</sub>, wypadek komunikacyjny<sub>1</sub>, kolizja<sub>2</sub>, zderzenie<sub>2</sub>,
      kolizja drogowa<sub>1</sub>, bezkolizyjny<sub>2</sub>, katastrofa budowlana<sub>1</sub>, wypadek
      drogowy<sub>1</sub>.
1. Znajdź wartość miary pokrewieństwa semantycznego Leacocka-Chodorowa ftp://www-vhost.cs.toronto.edu/public_html/public_html/pub/gh/Budanitsky+Hirst-2001.pdf
   pomiędzy następującymi parami leksemów:
   1. szkoda<sub>2</sub> - wypadek<sub>1</sub>,
   1. kolizja<sub>2</sub> - szkoda majątkowa<sub>1</sub>,
   1. nieszczęście<sub>2</sub> - katastrofa budowlana<sub>1</sub>.

## Przydatne informacje

1. Słowosieć jest słownikiem semantycznym, który posiada dwie podstawowe cechy:
   1. wyróżnia **znaczenia słów**, tzn. _zamek_ w znaczeniu _budowli_ oraz _zamek_ w znaczeniu _urządzenia_ posiadają osobne
      wpisy w słowosieci,
   1. opisuje znaczenia słów za pomocą **relacji semantycznych**, np. _zamek<sub>1</sub>_ jest **hiponimem**
      _budynku<sub>1</sub>_, a _zamek<sub>2</sub>_ jest **hiperonimem** _zatrzasku<sub>2</sub>_.
1. Znaczenia słów w słowosieci są odróżniane za pomocą indeksu dolnego _zamek<sub>1</sub>_ oznacza pierwsze znaczenie, a
   _zamek<sub>2</sub>_ drugie znaczenie, itd.
1. Biblioteka [NLTK](https://www.nltk.org/) dla Pythona posiada [implementację](http://www.nltk.org/howto/wordnet.html) miary Leacocka-Chodorowa,
   ale nie posiada integracji z polską wersją WordNetu.
1. Biblioteka [pywnxml](https://github.com/ppke-nlpg/pywnxml) pozwala na wczytanie polskiego WrodNetu (po tym jak plik
   visdisc.xml zostanie poprawiony poprzez uzupełnienie tagu WNXML na początku oraz na końcu pliku). Nie posiada jednak
   implementacji miary Leacocka-Chodorowa.
1. Istnieje również dostęp do Słowosieci poprzez [webowe API](http://api.slowosiec.clarin-pl.eu/docs/index.html).
