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

Za pomoci jazyka XML som vytvoril prezentáciu reprezentujúcu niekoľko typov slajdov. Štruktúru XML prezentácie som vytvoril prostredníctvom jazyka RELAX NG. Následne som vytvoril XSL súbor, ktorý tvorý šablónu pre transformáciu XML prezentácie do formátu XHTML. K XSL súboru som pripojil CSS súbor reprezentujúci štýl výstupného XHTML súboru. Súčasťou riešenia je aj XSL súbor pre transformáciu XML prezentácie do formátu PDF.

---

#### Štruktúra XML prezentácie
* koreňovým elementom je element ```presentation```, ktorý obsahuje minimálne jeden element ```slide```
* atribút ```type``` elementu ```slide``` určuje typ konkrétneho slajdu
* každý element ```slide``` musí obsahovať element ```title``` reprezentujúci nadpis daného slajdu
* o tom, čo je ďalším obsahom elementu ```slide``` rozhoduje už spomínaný atribút ```type```
* medzi základné elementy, ktoré môže ```slide```obsahovať sú ```list``` resp. trojúrovňový zoznam, ```image``` resp. obrázok, ```table``` resp. tabuľku alebo ```resource``` resp. zdroj
* jednotlivé typy slajdov obsahujú kombinácie základných elementov
* ```title-slide``` obsahuje okrem ```title``` iba autora
* ```content``` nemá žiadny obsah, pretože sa generuje automaticky
* ```list-only``` obsahuje trojúrovňový zoznam
* ```list-image``` obsahuje obrázok a trojúrovňový zoznam
* ```comparison``` obsahuje dva trojúrovňové zoznamy
* ```table-only``` obsahuje tabuľku s popisom
* ```image-only``` obsahuje obrázok s popisom
* ```resources``` obsahuje použité zdroje prezentácie
* XML prezentácia je uložená v súbore **presentation.xml**
* je valídna podľa schémy vytvorenej v jazyku RELAX NG uloženej v súbore **relax_ng.rng**
* validácia XML prezentácie bola testovaná v nástroji XMLBlueprint **Jing** procesorom

---

#### Typy slajdov vo formáte XHTML
* [Titulný slajd][1]{:target="_blank"}
* [Obsah][2]{:target="_blank"}
* [Zoznam][3]{:target="_blank"}
* [Zoznam-obrázok][4]{:target="_blank"}
* [Obrázok-zoznam][5]{:target="_blank"}
* [Obrázok][7]{:target="_blank"}
* [Porovnanie][8]{:target="_blank"}
* [Tabuľka][9]{:target="_blank"}
* [Zdroje][11]{:target="_blank"}

---

#### XSL pre transformáciu do XHTML
* uložený v súbore **transformation.xsl**
* je založený na princípe templatov podľa potreby pre každý typ slajdu a iné potrebné elementy
- v úvodnej časti sú prostredníctvom DTD definované tri súbory
  * ```style.css``` - CSS súbor reprezentujúci štýl výstupného XHTML súboru
  * ```nested_list.xsl``` - implementácia trojúrovňového zoznamu, ktorý som sa rozhodol definovať takto, pretože sa využíva vo viacerých častiach XSL súboru a mohlo by teda dôjsť k redudancii kódu
  * ```image.xsl``` - implementácia zobrazovania obrázkov, definovaný opäť z dôvodu, že sa používa vo viacerých častiach XSL súboru
- ```<xsl:template match="slide" priority="2">``` je template, ktorý obsahuje        
  * základnú html štruktúru výstupného XHTML súboru
  * funkciu ```result-document```, ktorá generuje každý slajd prezentácie do samostatného XHTML súboru
  * implementáciu pridávania čísel slajdov
* ďalej nasledujú templaty pre písma ```italic```, ```bold``` a ```underline```
* obsahom zvyšku XSL súboru sú templaty pre konkrétny typ slajdu
* každý z týchto templatov obsahuje potrebnú implementáciu transformácie do výslednej podoby podľa konkrétneho obsahu slajdu
* súbor automaticky generuje obsah s reálnymi klikateľnými odkazmi na jednotlivé slajdy resp. XHTML súbory
* tranformácia do formátu XHTML vykonával **SAXON**
- používateľ má možnosť zadať dva špeciálne parametre pri spúšťaní transformácie
  * ```page-number``` - umožňuje vypnúť generovanie čísel slajdov (defaultne generuje čísla)
  * ```font-type``` - umožňuje nastaviť vlastné písmo prezentácie (defaultne Thimes New Roman)

---

#### XSL pre transformáciu do PDF
* uložený v súbore **mytrans.xsl**
* založený na rovnakom princípe ako XSL pre transformáciu do XHTML
- v úvodnej časti sú prostredníctvom DTD definované dva súbory
  * ```nested_list_fo.xsl``` - implementácia trojúrovňového zoznamu, ktorý som sa
  rozhodol definovať takto, pretože sa využíva vo viacerých častiach XSL súboru a mohlo by teda dôjsť k redudancii kódu
  * ```image_fo.xsl``` - implementácia zobrazovania obrázkov, definovaný opäť z dôvodu, že sa používa vo viacerých častiach XSL súboru
* ```<xsl:template match="/">``` obsahuje základnú štruktúru pdf dokumentu, veľkosti slajdov, generovanie čísel slajdov ...
* súbor automaticky generuje obsah s reálnymi klikateľnými odkazmi na jednotlivé slajdy
* nasledujú rovnaké templaty ako pri predošlom XSL súbore
* namiesto html tagov a css štýlu sú využívané ```fo``` objekty a ich vlastnosti
* transformáciu do formátu PDF zabezpečuje **pdf_xep_mytrans.bat** bat súbor, rovnaký ako pri generovaní dokumentu v Docbooku

---

[1]: /images/1.xhtml
[2]: /images/2.xhtml
[3]: /images/3.xhtml
[4]: /images/4.xhtml
[5]: /images/5.xhtml
[7]: /images/7.xhtml
[8]: /images/8.xhtml
[9]: /images/9.xhtml
[11]: /images/11.xhtml
