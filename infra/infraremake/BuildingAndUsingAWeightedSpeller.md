This document and the hfst speller setup in our infra was inspired by
[https://kitwiki.csc.fi/twiki/bin/view/KitWiki/HfstSpellCheckerBuildingTutorialFsmnlp2012]
(in English).

# Weights in spellers

## Weight classes

The weights should be restricted to signed integers in the range
`-32 000 - +32 000`. Weights are usually positive, with a higher weight
meaning less likelyhood of being relevant. Negative weights are usually used to
promote a candidate. The weights have no influence on whether a word is
accepted, only on the ranking of suggestions.

To make the interaction of the weights more predictable, we group types of
weights into classes of power of tens:

* **10^0 (0-9)**:        Tiny adjustments, nit-picking
* **10^1 (10-90)**:      Smaller adjustments
* **10^2 (100-900)**:    Regular edits
* **10^3 (1000-9000)**:  Heavy-handed weights
* **10^4 (10000-...)**:  Most heavy demotion - do not suggest. Although not yet
                   implemented, there will probably be a hard-coded limit of
                   20 000 - anything with this or a higher weight will **never**
                   be suggested.

It is possible to use fractions (the weighted hfst format allow any real as
weight), but in some applications only integers will be accepted, and weight
differences on the decimal scale will be ignored. It is thus best to stay in
the integer world for maximum compatibility with all tools.

Each higher weight class will usually override ordering based on weights from
lighter weight classes.

## Weight sources and total weight calculation

Sources:
* frequency corpus + default weight for unseen word forms
* tags
* morphological structure (compounding & derivation)
* error model edits

The actual weight for any given suggestion is the sum of all the weights.

----
**Old version below:**

# Korleis vi lagar forslag i hfst

1. feilskrive ord inn
1. vi bruker ein feilmodell til å generera mange ulike forslag
    1. kvart forslag får ei vekt ut i frå kva slags endringar vi gjer i høve til
   inn-ordet
1. alle forslag blir sjekka mot stavekontrollen
1. ikkjeeksisterande ord blir fjerna
1. resten av forslaga blir sorterte etter vekt
1. lista med forslag blir vist til brukaren

(I prinsipp fungerer alle stavekontrollar etter denne modellen. Det som skil dei
er teknologi og metodar for å generera og vekta forslaga.)

Døme: vi vil gå frå `gøølli` til `gööli`

I redigeringsavstand er det 3 operasjonar: `ø -> ö, ø -> ö, l -> 0`, dvs.
redigeringsavstand 3. Dette er for mykje for standardreglane, som berre dekkjer
redigeringsavstand 2, og vi vil ikkje få det rette forslaget. I staden kan vi
leggja til ein ny regel, motivert av det vi veit om skrivefeil i sørsamisk:

* `øø -> öö`, vekt 0.2

Attåt `l->0`-endringa med vekt 1.0 (standardvekt for standardreglane) blir
total vekt på forslaget `gööli` 1.2, og vi har redusert talet på operasjonar
til 2.

Utrekning av straffepoeng i vektinga av rettekandidatar:

```
    regel    vekt
    -------------
    øø -> öö 0.2
  + l  -> 0  1.0
-----------------
Samla vekt = 1.2
=================
```

Vi kan testa feilmodellen med denne kommandoen (`errmodel.default.hfst` er
namnet på den ferdige feilmodellfila, fila ligg i
`$GTLANG/tools/spellcheckers/fstbased/hfst/`):

```
hfst-lookup errmodel.default.hfst

eller - for å sjekka genererte forslag for eitt ord:

echo "gøølli" | hfst-lookup errmodel.default.hfst | less
```

Då får vi slike forslag:
```
gøølli  göölli  0.200195
gøølli  göølli  0.500000
gøølli  gøölli  0.500000
gøølli  gøøllï  0.500000
gøølli  gööllï  0.700195
gøølli  gööllï  0.700195
gøølli  gööllï  0.700195
gøølli  øølli   1.000000
...
gøølli  gööli   1.200195 # forslag nr 989 av i alt 873 169 forslag.
```

```
eksempler dublering:
luhte -> luhtte

eksempler forenkling:
buohkkat -> buohkat

eksempler substitusjon:
mañis -> maŋis

eksempler omkast:
geakti -> geatki
```

# Stavekontroll i nye infra

I mappa
`$GTLANG/tools/spellcheckers/fstbased/hfst/`

er det no to nye filer:

* `strings.default.txt`
* `words.default.txt`

I tillegg til:

* `editdist.default.txt`

## words.default.txt

Namnet på fila har tre delar, vi kan ha ei anna
fil `words.ocr.txt` for å rette ord i ocr.
Vi er ikkje der enno, men skal dit. `default` er
standardfeilmodellen

Denne fila inneheld heile ord (døme: *jih*)

```
jih:jïh 0.0
```

Formatet er:
```
ordinn:ordut<tab>vekt
```
Mellomrom i staden for tabulator gjev syntaksfeil.

Vekting: Talverdiar frå 0.0 og oppover.
Ord med lågt tal vinn.

## strings.default.txt

```
øø:öö   0.2
ää:ææ   0.2
```

Syntaksen er den same som for `words.default.txt`.
Fila skal innehalda bokstavsekvensar for typiske feil som ikkje elles blir retta
med den vanlege feilmodellen. Enkeltbokstav til annan enkeltbokstav kan ein gje
høgare prioritet i neste fil:

## editdist.default.txt

Denne fila inneheld ei liste over teikn og bokstavar som ein *ikkje* vil ha
med i standardfeilmodellen, og ei liste over bokstavpar som ein vil gje ei anna
vekt enn standardvekta på 1.0.

I lag med stavekontrolltransduceren blir denne fila brukt for å laga ein feilmodell for å retta alle feil med redigeringsavstand 1 og 2. Feilmodellen
blir laga slik:

1. hent ut alle symbol frå stavekontroll-fst-en
1. fjern alle symbol som er på meir enn eitt teikn
1. fjern alle enkeltteikn som er lista opp i fila `editdist.default.txt`
1. lag ein modell med redigeringsavstand 1 for symbola som vi no står att med
    1. for symbolpar/bokstavpar som er lista opp i `editdist.default.txt` med anna
   vekt, bruk vekta spesifisert der

## errmodel.default.hfst

Denne fila blir laga slik:

1. lag ein enkel feilmodell frå `editdist.default.txt`
1. slå i hop (union) med feilmodellen frå `strings.default.txt`
1. repeter fst-en frå førre punkt for å dekkja redigeringsavstand 2, med fri
  kombinasjon av enkel redigeringsavstand og meir spesifikke bokstavsekvensar
1. slå i hop (union) med feilmodellen frå `words.default.txt`

Ein kan testa feilmodellen slik det er skildra ovanfor.

# Kommandoer

Om ein står i katalogen `$GTLANG/tools/spellcheckers/fstbased/hfst/` og vil
testa ein nylaga stavekontroll:

```
voikkospell -p . -d sma-x-standard -s
```

Dersom ein har installert stavekontrollen med `sudo make install` er det nok
med:

```
voikkospell -d sma-x-standard -s
```

Det er lett å køyra ein heil tekst gjennom stavekontrollen:

```
$ echo "Gueli lij bueries" | preprocess | voikkospell -p . \
  -d sma-x-standard -s
W: Gueli
S: Gurli
S: Garli
S: Gulen
S: Vulli
S: Vuelie
C: lij
W: bueries
S: buerie
S: Dåeries
S: fuerie
S: tjueries
S: suepies
```

For meir informasjon om korleis ein bruker `voikkospell`, bruk kommandoen

```
man voikkospell
```
