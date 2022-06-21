# A language identification classifier to extract Russian loanwords from Yakut texts

A general-purpose language classifier that uses trigrams to determine the input language has been trained on a special dataset to detect Russian loanwords in Yakut texts. It is expected to capture non-assimilated Russian loanwords, that is, word forms whose stems retain the original spelling in Yakut texts. This means that Russian loan word like "оскуола" (школа), "харандаас" (карандаш), "норуот" (народ) that underwent spelling changes accordingly to Yakut phonetics should not be detected. On the other hand, Russian loan words that did not experiment spelling changes should be identified, even if they appear with attached suffixes, for example "рудник*тар*" (рудники), "Москва*ҕа*" (в Москве) or Yakut inflections like "федераль*ай*" (федеральный), "социальн*ай*" (социальный).

Two labeled training sets are provided: "train_wikipedia_wordforms.csv" and "train_wikipedia_wordforms_unique.csv". Both training sets are essentialy the same, with the only difference being that "train_wikipedia_wordforms_unique.csv" contains each wordform only once. The training sets were created on the base of the Yakut Wikipedia corpus from the Leipzig Corpora Collection [1].

Non-assimilated word forms were automatically labeled in the datasets (label "True") if they contained one of the letters that are exclusively used in lexical elements borrowed from the Russian language { е, я, ю, ё, в, г, ж, з, ф, ц, ш, щ, ъ } or if they did not conform with one of the following characteristics of the Yakut word form described by Kharitonov [2]:   

1. at the beginning of a Yakut word form there is no more than one consonant;
2. at the end of a Yakut word there is no more than one consonant. An exception to this is the combination of a sonorant consonant with a voiceless consonant, where the sonorant always comes first, such as "рт" и "лт";
3. in the middle of a Yakut word, there are no more than two consonants next to each other;
4. consonants { ҕ, й, ҥ, p, ль } never occur at the beginning of a Yakut word;
5. consonants { б, г, ҕ, д, дь, ль, нь, һ, ч } do not appear at the end of the Yakut words.

The rest of the word forms in the datasets were marked with the label "False".

Conducted experimens showed that the classifier achieves better performance when trained with the dataset with unique word forms "train_wikipedia_wordforms_unique.csv".


[1] Dirk Goldhahn, Thomas Eckart and Uwe Quasthoff (2012): Building Large Monolingual Dictionaries at the Leipzig Corpora Collection: From 100 to 200 Languages. In: Proceedings of the Eighth International Conference on Language Resources and Evaluation (LREC'12), 2012, p. 769-765. URL: http://www.lrec-conf.org/proceedings/lrec2012/pdf/327_Paper.pdf (last access 16/06/2022).

[2] Харитонов Л.Н. Современный якутский язык. Часть первая: фонетика и морфология // Научно-Исследовательский Институт языка, литературы и истории ЯАССР // Госиздат ЯАССР, Якутск – 1947.
