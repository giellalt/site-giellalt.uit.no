# Semantiske tagger - organisering, skripting 4.6.2019

Tilstede: Linda, Sjur, Lene, Trond, Børre

## Dokumentasjon av semtagger
Må lages, både med filosofien bak, regel for laging av nye tagger og med en kort forklaring og eksempel for hver enkelt tagg

## Semtaggene skal oppdateres:

* root.lexc for hvert enkelt språk (dette som source) => giella-shared

* CG for disambiguation.cg3, functions.cg3, dependency.gc3, tools/grammarcheckers/grammarchecker.cg3, tools/grammarcheckers/grc-disambiguator.cg3, tools/tokenisers/mwe-dis.cg3, src/syntax/valency.cg3

sme/src/syntax/semsets.cg3

i to forskjellige format:
LIST SEM-TAGS = Sem/Hum Sem/Hum_Org .... ;

LIST Sem/Hum = Sem/Hum Sem/Hum_Org .... ;
LIST Sem/Org = Sem/Hum_Org Sem/Org ... ;
LIST Sem/Tool = Sem/Tool Sem/Tool-catch Sem/Tool-write Sem/Body_Obj_Tool-catch ..... ;
LIST Sem/Tool-catch = Sem/Body_Obj_Tool-catch ;
LIST Sem/Build = Sem/Build Sem/Build_Org Sem/Build-room ;  #ikke Sem/Buildpart

Syntaks: Ein tagg er definert som:

1. bokstavstreng mellom [[/_] og taggslutt
1. bokstavstreng mellom [[/_] og -
1. bokstavstreng mellom [[/_] og _ (inkludert - i same tagg)

```
cat sme/src/morphology/root.lexc sma/src/morphology/root.lexc smj/src/morphology/root.lexc smn/src/morphology/root.lexc |grep 'Sem/' |tr '\t' ' ' |cut -d '+' -f2 |cut -d ' ' -f1 |sort -u > allsemtags
```

## Apertium

### Apertium-style
```
sem_act
sem_act_clth
sem_act_tool-it
```

### tools/mt/apertium/tagsets/gt2apertium.cg3relabel (semsets bør være i egen fil):
```
MAP (Sem/Act) (sem_act) ;
MAP (Sem/Act_Clth) (sem_act_clth) ;
MAP (Sem/Act_Domain) (sem_act_domain) ;
MAP (Sem/Act_Event) (sem_act_event) ;
```

OBS, egen behandling for disse taggene:
```
MAP (Sem/Mal) (ant m) ;
MAP (Sem/Fem) (ant f) ;
MAP (Sem/Sur) (cog) ;
```

### apertium-l1-l2.l1-l2.t1x og apertium-l1-l2.l2-l1.t1x (semsets bør være i egen fil)
```
    <attr-item tags="sem_hum_mat_tool"/>
    <attr-item tags="sem_hum_obj"/>
```

```
cat allsemtags | tr '/' '_' |tr '[A-Z]' '[a-z]' > semtags_apertiumstyle
cat semtags_apertiumstyle | sed 's/^/(/' |sed 's/$/) ;/'> aperallsemtags
cat allsemtags | sed 's/^/MAP (/' |sed 's/$/)/' > first
paste -d ' ' first aperallsemtags  > relabel_apertiumstyle.txt
cat semtags_apertiumstyle |sed 's/^/      <attr-item tags="/' |sed 's/$/"\/>/' > apertiumtx1.txt
```

##  Andre ting

* vi treng eit verkty for å sjekka taggkonsistens (alfabetisk rekkjefylgje på multitaggar)
* vil det vera mogleg å gå vekk frå multitaggane i framtida, og heller konvertera automatisk til multitaggar for apertium?

##  Plan

* **Sjur, Børre** ser på skriptet
* når semtag-definisjonan fjernes fra CG filan gjøres det sammen med de som jobber med CG filan: **Linda, Lene**
* lage definisjoner og veiledning for semtaggan med eksempler/moteksempler
