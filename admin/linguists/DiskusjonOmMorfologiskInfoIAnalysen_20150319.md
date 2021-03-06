Diskusjonen startet på møte 19. mars 2015.

# Morfologisk informasjon i korpusanalysen

Status i dag: mye informasjon blir fjerna

Vi vil ta vare på mer informasjon
* om derivasjon
* om både dynamiske og leksikaliserte samansetjingar/avleiingar

Saker:
* kva gjer vi i lookup2cg? Avklart på separat møte, vi hiv ut all lingv. pros.
* korleis skal taggane for leksikaliserte ord sjå ut?
* kva er eit lemma?

Spørsmål:
* vil vi ha kopling til rotlemma?
* kor stor del av den morfologiske historia vil vi ta vare på?
* kva vil vi koda?
* kva slags "syntaks" vil vi ha for taggane for morf.historia?

Fordeler med leksikalisering:
* ordbøker og MT
* prioritering av forslag i stavekontrollen (de leksikaliserte kommer først)
* mulighet for å legge til semantiske tagger uavhengig av derivasjonstype
* estetiske (reint syntaktiske) lesingar i syntaktisk analyse

Alternativer:
1. Bruke kompleks analyse istedenfor leksikalisering
1. Legge til tagger om derivasjon til dagens analyse. I dag har vi en slik i sme: +NomAg
1. Ta vare på kompleks analyse som underlesning
1. Legge til definerte underlesninger i et skript, mellom FST og cg3

**1. Bruke kompleks analyse istedenfor leksikalisering:**

En både-og-løsning vil kunne kreve to disambigueringsfiler

**2. Legge til tagger:**

Vi har i dag dette for NomAg for å løse homonymi
```
vuovdi   = selger
vuovdi	vuovdi+N+NomAg+Sg+Nom  <= info i tagg til det leksikaliserte lemmaet
vuovdi	vuovdit+V+TV+Der/NomAg+N+Sg+Nom <= kompleks analyse
```

pga av homonymi med vuovdi+N = skog som har ulikt bøyningsparadigme

For derivasjonen Der/NomAct har vi det ikke

```
vuovdin	vuovdin+N+Sg+Nom  <== +NomAct ville være fordel for disambiguering av Acc vs Gen
vuovdin	vuovdit+V+TV+Der/NomAct+N+Sg+Nom
```

**3. Ta vare på kompleks analyse som underlesning** \\
Denne diskuterte vi ikke

**4. Legge til definerte underlesninger i et skript, mellom FST og cg3**

```
"<vuovdin>"
    "vuovdin" N NomAct Sg Nom
        "vuovdit" V TV

"<ealli>"
    "ealli" N NomAg Sg Nom Sem/Ani
        "eallit" V IV
```

```
$ echo čorgejeaddji | hfst-proc2 --xerox tools/preprocess/tokeniser-disamb-gt-desc.pmhfst | cg-conv -f
"<čorgejeaddji>"
	"čorgejeaddji" N NomAg Sem/Hum Sg Nom
	"čorgejeaddji" Der/NomAg N Sg Nom
		"čorget" V TV

```

## Konsekvensar for ulike applikasjonar/komponentar:
* CG (disambiguering) - må tilpasses ny lookup2cg
* ordbøker / Oahpa osv
* MT
* korp
* grammatikkontroll
* talesyntese(?)

Eksempler:
```
sme$ usme
borahahtti - (ordboka: spiselig A)
borahahtti	borrat+V+TV+Der/h+V+Der/ahtti+V+TV+PrsPrc
borahahtti	borrat+V+TV+Der/h+V+Der/ahtti+V+TV+Der/NomAg+N+Sg+Nom
borahahtti	borahit+V+TV+Der/ahtti+V+TV+PrsPrc
borahahtti	borahit+V+TV+Der/ahtti+V+TV+Der/NomAg+N+Sg+Nom
borahahtti	borahahtti+A+Attr
borahahtti	borahahtti+A+Sg+Nom

borahahtti
borahahtti	borrat+V+TV+Der/h+V+Der/ahtti+V+TV+PrsPrc
borahahtti	borrat+V+TV+Der/h+V+Der/ahtti+V+TV+Imprt+Du2
borahahtti	borrat+V+TV+Der/h+V+Der/ahtti+V+TV+Der/NomAg+N+Sg+Gen
borahahtti	borrat+V+TV+Der/h+V+Der/ahtti+V+TV+Der/NomAg+N+Sg+Acc
borahahtti	borrat+V+TV+Der/h+V+Der/ahtti+V+TV+Der/NomAg+N+Sg+Nom
borahahtti	borahit+V+TV+Der/ahtti+V+TV+PrsPrc
borahahtti	borahit+V+TV+Der/ahtti+V+TV+Imprt+Du2
borahahtti	borahit+V+TV+Der/ahtti+V+TV+Der/NomAg+N+Sg+Gen
borahahtti	borahit+V+TV+Der/ahtti+V+TV+Der/NomAg+N+Sg+Acc
borahahtti	borahit+V+TV+Der/ahtti+V+TV+Der/NomAg+N+Sg+Nom
borahahtti	borahahtti+A+Attr
borahahtti	borahahtti+A+Sg+Nom => A = PrsPrc 'borahit/borrat'
borahahtti	borahahtti+A+Sg+Gen
borahahtti	borahahtti+A+Sg+Acc

$ usmj
nuorttal	nuorttal+Adv +
nuorttal	nuorttal+Po
nuorttal	nuorttal+Pr

nuorttalappo	nuorttalabbo+A+Comp+Pl+Nom
nuorttalappo	nuorttalabbo+A+Comp+Sg+Gen

nuorttalappot	nuorttalabbo+A+Comp+Der/at+Adv
nuorttalappot	nuorttalappot+Adv
- subst->komp->adj->adv

$ usme

geahppaseappot  geahpas+A+Comp+Der/at+Adv
geahppaseappot  geahppaseappot+Adv  <== denne vinner i dis.cg3
```

## Bz 1308:
Eksempler på ikke veldig produktive deriverte verb hvor derivasjonen ikke kommer fram i FST.
Spørsmålet er om vi skal synliggjøre slik derivasjon.

Spesielt gjelder det verb på -lit (i parantes er mulig analyse som FST ikke gir idag):
* oaidnalit    oaidnalit+V+IV+Inf (oaidnit V Der/lit)
* náitalit    náitalit+V+IV+Inf (náitit V Der/lit)
* heaitalit    heaitalit+V+TV+Inf (heaitit V Der/lit)
* álgalit    álgalit+V+IV+Inf (álgit V Der/lit)
* riidalit    riidalit+V+IV+Inf (riidit V Der/lit)

Men også verb på -šit:
* bealkkašit    bealkkašit+V+TV+Inf (bealkit V Der/šit)
* vávjjašit    vávjjašit+V+TV+Inf (vávjit V Der/šit)
