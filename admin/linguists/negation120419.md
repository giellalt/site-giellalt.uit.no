Notes from an ad-hoc discussion 19.4.2012

# Negated Preterite

## Motivation

Up until now negated preterite sentences in SME have not had a preteritum tag. The idea has been that it is the combination of negation verb and perfectum participle that together express the preterite. The lack of a real preteritum tag is problematic, and there is also one verb (the copula) that has a special preteritum form different from the participle (but which is not tagged as such).

## Actions
* We duplicate the hitherto perfectum participle, giving the twin form
  a reading containing the tag +Prt in addition to the reading containing
  +PrfPrc. The pair *lean/leamaš* get one tag each (Prt/PrfPrc).

```
  borran	borrat+V+TV+PrfPrc
  borran	borrat+V+TV+Ind+Prt+ConNeg  <=== new
  bora	    borrat+V+TV+Ind+Prs+ConNeg
  leamaš	leat+V+IV+PrfPrc
  lean	    leat+V+IV+PrfPrc <== remove
  lean	    leat+V+IV+Ind+Prt+ConNeg  <=== new
```

* CG rules are changed accordingly.

# Negated imperative

## Motivation
Today, +Imprt is visible on the negation verb **and** on the main verb.
One is enough. We follow the morphology.

## Discussion

```
boađe	boahtit+V+IV+Imprt+ConNeg <== remove

in boađe    - boađe	boahtit+V+IV+Ind+Prs+ConNeg
in boahtán  boahtit+V+IV+Ind+Prt+ConNeg <== ny
	ii+V+IV+Neg+Ind+Sg1
	boahtit+V+IV+PrfPrc

ale		ii+V+IV+Neg+Imprt+Sg2
boađe   Imprt ==> boađe	boahtit+V+IV+Imprt+ConNeg

in boađáše  Cond  boađáše	boahtit+V+IV+Cond+Prs+ConNeg
ii bođeš	Pot	  bođeš		boahtit+V+IV+Pot+Prs+ConNeg

boađe
boađe	boahtit+V+IV+Imprt+ConNeg
boađe	boahtit+V+IV+Ind+Prs+ConNeg

boađe
boađe	boahtit+V+IV+ConNeg            <============ 1
boađe	boahtit+V+IV+Ind+Prs+ConNeg   <============2

boahtán  boahtit+V+IV+PrfPrc                   1
boahtán  boahtit+V+IV+Ind+Prt+ConNeg <== ny 2

in
in	ii+V+IV+Neg+Ind+Sg1

in
in	ii+V+IV+Neg+Ind+Prs+Sg1
in	ii+V+IV+Neg+Ind+Prt+Sg1
ale		ii+V+IV+Neg+Imprt+Sg2
```

## Actions
1. remove the +Imprt tag on the main verb in front of +ConNeg
1. An extra form parallel to PrfPrc which is +Ind+Prt+ConNeg
1. Remove +Imprt from +Imprt+ConNeg (boađe)
1. lean	    leat+V+IV+PrfPrc <== remove
1. lean	    leat+V+IV+Ind+Prt+ConNeg  <=== new
1. follow-up on the CG to check that the removed tag doesn't create changed output
