# Семинар 4
## Структура описательного модуля данных и XML-схема для разработки конструкции изделия

### Структура описательного модуля данных

Модуль данных в соответствии со спецификацией S1000D состоит из двух основных частей:[^6][^11][^7]

#### 1. Идентификационно-статусная часть (Identification and Status Section)

Эта часть содержит метаданные для управления модулем в общей базе данных (CSDB):

**Адрес модуля данных (dmAddress)**

- Код модуля данных (DMC) - уникальный идентификатор
- Название модуля данных
- Тип информации

**Статус модуля данных (dmStatus)**

- Статус безопасности
- Информация об ответственных лицах
- Применимость
- Контроль качества
- Ссылки на бизнес-правила (BREX)[^12]


#### 2. Содержательная часть (Content Section)

Для описательного модуля используется схема **descript.xsd**, которая содержит следующие основные элементы:[^5][^13][^6]

**Описание изделия (description)**

- Параграфы с текстовой информацией
- Предупреждения и примечания
- Ссылки на иллюстрации

**Технические данные (techData)**

- Характеристики изделия
- Спецификации компонентов
- Параметры конфигурации


### XML-схема описательного модуля данных

Ниже представлена XML-схема для описательного модуля данных о разработке конструкции изделия:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<dmodule xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="http://www.s1000d.org/S1000D_4-2/xml_schema_flat/descript.xsd">
  
  <!-- ========================================== -->
  <!-- ИДЕНТИФИКАЦИОННО-СТАТУСНАЯ ЧАСТЬ         -->
  <!-- ========================================== -->
  <identAndStatusSection>
    
    <!-- Адрес модуля данных -->
    <dmAddress>
      <!-- Код модуля данных (DMC) -->
      <dmIdent>
        <!-- Код идентификации модели (АДБ-22-06 из задания) -->
        <dmCode modelIdentCode="ADB2206" systemDiffCode="AAA" 
                systemCode="00" subSystemCode="0" subSubSystemCode="0" 
                assyCode="00" disassyCode="00" disassyCodeVariant="A" 
                infoCode="040" infoCodeVariant="A" itemLocationCode="D"/>
        <!-- Язык модуля данных -->
        <language languageIsoCode="ru" countryIsoCode="RU"/>
        <!-- Номер издания -->
        <issueInfo issueNumber="001" inWork="00"/>
      </dmIdent>
      
      <!-- Название модуля данных -->
      <dmAddressItems>
        <issueDate year="2025" month="11" day="11"/>
        <dmTitle>
          <techName>Система разработки конструкции изделия</techName>
          <infoName>Описание архитектуры обмена данными между КБ</infoName>
        </dmTitle>
      </dmAddressItems>
    </dmAddress>
    
    <!-- Статус модуля данных -->
    <dmStatus issueType="new">
      <!-- Классификация безопасности -->
      <security securityClassification="01"/>
      
      <!-- Ответственные лица -->
      <responsiblePartnerCompany enterpriseCode="MGTU-STANKIN">
        <enterpriseName>МГТУ СТАНКИН</enterpriseName>
      </responsiblePartnerCompany>
      
      <!-- Информация о создателе -->
      <originator enterpriseCode="KB1">
        <enterpriseName>Конструкторское бюро № 1 (главное)</enterpriseName>
      </originator>
      
      <!-- Применимость -->
      <applic>
        <displayText>
          <simplePara>Применимо для всех участников разработки</simplePara>
        </displayText>
      </applic>
      
      <!-- Ссылка на бизнес-правила -->
      <brexDmRef>
        <dmRef>
          <dmRefIdent>
            <dmCode modelIdentCode="S1000D" systemDiffCode="A" 
                    systemCode="00" subSystemCode="0" subSubSystemCode="0" 
                    assyCode="00" disassyCode="00" disassyCodeVariant="A" 
                    infoCode="022" infoCodeVariant="A" itemLocationCode="D"/>
          </dmRefIdent>
        </dmRef>
      </brexDmRef>
      
      <!-- Контроль качества -->
      <qualityAssurance>
        <unverified/>
      </qualityAssurance>
    </dmStatus>
  </identAndStatusSection>
  
  <!-- ========================================== -->
  <!-- СОДЕРЖАТЕЛЬНАЯ ЧАСТЬ                     -->
  <!-- ========================================== -->
  <content>
    <description>
      
      <!-- Раздел 1: Общее описание системы -->
      <levelledPara>
        <title>Общее описание системы разработки</title>
        <para>
          Система распределенной разработки конструкции изделия включает 
          пять конструкторских бюро (КБ-1, КБ-2, КБ-3, КБ-4, КБ-5), 
          взаимодействующих в процессе проектирования сложного механического изделия.
        </para>
        
        <!-- Подраздел: Архитектура системы -->
        <levelledPara>
          <title>Архитектура системы обмена данными</title>
          <para>
            КБ-1 является главным конструкторским бюро, координирующим 
            деятельность остальных участников. Обмен данными об изделии 
            осуществляется на основе стандарта ISO 10303 STEP с использованием 
            прикладных протоколов (ПП).
          </para>
        </levelledPara>
        
        <!-- Подраздел: Состав программных средств -->
        <levelledPara>
          <title>Состав программных средств</title>
          <para>
            Все пять конструкторских бюро оснащены системами 
            автоматизированного проектирования (САПР). Три конструкторских 
            бюро (КБ-1, КБ-2, КБ-3) дополнительно используют системы управления 
            данными об изделии (PDM-системы).
          </para>
          
          <!-- Таблица распределения систем -->
          <table>
            <title>Распределение программных систем по КБ</title>
            <tgroup cols="4">
              <colspec colname="c1"/>
              <colspec colname="c2"/>
              <colspec colname="c3"/>
              <colspec colname="c4"/>
              <thead>
                <row>
                  <entry>Конструкторское бюро</entry>
                  <entry>САПР</entry>
                  <entry>PDM-система</entry>
                  <entry>Прикладной протокол</entry>
                </row>
              </thead>
              <tbody>
                <row>
                  <entry>КБ-1 (главное)</entry>
                  <entry>Да</entry>
                  <entry>Да</entry>
                  <entry>ПП-1, ПП-2</entry>
                </row>
                <row>
                  <entry>КБ-2</entry>
                  <entry>Да</entry>
                  <entry>Да</entry>
                  <entry>ПП-1, ПП-3</entry>
                </row>
                <row>
                  <entry>КБ-3</entry>
                  <entry>Да</entry>
                  <entry>Да</entry>
                  <entry>ПП-1, ПП-4</entry>
                </row>
                <row>
                  <entry>КБ-4</entry>
                  <entry>Да</entry>
                  <entry>Нет</entry>
                  <entry>ПП-1, ПП-5</entry>
                </row>
                <row>
                  <entry>КБ-5</entry>
                  <entry>Да</entry>
                  <entry>Нет</entry>
                  <entry>ПП-1, ПП-6</entry>
                </row>
              </tbody>
            </tgroup>
          </table>
        </levelledPara>
      </levelledPara>
      
      <!-- Раздел 2: Прикладные протоколы STEP -->
      <levelledPara>
        <title>Прикладные протоколы ISO 10303 STEP</title>
        <para>
          Для обмена данными об изделии используются прикладные протоколы 
          стандарта ISO 10303 STEP. Основным протоколом является ПП-1, 
          который поддерживается всеми участниками и обеспечивает обмен 
          базовой конструкторской информацией.
        </para>
        
        <!-- Подраздел: ПП-1 (общий протокол) -->
        <levelledPara>
          <title>ПП-1: Базовый протокол обмена</title>
          <para>
            Прикладной протокол ПП-1 соответствует ISO 10303-203 (Configuration 
            Controlled 3D Designs) и включает следующие типы данных:
          </para>
          <randomList>
            <listItem>
              <para>Геометрические данные (твердотельные модели, поверхности, каркасы)</para>
            </listItem>
            <listItem>
              <para>Топологическая информация о сборках</para>
            </listItem>
            <listItem>
              <para>Данные конфигурационного управления</para>
            </listItem>
            <listItem>
              <para>Метаданные о версиях и изменениях конструкции</para>
            </listItem>
          </randomList>
        </levelledPara>
        
        <!-- Подраздел: Специализированные протоколы -->
        <levelledPara>
          <title>Специализированные прикладные протоколы</title>
          <para>
            Каждое конструкторское бюро использует собственный специализированный 
            протокол (ПП-2...ПП-6) для внутренних процессов и специфичных 
            требований к представлению данных.
          </para>
          
          <note>
            <notePara>
              Использование минимального количества прикладных протоколов 
              (один общий ПП-1 и по одному специализированному на каждое КБ) 
              оптимизирует процесс обмена данными и снижает сложность интеграции.
            </notePara>
          </note>
        </levelledPara>
      </levelledPara>
      
      <!-- Раздел 3: Процесс обмена данными -->
      <levelledPara>
        <title>Процесс обмена данными между конструкторскими бюро</title>
        
        <!-- Подраздел: Централизованная модель обмена -->
        <levelledPara>
          <title>Централизованная модель обмена (Вариация 1)</title>
          <para>
            В первой вариации все конструкторские бюро напрямую взаимодействуют 
            с главным КБ-1. КБ-1 выполняет функции координирующего центра и 
            обеспечивает согласованность данных между всеми участниками проекта.
          </para>
          <para>
            Обмен данными осуществляется с использованием протокола ПП-1 
            для передачи основной конструкторской информации между КБ-1 и 
            другими бюро. Внутри каждого КБ используются специализированные 
            протоколы для работы с локальными данными.
          </para>
        </levelledPara>
        
        <!-- Подраздел: Иерархическая модель обмена -->
        <levelledPara>
          <title>Иерархическая модель обмена (Вариации 2 и 3)</title>
          <para>
            Во второй и третьей вариациях используется иерархическая структура 
            обмена данными, где некоторые КБ являются дочерними по отношению 
            к другим. Это позволяет распределить нагрузку по согласованию 
            данных и организовать более эффективную работу над подсистемами изделия.
          </para>
        </levelledPara>
        
        <!-- Предупреждение -->
        <warning>
          <warningAndCautionPara>
            При обмене данными необходимо обеспечить контроль версий и 
            синхронизацию изменений между всеми участниками для предотвращения 
            конфликтов данных и потери информации.
          </warningAndCautionPara>
        </warning>
      </levelledPara>
      
      <!-- Раздел 4: Структура данных об изделии -->
      <levelledPara>
        <title>Структура данных об изделии</title>
        <para>
          Данные об изделии организованы в соответствии с принципами 
          стандарта ISO 10303 и включают следующие основные компоненты:
        </para>
        
        <!-- Подраздел: Геометрические данные -->
        <levelledPara>
          <title>Геометрические данные</title>
          <para>
            Геометрическая модель изделия представлена в виде твердотельных 
            моделей компонентов и сборок. Каждый компонент имеет уникальный 
            идентификатор и связан с технической документацией.
          </para>
        </levelledPara>
        
        <!-- Подраздел: Конфигурационные данные -->
        <levelledPara>
          <title>Конфигурационные данные</title>
          <para>
            Конфигурационные данные определяют состав изделия, версии 
            компонентов, правила сборки и применимость различных вариантов 
            конструкции. Эти данные управляются через PDM-системы в КБ-1, 
            КБ-2 и КБ-3.
          </para>
        </levelledPara>
        
        <!-- Подраздел: Метаданные -->
        <levelledPara>
          <title>Метаданные</title>
          <para>
            Метаданные включают информацию об авторах изменений, датах 
            модификаций, статусе согласования, ссылках на связанные 
            документы и другую управляющую информацию, необходимую для 
            организации коллективной работы.
          </para>
        </levelledPara>
      </levelledPara>
      
      <!-- Раздел 5: Требования к системам -->
      <levelledPara>
        <title>Требования к программным системам</title>
        
        <!-- Подраздел: Требования к САПР -->
        <levelledPara>
          <title>Требования к системам САПР</title>
          <para>
            Системы САПР, используемые в конструкторских бюро, должны 
            поддерживать экспорт и импорт данных в формате STEP в 
            соответствии с протоколом ISO 10303-203 (AP203) или 
            ISO 10303-214 (AP214).
          </para>
        </levelledPara>
        
        <!-- Подраздел: Требования к PDM-системам -->
        <levelledPara>
          <title>Требования к PDM-системам</title>
          <para>
            PDM-системы должны обеспечивать управление версиями, контроль 
            доступа, отслеживание изменений и интеграцию с системами САПР 
            для автоматической синхронизации конструкторских данных.
          </para>
        </levelledPara>
      </levelledPara>
      
    </description>
  </content>
</dmodule>
```


### Обоснование структуры XML-схемы

**1. Идентификационно-статусная часть**

Код модуля данных (DMC) построен согласно требованиям главы 5.2.1.2 спецификации S1000D:[^13][^14]

- **modelIdentCode**: "ADB2206" - идентификатор модели из задания
- **systemCode**: "00" - код системы (общая система разработки)
- **infoCode**: "040" - код описательной информации
- **itemLocationCode**: "D" - проектные данные

Статусная секция включает ссылку на бизнес-правила (BREX), что соответствует главе 3.9.5.2.2 спецификации и обеспечивает валидацию модуля.[^12]

**2. Содержательная часть**

Структура содержательной части соответствует схеме descript.xsd и использует:[^5][^6]

- **levelledPara**: для иерархической организации информации
- **table**: для структурированного представления данных о распределении систем
- **randomList**: для перечисления типов данных в протоколах
- **note** и **warning**: для важных замечаний и предупреждений

**3. Интеграция с ISO 10303 STEP**

Схема предусматривает описание прикладных протоколов ISO 10303, что обеспечивает совместимость с процессом обмена данными, описанным в Практическом задании №2.[^9][^15][^1][^8]

### Преимущества предложенной структуры

1. **Модульность**: Описательный модуль является самостоятельной информационной единицей, которая может повторно использоваться в различных публикациях[^7][^6]
2. **Расширяемость**: Структура позволяет добавлять новые разделы и детализировать информацию без изменения базовой схемы[^4][^11]
3. **Стандартизация**: Соответствие спецификации S1000D обеспечивает совместимость с международными стандартами технической документации[^16][^2]
4. **Управляемость**: Идентификационно-статусная часть содержит всю необходимую информацию для управления модулем в CSDB[^17][^18]
5. **Интероперабельность**: Интеграция с ISO 10303 STEP обеспечивает обмен данными между различными программными системами[^19][^8][^9]

### Рекомендации по использованию

Разработанный описательный модуль данных должен быть размещен в общей базе исходных данных (CSDB) и связан с другими модулями данных проекта. Для полноценного описания системы разработки рекомендуется создать дополнительные модули:[^3][^11][^17]

- **Процедурный модуль** (proced.xsd) - для описания процессов обмена данными
- **Модуль каталога деталей** (ipd.xsd) - для описания структуры изделия
- **Модуль планирования** (schedul.xsd) - для графика разработки

Данная структура обеспечивает полноту документирования процесса распределенной разработки конструкции изделия с использованием современных международных стандартов технической документации.
<span style="display:none">[^20][^21][^22][^23][^24][^25][^26][^27][^28][^29][^30][^31][^32][^33][^34][^35][^36][^37][^38][^39][^40][^41][^42][^43][^44][^45][^46][^47][^48][^49][^50][^51][^52][^53][^54][^55][^56][^57][^58][^59][^60]</span>

<div align="center">⁂</div>

[^1]: Prakticheskaia-rabota-2-Sidorov-A.V.-1.pdf

[^2]: https://s1000d.ru/userforum/2010/summary/index.html?view=print

[^3]: https://cals.ru/sites/default/files/downloads/tgb/Code.pdf

[^4]: https://ru.wikipedia.org/wiki/S1000D

[^5]: https://www.navsea.navy.mil/portals/103/documents/nswc_carderock/navsea%20s1000d%20taag.pdf

[^6]: https://markupuk.org/2018/webhelp/ar02s01s03s01.html

[^7]: https://s1000d.org/?page_id=2

[^8]: https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=821600

[^9]: https://en.wikipedia.org/wiki/ISO_10303

[^10]: https://www.datakit.com/en/step_protocols.php

[^11]: https://www.oxygenxml.com/doc/ug-editor/topics/s1000d-doc-type.html

[^12]: https://www.pennantplc.com/s1000d-business-rules/

[^13]: https://www.bundesheer.at/fileadmin/Bilder/Service/Formulare/ASD_-_National_Style_Guide/nsg-at_en.pdf

[^14]: https://smartifysol.com/s1000d-specification/

[^15]: https://keytodata.com/en/glossary/step-application-protocols-ap203-ap214-ap242/

[^16]: https://cals.ru/sites/default/files/downloads/conf/20130531_02_s1000d_41_chto_novogo_zanozin.pdf

[^17]: https://cals.ru/sites/default/files/downloads/tgb/MU S1000D_1.pdf

[^18]: https://itorum.ru/articles/semejstvo-produktov-arbortext/

[^19]: https://josephwebb.net/step_files_responsive.html

[^20]: https://fedresurs-demo.interfax.ru/helps/Sfacts/Спецификация требований на загрузку сообщений из xml-файлов (версия 1.14 действует с 27.01.2017).pdf

[^21]: https://studfile.net/preview/11070075/page:84/

[^22]: https://www.s1000d.ru/userforum/presentations/Day_3_Track2_03_UAC_Experience_PTS_RU.pdf

[^23]: https://old.cals.ru/standards/nd_ils/s1000DR/index.html

[^24]: https://philosoft-services.com/content/ru/articles/s1000dcat.html

[^25]: https://www.aviationunion.ru/media/news/839/

[^26]: https://www.aviationunion.ru/upload/medialibrary/20d/81091siqponukfdtuemgcbqn9ll177ks/PZ_1.2.323_1.091.20_pervayaredaktsiya.pdf

[^27]: https://cargo.rzd.ru/api/media/resources/1870539?action=download

[^28]: http://www.s1000d.org/S1000D_2-1/xml_schema/dml/dml.xsd

[^29]: https://www.gosniias.ru/pages/27/rndocs.pdf

[^30]: https://mdlp.crpt.ru/static/document/api_mdlp_ru.pdf

[^31]: https://meganorm.ru/Data/662/66295.pdf

[^32]: https://www.aeroflot.ru/media/aflfiles/monitoring_tsen/04_2023/forma_kp-140423.docx

[^33]: https://cyberleninka.ru/article/n/razvitie-sistemy-garmonizatsii-i-tsifrovizatsii-standartov-dlya-uvelicheniya-doli-avtomatizirovannogo-dokumentooborota-v

[^34]: https://www.docuneering.com/s1000d/demo/

[^35]: https://www.youtube.com/watch?v=RX6E5NldDWQ

[^36]: https://delosconsulting.in/wp-content/uploads/2021/01/s1000d_Issue_4_0.pdf

[^37]: https://quicksearch.dla.mil/Transient/A8B8148DB93B474994907EBA11E4BF8C.pdf

[^38]: https://www.s1000d.ru/userforum/presentations/Day_3_02_Whats_New_4_1.pdf

[^39]: https://primalingua.com/s1000d_issue_4.2.pdf

[^40]: https://www.s1000d.ru/userforum/presentations/Day_1_01_S1000D_Tutorials.pdf

[^41]: https://www.slideshare.net/slideshow/sdls1000d-training-44242973/44242973

[^42]: https://pdfcoffee.com/s1000d-pocket-guide-pdf-free.html

[^43]: https://xignal-s1000d.com/new-to-s1000d-heres-our-s1000d-faq/

[^44]: https://www.docuneering.com/s1000d/demo/pdf/s1000d-issue-2.3/PMC-S1000DBIKE-X1234-00023-00_002-00_EN-US.pdf

[^45]: https://adam.4dconcept.fr/s1000d/?lang=en

[^46]: https://cdn.standards.iteh.ai/samples/86075/0e6c8489b6fc4236940fc715f78253ff/ISO-TS-10303-15-2024.pdf

[^47]: https://www.navsea.navy.mil/Home/Warfare-Centers/NSWC-Carderock/Resources/Technical-Information-Systems/Navy-XML-SGML-Repository/DTDs-Schemas/ISO-10303-Ship-Product-Model-Data-Schema-Suite/ISO-10303-Ship-Product-Model-Data-Schema-Suite-D/

[^48]: https://www.oasis-open.org/standard/plcslibv1-0/

[^49]: https://www.iso.org/obp/ui/

[^50]: https://www.iso.org/standard/38310.html

[^51]: https://www.raypcb.com/step-ap203-vs-ap214-vs-ap242/

[^52]: https://meganorm.ru/Data/792/79232.pdf

[^53]: https://www.inderscienceonline.com/doi/abs/10.1504/IJPLM.2005.007347

[^54]: https://www.capvidia.com/blog/best-step-file-to-use-ap203-vs-ap214-vs-ap242

[^55]: https://www.loc.gov/preservation/digital/formats/fdd/fdd000449.shtml

[^56]: https://dl.acm.org/doi/10.1115/1.1354995

[^57]: https://www.3dfindit.com/ru/corporate/engiclopedia/step-ap203-ap214-ap242-differences-application

[^58]: https://docs.oasis-open.org/plcs/dexlib/cs01/help/dex/techdes_p28.htm

[^59]: https://cccp3d.ru/topic/27173-step-ap214-vs-ap203/

[^60]: https://docs.cntd.ru/document/1304228453/titles/65E0IS

