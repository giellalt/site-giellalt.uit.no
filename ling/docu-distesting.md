    Tokens =    Number of tokens in the text

        Alternative 1: Process with hfst:
                cat file.txt|hfst-tokenise tools/tokenisers/tokeniser-disamb-gt-desc.pmhfst

                Alternative 2: Process with perl:
                cat file.txt | preprocess --abbr=bin/abbr.txt | wc -l)
                (or: "ccat -l sme" instead of "cat", if input is corpus files in our xml format)

    Parses =    Number of parses given (number of the following command, minus the
                number of tokens)

            Alternative 1: process with hfst
            cat file.txt|hfst-tokenise -g  tools/tokenisers/tokeniser-disamb-gt-desc.pmhfst

                Alternative 2: process with perl:
            cat file.txt | preprocess --abbr=bin/abbr.txt | lookup -flags mbTT
                -utf8 src/analyser-gt-desc.xfst | lookup2cg | vislcg3 --g=src/syntax/disambiguation.cg3 | wc -l
    CorrTag =   Number of tokens that did not have their correct tag removed
                (This number must be manually arrived at: Tokens - errouneous_analyses

    Ambiguity = #Parses / #Tokens
    Precision = #CorrTag / # Parses
    Recall =    #CorrTag / # Tokens
