This is a document for the technical documentation of our spellers based
on open source, by example from Debian this presently includes Aspell,
iSpell and MySpell.

It is hastily written, and will be split up in sensible subdocuments as
soon as we have time to do so. Just now it is here as a survival kit for
aspell newcomers.

File Overview
=============

The files are in the gt/sme/aspell directory. Cf. the list with
explanation:

-   **Makefile.pre:**
    This file is used when generating Makefile in distribution package
-   **configure:**
    Used for generating the Makefile in distribution package
-   **info:**
    The info file is the main file which contains most of the
    information.
-   **sme.cmap:**
    File contains the mappings of the characters into aspell internal
    format used in our wordlist.
-   **sme.cset :**
    File contains the characterset of the characters used in aspell
    internal format.
-   **sme.cwl :**
    This is compressed form of the wordlist.
-   **sme.dat :**
    Data file of the language.
-   **sme.multi:**
    Listing of the dictionary files
-   **sme.wl :**
    Wordlist
-   **sme\_affix.dat:**
    Contains the affixes of the language.
-   **sme\_phonet.dat ???:**
    It is possible to define some substitution sequences as more likely
    than others.

The format of the files
=======================

The way it works
----------------

The fullform wordlist `sme.wl` is created from transducer with Xerox
finite-state tools.

The Makefile
------------

Here we need some words on what it does and especially what it doesn't.

We postpone the makefile documentation (how it does it).

sme\_affix
----------

This file is a manually created affix file for North Sami.

### The format of the affix file

Affix is either a prefix or a suffix that can be attached to root words
to make other words. Here is an example of how to define a suffix.

    SFX I Y 5
    SFX I   a                   ii                      [^ij]a
    SFX I   0                   i                       [ij]a
    SFX I   e                   ii                      e
    SFX I   0                   i                       [i??]
    SFX I   i                   ??i                      i

The first line has 4 fields.

1.  SFX indicates this is a suffix
2.  I is the name of the character which represents this suffix
3.  Y indicates it can be combined with other affix entries
4.  5 indicates it has 5 entries stored in this prefix

The remaining lines describe the information for the 5 entries.

1.  SFX indicates this is a suffix
2.  I is the name of the character which represents this suffix
3.  a the string of chars to strip off before adding affix
4.  ii the prefix string to add (a 0 indicates the NULL string)
5.  \[^ij\]a the conditions which must be met before prefix can be added

### Suffix lexica

The suffix lexica are

-   **PFX A:**
    North-, South-, prefixes to proper nouns
-   **PFX B:**
    ii-, the negative prefix
-   **SFX E:**
    the suffixes for the Prop lexica ACCRA (V-final) and LONDON
    (odd-syll C-final)
-   **SFX F:**
    suffixes for the Prop lexica NYST?? (heavy vow), C-FI-NEN and CNAME
    (C-final)
-   **SFX G:**
    suffixes for the Prop lexicon BERN (even-syll C-final)
-   **SFX H:**
    suffixes for GOAHTI etc, even-syll nouns
-   **SFX I:**
    suffixes for STAHTA, IIJA, even-syll nouns without illative vow alt
-   **SFX J:**
    suffixes for SEAMU
-   **SFX K:**
    suffixes for MALIS, BU/MUS
-   **SFX L:**
    suffixes for DIMINC
-   **SFX N:**
    suffixes for verbs.

At present, the status is

    PFX A Y 9
    PFX B Y 1
    SFX E Y 31
    SFX F Y 69
    SFX G Y 18
    SFX H Y 156
    SFX I Y 121
    SFX J Y 214
    SFX K Y 70
    SFX N Y 149

Status quo:

-   **Implemented:**
    Proper nouns, nouns, even-syllabic verbs, contracted verbs (??)
-   **Missing:**
    Adjectives are missing completely. Three-syllabic nouns and
    three-syllabic verbs are missing.

Methods for adding them (how the suffixes have been added so far).

A nice strategy would be to generate suffixes automatically, like the
way it was done for the Finnish ispell file. Let us look into that
possibility. While waiting, let us consider adding the following chunk
to sme\_affix.dat.

    SFX M   0
    SFX M   it            a                 it
    SFX M   it            an                it
    SFX M   it            at                it
    SFX M   0            e                  t
    SFX M   0            eaba               t
    SFX M   0            eaddji             t
    SFX M   0            eadnot             t
    SFX M   0            eadnu              t
    SFX M   0            eahkket            t
    SFX M   0            eahkki             t
    SFX M   0            eahkkot            t
    SFX M   0            eahkku             t
    SFX M   0            eahppi             t
    SFX M   0            ea????a              t
    SFX M   0            ea????an             t
    SFX M   0            ea????at             t
    SFX M   0            ea??                t
    SFX M   0            ea????aba            t
    SFX M   0            ea????abeahtti       t
    SFX M   0            ea????abehtet        t
    SFX M   0            ea????at             t
    SFX M   0            ea??????              t
    SFX M   0            edje               t
    SFX M   0            edne               t
    SFX M   0            ehket              t
    SFX M   0            ehkon              t
    SFX M   0            ehkos              t
    SFX M   0            ehkoset            t
    SFX M   0            ehkoska            t
    SFX M   0            ehkot              t
    SFX M   0            ehpet              t
    SFX M   0            eidde              t
    SFX M   0            eiddet             t
    SFX M   0            eigga              t
    SFX M   0            eimme              t
    SFX M   0            eimmet             t
    SFX M   0            etne               t
    SFX M   0            etnot              t
    SFX M   0            ettiin             t
    SFX M   0            e??                 t
    SFX M   0            e????e               t
    SFX M   0            e????et              t
    SFX M   0            haga               t
    SFX M   0            ii                 t
    SFX M   0            in                 t
    SFX M   0            it                 t
    SFX M   0            iv????e              t
    SFX M   0            iv????en             t
    SFX M   0            iv????et             t
    SFX M   0            iv????ii             t
    SFX M   0            iv????iide           t
    SFX M   0            iv????iidet          t
    SFX M   0            iv????iiga           t
    SFX M   0            iv????iime           t
    SFX M   0            iv????iimet          t
    SFX M   0            keahtt??            t

Initially, we inserted flags in the fsm's source code. Now, the tags
`A, B, C, etc.` are generated via aspell's `munch` command,
intended-to-be made part of the Makefile routine.

The wordlist sme.wl
-------------------

The list sme.wl contains 1000 lines (why?). For the words *A-vitamiidna*
and some other vitamins, it has full paradigms, whereas for place names
it has only stems. Why?

Because sme.wl is only a dummy file?

Because the proper nouns have been enrolled in the sme\_suffix.dat file,
and therefore are represented only by their stems, whereas the vitamins
are unenrolled, and therefore represented by fullforms?

### Adding flags to wordlist

Flags are inserted to the wordlist with `munch-list` aspell command.
Munch-list takes the wordlist `sme.wl` and affix information file
`sme_affix.dat` and generates a munched wordlist with wordroots that
have appropriate affix tags.

The munching must be done in small bits, because it consumes RAM very
much. The plan is to use 1 million words at a time, and catenate the
output into one uniform wordlist.

After the wordlist has been munched, it can be compressed and the output
is a compressed wordlist `sme.cwl`.

The file sme\_phonet.dat
------------------------

In aspell common misspellings are given more weight than other
substitutions. This can be a part of sma\_affix.dat file (it will then
be MySpell compatible), but in aspell it is done as a separate file
`sme_phonet.dat`

Format: The list is a tab-separated file, wshere each line has the form
`sourceletter(s) whitespace(s) targetletter(s)`. We would like to add
the following type of substitutions:

-   Long ?? vs. short ??
-   The S??mi letters vs. the nonmodified Latin letters
-   t versus its non-reduced consonants
-   consonant gradation pairs
-   Probably something around loan words:

<!-- -->

            a   ??
            ??   a
            c   ??
            tt  t
            tt  dd
            ...
