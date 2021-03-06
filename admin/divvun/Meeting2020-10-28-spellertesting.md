20202.10.27 Stavekontrolltesting

Til stades: Børre, Sjur, Tommi

Saker:
* stavekontrolltesting og GitHub-integrering

Ta utgangspunkt i https://github.com/divvun/divvunspell/ og accuracy-tester

`accuracy-tester` genererer json-data. Må konverterast til noko som kan visast direkte i GitHub - kan vera MD eller noko som MD kan lenka til.

Testdata finst for alle språk i `test/data/typos.txt` (TSV-fil).

Kva vi vil ha:
* ein modernisert replika av det vi har hatt
* grunnleggjande mål i ein historisk graf - TSV-fil med ei linje pr testa versjon

# TSV-fil og historisk graf

Data som må vera med:
* commithash
* tidsstempel
* forslagskvalitet i prosent (top1, top5, lenger ned, ingen forslag, berre feil)

TSV-format:
```
hash	dato	Release/description	top1	top5	lower5	nosugg	wrongsugg
```

#  Detaljert rapport

* json-fil frå `accuracy-tester`
* konvertering til tabell eller liknande (no: NodeJS-app skriven av Brendan)
    - helst direkte integrerbar med MD-dokument slik at ein får automatisk vising i GH

Manglar i Brendan-versjonen:

* redigeringsavstand
* statistikk basert på redigeringsavstand
* true/false negative/positive

Gamalt format, kolonner:
* input
* true/false negative/positive
* expected output
* redigeringsavstand
* plass for rett forslag
* tidsbruk
* faktiske forslag (rett framheva)
* merknader, bugzilla-lenker

Brendan-format, kolonner:
* input + expected output, plass for rett forslag, tidsbruk
* faktiske forslag (rett framheva)

Redigeringsavstand bør koma frå `accuracy-tester`, dvs Rust, og skrivast ut i json-rapporten som ein del av testresultata. Noko i stil med:

```
    {
      "input": "mnngan",
      "expected": "mænngan",
      "edit_dist": 1,   # <== nytt felt
      "suggestions": [
        {
          "value": "mænngan",
          "weight": 21.669922
        },
...
      ],
      "position": 0,
      "time": {
        "secs": 0,
        "subsec_nanos": 5624911
      }
    },
```

Tommi prøver å leggja inn dette, spør Brendan om hjelp om det trengst. Forslag til Rust-crate:
[https://docs.rs/distance/0.4.0/distance/]

#  Arbeid framover

Status 20202.11.4:

* integrera detaljrapporten i MD-dokument for kvart språk
    - grafikk som viser fordeling mellom dei ulike typane (svg - offline eller på direkten?)
    - tabell med alle detaljar - er MD rette formatet?
* integrera historisk rapport i MD-dokument - Tommi
    - grafikk som viser historisk utvikling (svg - offline eller på direkten?)
* integrera i make

##  Ferdig

* leggja inn redigeringsavstand i json-rapporten (Tommi) - FERDIG
    - har lagt til funksjon for å leggja til samandrag til ei fil som viser utviklinga over tid
* data lagrast (inntil vidare) i `tools/spellcheckers/test/` (Sjur) - FERDIG
* legg inn javascript og CSS i gtsvn igjen (frå giella-core), slik at gamle testresultat fungerer igjen (Sjur) - FERDIG for lang-XXX-repoa.
