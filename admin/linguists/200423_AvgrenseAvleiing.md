Lingvistmøte smj & sme: overgenerering med derivasjonane

Tid: 23.4.2020

Til stades: Duommá, Inga, Lene, Sjur, Trond

# Konklusjon

## Konklusjon frå møtet
* Vi skal endre +Comp og +Superl til +DerN+Der/Comp+A (nummeret på DerN må vi sjå på)
* Vi bør observere og deretter forbetre 12345-grammatikken, og evt andre begrensninger
* måtar å avgrensa derivasjonane på:
    - Bare for normativ HFST: ved hjelp av Der12345-grammatikken
    - For all analyse/generering: ved hjelp av fortsettingsleksikoner
    - For all analyse/generering: ved hjelp av diakritiske flagg som også fungerer på desc (Px er løst slik)
    - Leksikalisere selve derivasjonen, feks. buoremusvuohta
    - Leksikalisere derivasjoner som er utgangspunkt for nye derivasjoner
* I smj endrer vi slik at på -dibme og -ahtes ikke får Comp og Superl (ahtes skal få nummer likt eller etter Comp/Superl)

## Steg framover

1. Legge Der/ til Comp/Superl
1. Deretter dei andre stega ovafor

Det finst [eit eige dokument for arbeidet framover](https://giellalt.github.io/lang/smi/AvgrenseAvleiing.html)

# Testing av (over)generering

Sjur har laget et verktøy som følger alle stier for lemmaer, slik at vi får lister med alle ordformer våre system produserer.

Kommando for "miehttse" og "bårråt" som kan kjøres i smj.

```
echo " ~\$[ M ] .o. @\"src/analyser-gt-norm.hfst\" .o. \$[ {miehttse} ] .o. ~\$[ \"+Cmp\" ]( \"#\" ) " | hfst-regexp2fst -E -F -f foma | hfst-fst2strings | tr ':' '\t' | grep "\tmiehttse\+" | grep "miehttse+" | sort -u | see

echo " ~\$[ B ] .o. @\"src/analyser-gt-norm.hfst\" .o. \$[ {bårråt} ] .o. ~\$[ \"+Cmp\" ]( \"#\" ) " | hfst-regexp2fst -E -F -f foma | hfst-fst2strings | tr ':' '\t' | sort -u | see
```

Dette scriptet  slepp gjennom former som ikkje blir akseptert av husmjNorm:

```
(base) tf-hsl-m0016:smj ttr000$ usmj
bårrådahttásappusjvuodada
bårrådahttásappusjvuodada	bårråt+Hom2+V+TV+Der/d+V+Der/NomAct+N+Der/ahtes+A+Comp+Der/Dimin+A+Sg+Attr+Der/vuota+N+Pl+Nom+PxDu2
...
(base) tf-hsl-m0016:smj ttr000$ usmjNorm
bårrådahttásappusjvuodada
bårrådahttásappusjvuodada	bårråt+Hom2+V+TV+Der/d+V+Der/NomAct+N+Der/ahtes+A+Comp+Der/Dimin+A+Sg+Attr+Der/vuota+N+Pl+Nom+PxDu2
...
(base) tf-hsl-m0016:smj ttr000$ husmj
bårrådahttásappusjvuodada
bårrådahttásappusjvuodada	bårråt+Hom2+V+TV+Der/d+V+Der/NomAct+N+Der/ahtes+A+Comp+Der/Dimin+A+Sg+Attr+Der/vuota+N+Abe
...
(base) tf-hsl-m0016:smj ttr000$ husmjNorm
bårrådahttásappusjvuodada
bårrådahttásappusjvuodada	bårrådahttásappusjvuodada+?	inf
```

Sjur har no ein betre versjon som tar omsyn til det, og ikkje inneheld desse formene (nedanfor)

#  Hvordan skal våre verktøy fungere?

Lage flest mulig ordformer, eller innskrenke etter bruk?

(Tidligere arbeid)[https://giellalt.github.io/lang/common/DerivationOverview.html]

Sammensetninger: heller leksikalisere

Komparinger som derivasjon?

##  Vi bør uansett gjøre litt vårrenskning. smj:

* Substantivene ser ganske greie ut.
    - Litt vel mye Px
    - Der/Car (-dibme) kompareres, dette syns jeg er rart:  fra nickel, lihkuheabbo	lihkku+N+Der/Car+A+Comp+v1+Sg+Nom
        - mánádabbo	mánná+N+Der/Car+A+Comp+Sg+Nom
        - mánádamos	mánná+N+Der/Car+A+Superl+Sg+Nom
    - Ingen +Der/lasj+Der/Vuohta,  men "mánálapvuohta"	mánná+N+Der/lasj+A+Comp+Attr+Der/vuota+N+Sg+Nom

*Adjektiv
**Komparering+vuohta er rart: Nuorapvuohta  fra nickel, nuoratvuohta	nuoratvuohta+?	inf

lexikalisert:

```
buoretvuohta
buoretvuohta	buoretvuohta+N+Sg+Nom	0,000000

buoremusvuohta
buoremusvuohta	buoremusvuohta+N+Sg+Nom	0,000000
```

* samme som nouns: nuoralapvuoda	nuorra+N+Der/lasj+A+Comp+Attr+Der/vuota+N+Pl+Nom nuoraletvuohta+?	inf
* samme som nouns dibme kompareres   nuorahetvuohta+?	inf

alla Marg ser ut til å väre utkommentert

-Spell har vi, exempel:

```
LEXICON LAS !!= * **@CODE@** from verbs: čirrolas, bealkálas etc
 :%> ATTR ;  ! To capture the attributive forms before going to N lexica.
+Use/-Spell: VUOHTA ;
```

eller ser Comp/Superlativ + Der/vuota til å väre utkommentert/ikke existerende:

```
LEXICON BUOREMUS !!= * **@CODE@**
 +Attr: K ; ! Attributive superlatives
 +Sg+Nom: K ;
###  JOHTOLAT0 ; !replaced to avoid compound
###  VUOHTA ;
 :a%> BUOREMUSSA- ;

LEXICON BUStem !!= * **@CODE@**
 ATTRCONT ;

LEXICON ATTRCONT  !!= * **@CODE@**  This lexicon is for forms with non-sub Attr, where we sub the rest.
                +Attr:  K                   ; ! Comp are also Attr.
   +Err/Orth+Cmp/Attr:  Rreal               ;
            +Err/Orth:  NAMAT               ; ! comp-only adj, not compound
       +Attr+Err/Orth:# NAMATLAGANLAGASCont ;
###           #+Err/Orth: NAMAT               ; ! comp-only adj
  +Use/Circ+Cmp/Attr+Cmp#:#   ALIT                ; ! both comp and independent adj !
```

* Verbene
    - får veldig mange rare ordformer
    - mye Px
    - For lulesamisk vil jeg legge til avledningen "bårån"

#  Bruk av verktøyet:

* Utvide yamltester slik at vi i større grad kan oppdage endringer vi gjør i fortsettelsesleksikoner
* GG?
* Andre bruksområder?

I smj har Inga sjekket inn tre kortere lister:

* fil-med-alle-ordformer-barrat.txt
* fil-med-alle-ordformer-miehttse.txt
* fil-med-alle-ordformer-nuorra.txt

I disse det bare Sg1, Nom og Com, og alle Px er fjernet. Det er da enklere å se gjennom listene.

Dette er eit resultat av Der12345-grammatikken, dvs. derivasjonar må vere av
typen Der(n) > Der(n+1), strengar som Der1 ... Der1 eller Der4 ... Der3 er ugrammatisk.
NB! Sjølv om dein tagg står under Der1 her (+Der1+Der/st) kan han vere tagga som
+Der2+Der/st i lexc, og dermed bli analysert som høyrande til kolonne 2 (for det leksikonet).

Sitat frå smj/src/fst/root.lexc (her ommøblert litt under diskusjonen):

```
+Der1           +Der2           +Der3            +Der4       +Der5       - positional tags

+Der/PassL                                                            VV - long passive láhpeduvvat
+Der/PassS                                                            VV - Short passive láhpput
+Der/PassD                                                            VV - dallat passive
+Der/adda                                                             VV
+Der/ahtja                                                            VV - only odd syll
+Der/ahttjá                                                           VV - only odd syll
+Der/Caus                                                             VV - previously Der/ahtte
+Der/alla                                                             VV
+Der/asste                                                            VV
+Der/d                                                                VV
+Der/dalla                                                            VV
+Der/dasste                                                           VV
+Der/l                                                                VV
+Der/ladda                                                            VV
+Der/lahtte                                                           VV
+Der/lasste                                                           VV
+Der/st                                                               VV
+Der/stahtte                                                          VV
+Der/stalla                                                           VV
+Der/stasste                                                          VV
+Der/tj                                                               VV
+Der/u/a/åd                                                           VV

+Der/lasj                                                             NN
+Der/Dimin                                                            NN

+Der/k                                                                NN / NA
+Der/r                                                                VN  - AA?

+Der/n                                                                NA
+Der/Car                                                              NA
+Der/ferjak                                                           NA
+Der/lasj                                                             NA
+Der/A                                                                NA
+Der/ravak                                                            NA
+Der/sasj                                                             NA
+Der/segak                                                            NA

##  !Der#2 tags - tags in second position
              +Der/dahtte                                             VV
              +Der/duhtte                                             VV
              +Der/NomAct                                             VN
			  +Der/Dimin                                              NN
              +Der/ahkes                                              VA
##  !Der#3 tags - tags in third position
                                +Der/duvva                            VV
                                +Der/InchL                            VV (previosuly Der/goahte)
                                +Der/mus                              VN
                                +Der/NomAg                            VN
                                +Der/dahka                            VN
                                +Der/NomAct                           VN   Realised in two different ways.
                                                                           This realisation is Der3. Outcommented
                                                                           to not define the tag twice, but kept
                                                                           here for documentation purposes.
                                +Der/lis                              VA

##  !Der#4 tags - tags in fourth position
                                                +Der/ahtes            NA ! only odd
##  !Der#5 tags - tags in fifth position
                                                             Der/AAdv NA AAdv, previously +Der/at
                                                             Der/vuotaNA AN
```

Oversy over Der-taggane i bårråt (etter Sjurs script nr. 2):

```
sme_test.txt |cut -f2|tr '+' '\n'|grep 'Der/'|sort|uniq -c|sort -nr
Tagg                Der-nummer
11857 Der/ahtes     4
7771 Der/vuota      5
6972 Der/NomAct     3
5828 Der/mus        3
1443 Der/InchL      3
 986 Der/stahtte    1
 986 Der/Caus
 980 Der/stasste
 980 Der/dasste
 980 Der/asste
 972 Der/stalla
 972 Der/dalla
 952 Der/PassL
 948 Der/dahtte
 868 Der/lis
 747 Der/ahkes
 698 Der/d
 696 Der/st
 493 Der/lahtte
 490 Der/lasste
 486 Der/ladda
 486 Der/alla
 486 Der/adda
 449 Der/NomAg
 444 Der/PassS
 382 Der/AAdv
 350 Der/l
 348 Der/u/a/åd
 296 Der/PassD
  93 Der/Dimin
```
