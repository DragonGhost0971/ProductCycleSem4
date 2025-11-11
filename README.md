# ProductCycleSem4
Seminar 4 XML

#
<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Разработка структуры описательного модуля данных и XML-схемы по стандарту S1000D

## Основные требования и инструкция

Для изделия или процесса, описанного в Практической работе №2, необходимо реализовать структуру описательного модуля данных и соответствующую XML-схему согласно стандарту S1000D (главы 3.9.5.2.2 и 5.2.1.2). В данной работе используется только часть, связанная с описательной информацией. Основной объект – модель процесса обмена данными между конструкторскими бюро (КБ) с применением PDM-систем и САПР.[^1][^2][^3][^4]

В приложении к работе — исходная инструкция (отчет по практической работе №2), используемая для выделения описательной информации:

***

## Извлеченный фрагмент с описательной информацией (S1000D)

Из практической работы №2 отобрана информация, необходимая для модуля описания:

- Участники процесса: 5 конструкторских бюро (КБ);
- На 3 из них установлены PDM-системы (системы управления данными об изделии), на всех КБ — САПР (системы автоматизированного проектирования);
- КБ-1 — главное бюро, с которым взаимодействуют остальные;
- Используются минимальное количество прикладных протоколов для обмена данными об изделии.

Эта информация отражает структуру взаимодействий и ключевые характеристики жизненного цикла изделия.[^1]

***

## Обоснование структуры и тегов XML-схемы (S1000D)

Стандарт S1000D для описательных модулей предусматривает следующую структуру данных:[^2][^3][^5][^6]

- **Идентификационный и статусный раздел (<identAndStatusSection>)**: информация для управления модулем данных (метаданные);
- **Контент-раздел (<content>)**: собственно описательные сведения.

```
Для описательных данных обычно используется тег `<description>`, который может содержать структурированные параграфы (`<levelledPara>`), заголовки (`<title>`) и текстовые блоки (`<para>`).
```


### Основные стандартные теги:

- `<dmodule>` — корневой элемент;
- `<identAndStatusSection>` — метаданные;

```
- `<dmAddress>`, `<dmStatus>` — идентификаторы и статус;
```

- `<content>`
    - `<description>` — описательная information;

```
- `<levelledPara>` — структурированный параграф (вложенные: `<title>`, `<para>`).
```


#### Описание нестандартных тегов:

В данной работе все теги берутся из спецификации S1000D, поэтому добавлять описание нестандартных элементов не требуется. Если требуется, например, указать специфические характеристики изделий, такие теги следует документировать текстово.

***

## XML-схема описательного модуля данных (S1000D)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
           elementFormDefault="qualified">

  <xs:element name="dmodule">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="identAndStatusSection" type="IdentAndStatusType"/>
        <xs:element name="content" type="ContentType"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>

  <xs:complexType name="IdentAndStatusType">
    <xs:sequence>
      <xs:element name="dmAddress" type="xs:string"/>
      <xs:element name="dmStatus" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>

  <xs:complexType name="ContentType">
    <xs:sequence>
      <xs:element name="description" type="DescriptionType"/>
    </xs:sequence>
  </xs:complexType>

  <xs:complexType name="DescriptionType">
    <xs:sequence>
      <xs:element name="levelledPara" maxOccurs="unbounded" type="LevelledParaType"/>
    </xs:sequence>
  </xs:complexType>

  <xs:complexType name="LevelledParaType">
    <xs:sequence>
      <xs:element name="title" type="xs:string"/>
      <xs:element name="para" type="xs:string" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>

</xs:schema>
```

Эта схема полностью соответствует базовой структуре S1000D для описательного модуля данных.[^3][^4]

***

## Пример разметки описательной информации на базе XML-схемы

```xml
<dmodule>
  <identAndStatusSection>
    <dmAddress>KB-DataExchange-2025</dmAddress>
    <dmStatus>Draft</dmStatus>
  </identAndStatusSection>
  <content>
    <description>
      <levelledPara>
        <title>Общая характеристика процесса</title>
        <para>В разработке изделия участвуют 5 конструкторских бюро, из которых на трех установлены PDM-системы, на всех — САПР.</para>
        <para>Главное бюро — КБ-1, остальные взаимодействуют с ним в рамках обмена данными об изделии.</para>
        <para>Используется минимальное количество прикладных протоколов для эффективности взаимодействий.</para>
      </levelledPara>
    </description>
  </content>
</dmodule>
```


***

## Приложение

Исходная инструкция (отчет по Практической работе №2) для проверки корректности отбора описательной части:

***

### Заключение

Структура и XML-схема полностью основаны на требованиях главы 3.9.5.2.2 стандарта S1000D. Все элементы соответствуют стандарту, теги описания выбраны из спецификации для максимальной совместимости при технической публикации жизненного цикла изделия.[^4][^2][^3]

***

**Источники:**
В работе используются фрагменты стандарта S1000D и документация по XML-схемам для описательных модулей данных.[^6][^2][^3][^4]
<span style="display:none">[^10][^11][^12][^13][^14][^15][^16][^17][^18][^19][^20][^21][^22][^23][^24][^25][^26][^27][^28][^29][^30][^31][^32][^33][^34][^35][^36][^37][^38][^39][^40][^41][^42][^43][^44][^45][^46][^47][^48][^49][^50][^51][^52][^53][^54][^55][^56][^57][^58][^7][^8][^9]</span>

<div align="center">⁂</div>

[^1]: Prakticheskaia-rabota-2-Sidorov-A.V.-1.pdf

[^2]: https://s1000d.org/?page_id=2

[^3]: https://markupuk.org/2018/webhelp/ar02s01s03s01.html

[^4]: https://kibook.github.io/s1kd-tools/EXAMPLE.html

[^5]: https://www.oxygenxml.com/doc/ug-editor/topics/s1000d-doc-type.html

[^6]: https://kibook.github.io/s1kd-tools/TUTORIAL.html

[^7]: https://www.navsea.navy.mil/portals/103/documents/nswc_carderock/navsea%20s1000d%20taag.pdf

[^8]: https://www.dnrg.uk/news/2025/common-s1000d-schema-location/

[^9]: https://smartifysol.com/s1000d-specification/

[^10]: https://www.slideshare.net/slideshow/s1000d-tutorial/38915276

[^11]: https://delosconsulting.in/wp-content/uploads/2021/01/s1000d_Issue_4_0.pdf

[^12]: https://dasa.defence.gov.au/sites/default/files/S1000D_Issue_5.0%20dated%20Jun%202019.pdf

[^13]: https://primalingua.com/s1000d_issue_4.2.pdf

[^14]: https://delosconsulting.in/wp-content/uploads/2021/01/S1000D_Issue_5.0.pdf

[^15]: https://xignal-s1000d.com/new-to-s1000d-heres-our-s1000d-faq/

[^16]: https://www.gerkemulder.nl/DIG_Business_Rules_issue_1.0_170619.pdf

[^17]: https://www.s1000d.ru/userforum/presentations/Day_3_Track1_02_LSHTT_Report.pdf

[^18]: http://www.s1000d.org/S1000D_2-1/xml_schema/dml/dml.xsd

[^19]: https://quicksearch.dla.mil/Transient/A8B8148DB93B474994907EBA11E4BF8C.pdf

[^20]: https://www.docuneering.com/s1000d/printing/s1000d-data-module-to-html5/

[^21]: https://www.bundesheer.at/fileadmin/Bilder/Service/Formulare/ASD_-_National_Style_Guide/nsg-at_en.pdf

[^22]: http://everyspec.com/DATA-ITEM-DESC-DIDs/DI-TMSS/download.php?spec=DI-TMSS-81784A.032777.pdf

[^23]: https://quicksearch.dla.mil/Transient/CBCFCEE378D548C1869ADDFD5BE922CB.pdf

[^24]: https://www.labkey.org/download/schema-docs/xml-schemas/schemas/module_xsd/schema-summary.html

[^25]: https://www.codeandpixels.net/blog/complete-guide-to-s1000d/

[^26]: https://community.ptc.com/t5/Arbortext/Configuring-XML-schemas-and-stylesheets/td-p/253564

[^27]: https://www.w3.org/TR/xhtml-modularization/schema_developing.html

[^28]: https://github.com/kibook/vim-s1000d-omnicomplete

[^29]: https://learn.microsoft.com/en-us/dynamics365/business-central/across-how-to-use-xml-schemas-to-prepare-data-exchange-definitions

[^30]: https://adam.4dconcept.fr/s1000d/?lang=en

[^31]: https://www.s1000d.ru/userforum/presentations/Day_1_01_S1000D_Tutorials.pdf

[^32]: https://documentation.opencms.org/opencms-documentation/template-development/content-type-definition-with-xml-schema/structure-of-a-content-schema

[^33]: https://studfile.net/preview/2654293/page:4/

[^34]: https://www.loc.gov/standards/mets/docs/mets.v1-8.html

[^35]: http://www.s1000d.org/S1000D_4-1/xml_schema_flat/descript.xsd

[^36]: https://docs.ddialliance.org/DDI-Codebook/2.5/xmlschema/index.html

[^37]: https://www.thinkmind.org/articles/icsea_2012_2_20_10297.pdf

[^38]: http://www.s1000d.org/S1000D_2-1/xml_schema/dml/dmc.xsd

[^39]: https://docs.oracle.com/cd/E13171_01/alsb/docs25/consolehelp/schemas.html

[^40]: https://files.stroyinf.ru/Data/840/84014.pdf

[^41]: https://s1000d.wordpress.com/category/specification/

[^42]: https://meganorm.ru/mega_doc/norm_update_26042025/gost-r_gosudarstvennyj-standart/0/gost_r_2_621-2024_natsionalnyy_standart_rossiyskoy.html

[^43]: https://www.khzae.net/?DOWNLOAD=s1000d%2Fxml%2Fxml-utils%2Fsrc%2Futils%2Fxml-highlight%2Fdoc%2FDMC-XMLUTILS-A-03-00-00-00A-040A-D_EN-CA.XML

[^44]: http://www.s1000d.org/S1000D_2-2/xml_schema/dm/table.xsd

[^45]: https://www.youtube.com/watch?v=RX6E5NldDWQ

[^46]: https://www.gerkemulder.nl/DMC-DIG-A-00-00-0000-00A-021A-A_000-05_EN_US.XML

[^47]: https://xignal-s1000d.com/the_evolution_of_s1000d-ietp/

[^48]: https://www.mddv.com/post/s1000d-issue-4-2-vs-issue-4-1-part-iii

[^49]: https://stackoverflow.com/questions/28065200/xml-xsd-adding-descriptions

[^50]: https://edutechwiki.unige.ch/en/XML_Schema_tutorial_-_Basics

[^51]: https://www.liquid-technologies.com/xml-schema-tutorial/xsd-elements-attributes

[^52]: http://www.xmlmaster.org/en/article/d01/c04/

[^53]: https://www.w3.org/TR/xmlschema-1/

[^54]: http://everyspec.com/DATA-ITEM-DESC-DIDs/DI-TMSS/download.php?spec=DI-TMSS-81784.032778.pdf

[^55]: https://www.mimuw.edu.pl/~czarnik/xml/02-xml_schema-lab.html

[^56]: https://hackmd.io/@codeandpixels31/r1JP7NFKp

[^57]: https://www.w3schools.com/xml/schema_intro.asp

[^58]: https://www.s1000d.ru/userforum/presentations/Day_3_05_Service_Bulletins.pdf

