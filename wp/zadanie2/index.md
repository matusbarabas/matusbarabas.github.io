---
layout: wp_layout
title: Zadanie 2
selected: webove_publikovanie
wp_selected: zadanie2
---

## Transformácia vybraného dokumentu do formátu DocBook

---

#### **Zadanie:**

Predmetom 2. zadania je spracovanie vybraného dokumentu (ideálne bakalárskeho projektu) z pôvodného ľubovoľného (Word, OpenOffice, LaTeX, …) formátu do formátu DocBook a vygenerovanie cieľového tvaru v PDF. Výsledný dokument bude mať rozsah minimálne 10 a maximálne 15 strán. Do rozsahu sa nezapočítavajú úvodné strany (obsah, zoznamy obrázkov a tabuliek), použitá literatúra a prílohy.

Požadované a kontrolné konštrukcie sú:

* štandardné členenie textu na kapitola, podkapitola, podpodkapitola, príloha, generovaný obsah,
* zvýraznenie slov, zvýraznenie členenia textu odrážkami alebo číslovaním,
* odkazy na iné časti vlastného dokumentu, prípadne odkazy na URL,
poznámka pod čiarou,
* zoznam použitej literatúry a zdrojov vrátane ich citácie v texte,
* vloženie obrázku a tabuliek, odkazy na ne v texte; zoznam obrázkov a tabuliek v úvode alebo závere textu,
* vytvorenie registra pojmov (indexu) s pojmami hierarchicky usporiadanými do dvoch úrovni, napríklad „cykly, while“, „cykly, for“ (najmenej ako ukážku na 10-15 pojmoch na predvedenie práce s registrom).

Súčasťou požiadaviek na zadanie je vytvorenie správy o zadaní 2, ktorá bude súčasťou vašej stránky o Webovom publikovaní na GitHube. Správa o rozsahu 150-250 slov bude obsahovať informácie o použitých elementoch a atribútoch, prípadne ukážky XML/XSLT demonštrujúce vykonané prispôsobenie DocBook šablon (nepovinné).

Na transformáciu zo zdrojového formátu DocBook do PDF použite upravenú šablónu na základe šablóny od Jiřího Koska (obsahuje i ukážku).

Výsledok 2. zadania vložte do **26. 03. 2016 23:59** do AISu ako jeden ZIP archív pomenovaný vaším AIS loginom (```Z2-aislogin.zip```). Archív musí obsahovať:

* zdrojové texty vo formáte DocBook a ďalšie súbory súvisiace s obsahom (napr. obrázky),
* skripty potrebné na preklad (dávkové súbory .bat)
* cieľový tvar súborov a pôvodný tvar textu bakalárskeho projektu (ideálne PDF),
* sprievodný textový súbor ```_Z1-aislogin.txt```, ktorý obsahuje zoznam súborov obsiahnutých v archíve a spôsob prekladu (transformáciu) autorského textu v DocBook do cieľového formátu.
* archív obsahovať najviac dva súbory navyše: github.url, s url vášho projektu na GitHub-e
Archív nesmie obsahovať žiadne externé knižnice (saxon, …).

---

#### **Riešenie:**

Na tranformáciu dokumentu z pôvodného formátu (vytvoreného v LaTeX) do formátu Docbook bola použitá moja rozpracovaná bakalárska práca. Okrem kompletnej zmeny súboru ```mojabp.xml``` boli vykonané zmeny aj v súbore ```thesis.xsl```, kde som pozmenil popisy obrázkov a tabuliek a upravil časť, v ktorej sa generujú zoznamy obrázkov a tabuliek. V súbore ```thesis-tp-fo.xsl``` boli prehodené title a meno autora a odsadzenia elementov.

#### **Splnenie požadovaných a kontrolných konštrukcií:**

#### Štandardné členenie textu na kapitola, podkapitola, podpodkapitola, príloha, generovaný obsah
Boli použité nasledovné tagy:
```
<book></book>
<bookinfo></bookinfo>  
<author></author>
<abstract></abstract>
<chapter></chapter>
<section></section>
<para></para>
<simpara></simpara>
<title><title>
<subtitle></subtitle>
```
---
#### Zvýraznenie slov, zvýraznenie členenia textu odrážkami alebo číslovaním
Na zvýraznenie slov som použil typ písma _italic_:
```
<emphasis>Monte-Carlo</emphasis>
```
ale aj typ písma **bold**:
```
<emphasis role="strong">server</emphasis>
```
Zvýraznenie členenia textu odrážkami:
```
<itemizedlist>
  <listitem>
    <para>oranžová - lopta</para>
  </listitem>
  <listitem>
    <para>zelená - ihrisko</para>
  </listitem>
  <listitem>
    <para>biela - čiary</para>
  </listitem>
  <listitem>
    <para>ružová - dresy robotov</para>
  </listitem>
  <listitem>
    <para>modrá - dresy robotov</para>
  </listitem>
  <listitem>
    <para>čiarna - všetko ostatné</para>
  </listitem>
</itemizedlist>
```
---
#### Odkazy na iné časti vlastného dokumentu, prípadne odkazy na URL, poznámka pod čiarou
Na odkazy na iné časti dokumentu som použil kon3trukciu ```<xref linkend='section_mrl_spl' />``` s odkazom na id ```  <section id="section_mrl_spl">```,
ale aj konštrukciu ```<link linkend='section_nao'>NAO robota</link>``` s odkazom taktiež na id danej sekcie.  
V mojom dokumente sa odkazujem aj na URL adresu, ktorú mám v poznámke pod čiarov:
```
<footnote>
  <para>
    <ulink url="http://www.robocup.org/a_brief_history_of_robocup"/>
  </para>
</footnote>
```
---
#### Zoznam použitej literatúry a zdrojov vrátane ich citácie v texte
Zoznam použitej literatúry:
```
<bibliography>
  <title>Literatúra</title>

  <bibliomixed id="bib.upennalizer"><abbrev>upennalizers</abbrev>Akatsuka,
    Christopher He, Yizheng Li, Jianqiao Mushonga, Tatenda Poudel, Sagar Zhu,
    Junda Automation, General Robotics:
    <title>The UPennalizers RoboCup 2015 Standard Platform League
    Team Description Paper</title>.
    Pennsylvania: University of Pennsylvania, 2015. 24 s.
  </bibliomixed>
    ...
<bibliography>
```
Citácie v texte pomocou ```<xref linkend="bib.upennalizer" />``` a ```<citation>upennalizers</citation>``` pri obrázkoch, pretože ```xref``` hádzalo do zoznamu obrázkov celé zdroje.
---
#### Vloženie obrázku a tabuliek, odkazy na ne v texte; zoznam obrázkov a tabuliek v úvode alebo závere textu
Obrázok:
```
<figure id="logo_bender"><title>
    <emphasis>Logo tímu Bender</emphasis>
      <footnote>
        <para>
          <ulink url="http://labss2.fiit.stuba.sk/TeamProject/2015/team19is-si/ine/logo.png"/>
        </para>
      </footnote>
    </title>
    <mediaobject>
      <imageobject>
        <imagedata align="center" fileref="images/bender.png" format="PNG" scale="80"/>
      </imageobject>
    </mediaobject>
</figure>
```
s odkazom ``` <xref linkend="logo_bender"/>```.  
Tabuľka:

```
<table id="table_robocup" xml:id="ex.calstable" frame='all'>
  <title><emphasis>Výsledky odohraných turnajov</emphasis></title>
  <tgroup cols='6' align='center' colsep='1' rowsep='1'>
    <colspec colname='c1'/>
    <colspec colname='c2'/>
    <colspec colname='c3'/>
    <colspec colnum='5' colname='c5'/>
    <thead>
      <row>
        <entry morerows='1' valign='middle'><para>Rok</para></entry>
        <entry morerows='1' valign='middle'><para>Mesto</para></entry>
        <entry namest="c3" nameend="c5" align="center">Finále</entry>
        <entry morerows='1' valign='middle'><para>Tretie Miesto</para></entry>
      </row>
      <row>
        <entry>Prvé miesto</entry>
        <entry>Skóre</entry>
        <entry>Druhé miesto</entry>
      </row>
    </thead>
    <tbody>
      <row>
        <entry>2016</entry>
        <entry>Leipzig, Nemecko</entry>
        <entry>B-Human</entry>
        <entry>3-0</entry>
        <entry>UT Austin Villa</entry>
        <entry>Nao-Team HTWK</entry>
      </row>
      <row>
        <entry>2015</entry>
        <entry>Hefei, China</entry>
        <entry>UNSW Australia</entry>
        <entry>3-1</entry>
        <entry>B-Human</entry>
        <entry>Nao-Team HTWK</entry>
      </row>
      <row>
        <entry>2014</entry>
        <entry>Jao Pessoa - Brazil</entry>
        <entry>rUNSWift</entry>
        <entry>5-1</entry>
        <entry>Nao-Team HTWK</entry>
        <entry>B-Human</entry>
      </row>
      <row>
        <entry>2013</entry>
        <entry>Eindhoven-Holandsko</entry>
        <entry>B-Human</entry>
        <entry>6-2</entry>
        <entry>Nao-Team HTWK</entry>
        <entry>UT Austin Villa</entry>
      </row>
      <row>
        <entry>2012</entry>
        <entry>Mexico City - Mexico</entry>
        <entry>UT Austin Villa</entry>
        <entry>4-2</entry>
        <entry>B-Human</entry>
        <entry>rUNSWift</entry>
      </row>
    </tbody>
  </tgroup>
</table>
```
s odkazom ```<xref linkend="table_robocup" />```.  
Zoznam obrázkov a tabuliek vytvorení zmenou súboru ```thesis.xsl```:
```
<xsl:param name="generate.toc">
  book,title,toc,figure,table
</xsl:param>
```
---
#### Vytvorenie registra pojmov (indexu) s pojmami hierarchicky usporiadanými do dvoch úrovni, napríklad „cykly, while“, „cykly, for“ (najmenej ako ukážku na 10-15 pojmoch na predvedenie práce s registrom)
Vytvorenie registra:
```
<index>
  <title>Register pojmov</title>
</index>
```
Pojmy usporiadané do dvoch úrovní:
```
<indexterm>
  <primary>Simspark</primary>
  <secondary>Server</secondary>
</indexterm>
```
