1. Møte 04.12.2020

kommando for å teste:
```sh
gramcheck-test.py -c test/grammarcheckers/real-NomAgIll-PrtSg3.yaml
```

 Regel                      |  FP |  FN |   TP |   TN | Kommentar | Yaml | ferdig
:-------------------------- | ---:| ---:| ----:| ----:| --------- | ---- | ------
real-Derh-Inf               |   0 |   9 |   70 |  165 | -- e ute  | x    | D
real-Derh-Inf-a-u           |  50 |  25 |   45 |  400 | -- e ute  | x    | D
real-ImprtPl2-PrsPl3        |  20 |   9 |   19 |    0 |           | x    |
real-ImprtPl2-Inf           |  35 | 200 |  480 |  300 |           | x    |
real-NomAgIll-PrtSg3        |  13 |  13 |   45 |  280 | -- e ute  |      | L
real-ImprtDu1-DerPassPrsSg3 |   0 |   0 |   10 |  200 |           | x    |
real-ImprtDu1-NSgNom        |   1 |  75 |   20 |  300 |           | x    |
real-PlNomPxSg2-PlNom       |  23 | 110 |   67 |  550 | -- e ute  | x    |
real-NSgIll-ASgNom          |  16 |  50 |   11 |  150 |           |      |
real-Ess-PrcPrf             |   1 | 100 |  470 |   11 | -- e ute  | x    | L jobbe med det
real-DerNomActSgGen-PrfPrc  |  50 | 200 |  150 |  800 | skal ut   | x    | D
real-DerNomActSgGen-PrsSg1  |  37 |  30 |   28 | 1450 | skal ut   | x    | D jobbar på det
real-ConNegII-PassPrsSg3    |   0 | 380 |    0 |  270 |           |      |
real-prs-pl3-not-imprt-pl2  |  40 |  90 |   65 |  325 |           |      |
real-Pl3-not-Inf            | 350 | 200 |  250 | 2000 |           |      |
real-ActioNom-PrfPrc        | 370 | 200 |  240 | 2000 |           |      |
real-PrtPl3-PrsSg3          | 550 | 500 | 2140 |  180 |           | x    |

    1. real-Derh-Inf.yaml

Total passes: 661, Total fails: 2, Total: 663
True positive: 171
True negative: 490
False positive 1: 0
False positive 2: 2
False negative 1: 0
False negative 2: 0
Precision: 98.8%
Recall: 100.0%
F₁ score: 99.4%

    1. real-NomAgIll-PrtSg3.yaml

* Total passes: 328, Total fails: 9, Total: 337
* True positive: 145
* True negative: 183
* False positive 1: 0
* False positive 2: 7
* False negative 1: 0
* False negative 2: 2
* Precision: 95.4%
* Recall: 98.6%
* F₁ score: 97.0%

    1. Om testinga

* ka brukte du for å regne ut TP, FP, FN? -- Google docs eller Terminalen?
- selve testfilan uten analyse (siden analysen ikke fungerte)
konklusjonen: yaml-testan burde være på plass for å teste

Yaml-tester til nå:
```
real-DerNomActSgGen-PrfPrc-notfixed.yaml
real-DerNomActSgGen-PrfPrc.yaml
real-DerNomActSgGen-PrsSg1.notfixed.yaml
real-DerNomActSgGen-PrsSg1.yaml
real-Derh-Inf.notfixed.yaml
real-Derh-Inf.yaml
real-Ess-PrfPrc.yaml
real-ImprtDu1-DerPassPrsSg3.notfixed.yaml
real-ImprtDu1-DerPassPrsSg3.yaml
real-ImprtDu1-NSgNom.notfixed.yaml
real-ImprtDu1-NSgNom.yaml
real-ImprtPl2-Inf.notfixed.yaml
real-ImprtPl2-Inf.yaml
real-ImprtPl2-PrsPl3.notfixed.yaml
real-ImprtPl2-PrsPl3.yaml
real-PlNomPxSg2-PlNom.yaml
real-PrtPl3-PrsSg3.notfixed.yaml
real-PrtPl3-PrsSg3.yaml
real-adnui-atnui.yaml
real-alddat.notfixed.yaml
real-johttui-johtui.yaml
syn-compound.notfixed.yaml
syn-compound.yaml
```

Ting som skal gjerast:

- Linda skal lage yaml filer for de typan som mangler
- Duommá jobber videre systematisk
- Sjur skal leggja inn påskeegg (`nuvviDspeller`)
	- har gjort, men har fått feil som eg ikkje forstår
- Sjur skal leggja inn støtte for yaml-testing
	- ikkje enno
- release: 10.12.2020

----------
Test 1/133: Sámediggi lea viidáseappot dovddahan ahte ii dárbbaš muddet gárduma vai ceavzilis rievssatmáddodat sihkkarastojuvvo, danne go dat rievssathivvodat mii bivdojuvvo gárdumis ii okto áitte rievssatmáddodaga, ja danne go gárdun viehka guhkás mudde iežas.
----------
[  1/133][FAIL fp2] : () => dovddahan:[] (real-Derh-Inf)
[  1/133][FAIL fp2] : () => gárdun:[gárdon] (real-DerNomActSgGen-PrtSg1)
Test 1 - Passes: 0, Fails: 2, Total: 2

----------
Test 2/133: Dan gal jáhkán roahkka oaččut dadjat, mojohallá son.
----------
[  2/133][FAIL fp2] : () => oaččut:[oažžut] (real-Derh-Inf)
Test 2 - Passes: 0, Fails: 1, Total: 1

----------
Test 3/133: Ovdal go studeantakoartta oaččut, fertet leat máksán lohkanbadjedivvaga ja dát máksu ferte leat registrerejuvvon.
----------
[  3/133][FAIL fp2] : () => oaččut:[oažžut] (real-Derh-Inf)
Test 3 - Passes: 0, Fails: 1, Total: 1

----------
Test 4/133: Jus fálaldaga dál oaččut, fertet gal geavahit vejolašvuođat.
----------
[  4/133][FAIL fp2] : () => oaččut:[oažžut] (real-Derh-Inf)
Test 4 - Passes: 0, Fails: 1, Total: 1

----------
Test 5/133: Muhtin barggu ovddas maid ovdal leat bargan oaččut dál bálkká.
----------
[  5/133][FAIL fp2] : () => oaččut:[oažžut] (real-Derh-Inf)
Test 5 - Passes: 0, Fails: 1, Total: 1

----------
Test 6/133: Dál sáhtát illudit bovdejumiid dihte maid oaččut.
----------
[  6/133][FAIL fp2] : () => oaččut:[oažžut] (real-Derh-Inf)
Test 6 - Passes: 0, Fails: 1, Total: 1

----------
Test 7/133: Don gii leat akto oaččut romantihkalaš áigodaga dán vahkku.
----------
[  7/133][FAIL fp2] : () => oaččut:[oažžut] (real-Derh-Inf)
Test 7 - Passes: 0, Fails: 1, Total: 1

----------
Test 8/133: Don álggat jurddašit ovddos guvlui, fuobmát ja oahpat makkár barggu galggat válljet.
----------
[  8/133][FAIL fp2] : () => galggat:[galgat] (real-Derh-Inf)
Test 8 - Passes: 0, Fails: 1, Total: 1

----------
Test 9/133: Oahppagirjji ja bargogirjji bargobihtáid barggadettiin oahpat geardduhit áššiid ja ávkkástallat dieđuiguin máŋgga láhkai.
----------
[  9/133][FAIL fp2] : () => oahpat:[oahppat] (real-Derh-Inf)
Test 9 - Passes: 0, Fails: 1, Total: 1

----------
Test 10/133: Váttisvuođaide mat leat leamaš gávnnat dál álkes čovdosa.
----------
[ 10/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 10 - Passes: 0, Fails: 1, Total: 1

----------
Test 11/133: Geahča gávnnat go moniid ja dihkiid sihkaldagas ja čohkumis.
----------
[ 11/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 11 - Passes: 0, Fails: 1, Total: 1

----------
Test 12/133: Ii Vars sáhte leat olles jierpmat.
----------
[ 12/133][FAIL fp2] : () => jierpmat:[jierbmat] (real-Derh-Inf)
Test 12 - Passes: 0, Fails: 1, Total: 1

----------
Test 13/133: Sølvi Myrskog guovllasta fárpalii ja oaidná oanehis juolggat ealgabeatnaga ja oahpes čeabetbátti ja duođašta leansmánnái, juo dat lea áhčis čeahpes ealgabeana.
----------
[ 13/133][FAIL fp2] : () => juolggat:[juolgat] (real-Derh-Inf)
Test 13 - Passes: 0, Fails: 1, Total: 1

----------
Test 14/133: Cubbot leat šođbes guhkes juolggat eallit man náhkki lea lávttas.
----------
[ 14/133][FAIL fp2] : () => juolggat:[juolgat] (real-Derh-Inf)
Test 14 - Passes: 0, Fails: 1, Total: 1

----------
Test 15/133: beasat njuolggat sisa.
----------
[ 15/133][FAIL fp2] : () => njuolggat:[njuolgat] (real-Derh-Inf)
Test 15 - Passes: 0, Fails: 1, Total: 1

----------
Test 16/133: Son muitala aitto leamaš ealu luhtte beannot mánu njuolggat, go daid muttuid lea hui ollu hommát ja barggut boazodoalus.
----------
[ 16/133][FAIL fp2] : () => njuolggat:[njuolgat] (real-Derh-Inf)
Test 16 - Passes: 0, Fails: 1, Total: 1

----------
Test 17/133: Heahtevástideaddji berre gulahallat riŋgejeaddjin sámegillii njuolggat.
----------
[ 17/133][FAIL fp2] : () => njuolggat:[njuolgat] (real-Derh-Inf)
Test 17 - Passes: 0, Fails: 1, Total: 1

----------
Test 18/133: Ovdal go čálát gearddut jietnadagaid // bustávaid maid mun logan nu ahte mun gulan leat go don gullan riekta.
----------
[ 18/133][FAIL fp2] : () => gearddut:[geardut] (real-Derh-Inf)
Test 18 - Passes: 0, Fails: 1, Total: 1

----------
Test 19/133: Earát suvvet dutnje dietnasa bargguid ovddas maid barggat sidjiide.
----------
[ 19/133][FAIL fp2] : () => barggat:[bargat] (real-Derh-Inf)
Test 19 - Passes: 0, Fails: 1, Total: 1

----------
Test 20/133: Dál fertet geahččalit oaidnit áššiid eará geahččanguovllus, dat maid dál barggat ii leat riekta.
----------
[ 20/133][PASS tn] : () => :[] ()
Test 20 - Passes: 1, Fails: 0, Total: 1

----------
Test 21/133: Muđui fertet fuolalaš dainna maid barggus barggat nu ahte it bargga boasttuvuođaid.
----------
[ 21/133][FAIL fp2] : () => barggat:[bargat] (real-Derh-Inf)
Test 21 - Passes: 0, Fails: 1, Total: 1

----------
Test 22/133: Váldooasis ožžot leat gárttat mielde mas oaidná gokko johttingeainnut, guottetbáikkit, gárddit ja eará leat.
----------
[ 22/133][FAIL fp2] : () => gárttat:[gártat] (real-Derh-Inf)
Test 22 - Passes: 0, Fails: 1, Total: 1

----------
Test 23/133: Fertet dušše vuosttas báli duostat // viimmat don ipmirdat // ii mihkkege šat nu guoskkat.
----------
[ 23/133][FAIL fp2] : () => duostat:[] (typo)
Test 23 - Passes: 0, Fails: 1, Total: 1

----------
Test 24/133: Maid dal juo vállježat de dovddat ahte eallin lea hui buorre skeaŋka.
----------
[ 24/133][FAIL fp2] : () => dovddat:[dovdat] (real-Derh-Inf)
Test 24 - Passes: 0, Fails: 1, Total: 1

----------
Test 25/133: Eanet dieđut bálkkašumis, historjjás ja movt don sáhtát árvalit evttohasaid gávnnat dáppe:
----------
[ 25/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 25 - Passes: 0, Fails: 1, Total: 1

----------
Test 26/133: Ollislaš geahčastaga juolluduvvon ohcamiin gávnnat dákko.
----------
[ 26/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 26 - Passes: 0, Fails: 1, Total: 1

----------
Test 27/133: Bálgá gávnnat deatnogáttis, Leavvajohnjálmmis.
----------
[ 27/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 27 - Passes: 0, Fails: 1, Total: 1

----------
Test 28/133: Eanet dieđuid doarjaga birra ja makkár njuolggadusat gusket juohkimii gávnnat Porsáŋggu gieldda ruovttusiidduin interneahtas.
----------
[ 28/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 28 - Passes: 0, Fails: 1, Total: 1

----------
Test 29/133: Doppe du goikui láddoža gávnnat ja roaŋkebeazis leat ártnat.
----------
[ 29/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 29 - Passes: 0, Fails: 1, Total: 1

----------
Test 30/133: Geahča maiddái Husbanken neahttasiidduid www.husbanken.no gos gávnnat ássandoarjaga rehkenastinmálle.
----------
[ 30/133][PASS tn] : () => :[] ()
Test 30 - Passes: 1, Fails: 0, Total: 1

----------
Test 31/133: Ii leat ge beare guhká ovdal gávnnat čovdosa erenoamáš váttis áššái.
----------
[ 31/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 31 - Passes: 0, Fails: 1, Total: 1

----------
Test 32/133: Dál ii leat ge guhká ovdal gávnnat čovdosa hui ártegis váttisvuhtii.
----------
[ 32/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 32 - Passes: 0, Fails: 1, Total: 1

----------
Test 33/133: Doppe leat olbmot geat sáhttet veahkehit du, jus dus leat váttisvuođat, ja jus eai sáhte veahkehit du, de muitalit dutnje gos gávnnat dan veahki maid justte don dárbbašat.
----------
[ 33/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
[ 33/133][FAIL fp2] : () => justte:[juste] (typo)
Test 33 - Passes: 0, Fails: 2, Total: 2

----------
Test 34/133: Vulle čujuha sániidis dien ja čujuha dainnage sániidis hal gávnnat guohtuma.
----------
[ 34/133][PASS tn] : () => :[] ()
Test 34 - Passes: 1, Fails: 0, Total: 1

----------
Test 35/133: Oasttit áhči mielde gávpogis mála!
----------
[ 35/133][PASS tn] : () => :[] ()
Test 35 - Passes: 1, Fails: 0, Total: 1

----------
Test 36/133: Bieđgguid miehtá dán nummira gávnnat maiddái historjjálaš dáhpáhusaid Sámis oanehaččat čálistuvvon.
----------
[ 36/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 36 - Passes: 0, Fails: 1, Total: 1

----------
Test 37/133: Go leat unnánat geat girdet dán geainnu, ja go áin lea vejolašvuohta seaivut Áltái árabut bearjadaga, de {heaittit}¢{heaitit} fálaldaga mii dál lea maŋŋit eahkes.
----------
[ 37/133][FAIL fn2] heaittit:heaitit (errorortreal) => :[] ()
Test 37 - Passes: 0, Fails: 1, Total: 1

----------
Test 38/133: Norgga njunušpolitihkkárat galggašedje sihtat Statoila {heaittit}¢{heaitit} doaimma guovllus, oaivvilda Beaska, Niillas, gii lea Norgga, Sámiid, Riikkasearvvi ja Sámiálbmot bellodaga Sámediggeáirras.
----------
[ 38/133][FAIL fp2] : () => Sámiálbmot:[Sámiálbmoga] (typo)
[ 38/133][FAIL fn2] heaittit:heaitit (errorortreal) => :[] ()
Test 38 - Passes: 0, Fails: 2, Total: 2

----------
Test 39/133: Mii galgat leat várrogasat vai eat váldde beare máŋga, ja ovttageardánis konklušuvnnaid dán áiggis go riikka lea morašdilis, muhto soames lohpádusaid gal {sáhtit}¢{sáhttit} dál eahkes juo lohpidit guhtet,guimmiidasamet.
----------
[ 39/133][FAIL fp2] : () => ovttageardánis:[ovttageardán] (typo)
[ 39/133][FAIL fp2] : () => ,guimmiidasamet:[, guimmiidasamet] (no-space-after-punct-mark)
[ 39/133][FAIL fn2] sáhtit:sáhttit (errorortreal) => :[] ()
Test 39 - Passes: 0, Fails: 3, Total: 3

----------
Test 40/133: Ii leat dušše erenomáš ahte sii besset togas {váccit}¢{vázzit}, muhto dát gávcci Áhkárvuona skuvlamáná besset measta ovddemužžii gitta ávvudit beaivvi.
----------
[ 40/133][FAIL fn2] váccit:vázzit (errorortreal) => :[] ()
Test 40 - Passes: 0, Fails: 1, Total: 1

----------
Test 41/133: Rektor Musta Anár skuvllas muitala ahte mánát galget bearjadat iđida ráidun {váccit}¢{vázzit} skuvllas Siidda museii.
----------
[ 41/133][FAIL fp2] : () => Anár:[Anára] (typo)
[ 41/133][FAIL fn2] váccit:vázzit (errorortreal) => :[] ()
Test 41 - Passes: 0, Fails: 2, Total: 2

----------
Test 42/133: Sii geat čohkkájit giddagasas besset kurssaid {váccit}¢{vázzit}, iežaset latnja, tv ja doaimmat, boarrásat fertejit čohkkát feaskáris ja besset unnimusat fitnat oktii olgun jahkái.
----------
[ 42/133][FAIL fn2] váccit:vázzit (errorortreal) => :[] ()
Test 42 - Passes: 0, Fails: 1, Total: 1

----------
Test 43/133: Guovddáš kemiija doahpagiid birra, maid modeallat čájehit, mo kemiijalaš ávdnasiidda bidjet namaid, geahččaleamit ja {oainnit}¢{oaidnit} mo kemiija geavahuvvo árgabeaivvis.
----------
[ 43/133][FAIL fn2] oainnit:oaidnit (errorortreal) => :[] ()
Test 43 - Passes: 0, Fails: 1, Total: 1

----------
Test 44/133: Du lagas fuolkkit Guovdageainnus goit besset du {oainnit}¢{oaidnit} dan beaivvi.
----------
[ 44/133][FAIL fn2] oainnit:oaidnit (errorortreal) => :[] ()
Test 44 - Passes: 0, Fails: 1, Total: 1

----------
Test 45/133: Vuoddji Isak Anders Eira protesterii, go oaivvildii vuoddji Mattis A. Eira rámšut ja {huikkit}¢{huikit} lobihemiid vuojedettiin.
----------
[ 45/133][FAIL fn2] huikkit:huikit (errorortreal) => :[] ()
Test 45 - Passes: 0, Fails: 1, Total: 1

----------
Test 46/133: Jeageleanan dulbmojuvvo ja guhttojuvvo, ja boazu láve dáhttut dálvet {garvvit}¢{garvvit} guovlluid gos lea guhttojuvvon bievlajagis.
----------
[ 46/133][FAIL fn2] garvvit:garvvit (errorortreal) => :[] ()
Test 46 - Passes: 0, Fails: 1, Total: 1

----------
Test 47/133: Sámediggi lea čađahan merkema dakko gokko lei linnjá dehe unnidit fievrrádusluotta negatiivvalaš váikkuhemiid ja maid {garvvit}¢{garvvit} vahágahttimis dáid.
----------
[ 47/133][FAIL fn2] garvvit:garvvit (errorortreal) => :[] ()
Test 47 - Passes: 0, Fails: 1, Total: 1

----------
Test 48/133: Lihkus ii leat uvdna jávkan ja eahkedis álgá visti {máizzat}¢{máizat} ja biktasat geahppánit joavkkus.
----------
[ 48/133][FAIL fn2] máizzat:máizat (errorortreal) => :[] ()
Test 48 - Passes: 0, Fails: 1, Total: 1

----------
Test 49/133: De viimmat bođii BlackSheeps lávddi ale maid álbmot ledje juo guhká vuordán beassat oaidnit ja álbmot álge huikit, biškut ja vel {deaškkut}¢{deaškut} gieđaid.
----------
[ 49/133][FAIL fn2] deaškkut:deaškut (errorortreal) => :[] ()
Test 49 - Passes: 0, Fails: 1, Total: 1

----------
Test 50/133: Mun Háliidivččen maid {guhkut}¢{guhkkut} nie go Hector.
----------
[ 50/133][FAIL fn2] guhkut:guhkkut (errorortreal) => :[] ()
Test 50 - Passes: 0, Fails: 1, Total: 1

----------
Test 51/133: Mun háliidan SKÁVŽŽÁID diktet {guhkut}¢{guhkkut}!
----------
[ 51/133][FAIL fn2] guhkut:guhkkut (errorortreal) => :[] ()
Test 51 - Passes: 0, Fails: 1, Total: 1

----------
Test 52/133: Dása dalle báhcá gažaldat gieldda stivrejeaddji politihkkárii, ahte leago son dákkár giellapolitihkka nu gohčoduvvon sámi oaivegávpoga njunuš áigu čađahit, gieldda váldogiellalágaid {rihkut}¢{rihkkut}, ja várra han eará lágaid ge?
----------
[ 52/133][FAIL fn2] rihkut:rihkkut (errorortreal) => :[] ()
Test 52 - Passes: 0, Fails: 1, Total: 1

----------
Test 53/133: Váldodoaimma áŋgiruššamiin lea mo ovdagáttut sáhttet olgguštit ja {rihkut}¢{rihkkut} olmmošvuoigatvuođaid.
----------
[ 53/133][FAIL fn2] rihkut:rihkkut (errorortreal) => :[] ()
Test 53 - Passes: 0, Fails: 1, Total: 1

----------
Test 54/133: FeFo miehtá ahte dat oažžu bisuhuvvot ja {čuoččut}¢{čuožžut} nugo juo lea ásahuvvon.
----------
[ 54/133][FAIL fn2] čuoččut:čuožžut (errorortreal) => :[] ()
Test 54 - Passes: 0, Fails: 1, Total: 1

----------
Test 55/133: Boaresvuohta dagahii ahte son ii šat nagodan {čuoččut}¢{čuožžut} go juolggit ledje visot bohtanan, Doaktárat leat muitalan ahte diabetes dahje sohkardávda dáidá leat okta sivain go ii šat nagodan lihkadit.
----------
[ 55/133][FAIL fn2] čuoččut:čuožžut (errorortreal) => :[] ()
Test 55 - Passes: 0, Fails: 1, Total: 1

----------
Test 56/133: Dat lea álki siiddus {čuoččut}¢{čuožžut} ja huikit ja jurddašit iežas máhttit buorebut dubmet, go son gii čiekčanšiljus lea.
----------
[ 56/133][FAIL fn2] čuoččut:čuožžut (errorortreal) => :[] ()
Test 56 - Passes: 0, Fails: 1, Total: 1

----------
Test 57/133: Oahpus oahppá ollu sámi kultuvra ja historjjá birra, muhto ii dušše dan – doppe oahppá maiddái movt galgá dakkár ovdánbuktimiid ráhkadit, movt galgá {vuoiŋŋat}¢{vuoigŋat} jus lea balus, movt čállit preassadieđáhusaid ja nu ain viidásit.
----------
[ 57/133][FAIL fp2] : () => ovdánbuktimiid:[ovdanbuktimiid] (typo)
[ 57/133][FAIL fn2] vuoiŋŋat:vuoigŋat (errorortreal) => :[] ()
Test 57 - Passes: 0, Fails: 2, Total: 2

----------
Test 58/133: Lea heittot go mánát fertejit eksosa čađa vázzit ja {vuoiŋŋat}¢{vuoigŋat}.
----------
[ 58/133][FAIL fn2] vuoiŋŋat:vuoigŋat (errorortreal) => :[] ()
Test 58 - Passes: 0, Fails: 1, Total: 1

----------
Test 59/133: Fuomáš maid dovdomearkkaid go geahpesvuolši feberiin, gosahat, raddebákčasat ja váttis {vuoiŋŋat}¢{vuoigŋat}.
----------
[ 59/133][FAIL fn2] vuoiŋŋat:vuoigŋat (errorortreal) => :[] ()
Test 59 - Passes: 0, Fails: 1, Total: 1

----------
Test 60/133: Máŋgii šattai skuvla mu friddjabáiki, doppe ožžon {vuoiŋŋat}¢{vuoigŋat} ja leat mánnán.
----------
[ 60/133][FAIL fn2] vuoiŋŋat:vuoigŋat (errorortreal) => :[] ()
Test 60 - Passes: 0, Fails: 1, Total: 1

----------
Test 61/133: Lei nu lossa áibmu ahte eat baljo sáhttán {vuoiŋŋat}¢{vuoigŋat}.
----------
[ 61/133][FAIL fn2] vuoiŋŋat:vuoigŋat (errorortreal) => :[] ()
Test 61 - Passes: 0, Fails: 1, Total: 1

----------
Test 62/133: Gilvaleddjiid mielas lea dát gilvvuid vearrámus hárjehallan go geađggi ferte doallat ratti vuostá ja dalle illá sáhttá {vuoiŋŋat}¢{vuoigŋat}.
----------
[ 62/133][FAIL fn2] vuoiŋŋat:vuoigŋat (errorortreal) => :[] ()
Test 62 - Passes: 0, Fails: 1, Total: 1

----------
Test 63/133: Vuojidettiin lea hui dehálaš dássedit čohkkát dahje {čuoččut}¢{čuožžut}.
----------
[ 63/133][FAIL fn2] čuoččut:čuožžut (errorortreal) => :[] ()
Test 63 - Passes: 0, Fails: 1, Total: 1

----------
Test 64/133: Jus dus lea skuhter, de soaitá buoret {čuoččut}¢{čuožžut} go vuoját vuostte luohkkái.
----------
[ 64/133][FAIL fn2] čuoččut:čuožžut (errorortreal) => :[] ()
Test 64 - Passes: 0, Fails: 1, Total: 1

----------
Test 65/133: Vaikke ievttá Ávviris biehttala vokalista Elling Borgersrud iežaset teavsttas {čuoččut}¢{čuožžut} ahte John-Reier lea goddon, muhto nu mot lávlla čilgejuvvo iežaset ruovttusiiddus, de lea álki áddet ahte dan guvlui geažuha joavkku iežaset oaiviliid.
----------
[ 65/133][FAIL fn2] čuoččut:čuožžut (errorortreal) => :[] ()
Test 65 - Passes: 0, Fails: 1, Total: 1

----------
Test 66/133: Nu ahte rokkit luottas leat sturron dan geasis, lohká Hætta, gii ii doaivvu buorre dušše {duokŋat}¢{duogŋat} luotta.
----------
[ 66/133][FAIL fn2] duokŋat:duogŋat (errorortreal) => :[] ()
Test 66 - Passes: 0, Fails: 1, Total: 1

----------
Test 67/133: Buohkat geat áigo boahtit {geahčat}¢{geahččat} fertejedje boahtit ovdalaš go doalut álge go Norgga Gonagas Harald bođi juste guđa áigge ja dat geat bohte su maŋis eai ožžon boahtit sisa, hirbmat dakkár fiinna doalut masa dábálaš sápmelaš ii leat hárjánan.
----------
[ 67/133][FAIL fn2] geahčat:geahččat (errorortreal) => :[] ()
Test 67 - Passes: 0, Fails: 1, Total: 1

----------
Test 68/133: Dure njuikii čuoččut ja dovddai ahte alggii šaddat balaheapmen.
----------
[ 68/133][FAIL fp2] : () => alggii:[álggii] (typo)
[ 68/133][FAIL fp2] : () => balaheapmen:[balaheamen, balaheapmin, balaheapmái] (typo)
Test 68 - Passes: 0, Fails: 2, Total: 2

----------
Test 69/133: Eambbo dieđuid gávnnat Sámedikki interneahtasiidduin; www.samediggi.no
----------
[ 69/133][FAIL fp2] : () => interneahtasiidduin:[interneahttasiidduin] (typo)
Test 69 - Passes: 0, Fails: 1, Total: 1

----------
Test 70/133: Oahpuid gávnnat dáppe http://samas.no/se/studier/v2015/http://samas.no/se/studier.
----------
[ 70/133][FAIL fp2] : () => :/:[: /] (no-space-after-punct-mark)
Test 70 - Passes: 0, Fails: 1, Total: 1

----------
Test 71/133: Helander mielde dákkár vuoiŋŋat leat: 1) jábmiidáimmu vuoiŋŋat, 2) deattán, 3) oainnekeahtes golgodávddat ja áicanvuloš golgodávddat, 4) golgodávddat olbmo hámis, 5) mánáhápmásaš febervuoigŋa, 6) biekka mielde johtti vuoiŋŋat, 7) ja nissonvuoigŋa, guhte johtiba ovtta fáru, 8) spárttuid váhnemat, 9) ihttomiid vuoiŋŋat, 10) galbmagálduid vuoiŋŋat ja 11) hávdeeatnama vuoiŋŋat.
----------
[ 71/133][PASS tn] : () => :[] ()
Test 71 - Passes: 1, Fails: 0, Total: 1

----------
Test 72/133: Sáhka su birra viidánii miehtá Syria, ja sii bukte su lusa buot buhcciid geain ledje buotlágán buozalvasat ja givssit, sin geain ledje bahá vuoiŋŋat, sin geain lei mánnováddu, ja lápmásiid, ja son buoridii sin.
----------
[ 72/133][PASS tn] : () => :[] ()
Test 72 - Passes: 1, Fails: 0, Total: 1

----------
Test 73/133: Mii eat áiggo dušše {bolttut}¢{boltut} bávttiid ja doaimmahit ruvkke, ja dastto de sáddet geđggiid olggobeallái suohkana gárvvistan dihte gávpemárkaniidda.
----------
[ 73/133][PASS tp] bolttut:boltut (errorortreal) => bolttut:[boltut] (real-Derh-Inf)
Test 73 - Passes: 1, Fails: 0, Total: 1

----------
Test 74/133: Mii eat áiggo dušše boltut bávttiid ja doaimmahit ruvkke, ja dastto de sáddet geđggiid olggobeallái suohkana gárvvistan dihte gávpemárkaniidda.
----------
[ 74/133][PASS tn] : () => :[] ()
Test 74 - Passes: 1, Fails: 0, Total: 1

----------
Test 75/133: Juos háliidat fáktádieđuid suohkana birra, gávnnat daid ja juos dovddat beroštumi bargagoahtit suohkanis, sávvamis sáhtit addit maid dieđuid rabas virggiid birra.
----------
[ 75/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
[ 75/133][FAIL fp2] : () => sáhtit:[sáhttit] (real-Derh-Inf)
Test 75 - Passes: 0, Fails: 2, Total: 2

----------
Test 76/133: Plagierenčuoččuhusat leat gomihuvvon máŋgga oktavuođas, omd. Nils Isak Eira, gean girjii mun lean čuoččuhuvvon plagieren, lea lohkan, ahte áššis ii leat mihkkege vuođuid plagierenčuoččuhusaide.  #čuoccuhuvvon!
----------
[ 76/133][FAIL fp2] : () => čuoccuhuvvon:[čuoččuhuvvon, cuoccuhuvvon] (typo)
Test 76 - Passes: 0, Fails: 1, Total: 1

----------
Test 77/133: Dál go aviissa logat de čurvot bajilčállagat gula ja oainne man birra mii čállit.
----------
[ 77/133][FAIL fp2] : () => bajilčállagat:[] (real-PlNomPxSg2-PlNom)
Test 77 - Passes: 0, Fails: 1, Total: 1

----------
Test 78/133: Mátkkoštallan oahpus logat dábálaš fága, muhto čiekŋudahtát mátkkoštallamii.
----------
[ 78/133][FAIL fp2] : () => Mátkkoštallan oahpus:[Mátkkoštallanoahpus] (msyn-compound)
Test 78 - Passes: 0, Fails: 1, Total: 1

----------
Test 79/133: Muhto jus logat dan plána, ”Suohkaniid ja fylkkasuohkaniid golut guovttegielalašvuhtii”, de boahtá ovdan ahte golut mat bohte oahpaheaddjebálkkáide ja mánáidgárdi suorgái eai leat váldon mielde raportas.
----------
[ 79/133][FAIL fp2] : () => raportas:[raporttas, raporta] (typo)
Test 79 - Passes: 0, Fails: 1, Total: 1

----------
Test 80/133: Doarjjastivra lea árvvoštallan ahte galgá go rievdadit SOF doarjjageavada, muhto ii gávnnat dan dárbun nu guhká go gávdnojit eará ruhtadaninstitušuvnnat mat sáhttet ruhtadit dien lágan doaimmaid.
----------
[ 80/133][FAIL fp2] : () => doarjjageavada:[doarjjageavadat, doarjatgeavada, doarjjageašvađa, doarjjagenavađa, doarjjageašađa] (typo)
Test 80 - Passes: 0, Fails: 1, Total: 1

----------
Test 81/133: Fágajoavku de árvvoštallá dan, ja de soaittát leat don, guhte čuoččut lávddis, go mii ávvudit sámi nationálabeaivvi.
----------
[ 81/133][PASS tn] : () => :[] ()
Test 81 - Passes: 1, Fails: 0, Total: 1

----------
Test 82/133: Don čuoččut dan dievá alde ja lea johka ja de lea stuorra stoalpu dákko mas lea čoarvi ja vel seainnit guovtte beale.
----------
[ 82/133][FAIL fp2] : () => guovtte:[guovtti] (typo)
Test 82 - Passes: 0, Fails: 1, Total: 1

----------
Test 83/133: Go čuoččut dies, ovddabealde lávddi, duháhiid olbmuid siste, bivastuvvan ja láktan, ja buohkat oktan Rogeriin lávlot , de áddet.
----------
[ 83/133][FAIL fp2] : () => lávlot ,:[lávlot,] (space-before-punct-mark)
Test 83 - Passes: 0, Fails: 1, Total: 1

----------
Test 84/133: Danin orru leamen nu go mii jáhkiimet, ahte biehttaleapmi mielddisbuktá heajut árvvoštallama go doarjun, muhto eat mii almmatge čuoččut ahte dat lea áidna sivva dan govvii maid mii dás oaidnit, mii čájeha makkár oaidnu guđesge lea fondii.
----------
[ 84/133][FAIL fp2] : () => doarjun:[doarjjun] (real-DerNomActSgGen-PrsSg1)
Test 84 - Passes: 0, Fails: 1, Total: 1

----------
Test 85/133: Daid stáhtaid gaskkas mat dál leat oččodeamen áigái ON-julggaštusa Eamiálbmotvuoigatvuođain, ii oktage šat čuoččut dan oainnu ahte eamiálbmogiin ii livčče iešmearridanvuoigatvuohta.
----------
[ 85/133][FAIL fp2] : () => stáhtaid:[stádaid] (typo)
Test 85 - Passes: 0, Fails: 1, Total: 1

----------
Test 86/133: Ovtta lihttái bálkkut láselihtiid, bohttaliid ja nu ain, mat leat ivdneláses ráhkaduvvon, nubbái lásegálvvu mii ii leat ivdneláses ráhkaduvvon, goalmmádii fas ruovdebovssaid, njealjádii aviissaid, bláđiid ja eará deaddiluvvon čállosiid, ja dál leat sirdán kontainera gosa mielkepáhkaid bálkkut Staoilii.
----------
[ 86/133][FAIL fp2] : () => Staoilii:[Statoilii] (typo)
Test 86 - Passes: 0, Fails: 1, Total: 1

----------
Test 87/133: Máŋggalágan vuoiŋŋat sáhtte árbevirolaš oainnu mielde dagahit olbmo buohccin.
----------
[ 87/133][FAIL fp2] : () => Máŋggalágan:[Máŋggalágana] (typo)
Test 87 - Passes: 0, Fails: 1, Total: 1

----------
Test 88/133: Dat buhtistii áimmu ja dávddat ja bahás vuoiŋŋat eai beassan ceaggat olbmuid eallima, dearvvašvuođa ja jápmima badjel.
----------
[ 88/133][FAIL fp2] : () => bahás:[bahá] (typo)
Test 88 - Passes: 0, Fails: 1, Total: 1

----------
Test 89/133: Go bahás vuoiŋŋat vahágahttet sámiid meahccebivddu ja guolásteami ja Baján addá daidda ánssášuvvon ráŋggáštusa, bálvalit olbmot su ovdal earáid (ipmiliid).
----------
[ 89/133][PASS tn] : () => :[] ()
Test 89 - Passes: 1, Fails: 0, Total: 1

----------
Test 90/133: Maiddái su ovddeš eallimat ja vuoiŋŋat leat miellagiddevaččat buddhisttaide, go dat muitalit mo son ráhkkanii šaddat Buddhan.
----------
[ 90/133][FAIL fp2] : () => Buddhan:[] (typo)
Test 90 - Passes: 0, Fails: 1, Total: 1

----------
Test 91/133: Dat buhtistii áimmu vai dávddat ja bahás vuoiŋŋat eai beassan cieggat olbmo rupmašii.
----------
[ 91/133][FAIL fp2] : () => bahás:[bahá] (typo)
Test 91 - Passes: 0, Fails: 1, Total: 1

----------
Test 92/133: 6. Animašuvdnafilmmas bohtet dávjá ovdan sirkumpolára eamiálbmogiid luondduoskkoldatlaš vuoiŋŋat, rituálat ja luonddunjuolggadusat.
----------
[ 92/133][FAIL fp2] : () => rituálat:[] (real-PlNomPxSg2-PlNom)
Test 92 - Passes: 0, Fails: 1, Total: 1

----------
Test 93/133: Ipmil hálddaša buot, muhto bahás vuoiŋŋat sáhttet váldit olbmuid iežaset háldui.
----------
[ 93/133][FAIL fp2] : () => bahás:[bahá] (typo)
Test 93 - Passes: 0, Fails: 1, Total: 1

----------
Test 94/133: Dát leat beargalagaid vuoiŋŋat mat dahket oavdumearkkaid.
----------
[ 94/133][FAIL fp2] : () => beargalagaid:[] (typo)
Test 94 - Passes: 0, Fails: 1, Total: 1

----------
Test 95/133: Stuorra ivdnegovvosiid fáddá leat dán viiddis eatnandieđalaš guovllu sierra álgoálbmogiid luondduipmilat ja - "vuoiŋŋat."
----------
[ 95/133][FAIL fp2] : () => viiddis:[viiddes] (typo)
Test 95 - Passes: 0, Fails: 1, Total: 1

----------
Test 96/133: Ja de ledje mearkkat: mášohis geasuheapmi Davviguovllu musihkkii, buolli sáhkkiivuohta oaidnit ja dovdat daid viiddis rabas Skandinavia árktalaš guvlui, dilihisvuohta galledit ja juo, máttuid vuoiŋŋat vurje mu ja gikte mu davás.
----------
[ 96/133][FAIL fp2] : () => viiddis:[viiddes] (typo)
Test 96 - Passes: 0, Fails: 1, Total: 1

----------
Test 97/133: Dás oidno ahte eaiggátdili eai šat čuoččut dárbbašeamen leat almennetlágan dilálašvuohtan, go eaiggátvuođadilli eatnamii orru adnomin sierra áššiin.
----------
[ 97/133][FAIL fp2] : () => almennetlágan:[] (typo)
Test 97 - Passes: 0, Fails: 1, Total: 1

----------
Test 98/133: Deattuhit ferte ahte Sámediggi ii čuoččut ahte dát vuoigatvuođat gullet sámiide okto, muhto go sámit lea sierra álbmot de das leat dánlágan vuoigatvuođat.
----------
[ 98/133][FAIL fp2] : () => Deattuhit:[Deattohabbo, Deattohat, Deattoheabbo, Deattohet, Deattohit, Deattohut] (typo)
[ 98/133][FAIL fp2] : () => dánlágan:[dánlágana] (typo)
Test 98 - Passes: 0, Fails: 2, Total: 2

----------
Test 99/133: Jos it máhte mo fanas sugadettiin dan dahkat, de oahpat dás.
----------
[ 99/133][FAIL fp2] : () => oahpat:[oahppat] (real-Derh-Inf)
Test 99 - Passes: 0, Fails: 1, Total: 1

----------
Test 100/133: www.hvakostertannlegen.no lea siidu gos oainnát man olu šattat máksit bátnedoaktárii go iskkat leat go dus ráiggit bániin.
----------
[100/133][FAIL fp2] : () => siidu:[] (typo)
Test 100 - Passes: 0, Fails: 1, Total: 1

----------
Test 101/133: Barggu dáfus lea identitehta huksen hui movttiidahtti oassi, ja don liikot njunuš bargui mas oaččut rámi.
----------
[101/133][PASS tn] : () => :[] ()
Test 101 - Passes: 1, Fails: 0, Total: 1

----------
Test 102/133: Bálgá guoras gávnnat čieža sierra fáttá divtta čullojuvvon Kuru granihttii.
----------
[102/133][FAIL fp2] : () => gávnnat:[gávdnat] (real-Derh-Inf)
Test 102 - Passes: 0, Fails: 1, Total: 1

----------
Test 103/133: Jus álo bidjá rihku buot njuolggadusaid mielde, de sáhttet šaddat beare olu rihkut.
----------
[103/133][PASS tn] : () => :[] ()
Test 103 - Passes: 1, Fails: 0, Total: 1

----------
Test 104/133: leat hui viiddis válddit ja ahte mearridanváldi uhccán lea sirdon báikkálaš vuolit orgánaide.
----------
[104/133][FAIL fp2] : () => viiddis:[viiddes] (typo)
Test 104 - Passes: 0, Fails: 1, Total: 1

----------
Test 105/133: Muhto danne go sii jáhkket ahte mii leat čužžon hui lahka gaskkaneamet ja dát šattai ge dego álbmotmiellačájáhussan.
----------
[105/133][FAIL fp2] : () => gaskkaneamet:[gaskaneamet] (typo)
Test 105 - Passes: 0, Fails: 1, Total: 1

----------
Test 106/133: Mannan gaskavahku mearridii Anára gielddastivrra ahte eai heaittit Menesjávrri skuvlla Anára gielddas.
----------
[106/133][FAIL fp2] : () => Menesjávrri:[Menešjávrri] (typo)
Test 106 - Passes: 0, Fails: 1, Total: 1

----------
Test 107/133: Gullabehtetgo lágideaddjit, allet heaittit Sámi,Grand,Prix, lávlestii vel láidesteaddji.
----------
[107/133][FAIL fp2] : () => ,Grand,Prix:[, Grand,Prix] (no-space-after-punct-mark)
[107/133][FAIL fp2] : () => ,Prix:[, Prix] (no-space-after-punct-mark)
Test 107 - Passes: 0, Fails: 2, Total: 2

----------
Test 108/133: Čiegarbivdun gohčoduvvui bivdovuohki mas olbmot gille gielaid čiegarluottaid ala masa gottit de darvánedje.
----------
[108/133][FAIL fp2] : () => čiegarluottaid:[] (typo)
Test 108 - Passes: 0, Fails: 1, Total: 1

----------
Test 109/133: Hardangerduoddaris Møsvatn ja Kaljord gaskkas Telemárkkus lei earenoamáš garra bajándálki bearjadaga, ja álddagas sáhttá dagahan ahte gottit čomistedje.
----------
[109/133][PASS tn] : () => :[] ()
Test 109 - Passes: 1, Fails: 0, Total: 1

----------
Test 110/133: Svalbárddas jávkkai goddi masá alfárot bivddu dihte, muhto muhtin áigodaga ráfáiduhttimis leat fas gottit laskan ja lohku lea dál 15000 heakka.
----------
[110/133][FAIL fp2] : () => alfárot:[álfárot, álfárut] (typo)
Test 110 - Passes: 0, Fails: 1, Total: 1

----------
Test 111/133: Dalle sálašmearri bázii rájálažžan, daningo maŋis boahtti gottit besse rokkiid dievadettiin dorvvolaččat rokkiid badjel.
----------
[111/133][FAIL fp2] : () => boahtti:[boahtte] (typo)
Test 111 - Passes: 0, Fails: 1, Total: 1

----------
Test 112/133: De gullogohte lávkkit, ja garvvit gehčče dušše dan guvlui gos gulloje.
----------
[112/133][FAIL fp2] : () => garvvit:[gárvvit] (typo)
Test 112 - Passes: 0, Fails: 1, Total: 1

----------
Test 113/133: Diekkár stuorahat mat ledje viežžan dien golbmasa reagas, čužžo ja váruhe ahte unnit garvvit barge.
----------
[113/133][FAIL fp2] : () => garvvit:[gárvvit] (typo)
Test 113 - Passes: 0, Fails: 1, Total: 1

----------
Test 114/133: Ovttastahtton našuvnnaid earenomáš rapportevra álgoálbmot olmmošvuoigatvuođaid hárrái, James Anaya, cealkagat sápmelaččaid diliid birra ja erenomašit ahte mearrasápmelaččat berrejit oažžut vuoigatvuođaid, lea dego {vuoittit}¢{vuoitit} golli lohká sámedikki presideantta Egil Olli.
----------
[114/133][PASS tp] vuoittit:vuoitit (errorortreal) => vuoittit:[vuoitit] (real-Derh-Inf)
[114/133][FAIL fp2] : () => rapportevra:[raportevrra] (typo)
[114/133][FAIL fp2] : () => álgoálbmot olmmošvuoigatvuođaid:[álgoálbmotolmmošvuoigatvuođaid] (msyn-compound)
[114/133][FAIL fp2] : () => erenomašit:[erenomážit] (typo)
Test 114 - Passes: 1, Fails: 3, Total: 4

----------
Test 115/133: Lea sápmelačča luonddu vuostá {oasttit}¢{oastit} luopmániid, sarridiid ja joŋaid.
----------
[115/133][PASS tp] oasttit:oastit (errorortreal) => oasttit:[oastit] (real-oastit)
Test 115 - Passes: 1, Fails: 0, Total: 1

----------
Test 116/133: Danin fertii 1800-logu Davvi-Norgga stuorámus industrifitnodat, Gávvuona veaikedoaimmahat, Englánddas {oasttit}¢{oastit} báktečina.
----------
[116/133][PASS tp] oasttit:oastit (errorortreal) => oasttit:[oastit] (real-oastit)
Test 116 - Passes: 1, Fails: 0, Total: 1

----------
Test 117/133: Vuoi rávki, go lea vajálduhttán ránuid {savnnjit}¢{savdnjit}, jáhkán mun álggán dainna dál.
----------
[117/133][PASS tp] savnnjit:savdnjit (errorortreal) => savnnjit:[savdnjit] (real-Derh-Inf)
Test 117 - Passes: 1, Fails: 0, Total: 1

----------
Test 118/133: Diibmá juo lei heajos jahki, ja dat gii áigu luopmániid dán geasi gávdnat váljjebuš ferte leat gillil {váccit}¢{vázzit}, lohká Áillu Jovnna.
----------
[118/133][PASS tp] váccit:vázzit (errorortreal) => váccit:[vázzit] (real-Derh-Inf)
[118/133][FAIL fp2] : () => váljjebuš:[válljemuš] (typo)
Test 118 - Passes: 1, Fails: 1, Total: 2

----------
Test 119/133: Sii leat čeahpi riŋget midjiide ja badjeolbmuide jus gávdnet jápma dahje roasmmohuvvan elliid, vaikke fertejit guhkás {váccit}¢{vázzit} ovdal olahit riŋget.
----------
[119/133][FAIL fn2] váccit:vázzit (errorortreal) => :[] ()
Test 119 - Passes: 0, Fails: 1, Total: 1

----------
Test 120/133: Muotka ii loga {sáhtit}¢{sáhttit} buohtastahttit sámi mánáiguin dán áššis, go sámi mánát leat bajásšaddan riikkas ja dávjá ohppet dárogiela seamma bures go sámegiela.
----------
[120/133][PASS tp] sáhtit:sáhttit (errorortreal) => sáhtit:[sáhttit] (real-Derh-Inf)
Test 120 - Passes: 1, Fails: 0, Total: 1

----------
Test 121/133: Norgga Sámiid Riikkasearvvi ja Sámiálbmot bellodaga Sámediggeáirras oaivvilda, ahte stáhta galggašii sihtat Statoila {heaittit}¢{heaitit} doaimma Alberta guovllus Kanadas.
----------
[121/133][PASS tp] heaittit:heaitit (errorortreal) => heaittit:[heaitit] (real-Derh-Inf)
[121/133][FAIL fp2] : () => Sámiálbmot:[Sámiálbmoga] (typo)
Test 121 - Passes: 1, Fails: 1, Total: 2

----------
Test 122/133: Diet vuordinbáiki lea heakkavárálaš, dat lea gasku mohki ja das oažžu vuodjit goittotge 80 km fártta, das eai leat seavndjadin čuovggat, nu soai eaba duostta bidjat mánáid {čuoččut}¢{čuožžut} dohko ja sii eai oba iežage duostta dan dahkat, muitala Scheie Anti.
----------
[122/133][PASS tp] čuoččut:čuožžut (errorortreal) => čuoččut:[čuožžut] (real-Derh-Inf)
[122/133][FAIL fp2] : () => seavndjadin:[seavdnjadin, seavnnjodin, seavnnjudin] (typo)
Test 122 - Passes: 1, Fails: 1, Total: 2

----------
Test 123/133: Dallego mun ledjen dien barggus, de mihtidin daid maid dárbbašin mihttoglásas ja firron dan amalgaman, maid mun geigejin bátnedoaktárii dárbbu mielde vai sáhtii báni {duokŋat}¢{duogŋat}, čilge Signe.
----------
[123/133][PASS tp] duokŋat:duogŋat (errorortreal) => duokŋat:[duogŋat] (real-Derh-Inf)
[123/133][FAIL fp2] : () => amalgaman:[amalgáman] (typo)
Test 123 - Passes: 1, Fails: 1, Total: 2

----------
Test 124/133: Jus šaddet olu ráiggit maid šaddá {duokŋat}¢{duogŋat}, de gal eai biste gápmagat nu guhká, lohká duojár Karen Máret Sara.
----------
[124/133][PASS tp] duokŋat:duogŋat (errorortreal) => duokŋat:[duogŋat] (real-Derh-Inf)
Test 124 - Passes: 1, Fails: 0, Total: 1

----------
Test 125/133: 13-jahkásaš Máijá Riitá Anti Rasmus lea eatnistis jearran čábbát ahte iigo son sáhtáše {duokŋat}¢{duogŋat} buvssaid maid son ieš lea ráigan, danne go duokŋaduvvon buvssat leat dál oalle modearnnat.
----------
[125/133][PASS tp] duokŋat:duogŋat (errorortreal) => duokŋat:[duogŋat] (real-Derh-Inf)
[125/133][FAIL fp2] : () => modearnnat:[modeartnat] (typo)
Test 125 - Passes: 1, Fails: 1, Total: 2

----------
Test 126/133: Mii leat ferten dan geahččalit {duokŋat}¢{duogŋat} vaikkuhanbarggusteamet, muhto ii leat álki dávistit Norgga stáhtahálddahussii čielggadannávccaid, gelbbolašvuođaviidodaga ja váikkuhanfámu ektui.
----------
[126/133][PASS tp] duokŋat:duogŋat (errorortreal) => duokŋat:[duogŋat] (real-Derh-Inf)
[126/133][FAIL fp2] : () => vaikkuhanbarggusteamet:[váikkuhanbarggusteamet] (typo)
Test 126 - Passes: 1, Fails: 1, Total: 2

----------
Test 127/133: Dán jagi bođii ge Olsen njealjádin, bures dahkkon go guktii lei ferten {duokŋat}¢{duogŋat} juvllaid.
----------
[127/133][PASS tp] duokŋat:duogŋat (errorortreal) => duokŋat:[duogŋat] (real-Derh-Inf)
Test 127 - Passes: 1, Fails: 0, Total: 1

----------
Test 128/133: Kárášjohkalaš viđa máná eadni Aud Scheie Anti lohká sudno vásihit geainnu Badjenjárgga bokte nu váralažžan, ahte eaba duostá mánáid diktit {čuoččut}¢{čuožžut} geaidnoguoras man gohččoda heaggaváralažžan.
----------
[128/133][PASS tp] čuoččut:čuožžut (errorortreal) => čuoččut:[čuožžut] (real-Derh-Inf)
[128/133][FAIL fp2] : () => gohččoda:[gohčoda, gohččojuvvoda] (typo)
Test 128 - Passes: 1, Fails: 1, Total: 2

----------
Test 129/133: Birasgáhttendepartemeanta oaivvildit ahte kulturmuitohoidu ii berre {čuoččut}¢{čuožžut} ealahusovdáneapmi badjel dan áššis, ja leat dohkkehan ahte luotta huksejuvvojit.
----------
[129/133][PASS tp] čuoččut:čuožžut (errorortreal) => čuoččut:[čuožžut] (real-Derh-Inf)
[129/133][FAIL fp2] : () => ealahusovdáneapmi:[ealáhusovdáneapmi] (typo)
Test 129 - Passes: 1, Fails: 1, Total: 2

----------
Test 130/133: Jus álo bidjá rihku buot njuolggadusaid mielde, de sáhttet šaddat beare olu rihkut – ja dat leat unohas oaidnit, omd. dán cealkagis:
----------
[130/133][FAIL fp2] : () => rihkut:[rihkkut] (real-Derh-Inf)
Test 130 - Passes: 0, Fails: 1, Total: 1

----------
Test 131/133: Hardangerduoddaris Møsvatn ja Kaljprd gaskkas Telemárkkus lei earenoamáš garra bajándálki bearjadaga, ja álddagas sáhttá dagahan ahte gottit čomistedje.
----------
[131/133][FAIL fp2] : () => Kaljprd:[Kaljord] (typo)
Test 131 - Passes: 0, Fails: 1, Total: 1

----------
Test 132/133: Suohkanstivrra joatkán ain bargat Dáloniid Listu prográmma vuođul, muhto oainnán lobálažžan {čuoččut}¢{čuožžut} Árjja listtus, go Dáloniid Listtus ii dáidde menestuvvat listu Ávjovári válgabiires, dadjá Hans Isak Olsen.
----------
[132/133][PASS tp] čuoččut:čuožžut (errorortreal) => čuoččut:[čuožžut] (real-Derh-Inf)
[132/133][FAIL fp2] : () => válgabiires:[válgabiirres] (typo)
Test 132 - Passes: 1, Fails: 1, Total: 2

----------
Test 133/133: Scherpf muitala ahte go lea dušše okta statueahtta, de leat sii gávnnahan ahte bálkkašupmi berre {čuoččut}¢{čuožžut} Beaivváža boarsttus Guovdageainnu kulturviesus.
----------
[133/133][PASS tp] čuoččut:čuožžut (errorortreal) => čuoččut:[čuožžut] (real-Derh-Inf)
[133/133][FAIL fp2] : () => statueahtta:[stafeahtta] (typo)
Test 133 - Passes: 1, Fails: 1, Total: 2

Total passes: 30, Total fails: 127, Total: 157
True positive: 18
True negative: 12
False positive 1: 0
False positive 2: 95
False negative 1: 0
False negative 2: 32
Precision: 15.9%
Recall: 36.0%
F₁ score: 22.1%
