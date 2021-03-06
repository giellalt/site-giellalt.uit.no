11.12.2015

Tilstede: Sjur, Francis, Trond, Kevin, Linda, Lene
#  Møte

Møte om ulike problem knytta til overgangen mellom fst og verda omkring (preprocess, lookup2cg, apertium)

* COPY/SUBSTITUTE
* V*
* Derivasjon + samansetjing
* MWE/

##  COPY/SUBSTITUTE

Apertium vil at input frå fst skal bli filtrert og ikkje lagt til. Når
ting blir **endra** i CG er det problematisk. Prinsipp: Vi vil ha morfologi
i fst og ikkje i cg.

### Praksis i dag:
* Vi endrar TV -> IV i CG (modulo kontekst), i staden for å ha det to gonger i FST.
* Namn er Sem/Plc i morfologien. Dei kan bli Sem/Sur avhengig av kontekst.

Eks.

SUBSTITUTE:TV-IV (V TV) (V IV) FAUXV (0 ("lávet") OR ("áigut")); #RemoveFromApertium

```
West-Virginia PLC ;
Ávvil PLCSUR ;

LEXICON PLCSUR
+Sem/Plc:
+Sem/Sur:
```
```
<e a="yr"><p><l>Avvevákkirášša<s n="np"/></l><r>Avvevákkirášša<s n="np"/></r></p><par n="PlcSur__np"/></e>
<e r="LR"><p><l>Avvil<s n="np"/><s n="sem_sur"/></l><r>Avvil<s n="np"/><s n="top"/></r></p><par n="__np"/></e>
<e><p><l>Avvil<s n="np"/><s n="sem_plc"/></l><r>Ivalo<s n="np"/><s n="top"/></r></p><par n="__np"/></e>
```

### Løysingar:
* TV/IV -> vi legg dei få verba det gjeld til to gonger, med kvar sin tagg
* Vi legg både Sem/Sur og Sem/Plc til i affixes/propernouns.lexc.
  I CG tar vi REMOVE Sem/Plc i staden for SUBSTITUTE Sem/Plc til Sem/Sur for å få korrekt tagg alt etter kontekst.

Dette har tre fordelar:
* Betre for Arpertium
* Mogleg å finjustere meir i FST-en
* Mogleg å bruke både SELECT og REMOVE på både Sem/Plc og Sem/Sur

### Hvem og når:
Lene, i neste uke


## Derivasjon: V*

Grammatikkontrollen kan ikkje bruke `lookup2cg`

Eksempel på regel som ikke fungerer i Apertium:

```REMOVE:derAdv (A* Adv) IF (0 LEX-ADV); ```

... *1 BARRIER V ...
(fordi V* Der/ N blir lese som verb)

```
sme$ echo 'ráhkisvuohta' | usme
ráhkisvuohta        ráhkis+A+Der/vuohta+N+Sg+Nom
ráhkisvuohta        ráhkisvuohta+N+Sg+Nom

sme$ echo 'ráhkisvuohta' | usme | lookup2cg
"<ráhkisvuohta>"
         "ráhkisvuohta" N Sg Nom
         "ráhkis" A* Der/vuohta N Sg Nom
```

ráhkisvuohta  ráhkis+A+Der/vuohta+N+Sg+Nom

### Løsning
Preprosesseringa legg til eit symbol til N, A, V før Der/..., som
i dag. Ikkje *, men eit anna symbol (som vi finn seinare).

CG: Fjern * tilslutt i CG med SUBSTITUTE

### Hvem og når:
Sjur, 2. uka i februar

##  Sammensetning

I dag:

lookup2cg:

```
"<mánábiila>"
         "máná#biila" N Sg Nom
"<mielkebiila>"
         "mielkebiila" N Sg Nom
```

Apertium:

```
$ echo mánábiila|apertium -f none -d . sme-nob-disam
"<mánábiila>"
        "biila" n sem_veh sg nom
                "mánná" n sem_hum cmp_sggen cmp

$ echo dáŋkabiila|apertium -f none -d . sme-nob-disam
"<dáŋkabiila>"
        "dáŋkabiila" n sem_veh sg nom
```

```
SELECT hjul IF (1 ("biila")); # vil matcha mánábiila

SELECT mat IF (1/1 ("is"));  # vil t.d. matcha vis neste ord er (dynamisk samansett) iskake
SELECT mat IF (1/* ("is"));  # vil t.d. matcha vis neste ord er (dynamisk samansett) iskaffekake eller kaffeiskake

REMOVE SUB:1 Cmp; # fjern alle samansette lesingar
```

vanskeleg: kan ikkje ha taggar frå underlesingar i SET som skal matcha på overlesingar:
```
"<mánábiila>"
        "biila" n sem_veh sg nom
                "mánná" n sem_hum cmp_sggen cmp
vil ikkje matcha SET foo = (sem_veh) + (cmp);
```

vanskeleg: kan ikkje ha krav på under- og overlesing *av same lesing* i same REMOVE-regel

```
"<ønskeliste>"
        "liste" N
                "ønske" V
        "liste" V
                "ønske" N
        "liste" N
                "ønske" N


Umogleg å laga reglar som fjernar V+N-samansetjingar (og prioriterer N+N):
REMOVE sub1=N + sub0=V IF (sub1=N + sub0=N); # ingen syntaks for dette enno
```

(frå [http://wiki.apertium.org/wiki/Subreadings#Wishlist] )

Dette diskuterte vi 19. mars:

[/lang/common/leksikalisering.html]

Vi gjennomfører dette i **februar**.

#  MWE og preprocess

Dette handlar om preprocess. Vi vil analysere og preprosessere i same steg.
Grammatikkontrollen vil kontrollere feilaktig særskriving (*sær skriving*).

Vi eksperimenterer med hfsts `pmatch`

```
sme$ usme
nr.
nr.        nr+N+ABBR+Nom
nr.        nr+N+ABBR+Gen
nr.        nr+N+ABBR+Attr
nr.        nr+N+ABBR+Acc

nr
nr        nr+N+ABBR+Nom
nr        nr+N+ABBR+Gen
nr        nr+N+ABBR+Attr
nr        nr+N+ABBR+Acc
```

```
sme$ echo 'Dat lei 2. girji.' | preprocess --abbr=tools/preprocess/abbr.txt
Dat
lei
2.
girji
.
sme$ echo 'Dat lei 2. Ja de bođiimet.' | preprocess --abbr=tools/preprocess/abbr.txt
Dat
lei
2
.
Ja
de
bođiimet
.
```

Dette kan bli betre med å ta med informasjon frå analysen.
