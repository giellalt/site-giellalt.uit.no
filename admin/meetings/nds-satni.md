        1. NDS og satni.org - eitt eller to system?

Møte 3.6. med Børre, Chiara, Sjur, Trond

* stutt intro og samanfatning av historia
* skilje mellom framsida og baksida (nettlesar vs server/API)
* kor mange ordbokssider skal vi ha? Ja takk!
* NDS: rotete kode, mykje som ikkje er i bruk eller gamalt, alt er i Python2
* med felles bakside vil det vera to personar som kan arbeida med den koden
* tungt å jobba med andre sin kode
* fleire språkspesifikke ting i NDS-koden:
    - derivasjonar & samansette ord: lemmatisert i Python, slik at ein kan òg slå opp delane for leksikaliserte ord
    - Børre har byrja å jobba med lemmatisering

LOC:
* [backend](https://github.com/divvun/satni-backend) 1259 (python, django)
* [frontend](https://github.com/divvun/satni-frontend) 13978 (javascript, React)

API:
* GraphQL
* paradigme: smi-cgi no
* Korp-lenker: spørjing i Javascript
* kan enkelt søkja i berre ei ordbok
* kan enkelt søkja i spesifikke språk(par)

Bookmarklet:
* gamal kode (10k liner), gamle funksjonar
* bør skrivast på ny mot nytt API

Spørsmål:
* kor skal paradigma bli henta?
* kva med forfattarspesifikke ordbøker?

Konklusjon:
* felles kode så langt det er mogleg og rimeleg, særleg baksida
* ulike grensesnitt og delvis funksjonalitet
* Chiara og Børre begynner å se på koden i fellesskap i juli
