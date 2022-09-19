# Project roadmap

**1st ITERATION**

1. **Analýza business procesů**
    * [ ]  diagramy aktivit (UML Behavioral-Activity)
    * [ ]  textové popisy procesů
2. **Analýza požadavků (UC model)**
    * [ ]  katalog požadavků (Extended-Requirements)
    * [ ]  diagramy případů užití (UML Behavioral-Use Case)
    * [ ]  popisy případů užití
    * [ ]  detailní rozpracování scénářů "hlavních/zajímavých/důležitých" případů užití - případy užití, které přímo podporují hlavní činnost zákazníka (minimální počet takto rozpracovaných případů užití je dán počtem členů v týmu). Takto detailně rozpracovaný případ užití by měl obsahovat hlavní scénář, alternativní scénáře, případně vazby include a extend na okolní případy užití
    * [ ]  seznam účastníků
    * [ ]  mapování případů užití na požadavky
3. **Analytický (doménový) model**
    * [ ]  diagram tříd - kardinality, názvy asociací (UML Structural-Class)
    * [ ]  popisy jednotlivých entit a jejich atributů
    * [ ]  stavový diagram pro vybrané entity (UML Behavioral-State Machine)

**2nd ITERATION**

Cíl: návrh architektury, doplnění analýzy, zahájení implementace

1. [ ] **Návrh logické architektury**
    
    Zvolené technologie (frameworky, knihovny, principy) pro:
    * [ ] uživatelské rozhraní
    * [ ] persistenci dat - zvolený způsob persistentního ukládání musí zajistit, že se nikdy nebudou používat názvy tabulek a názvy jejich sloupečků v kódu jinde, než v datové vrstvě.
    * [ ] provázání balíčků/komponent - IoC
    * [ ] rozdělení systému do balíčků (logických celků) - diagram balíčků v kontextu zvolené technologie (UML Structural-Package)
        * minimálním požadavkem je oddělení prezentační vrstvy od zbytku aplikace tj. alepsoň dvouvrstvá aplikace
2. [ ] **Databázový model** - diagram tříd (UML Structural-Class)/alternativně detailní popis rozhraní, které bude používáno pro načítní/ukládání dat, pokud aplikace nemá vlastní databázi
    * primární klíče
    * cizí klíče
    * datové typy
    * dekompozice m:n vazeb
    * směry asociací
    * přiřazení zodpovědností (metod)
3. [ ] **Implementace první verze aplikace s využitím zvolených technologií/knihoven/frameworků a navržené architektury**
    * založena na objektově orientovaném přístupu (zapouzdrření, dědičnost, polymorfismus)
    * dodržená zvolená architektura dvouvrstvá/třívrstvá
    * SQL kód není přípustný jinde než v datové vrstvě
    * názvy tabulek, sloupečků v db není přípustné použít jinde než v datové vrstvě (refaktoring databáze např. přejmenování tabulky nesmí způsobit změny ve zdrojových kódech mimo datovou vrstvu)
    * vrstvy odděleny pomocí rozhraní (programátor řešící prezentační/business vrstvu musí být schopen implementovat požadovanou funkčnost na základě popisu těchto rozhraní, bez znalosti implementace datové vrstvy)
    * změna ve způsobu ukládání/načítání dat musí ovlivnit pouze třídu implementující toto rozhraní. Zbytek systému musí zůstat beze změny (např. data o klientech nebudeme načítat/ukládat z lokální databáze, ale pomocí REST služby)
    * instalační balíček obsahující spustitelný základ aplikace - v aplikaci musí být implementovány alespoň 1-2 případy užití
4. [ ] **Zdrojové kódy aplikace**
    * musejí být po celou dobu vývoje verzovány v SVN nebo GITu (nelze na závěr nahrát do SVN nebo GITu zazipovaný adresář obsahující zdrojové kódy!!!)
    * musejí obsahovat standardní dokumentační komentáře

**3'd ITERATION**
1. [ ] refaktoring implementace na základě připomínek druhé iterace
2. [ ] dokumentace navrhovaného/implementovaného řešení - cílem je předat "programátorskou" kuchařku pro navazující tým, dle které budou schopni v započaté práci pokračovat
3. [ ] popis komunikace softwarových tříd při realizaci implementovaných scénářů případů užití z druhé iterace
4. [ ] instalační příručka
5. [ ] vygenerovaná dokumentace (statické html) ze zdrojových kódů (např. JavaDoc, Doxygen) - detailně musí být zdokumentovány všechny rozhraní (interfaces) a třídy a jejich metody podílející se na implementovaných případech užití
