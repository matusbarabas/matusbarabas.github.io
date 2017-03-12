# Link na stránku: https://matusbarabas.github.io

Vlastné premenné:  
* selected - slúži na zistenie, ktorý z tabov v headri je aktívny, napr. v `/cv/index.md`
* wp_selected - zistenie aktívneho tabu v menu postránky Webové publikovanie `/wp/index.md`
* about_me_selected - aktívne taby na podstránke O mne `/about/index.md`
* date - dátum napísania príspevku, napr. v `/_posts/2017-02-21-working-on-page.md`
* published - označuje publikovaný alebo zatiaľ nepublikovaný príspevok (ak je false, neuverejní sa na stránke), napr. v `/_posts/2017-02-21-working-on-page.md`
* reading_plugin - boolean, ktorý určuje, či sa používa daný plugin, alebo nie `/post/index.md`
* používateľské mená na rôznych sociálnych sieťach v `_config.yml`

Kolekcie:  
* použil som kolekciu pre životopis, ktorá obsahuje všetky moje údaje, skúsenosti a zručnosti `/_cv_collection/cv.md`

Dátové súbory:  
* photos.yml - súbor s fotkami tj. linkom a popisom `/_data/photos.yml`
* song_list.yml - zoznam pesničiek s linkom a názvom  `_data/song_list.yml`

Filtre:  
* date_to_long_string - zobrazuje dátum poslednej zmeny na stránke, napr. v `/_layouts/about_me_layout.html`
* markdownify - konvertuje Markdown do HTML - použitý napr. pri ťahaní údajov z kolekcie cv `/_layouts/cv_layout.html`
* sort - fotky sú zoradené abecedne podľa popisu `/_layouts/photos_layout.html`
* number_of_words - v príspevkoch sa počíta počet slov `/_layouts/post.html`

Tagy:  
* case, napr. v `/_layouts/wp_layout.html`
* for, napr. v `/_layouts/photos_layout.html`
* if, napr. v `/layouts/posts_layout.html`

Plugin:  
* reading_time - plugin, ktorý pre každý príspevok na základe počtu slov vypočítava približnú dobu čítania (zapína sa prepísaním premennej reading_plugin v súbore index.md priečinka post na true)
* jemoji - zobrazuje smajlíky, ukážka v `/_posts/2017-03-03-add-jemoji.md`

Layouty:
* default layout, ktorý používa každa podstránka - includuje linky bootstrapu, header a footer, ktoré sa na podstránkach nemenia `/_layouts/default.html`
* about_me_layout - obsahuje horné prepínanie medzi tabmi, základné informácie o mne a playlist obľúbenej hudby `/_layouts/about_me_layout.html`
* cv_layout - konštrukcia pre životopis, dáta sa ťahajú z kolekcie, znovopoužiteľný, stačí prepísať dáta v kolekcii `/_layouts/cv_layout.html`
* photos_layout - fotogaléria, dá sa použiť aj na iné fotky resp. obrázky s rôznymi popismy, stačí meniť dátový súbor `/_layouts/photos_layout.html`
* posts_layout - rozloženie príspevkov o aktuálnom dianí na stránke `/_layouts/posts_layout.html`
* wp_layout - obsahuje bočné menu, dá sa použiť na rôzny typ inej podstránky, v mojom prípade obsahuje podstránky pre všetky tri zadania predmetu `/_layouts/wp_layout.html`

Podstránky:
* O mne
 * Obľúbená hudba
* Životopis
* Fotogaléria
* Príspevky
* Webové publikovanie
  * Zadanie 1
  * Zadanie 2
  * Zadanie 3
