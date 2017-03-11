# Link na stránku: https://matusbarabas.github.io

Vlastné premenné:  
* selected - slúži na zistenie, ktorý z tabou v hlavnom nav-bare je aktívny
* wp_selected - zistenie aktívneho tabu v menu postránky Weboé publikovanie
* about_me_selected - akt9vne taby na podstránke O mne
* date - dátum napísania príspevku
* published - označuje publikovaný alebo zatiaľ nepublikovaný príspevok (ak je false, neuverejní sa na stránke)
* reading_plugin - boolean, ktorý určuje, či sa používa daný plugin, alebo nie

Kolekcie:  
* použil som kolekciu pre životopis, ktorá obsahuje všetky moje údaje, skúsenosti a zručnosti

Dátové súbory:  
* photos.yml - súbor s fotkami tj. linkom a popisom
* song_list.yml - zoznam pesniciek s linkom a názvom

Filtre:  
* date_to_long_string - zobrazuje dátum poslednej zmeny na stránke, je obsiahnutý v názve príspevku
* markdownify - konvertuje markdown do HTML - použitý napr. pri ťahaní údajov z Kolekcie
* sort - fotky sú zoradené abecedne podľa popisu
* number_of_words - v príspevkoch sa počíta počet slov

Tagy:  
* na stránke je použitých množstvo tagov ako npr. for cykly, if, case ...

Plugin:  
* reading_time - plugin, ktorý pre každý príspevok na základe počtu slov vypočítava približnú dobu čítania (zapína sa prepísaním premennej reading_plugin v súbore index_md priečinka post)
* jemoji - zobrazuje smajlíky (ukážka je v prípevku Pridal som smajlíky)

Layouty:
* default layout, ktorý používa každa podstránka - includuje linky bootstrapu, header a footer, ktorá sa na podstránkach nemení
* about_me_layout - obsahuje horné prepínanie medzi tabmi
* cv_layout - konštrukcia pre životopis, dáta sa ťahajú z kolekcie, znovopoužiteľný, stačí prepísať dáta v kolekcii
* photos_layout - fotogaléria, dá sa použiť aj na iné fotky resp. obrázky s rôznymi popismy, stačí meniť dátový súbor
* posts_layout - rozloženie príspevkov
* wp_layout - obsahuje bočné menu, dá sa použiť na rôzny typ inej podstránky
