Lingvistmøte smj & sme om tagging og begrensning av derivasjoner

Til stede: Inga, Sjur, Linda, Lene, Thomas, Trond

#  Tagger

##  Gram/xxx

Hvilke Gram-tagger trenger vi, og harmonisering mellom samiske språk
```
I smj:
  +Gram/Comp      !!≈ * @CODE@ = Inherent comp, lexicalized derivation
  +Gram/Superl    !!≈ * @CODE@ = Inherent superl, lexicalized derivation
  +Gram/Dimin     !!≈ * @CODE@ = Inherent diminutive, lexicalized derivation
  +Gram/NomAg     !!≈ * @CODE@ = Inherent Actor Noun From Verb - Nomen Agentis, lexicalized derivation
  +Gram/r         !!≈ * @CODE@ = Inherent -r derivation. guollit-guollár
  +Gram/NomAct    !!≈ * @CODE@ = Inherent Actio Noun From Verb - Nomen Actionis, lexicalized derivation
  +Gram/NomInstr  !!≈ * @CODE@ = Inherent Intsrumental noun From Verb, Nomen instrumentalis,lexicalized derivation
  +Gram/TAbbr     !!≈ ; @CODE@ : Transitive abbreviation (it needs an argument)
  +Gram/NoAbbr    !!≈ ; @CODE@ : Intransitive abbreviations that are homonymous
  +Gram/TNumAbbr  !!≈ ; @CODE@ : Transitive abbreviation if the following
  +Gram/NumNoAbbr !!≈ ; @CODE@ : Transitive abbreviations for which numerals
  +Gram/TIAbbr    !!≈ ; @CODE@ : Both transitive and intransitive abbreviation
  +Gram/IAbbr     !!≈ ; @CODE@ : Intransitive abbreviation (it takes no argument)
  +Gram/3syll     !!≈ ; @CODE@ : trisyllabic verbs
  +Gram/SentInit  !!≈ ; @CODE@ : copula verb le-
 ```

Bør også disse få Gram:
*  +Gram/IV
*  +Gram/TV
i staden for +TV og +IV som no, jf grønlandsk.

`+Gram/xxx` blir brukt òg for leksikaliserte deriverte ord som ein parallell til dynamisk derivasjon.

Alle Gram-taggar er **alltid** valfrie ved generering, men ikke alle skal være valgfri for dict- og MT-generering, f.eks. +Gram/NomAg

smj: politihkkár+N+Gram/r+Sg+Nom, tydelig for brukere at dette er en avledning av det ikke mye brukte "politihkkit" og ikke tilpasning av "politiker"

Harmonisere slik at også nordsamisk får +Gram/NomAg, nå er det:
* vuovdi	vuovdi+N+NomAg+Sg+Nom

IV og TV kan endres til +Gram/IV og +Gram/TV (vente med denne?)

TILTAK:
* Harmonisere alle samiske språk +NomAg > +Gram/NomAg osv. (dynamiske Der og leksikaliserte Gram skal være like). Dette forutsetter at +Gram/NomAg kan være obligatorisk for dict- og MT-generering

Sammenlikning av NomAg-taggen i flere språk
```
uit-mac-443:giellalt ttr000$ grep NomAg lang-*/src/fst/root.lexc
lang-kpv/src/fst/root.lexc:+Der/NomAg  !!≈ * **@CODE@**
lang-mdf/src/fst/root.lexc: +NomAg
lang-mdf/src/fst/root.lexc: +Der/NomAg
lang-myv/src/fst/root.lexc: +NomAg   !!≈ * @CODE@ Actor Noun From Verb - Nomen Agentis
lang-myv/src/fst/root.lexc:+Der/NomAg
lang-sje/src/fst/root.lexc:+NomAg		  !!= * @CODE@ Agent noun
lang-sje/src/fst/root.lexc:+Der/NomAg 	  !!= * @CODE@ Derived agent noun
lang-sma/src/fst/root.lexc: +Der/NomAg     !!≈ |            |            | **@CODE@** | VN   | Nomen Agentis
lang-sma/src/fst/root.lexc:  %^NOMAGieDISIMP !!≈ | @CODE@ | diphthong simplification for NomAg ie stems
lang-sme/src/fst/root.lexc: +NomAg   !!≈ * **@CODE@** Actor Noun From Verb - Nomen Agentis, +N+NomAg
lang-sme/src/fst/root.lexc: +Err/Confused-NomAgIll   !!≈ * **@CODE@** grammarcheking rela word error confusion pairs
lang-sme/src/fst/root.lexc:!+Der/eaddji  ! XN = +Der/NomAg
lang-sme/src/fst/root.lexc: +Der/NomAg
lang-smj/src/fst/root.lexc: +NomAg   !!≈ * @CODE@ Actor Noun From Verb - Nomen Agentis
lang-smj/src/fst/root.lexc:  +Gram/NomAg !!≈ * @CODE@ = Inherent Actor Noun From Verb - Nomen Agentis, lexicalized derivation
lang-smj/src/fst/root.lexc:+Der/r !!≈ * @CODE@ VN  - NomAg contracted verbs - guollit-guollár
lang-smj/src/fst/root.lexc: +Der/NomAg !!≈ * @CODE@ VN -diddje
lang-smn/src/fst/root.lexc: +NomAg
lang-smn/src/fst/root.lexc: +Der/NomAg
lang-sms/src/fst/root.lexc:+NomAg	  !!= * @CODE@ CHECK ME
lang-sms/src/fst/root.lexc:+Der/NomAg	!!= * @CODE@ agent V»N
lang-vro/src/fst/root.lexc: +Der/JA !!= **@CODE@**	NomAg
```

##  Cmp/Sh - (Bug 2695)
I MT er det problematisk å lage dynamiske sammensetninger, pga. +Cmp/Sh taggen.

Sammenlikning av sme og smj:
```
boradanbeavdi	boradit+V+TV+Der/NomAct+N+Cmp/SgNom+Cmp#beavdi+N+Sg+Nom
boradanbeavdi	boradit+V+TV+Der/NomAct+N+Cmp/SgNom+Cmp#beavdi+N+Sg+Nom

borranbeavdi	borran+N+Cmp/SgNom+Cmp#beavdi+N+Sg+Nom

echo boradangirji |apertium -d. sme-smj
bårådibmegirjje
```

Her ville bårådimgirjje vært bedre.

```
boradangirji	boradit+V+TV+Der/NomAct+N+Cmp/SgNom+Cmp#girji+N+Sg+Nom
bårådibmegirjje	bårådit+V+TV+Der/NomAct+N+Cmp/SgNom+Cmp#girjje+N+Sg+Nom
bårådimgirjje	bårådit+V+TV+Der/NomAct+N+Cmp/Sh+Cmp#girjje+N+Sg+Nom
```

For å kunne generere bårådimgirjje må Cmp/SgNom endres til Cmp/Sh, noe som er mulig i MT, men problemet er at dette skal gjelde bare ulikestavelsesverb, NomAct-substantiver avledet fra ulikestavelsesverb og firestavelsessubstantiver, og da krever det en større ommøblering av bidixfila, hvor man må lage egne stier for disse verbene og substantivene.

På nordsamisk er ikke boradeapmigirji mulig, derfor er Cmp/Sh default og ikke uttrykt i tagger. Også på lulesamisk er Cmp/Sh default, men den lange formen er også mulig. Hvis det ikke hadde vært samme tagger, så kunne man brukt +Use/NG, dvt. kunne man ha +Cmp/Sh som en tilleggstagg i analysen, men som ikke er obligatorisk i genereringa.

En annen mulighet er å endre sme, slik at taggene er som i smj, men i MT vil det da være problemer hvis innputt er et tostavelsesverb og output er et trestavelsesverb, eller motsatt, noe som ofte er tilfellet.

Gjøre Cmp-taggene ikke-obligatoriske, kombinert med +Use/NG: da kan vi ikke skille mellom genitiv og nominativ, f.eks. eatnigiella vs. eadnegiella

Løsning:
* Vi lar default typen bare ha +Cmp/SgNom+Cmp, og legger til en ekstra tagg for stien som ikke er vanlig, feks. +Cmp/Long+Cmp/SgNom+Cmp

##  +A+Attr+Der/vuota vs. +A+Der/vuota

Eksempel fra sme:
```
ráhkisvuohta
ráhkisvuohta	ráhkis+A+Der/vuota+N+Sg+Nom
ráhkisvuohta	ráhkisvuohta+N+Sg+Nom

ráhkesvuohta
ráhkesvuohta	ráhkesvuohta+N+Sg+Nom	0,000000
ráhkesvuohta	ráhkis+A+Attr+Der/vuota+N+Sg+Nom
```

Dette er den eneste derivasjonen vi har lagt til ekstra informasjon til venstre for +Der/.
For MT er problemet samme som med Cmp/Sh-taggenn (se forrige sak)

Løsninger:
* Vi lar default være +A+Der/vuota+N, og legger til en ekstra tagg for stien som ikke er vanlig, f.eks. blir A+Sg+Nom+Der/vuota+N eller A+Attr+Der/vuota+N

#  Avgrensing av derivasjoner

Sjå [dette dokumentet](200423_AvgrenseAvleiing.html) (frå 23.4. 2020)

Smj: Har fjerna Der/Comp og Der/Superl fra leksikonene DIBME og AHTES. Der/Dimin er endret fra Der1 til Der2. (Har også lagt til ny Der/NomInstr)

Se ellers liste i [dette dokumentet](https://giellalt.github.io/lang/smi/AvgrenseAvleiing.html).

```
bálkkáhit
bálkkáhit	bálkáhit+Err/Orth+V+TV+Inf	0,000000
bálkkáhit	bálkáhit+Err/Orth+V+TV+Ind+Prs+Pl1	0,000000
bálkkáhit	bálkáhit+Err/Orth+V+TV+Ind+Prs+Pl3	0,000000
bálkkáhit	bálkáhit+Err/Orth+V+TV+Ind+Prt+Sg2	0,000000
bálkkáhit	bálká+N+Der/Car+A+Der/Comp+A+Attr	0,000000
bálkkáhit	bálká+N+Der/Car+A+Der/Comp+A+Sg+Nom	0,000000 OBS, denne skulle vært borte
bálkkáhit	bálkkáheapme+A+Der/Comp+A+Attr	0,000000
bálkkáhit	bálkkáheapme+A+Der/Comp+A+Sg+Nom	0,000000

náhkehit
náhkehit	nahkehit+Err/Orth-a-á+V+TV+Inf	0,000000
náhkehit	nahkehit+Err/Orth-a-á+V+TV+Ind+Prs+Pl1	0,000000
náhkehit	nahkehit+Err/Orth-a-á+V+TV+Ind+Prs+Pl3	0,000000
náhkehit	nahkehit+Err/Orth-a-á+V+TV+Ind+Prt+Sg2	0,000000
náhkehit	náhkki+N+Der/Car+A+Der/Comp+A+Attr	0,000000  OBS, denne skulle vært borte
náhkehit	náhkki+N+Der/Car+A+Der/Comp+A+Sg+Nom	0,000000
```


Eksempel på ekte infinitiv som blir analysert som Comp (Lene har forbetra dis, desse blir Inf i neste korpus)
```
    46	17142 "deattuhit" V
    59	14872 "vuoruhit" V
    68	13399 "evttohit" V
   103	8121 "veahkehit" V
   127	6240 "jođihit" V
   130	6111 "doaimmahit" V
   133	5973 "oahpahit" V
   151	5377 "fuolahit" V
   869	 363 "eavttuhit" V
   890	 348 "geasehit" V
```

TILTAK:
* Fjerne de resterende +Der/Car som får komparering (**Lene**)
* Lage eget leksikon for -heapme som brukes med komparering (**Lene**)
* Endre Der/Dimin endres fra Der1 til Der2 også i sme og sma og smn (**Thomas, Trond** sistnevnte for smn)
* Observere og deretter forbetre 12345-grammatikken
    - se på grepkorpus: /home/corpus/grep_corpus/2021-01_hfst/ på gtweb og i Korp
    - Vi bør holde et Korp kurs for alle: hvordan søke etter slike ting i Korp
* **Nytt møte om en måned for oppfølging**
