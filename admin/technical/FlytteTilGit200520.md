Github-flytting og Zulip - møte 20.5.2020

Til stades: Chiara, Sjur, Trond, Linda, Børre, Inga, Thomas, Siri

Saker:

* røynsle så langt, + og -
* korleis fungerer Zulip
* lenke til gamal giella-core / -shared
* handsaming av mange katalogar (gut ikkje ferdig)
* grafisk klient
* manglande dokumentasjon (MigratingToGit.jspwiki er ein start)
* innsjekkingsrettar
* .profile

#  røynsle så langt, + og -

Dei fleste får til å kompilera og sjekka inn.

#  Cornerstone

Inga har problem, tek det etter møtet.

# lenke til gamal giella-core / -shared

Blir ikkje lenger laga.

# handsaming av mange katalogar

* git: `gut` er svaret (må byggjast sjølv med Rust nettopp no)

# grafisk klient

* svn: Cornerstone
* git: det finst mange, krev ein eigen runde.

# manglande dokumentasjon

Dokumentet *MigratingToGit.jspwiki* er ein start. For å ta ein
titt og redigere i løpet av dette møtet, sjå Untitled 7 i see.

# innsjekkingsrettar

Alle har fått det no, via teamet GiellaLT

#  korleis fungerer Zulip

# .profile

GTLANGS=$HOME/der-alle-språkene-er
export GTCORE=$HOME/giella-core # der giella-core er
test -r "$GTCORE"/devtools/init.d/init.sh && . "$GTCORE"/devtools/init.d/init.sh

problem: Vi har init.sh i både giella-core (git) og gtcore (svn)

# git-repositoriet

Den sentrale fila som presenterer språket er **README** i lang-XXX.
I vår dokumentasjon er den tilsvarande fila doc/WhatIsThis.jspwiki.

# Zulip

**Støy:** Ikkje abonner på det du ikkje er interessert i. Vel
alternativet *Mute the topic*. Mappa blir grå, og du får ikkje melding.

**Innsjekkingsmeldingane:** Zulip viser berre innsjekkingsmelding,
ikkje filnamn. Vi bør (så lenge dette ikkje er fiksa) skrive filnamnet.

# Neste møte

Trond og Chiara tar eit eige Git-møte med Sjur i neste veke.

Elles ser vi an om vi treng fleire møte for svn-arbeid.
