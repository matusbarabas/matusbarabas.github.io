---
layout: wp_layout
title: Zadanie 3
selected: webove_publikovanie
wp_selected: zadanie3
---

## XML prezentácia

---

#### **Zadanie**

Analyzujte možnosti zápisu jednoduchej prezentácie v jazyku XML. Identifikujte základné súčasti prezentácie a navrhnite XML elementy pre ich označkovanie (metadátové, štrukturálne, inline). Dbajte na znovupoužiteľnosť a vyvarujte sa redundancií. Návrh elementov zrealizujte opísaním typu dokumentu pomocou vybraného jazyka (DTD, XSD, RELAX NG) spolu s vysvetlením účelu jednotlivých elementov. Vo vami navhrnutom jazyku vytvorte ukážkovú prezentáciu, ktorá bude demonštrovať možnosti tvorby prezentácií podľa definície typu dokumentu.

Navrhnite a vytvorte XSLT šablóny pre konverziu prezentácie z XML do XHTML+CSS a pre konverziu prezentácie z XML do PDF. Klaďte dôraz na znovupoužitie jednotlivých šablon pre viaceré výstupné formáty. Umožnite zadávanie parametrov transformácií.

Súčasťou požiadaviek na zadanie je vytvorenie správy o zadaní 3, v ktorej zdokumentujete splenie jednotlivých bodov zadania. Správa bude súčasťou vašej stránky o Webovom publikovaní na GitHube.

Hodnotenie (max 14 bodov):

* opis typu dokumentu + opis účelu navrhnutých elementov - možnosť výberu (práve jedného) z variantov:
  * DTD (max 3 body)
  * XML Schema (max 4 body)
  * RELAX NG (max 4+1 bodov)
* vytvorenie ukážkovej XML prezentácie demonštrujúcej možnosti definície typu dokumentu (max 2 body)
* základný návrh XSL transformácií, ich vhodnosť, parametrizácia (max 3 body)
* vytvorenie XSLT pre konverziu prezentácie z XML -> XHTML+CSS (max 3 body)
  * každý slide bude v samostatnom XHTML súbore
* vytvorenie XSLT pre konverziu prezentácie XML -> PDF (max 2 body)

Výsledok zadania vložte do 7. 5. 23:59 do AISu ako jeden ZIP archív pomenovaný vaším AIS loginom (Z3-aislogin.zip). Archív musí obsahovať:

* zdrojové súbory a ďalšie súbory súvisiace s obsahom (napr. obrázky),
* skripty potrebné na preklad (dávkové súbory .bat),
* cieľový tvar súborov,
* sprievodný textový súbor (```_Z3-priezvisko.txt```), ktorý obsahuje zoznam súborov obsiahnutých v archíve a spôsob prekladu (transformáciu) do cieľového formátu.

Archív nesmie obsahovať žiadne externé knižnice (saxon, …).

---

#### **Riešenie**
