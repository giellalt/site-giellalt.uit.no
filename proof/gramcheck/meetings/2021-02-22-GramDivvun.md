meattáhusmerken/GramDivvun
Duommá, Linda ja Ritva

11:05-12:00

* geahččat yaml teasttaid ja mo dat doibmet ja čilget dan Ritvai
    ** rádji juste njuolggadusii lea 75% precision
* Duommá muitala iežas ohcanstrategijjaid birra
    ** korpas smártta ohcan
    ** dál leat moaddelot duhát cealkaga
* GramDivvun váttisvuođat (Wordas)

* ođđa feailatyhppat:
    - yaml formahta:
    - "Árktalaš ráđi jođiheapmi lea dán vuoru dan dáfus hárvenaš {}¥{leamaš}, ahte ságadoalliriikka báiki lea guhtta jagi maŋŋálaga davviriikkaid hálddus. " #SYN MISSING: Ii fuomáš/máhte lasihit váldovearbba "leamaš": lea leamaš
    - lang-sme/tools/grammarcheckers/tests/
.yaml, notfixed.yaml

ps-011_arktalas_parlamentarihkkariid_coakkamis.correct.txt
--------------------------------

    1. Dánmárkku olgoáššiidministtar Lene Espersen muitalii čoakkáma álggus Dánmárkku árktalaš ráđi ságadoalli áigodaga ulbmiliin.
* NB!! FALSE POSITIVE: GramDivvun evttoha divodusaid sátnái "olgoáššiidministtar" vaikko DÁKKO II LEAT MEATTÁHUS!! (Dat lea čállon riekta!) --- disambigueren

    1. Lene Espersen muitalii čoakkáma álggus Dánmárkku árktalaš ráđi ságadoalli áigodaga ulbmiliin.
* CAP: Ii fuomáš divvut "Árktalaš ráđi": stuorra ovdabukstáva

    1. Árktalaš ráđi jođiheapmi lea dán vuoru dan dáfus hárvenaš, ahte ságadoalliriikka báiki lea guhtta jagi maŋŋálaga davviriikkaid hálddus.
* SYN MISSING: Ii fuomáš/máhte lasihit váldovearbba "leamaš": lea leamaš
--- Linda: dása lea váttis čállit njuolggadusa?

    1. Ságadoallivuohta sirdása Norggas Dánmárkui, mas dat sirdása Ruŧŧii jagi geahčen.
* NB!! FALSE POSITIVE: GramDivvun evttoha divodusaid sátnái "Ságadoallivuohta" vaikko DÁKKO II LEAT MEATTÁHUS!! (Dat lea čállon riekta!) #fixed - lasihuvvon

    1. Dánmárku sávvá gávdnat iežas jođihanáigodaga áigge čovdosa ođđa bissovaš dárkojeddjiid váldimii árktalaš ráđđái.
* CAP: Ii fuomáš divvut "Árktalaš ráđi": stuorra ovdabukstáva

    1. Eatnamat dego Kiinná, Lulli-Korea ja Japana ja organisašuvnnat dego Eurohpá uniovdna leat viggame árktalaš ráđi bissovaš dárkojeaddjin.
* Ii fuomáš divvut "Eurohpá Uniovdna", "Árktalaš ráđi": stuorra ovdabukstáva #fixed - lasihuvvon

    1. Válden ovdan dan, ahte mot árktalaš ráđđái sáhttá váldit dárkojeddjiid, mat eai gudnejahte olmmošvuoigatvuođaid ja álgoálbmogiid vuoigatvuođaid ja mot árktalaš ráđi váldegaskavuođaid, politihka ja olmmošvuoigatvuohtalinnjái geavalii dákkár ođđa dárkojeddjiid mielde.
* CAP: Ii fuomáš divvut "Árktalaš ráđđái", "árktalaš ráđi": stuorra ovdabukstáva
* KASUS: Ii fuomáš divvut "vuoigatvuođaid": vuoigatvuođaide - valeansa
* KASUS: Ii fuomáš divvut "politihka": politihkkii - valeansa

    1. Evttohin, ahte ođđa dárkojeaddjit eai galggale váldojuvvot mielde muđuid go dakkár organisašuvnnat, main lea gaskavuohta árktalaš guvlui dego EU ja Unesco.
* CAP: Ii fuomáš divvut propernoun/ACR "UNESCO": stuorra bustávat #fixed

    1. Dánmárkku olgoáššiidministtar dajai dása, ahte sii dollet geažos áigge ovdan olmmošriektegažaldagaid ja čujuhii maid Norgga olgoáššiidministtar Størei.
* KASUS: Ii fuomáš divvut "olgoáššiidministtar": olgoáššiidministtarii
* NB!! Evttoha boasttu divodusaid: olgogáššiidministtar, olgoáššuidministtar, jnv.   #fixed - lasihuvvon

    1. Ođđa lahtut galggale váldojuvvot danin, vai ságastallan árktalaš guovlluin ii sirdásivčče eará forumiidda muhto bisolii árktalaš ráđi kontevsttas.
* CAP: Ii fuomáš divvut "Árktalaš ráđi": stuorra ovdabukstáva
