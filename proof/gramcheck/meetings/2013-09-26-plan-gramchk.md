26.09.2013

present:
* Sjur
* Linda

grammar checker project plan

0 intro
* working definition: errors that cannot be resolved by the spellchecker
* Excluding real word errors by default

1 done until now:

* error type classification
    - lexical errors (&lex-majuscule)
    - morphosyntactic errors (&msyn-inf_not_actio)
    - syntactic errors (&syn-case_congruence)
    - real-word errors (&real-vuosttaš)
    - correct tags (&corr-not-compound)

* additional error types
    - punctuation errors
    - number formatting errors
    - capitalisation errors

    - specific syntactic grammar for the grammar checker philosophy: sme-gramdis.rle, rules are marked (REMOVE:GramPo)
    - grammarchecker grammar: sme-gramchk.rle
    - publication: Constraint Grammar based Correction of Grammatical Errors for North Sámi LREC 2012

2 todo:

* practical things:
    - move SME (and GC) from old to new infrastructure
    - meetings with Francis

* maintenance:
    - add/change/update semantic/syntactic tags

* work on things started:
    - Duommá's 250 word list (compounds that lead to real word errors) - excluding real word errors by default
    - rules for valency example sentences collected in gramchkcorpus.txt

* errors:
    - find out which types of errors are most frequent
    - error corpus - size?? other sources??
        - $GTFREE/goldstandard/orig/sme (xserve)
        - main/gt/sme/src/gramchk/gramchkcorpus.txt
* possible classes?

* presentation:
    - sponsor-demonstrations
    - release early/often (Open Source principles)
    - we cannot make a Microsoft Office grammar checker - prohibited by MS - users can protest by writing to them ;) (we can only deliver to LibreOffice)
    - look at a graphic grammarchecker (voikko - Finnish)
    - http://wiki.apertium.org/wiki/Spellchecking

* rules:
    - for real word errors: which semantic tags can be combined? - dálkkádat + rap + poarta
    - bigrams and statistics for compounds?
    - fix/annotate grammatical errors (compounds) already in
  preprocessing/tokenization/morphological analysis (i.e. treat space as
  compound border for relevant POS's) (other ideas - Eckhard?)
    - hfst-proc må truleg oppdaterast for å gje alle analyser av potensielle
  samansetjingsfeil

Samansetjingsfeil - særskriving:

```
[N Nom]         [N ...] ===== kasusfeil (Gen not Nom) / sammensettingsfeil
[N Nom/N Gen]   [N ...] =====
[N Gen]         [N ...] =====
[N Nom+VR]      [N ...] ===== med vokalreduksjon (VR) - alltid feil
[N Nom/N Gen+VR][N ...] ===== --"--
[N Gen+VR]      [N ...] ===== --"--
```

VR = Vokalreduksjon

what is one word?
* stavekontroll - space before and after
* tokenizer:
    - space as a possible sign in a compound (in the case:
  [[N Nom] [[N ...] the error tag can get annotated right away)
    - CG needs to clean up - disambiguate

* tools to be used:
    - dependencies
    - valencies
    - semantic roles
    - semantic prototypes

    - evaluation:
        - precision and recall
        - how much has been resolved
