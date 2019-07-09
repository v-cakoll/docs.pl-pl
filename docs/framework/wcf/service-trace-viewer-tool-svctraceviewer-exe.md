---
title: Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 02d2dd74031f280808027df1c0b7b78a90e6cd52
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664110"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)

Narzędzie do śledzenia usług Windows Communication Foundation (WCF) pomaga analizować dane śledzenia diagnostycznego, które są generowane przez architekturę WCF. Przeglądarki danych śledzenia usługi umożliwia łatwe scalania, przeglądać i filtrować komunikaty śledzenia w dzienniku, aby zdiagnozować, naprawy i sprawdź problemów z usługą WCF.

## <a name="configuring-tracing"></a>Konfigurowanie śledzenia

Dane śledzenia diagnostycznego zapewniają informacje, które wskazują na to, co się dzieje w całym działania aplikacji. Jak wskazuje nazwa, można wykonać operacji z ich źródła do miejsca docelowego, a także pośrednich punktów.

Można skonfigurować śledzenie z użyciem pliku konfiguracji aplikacji — albo plik Web.config dla aplikacji hostowanych w sieci Web, lub *Appname*.config samodzielnie hostowanej aplikacji. Oto przykład:

```xml
<system.diagnostics>
    <trace autoflush="true" />
    <sources>
            <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"
                    propagateActivity="true">
            <listeners>
               <add name="sdt"
                   type="System.Diagnostics.XmlWriterTraceListener"
                   initializeData= "SdrConfigExample.e2e" />
            </listeners>
         </source>
    </sources>
</system.diagnostics>
```

W tym przykładzie określono nazwę i typ odbiornik śledzenia. Odbiornik o nazwie `sdt` i standardowy odbiornik śledzenia .NET Framework (System.Diagnostics.XmlWriterTraceListener) jest dodawany jako typu. `initializeData` Atrybut jest używany, aby ustawić nazwę pliku dziennika dla tego odbiornika jako `SdrConfigExample.e2e`. Dla pliku dziennika można zastąpić w pełni kwalifikowaną ścieżkę do nazwy pliku prostego.

Ten przykład tworzy plik w katalogu głównym o nazwie SdrConfigExample.e2e. Gdy używasz przeglądarki danych śledzenia można otworzyć pliku, zgodnie z opisem w sekcji "Otwieranie i wyświetlanie WCF pliki śledzenia", widać wszystkie komunikaty, które zostały wysłane.

Poziom śledzenia jest kontrolowane przez `switchValue` ustawienie. Poziomy śledzenia dostępne są opisane w poniższej tabeli.

|Poziom śledzenia|Opis|
|-----------------|-----------------|
|Krytyczny|-Rejestruje wpisy dziennika zdarzeń i bezawaryjną i informacje o śledzeniu korelacji. Poniżej przedstawiono kilka przykładów, gdy można na przykład poziom krytyczny:<br />-AppDomain zakończył działanie z powodu nieobsługiwanego wyjątku.<br />-Aplikacja nie powiedzie się rozpocząć.<br />-Komunikat, który spowodował awarię, pochodzi z procesu MyApp.exe.|
|Błąd|— Rejestruje wszystkie wyjątki. Możesz użyć poziom błędu w następujących sytuacjach:<br />-Kod uległ awarii z powodu wyjątku Nieprawidłowe rzutowanie.<br />Wyjątek "nie można utworzyć punktu końcowego" powoduje awarię podczas uruchamiania aplikacji.|
|Ostrzeżenie|-Istnieje warunek, który następnie może spowodować błąd lub błąd krytyczny. Możesz użyć tego poziomu w następujących sytuacjach:<br />— Aplikacja odbiera więcej żądań nie zezwala na jego ustawienia ograniczenia przepustowości.<br />-Odbieranie kolejka jest w 98 procent jego skonfigurowaną pojemność.|
|Informacje|-Komunikaty przydatne do monitorowania i diagnozowania stanu systemu, pomiaru wydajności lub profilowania są generowane. Korzystanie z takich informacji o pojemności planowanie i zarządzanie wydajnością. Możesz użyć tego poziomu w następujących sytuacjach:<br />— Wystąpił błąd po wiadomości osiągnięto domeny aplikacji i została przeprowadzona.<br />-Błąd wystąpił podczas tworzenia powiązania protokołu HTTP.|
|Pełny|Debugowanie poziomie śledzenia dla obu kod użytkownika i obsługi. Ustaw to poziom po:<br />— Nie masz pewności, którą metodę w kodzie została wywołana, gdy wystąpił błąd.<br />-Masz nieprawidłowy punkt końcowy z konfiguracją i usługę udało się uruchomić, ponieważ wpis w magazynie rezerwacji jest zablokowany.|
|ActivityTracing|Zdarzenia przepływ między działaniami przetwarzania i składników.<br /><br /> Ten poziom umożliwia administratorów i deweloperów skorelować aplikacji w tej samej domenie aplikacji.<br /><br /> -Ślady działania granice: uruchamianie/zatrzymywanie.<br />-Ślady transferów.|

 Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W przykładzie konfiguracji, odbiornik o nazwie `sdt` i standardowy odbiornik śledzenia .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jest dodawany jako typu. Użyj `initializeData` można ustawić nazwę pliku dziennika dla tego odbiornika. Ponadto można zastąpić w pełni kwalifikowaną ścieżkę do nazwy pliku prostego.

Począwszy od programu .NET Framework 4.8 kontrolek ComboBox niektóre kompozycje o wysokim kontraście są wyświetlane w prawidłowy kolor. Możesz wyłączyć tę zmianę, usuwając następujące ustawienie na podstawie *svcTraceViewer.exe.config* pliku:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

## <a name="using-the-service-trace-viewer-tool"></a>Za pomocą narzędzia podglądu śledzenia usług

### <a name="opening-and-viewing-wcf-trace-files"></a>Otwieranie i wyświetlanie plików śledzenia WCF

Przeglądarki danych śledzenia usługi obsługuje trzy typy plików:

- Usługi WCF (.svcLog) pliku śledzenia

- Zdarzenia śledzenia w pliku (.etl)

- Plik śledzenia crismon

 Przeglądarki danych śledzenia usługi umożliwia Otwórz każdy plik śledzenia obsługiwanych, dodać i integracja śledzenia dodatkowe pliki, lub otworzyć i jednocześnie scalania grupy plików śledzenia.

##### <a name="to-open-a-trace-file"></a>Aby otworzyć plik śledzenia

1. Rozpocznij przeglądarki danych śledzenia usługi za pomocą okno polecenia przejdź do lokalizacji instalacji usługi WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin), a następnie wpisz `SvcTraceViewer.exe`.

> [!NOTE]
> Narzędzie przeglądarki danych śledzenia usługi można skojarzyć z dwóch typów plików: .svclog i .stvproj. Dwa parametry wiersza polecenia umożliwia rejestrowanie i wyrejestrowywanie rozszerzeń plików.
>
> / register: zarejestrowanie stowarzyszenia rozszerzenia pliku ".svclog" i ".stvproj" SvcTraceViewer.exe
>
> / unregister: unregister skojarzenie rozszerzenia pliku ".svclog" i ".stvproj" SvcTraceViewer.exe

1. Po uruchomieniu przeglądarki danych śledzenia usługi kliknij **pliku** i wskaż **Otwórz**. Przejdź do lokalizacji, w którym są przechowywane pliki śledzenia.

2. Kliknij dwukrotnie plik śledzenia, który chcesz otworzyć.

    > [!NOTE]
    > Naciśnij klawisz SHIFT podczas klikania wielu plików śledzenia, wybierz i otwórz je jednocześnie. Przeglądarki danych śledzenia usługi Scala zawartość wszystkich plików i przedstawia jeden widok. Na przykład możesz otworzyć pliki śledzenia zarówno klient, jak i usługi. Jest to przydatne, gdy włączono rejestrowanie i działania Propagacja komunikatów w konfiguracji. W ten sposób można sprawdzić w wymianie wiadomości między klientem a usługą. Można również przeciągnąć wielu plików w przeglądarce lub użyj **projektu** kartę. Zobacz sekcję Zarządzanie projektu, aby uzyskać więcej informacji.

3. Aby dodać pliki śledzenia dodatkowych kolekcji, która jest otwarta, kliknij **pliku** i wskaż **Dodaj**. W otwartym oknie przejdź do lokalizacji plików śledzenia, a następnie kliknij dwukrotnie plik, który chcesz dodać.

> [!CAUTION]
> Nie zaleca się załadowanie pliku dziennika śledzenia większy niż 200MB. Jeśli użytkownik podejmie próbę załadowania pliku przekracza ten limit, proces ładowania może potrwać długo zależnie od zasobu komputera. Narzędzie przeglądarki danych śledzenia usługi może nie być dynamiczny przez długi czas lub go może wyczerpać pamięci maszyny. Zaleca się konfigurowania ładowania częściowego, aby tego uniknąć. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz sekcję "Podczas ładowania dużych śledzenia Files".

#### <a name="event-tracing-and-crimson-tracing"></a>Śledzenie zdarzeń i śledzenia Crismon

Podgląd w formacie natywnym jest format śledzenie aktywności, który emituje WCF. Dane śledzenia emitowane w innym formacie muszą zostać przekonwertowane, zanim przeglądarka wyświetla je. Obecnie oprócz format śledzenie aktywności, przeglądarka obsługuje śledzenie zdarzeń i śledzenia crismon.

Podczas otwierania pliku, który nie zawiera ślady działania przeglądarki próbuje przekonwertować plik. Należy określić nazwę i lokalizację pliku, który będzie zawierał dane śledzenia przekonwertowana. Po konwersji danych przeglądarka wyświetla zawartość nowego pliku.

> [!NOTE]
> Konwersja wymaga miejsca na dysku do przechowywania danych śledzenia przekonwertowana. Upewnij się, że masz wystarczającą ilość miejsca na dysku do przechowywania danych, przed rozpoczęciem konwersji. W przeciwnym razie konwersji nie powiedzie się.

### <a name="managing-projects"></a>Zarządzanie projektami

Przeglądarka obsługuje projekty, aby ułatwić wyświetlanie wielu plików śledzenia. Na przykład jeśli masz plik śledzenia klienta i plik śledzenia usługi, można je dodać do projektu. Następnie za każdym razem, gdy otworzysz projekt, wszystkie pliki śledzenia w projekcie są ładowane jednocześnie.

Istnieją dwa sposoby zarządzania projektami:

- W **pliku** menu, można otworzyć, Zapisz i zamknij projektów.

- W **projektu** karcie, można dodać pliki do projektu.

### <a name="viewing-wcf-traces"></a>Wyświetlanie WCF śladów

Usługi WCF emituje danych śledzenia przy użyciu formatu śledzenie aktywności. W modelu śledzenie aktywności w poszczególnych ślady są grupowane w działania zgodnie z ich celem. Przepływ sterowania logiczne są przesyłane między działaniami. Na przykład w okresie istnienia aplikacji, wiele "działania wysyłania komunikatu" pojawiają się i znikają. Aby uzyskać więcej informacji dotyczących przeglądania danych śledzenia i działań i interfejsu użytkownika przeglądarki danych śledzenia usługi zbyt zobacz [za pomocą przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów z](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).

#### <a name="switching-to-different-views"></a>Przełączanie do różnych widoków

Przeglądarki danych śledzenia usługi udostępnia następujące widoki. Są wyświetlane jako karty w lewym okienku podglądu, a także jest możliwy z **widoku** menu.

- Wyświetl działania

- Widok projektu

- Widok komunikatów

- Widok wykresu

##### <a name="activity-view"></a>Wyświetl działania

Po otwarciu plików śledzenia są widoczne ślady, pogrupowane według działań i wyświetlane w **działania** widoku w okienku po lewej stronie.

**Działania** nazwy działań Wyświetla widok, Liczba śladów w działaniu, czas trwania godzina rozpoczęcia, czas zakończenia.

Klikając dowolny działania wymienione na liście, dane śledzenia w przypadku tego działania są wyświetlane w okienku śledzenia, po prawej stronie. Następnie możesz wybrać śledzenia, aby wyświetlić jego szczegóły.

Możesz wybrać wiele działań, naciskając klawisz **Ctrl** lub **Shift** klucz i klikając odpowiednią działań. W okienku śledzenia są wyświetlane wszystkie ślady wybrane działania.

Możesz kliknąć dwukrotnie działanie, aby wyświetlić ją w **wykres** widoku. Alternatywna metoda polega na wybierz działanie, a następnie przejdź do **wykres** widoku.

> [!NOTE]
> Działanie "000000000000" jest specjalnym działaniu, które nie mogą być wyświetlane w widoku wykresu. Ponieważ inne działania są z nim połączone, wyświetlanie to działanie ma wpływ zmniejszenie wydajności.

Możesz kliknąć tytuł kolumny, aby posortować listę działań. Działania, które zawierają zapisy ostrzeżeń mają żółte tło i tych, które zawierają zapisy błędów ma jeden czerwony.

Istnieją różne typy działań i każdy typ odnosi się do ikony po lewej stronie każdego działania. Mogą odwoływać się w sekcji ikony śledzenia opis ich znaczenia.

##### <a name="project-view"></a>Widok projektu

Ten widok umożliwia zarządzanie pliki śledzenia w bieżącym projekcie. Zobacz sekcję Zarządzanie projektu, aby uzyskać więcej informacji.

##### <a name="message-view"></a>Widok komunikatów

Ten widok umożliwia wyświetlanie wszystkich dziennik komunikatów ślady, łącznie z procesu akcji, daty/godziny, Acivity i w, / i przejdź do szczegółów śladu skojarzone komunikatu dziennika. Możesz grupować danych śledzenia dziennika komunikatów Hranice Aktivity, proces/wątek lub wysyłania i odbierania dla zapewnienia łatwiejszej nawigacji przepływu wiadomości.

##### <a name="graph-view"></a>Widok wykresu

Ten widok przedstawia dane śledzenia dla konkretnych działań w formie wykresu. Formularz wykresu umożliwia Zobacz stopniową wykonywania zdarzeń i współzależności między wiele działań, gdy dane są przenoszone między nimi.

Aby przełączyć się do **wykres** wyświetlić, wybierz działanie w **działania** wyświetlić, a następnie kliknij przycisk **działania** karty lub komunikatów dziennika śledzenia w **komunikat**Widoku. Jeśli wiele plików śledzenia są ładowane i działanie polega na ślady z więcej niż jeden plik, wszystkie istotne dane śledzenia są wyświetlane w widoku wykresu. Ponadto dwukrotne kliknięcie działań i danych śledzenia dziennika komunikatów prowadzi Cię do **wykres** widoku.

W **wykres** widoku w poszczególnych kolumnach reprezentuje działanie, a każdy blok, w kolumnie — śledzenia. Działania są pogrupowane według procesu (lub wątku). Małe strzałki między działaniami reprezentują transferu. Big strzałki między procesami reprezentują wymianę komunikatów. Działania w zaznaczenie jest zawsze na żółto.

###### <a name="selecting-traces-in-the-graph"></a>Wybieranie ślady na wykresie

1. Kliknij blok na wykresie.

2. W górę i w dół kluczy, aby wybrać jej sąsiednich ślady.

3. Sprawdź informacje o śledzeniu w okienku śledzenia i okienka szczegółów.

###### <a name="expanding-or-collapsing-activity-transfers"></a>Rozwijanie lub zwijanie transferów działań

Podczas działania w zaznaczeniu przenosi się do kolejnego działania, można rozwinąć transferów działań. Pozwala ona do wykonania transferu.

Aby rozwinąć lub zwinąć transferów działań

1. Znajdź śledzenia transferu znakiem "+" po lewej stronie ikony transferu.

2. Kliknij przycisk "+" lub naciśnij **Ctrl** i "+" za pomocą klawiatury.

3. Następne działanie jest wyświetlana na wykresie.

4. Element "-" pojawia się po lewej stronie ikony transferu. Kliknij przycisk "-" Zaloguj się i nacisnąć klawisz Ctrl i "-", zwija transferu działania.

> [!NOTE]
> Gdy działanie ma wiele przeniesienia do niego i jedną przeniesień Rozwiń, są wyświetlane działań, które powoduje nowe działanie z działania głównego. Te nowe działania są wyświetlane w formularzu zwinięty. Jeśli chcesz wyświetlić szczegóły tych działań, powiększyć je w pionie, klikając ikonę rozwijania w nagłówku wykresu.

###### <a name="expanding-or-collapsing-activities-vertically"></a>Rozwijanie lub zwijanie działań w pionie

Podgląd Ukrywa niepotrzebne szczegółowo wykres aktywności, zwijając działań. W przypadku zwinięty działania śledzenia poszczególnych nie są wyświetlane. Są wyświetlane tylko transfery śledzenia. Jeśli chcesz wyświetlić wszystkie ślady w działaniu, rozwiń węzeł działania w pionie klikając symbol rozwijania działalności w nagłówku wykresu.

Aby rozwinąć lub zwinąć działań w pionie

1. Kliknij ikonę "+" w nagłówku działania, aby rozwinąć działania w pionie.

2. Należy zauważyć, że wszystkie ślady są wyświetlane na wykresie.

3. Kliknij przycisk "-" ikona w nagłówku działania, aby zwinąć działania w pionie.

4. Zwróć uwagę że tylko ważne w przypadku transferów komunikatu dzienników, ostrzeżenie i śledzenia wyjątków są wyświetlane w działaniu.

###### <a name="options"></a>Opcje

Można wybrać dwie opcje z **opcja** menu w widoku wykresu.

- Pokaż działanie granic ślady po usunięciu zaznaczenia Ignoruj ślady granic działania na wykresie.

- Pokaż pełne ślady Non komunikat, który w przypadku usunięcia zaznaczenia Ignoruj pełne poziomu ślady, z wyjątkiem komunikatów śledzenia. W większości przypadków pełne śledzenie poziomu są mniej ważne w przypadku analizy. Ta opcja jest przydatna, gdy użytkownik nie chce analizować pełne śledzenie poziomu i tylko chcesz skupić się na bardziej ważne ślady.

###### <a name="layout-mode"></a>Tryb układu

Podgląd w dwóch trybach układu: **Proces** i **wątku**. To ustawienie określa Największa jednostka organizacji. Wartość domyślna jest w trybie układu **procesu**, co oznacza, że działania są pogrupowane według procesów na wykresie.

###### <a name="execution-list"></a>Lista wykonywania

Możesz wybrać, który proces lub wątek do wyświetlenia na wykresie z tej listy rozwijanej. Na przykład jeśli masz pliki śledzenia dwóch klientów (A i B) i jedną usługę, otwarte, a tylko mają być wyświetlane na wykresie usługi i klienta A, możesz usunąć zaznaczenie klienta B z listy.

#### <a name="viewing-trace-details"></a>Szczegóły śladu wyświetlania

Aby wyświetlić szczegóły śledzenia, należy wybrać śledzenia w okienku śledzenia. Szczegółowe informacje są wyświetlane w okienku szczegółów.

##### <a name="trace-pane"></a>Okienko śledzenia

Górnym okienku po prawej stronie w podglądzie śledzenia usługi to okienko śledzenia. Wyświetla listę wszystkich śladów w wybrane działanie zawierającego dodatkowe informacje, na przykład poziom śledzenia, identyfikator wątku i nazwę procesu.

Nieprzetworzonym kodzie XML śledzenia można skopiować do Schowka, kliknij prawym przyciskiem myszy śledzenia i wybierając **śledzenia kopiowania do Schowka**.

##### <a name="detail-pane"></a>Okienko Szczegóły

Dolne okienko po lewej stronie w podglądzie śledzenia usługi jest w okienku szczegółów. Zawiera trzy karty, aby wyświetlić szczegóły śledzenia.

**Sformatowany** widoku są wyświetlane informacje w sposób bardziej zorganizowane. Wyświetla listę wszystkich znanych elementów XML w tabelach i drzewa, dzięki czemu łatwiej odczytywać i zrozumienie informacji.

**XML** widoku są wyświetlane XML odpowiadający wybranej śledzenia. Obsługuje ona kolor wyróżnienia i składni. Kiedy używasz **znaleźć** wyszukiwać ciągi, zawiera opis wyników wyszukiwania.

**Komunikat** widok zawiera część wiadomości XML danych śledzenia dziennika komunikatów. Może to być niewidoczne, po wybraniu śledzenia bez wiadomości.

### <a name="filtering-wcf-traces"></a>Filtrowanie śledzenia WCF

Aby ułatwić analiza śledzenia, można filtrować je w następujący sposób:

- Na pasku narzędzi filtru zapewnia dostęp do wstępnie zdefiniowanych i niestandardowych filtrów. Można ją włączyć za pomocą **widoku** menu.

- Wstępnie zdefiniowany filtr podglądu można selektywnie filtrować części śledzenia WCF. Domyślnie ustawiono zezwalająca na wszystkie ślady infrastruktury do przekazywania. Ustawienie tego filtru są zdefiniowane w **opcje filtrowania** podmenu w obszarze **widoku** menu.

- Filtry niestandardowe wyrażenie XPath użytkownikom pełną kontrolę nad filtrowania. Można zdefiniować w **niestandardowy filtr** w obszarze **widoku** menu.

Zostanie wyświetlona tylko tych śladów, które przechodzi przez wszystkie filtry.

#### <a name="using-the-filter-toolbar"></a>Używanie paska narzędzi filtru

Pasek narzędzi Filtr pojawia się u góry tego narzędzia. Jeśli nie jest obecny, możesz to zrobić w **widoku** menu. Pasek ma trzy składniki:

- Szukać: **Wyszukaj** definiuje do przeszukania operacja filtru tematu. Na przykład, jeśli chcesz znaleźć wszystkie ślady, które są emitowane w kontekście procesu X, Ustaw to pole na X i **wyszukiwania w** pole "Proces Name". Wybrano tej zmiany w kontrolce selektora daty/godziny, gdy filtr na podstawie czasu.

- Szukaj w: To pole określa typ filtru do zastosowania.

- Poziom: Ustawienie poziomie definiuje minimalny poziom śledzenia może za pomocą filtru. Na przykład jeśli poziom jest ustawiona, aby wskazywał błąd i w górę, są wyświetlane tylko dane śledzenia na poziomie błędu i krytyczne. Ten filtr łączy się z kryteriami, wyszukaj i wyszukaj w.

**Filtr teraz** przycisk uruchamia operację filtrowania. Niektóre filtry, szczególnie w przypadku, gdy są one stosowane do dużych zestawów danych potrwać bardzo długo. Operacja filtru można anulować, naciskając klawisz **zatrzymać** znajdujący się na pasku stanu w obszarze **operacji** menu.

**Wyczyść** przycisk resetuje wstępnie zdefiniowanych i niestandardowych filtrów, aby zezwolić na wszystkie ślady dopuszczone.

#### <a name="filter-options"></a>Opcje filtru

Podgląd automatycznie usunąć śledzenia WCF z widoku. Można usunąć wybrane dane śledzenia emitowane przez określonych obszarach usług WCF, na przykład, usunięcie transakcji związane z ślady z widoku.

Ustawienie tego filtru są zdefiniowane w **opcje filtrowania** podmenu w obszarze **widoku** menu.

#### <a name="custom-filters"></a>Filtry niestandardowe

Jeśli znasz język ścieżki XML (XPath) służy do tworzenia niestandardowych filtrów do wyszukiwania danych śledzenia dla każdego elementu XML zainteresowania. Filtry są dostępne za pośrednictwem narzędzi filtru.

Filtry niestandardowe mogą zawierać parametrów. Można również zaimportować istniejące filtry niestandardowe.

##### <a name="creating-a-custom-filter"></a>Tworzenie niestandardowego filtru

Filtry można tworzyć na dwa sposoby:

###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Utworzenie filtru niestandardowego za pomocą Kreatora szablonu

Można kliknąć istniejących śledzenia i utworzyć filtr oparty na strukturze śledzenia. W tym przykładzie tworzy niestandardowy filtr oparty na identyfikator wątku.

1. W okienku śledzenia w prawym górnym obszarze podglądu wybierz śledzenia, który zawiera element, którego chcesz filtrować.

2. Kliknij przycisk **utworzyć niestandardowy filtr** znajdujący się w górnej części okienka śledzenia.

3. W oknie dialogowym Wprowadź nazwę filtru. W tym przykładzie wprowadź `Thread ID`. Można również podać opis filtru.

4. Widok drzewa po lewej stronie wyświetla strukturę rekord śledzenia, który został wybrany w kroku 1. Przejdź do elementu, którego chcesz utworzyć warunek. W tym przykładzie, przejdź do ThreadID muszą znajdować się w wyrażenie XPath: /E2ETraceEvent/System/Execution/@ThreadID węzła. Kliknij dwukrotnie atrybut ThreadID w widoku drzewa. Spowoduje to utworzenie wyrażenia dla atrybutu po prawej stronie okna dialogowego.

5. Zmień wartość pola parametrów dla warunku ThreadID z Brak, aby "{0}". Ten krok powoduje włączenie wartość ThreadID skonfigurowane, po zastosowaniu filtru. (Zobacz jak zastosować sekcja filtru) Można zdefiniować maksymalnie cztery parametry. Warunki są łączone za pomocą operatora OR.

6. Kliknij przycisk **Ok** do utworzenia filtru.

> [!NOTE]
> Po utworzeniu filtru przy użyciu Kreatora szablonów, można ją edytować tylko ręcznie. Nie jest możliwe uruchomić Kreatora tworzenia filtru, który został utworzony wcześniej. Ponadto warunki filtr XPath w Kreatorze szablonu są łączone za pomocą operatora OR. Jeśli potrzebujesz i operacji, można edytować wyrażenie filtru, po jego utworzeniu.

###### <a name="creating-a-custom-filter-manually"></a>Ręczne tworzenie niestandardowego filtru

Menu niestandardowe filtry umożliwia ręczne wprowadzenie filtrach XPath.

1. W menu Widok, kliknij przycisk **niestandardowe filtry** elementu menu.

2. W wyświetlonym oknie dialogowym kliknij **nowy.**

3. Minimum Określ nazwę filtru i XPath wyrażenia.

4. Kliknij przycisk **OK**.

###### <a name="applying-a-custom-filter"></a>Stosowanie niestandardowego filtru

Po utworzeniu niestandardowego filtru jest dostępny do narzędzi filtru. Wybierz filtr, który chcesz zastosować w **wyszukiwania w** pole filtru paska narzędzi. W poprzednim przykładzie należy wybrać identyfikator wątku.

1. Określ wartość, którego szukasz w **Znajdź** pola. W tym przykładzie należy wprowadzić identyfikator wątku, który chcesz wyszukać.

2. Kliknij przycisk **filtr teraz**i sprawdź, czy wynik operacji.

Jeśli filtr korzysta z wielu parametrów, wprowadź je przy użyciu ";" jako separator w **Znajdź** pola. Na przykład następujący ciąg definiuje 3 parametry: "1; findValue tekst". Podgląd dotyczy '1' {0} parametru filtru. 'findValue' i 'text' są stosowane do {1} i {2} odpowiednio.

###### <a name="sharing-custom-filters"></a>Udostępnianie filtry niestandardowe

Filtry niestandardowe mogą być współużytkowane w różnych sesjach i różnych użytkowników. Możesz wyeksportować filtry do pliku definicji i zaimportować ten plik w innej lokalizacji.

 Aby zaimportować filtr niestandardowy:

1. W **widoku** menu, kliknij przycisk **niestandardowe filtry**.

2. W wyświetlonym oknie dialogowym kliknij **importu** przycisku.

3. Przejdź do pliku niestandardowego filtru (.stvcf), kliknij plik, a następnie kliknij przycisk **Otwórz** przycisku.

Aby wyeksportować niestandardowy filtr:

1. W menu Widok, kliknij przycisk **niestandardowe filtry**.

2. W wyświetlonym oknie dialogowym Wybierz filtr, który chcesz wyeksportować.

3. Kliknij przycisk **wyeksportować** przycisku.

4. Określ nazwę i lokalizację pliku definicji niestandardowego filtru (.stvcf), a następnie kliknij przycisk **Zapisz** przycisku.

> [!NOTE]
> Te filtry niestandardowe można tylko zaimportować i wyeksportować z przeglądarki danych śledzenia usługi. Nie można ich odczytać, za pomocą innych narzędzi.

### <a name="finding-data"></a>Znajdowanie danych

Podgląd oferuje następujące sposoby znajdowania danych:

- Pasek narzędzi wyszukiwania zapewnia szybki dostęp do najbardziej typowe opcje wyszukiwania.

- Okno dialogowe znajdowania umożliwia znaleźć więcej opcji. Nie jest dostępny za pośrednictwem **Edytuj** menu lub przez krótki klawiszy Ctrl + F.

Pasek narzędzi wyszukiwania pojawia się u góry strony podglądu. Jeśli nie jest obecny, możesz to zrobić w **widoku** menu. Pasek ma dwa składniki:

- Znajdź: Umożliwia wprowadzenie słowa kluczowe do wyszukania.

- Szukaj w: Umożliwia wprowadzenie zakresu wyszukiwania. Możesz wybrać, czy do wyszukania we wszystkich działaniach lub bieżące działanie.

Okno dialogowe znajdowania oferuje dwie opcje dodatkowe:

- Znajdź element docelowy:

  - Opcji "nieprzetworzonych danych dzienników dane" przeszukuje wszystkie nieprzetworzone dane słowo kluczowe.

  - Opcji "XML Text" i "Atrybut XML" Wyszukiwanie tylko w elementach XML.

  - Opcja "Rejestrowany komunikat" przeszukuje słowo kluczowe tylko w wiadomości.

- Ignoruj działanie główne: Wyszukiwanie ignoruje ślady w działaniu "000000000000". Zwiększa wydajność w plikach dużych śledzenia w czasie działania głównego zawiera tysiące ślady, z których większość czy opłata za transfery.

### <a name="navigating-traces"></a>Nawigacja śladów

Ponieważ dane śledzenia są zapisywane krok po kroku podczas wykonywania aplikacji, przechodząc ślady mogą pomóc debugowania aplikacji. Przeglądarki danych śledzenia usługi udostępnia różne sposoby do nawigowania po danych śledzenia.

#### <a name="step-forward-or-backward"></a>Krok do przodu lub Wstecz

Należy wziąć pod uwagę każdego śledzenia jako linię kodu w programie, przechodzenie do przodu jest bardzo podobny do "Przekrocz nad" w Visual Studio rozwoju środowiska IDE (Integrated). Różnica polega na tym, że można również przejść do tyłu w śladach. Przechodzenie do przodu polega na przejściu do następnej śledzenia w działaniu.

- Step Forward: Użyj **działania** menu lub naciśnij pozycję "F10". Można również używać klucza strzałkę "nie działa", w okienku śledzenia.

- Krok do tyłu Użyj **działania** menu lub naciśnij pozycję "F9". Można również używać klucza strzałkę "up", w okienku śledzenia.

> [!NOTE]
> Może to potrwać należy do działania wykonywane w ramach innego procesu lub nawet na innym komputerze, ponieważ komunikatów WCF może wykonywać działania identyfikatorów, które rozciągają się maszyn.

#### <a name="follow-transfer"></a>Postępuj zgodnie z przeniesienia

Transfer danych śledzenia są specjalne śledzenia w pliku śledzenia. Działanie może przesyłać do kolejnego działania, śledzenia transferu. Na przykład "Działanie A", mogą przesyłać do "Działanie B". W takiej sytuacji istnieje śledzenia transferu działalność"A" o nazwie "do: Działanie"i ikona transferu. Ślad transferu jest łącze między dwoma ślady. W "Działanie B" mogą również istnieć ślad transferu na koniec działania, aby przesłać "Działanie A". Jest to podobne do wywołania funkcji w programach: Wywołuje usługę B, następnie B zwraca.

"Follow transferu" przypomina "Krok po kroku" w debugerze. Następuje przeniesienie od A do B. Nie ma żadnego wpływu na pozostałe dane śledzenia.

Istnieją dwa sposoby, aby wykonać przeniesienie: myszy lub klawiatury:

- Przez myszy: Kliknij dwukrotnie śledzenia transferu w okienku śledzenia.

- Przez klawiatury: Wybierz śledzenia transferu i użyj "Transfer postępuj zgodnie z" w **działania** menu lub naciśnij pozycję "F11"

> [!NOTE]
> W wielu przypadkach przesyłania działanie A do B działania działanie A czeka, aż działanie B przesyła powrót do działania A. Oznacza to, że działanie A ma bez śledzenia zarejestrowane w trakcie okresu, gdy działanie B jest aktywnie śledzenia. Jednak jest również możliwe, że działanie A nie czeka i ślady dzienników w dalszym ciągu. Istnieje również możliwość, że działanie B nie są przekazywane do działania A. W związku z tym, transferów działań nadal różnią się od wywołania funkcji w tym sensie. Możesz zrozumieć działanie transferów w widoku wykresu.

#### <a name="jump-to-next-or-previous-transfer"></a>Przejdź do następnej lub poprzedniej transferu

Podczas analizy bieżącego działania lub wybrane działania po wybraniu wielu działań, możesz szybko znaleźć działań, które przekazuje go do. "Skok do przesyłania dalej" umożliwia umieszczanie dalej śledzenia transferu w działaniu. Po odnalezieniu śledzenia transferu służy "Follow transferu" Aby wejść do następnego działania.

- Przejdź do następnego przeniesienia: Użyj **działania** menu lub naciśnij pozycję "Ctrl + F10".

- Przejdź do poprzedniego transferu: Użyj **działania** menu lub naciśnij pozycję "Ctrl + F9".

#### <a name="navigate-in-graph-view"></a>Nawigowanie w widoku wykresu

Mimo że nawigacja w okienku śledzenia i okienku aktywności jest podobne do debugowania, za pomocą **wykres** widok zawiera dużo lepiej w nawigacji. Zobacz sekcję "Widoku wykresu", aby uzyskać więcej informacji.

### <a name="loading-large-trace-files"></a>Trwa ładowanie plików śledzenia duże

Pliki śledzenia mogą być bardzo duże. Na przykład w przypadku równoczesnego włączenia śledzenia na poziomie "Pełne", wynikowy plik śledzenia dla uruchamiania za kilka minut można łatwo można kilkuset megabajtów lub jeszcze większym, w zależności od wzorca szybkość i komunikacji sieciowej.

Po otwarciu pliku śledzenia bardzo duże w podglądzie śledzenia usługi wydajność systemu może negatywnie wpłynąć na. Szybkość ładowania i czas odpowiedzi po załadowaniu może działać powoli. Rzeczywista szybkość różni się od czasu do czasu, w zależności od konfiguracji sprzętu. W większości komputerów podczas ładowania pliku śledzenia jest większy niż 200M powoduje znaczne pogorszenie wydajności. Ślady plików większych niż 1G narzędzie może zużyć całą dostępną pamięć lub przestanie odpowiadać bardzo długi czas.

Aby uniknąć powolne ładowanie i czas odpowiedzi w analizie śledzenia duże pliki, przeglądarki danych śledzenia usługi zawiera funkcję o nazwie "Częściowe ładowanie", które są ładowane są tylko niewielką część śledzenia w czasie. Na przykład masz plik śledzenia ponad 1GB, uruchomione przez kilka dni na serwerze. Jeśli wystąpiły błędy, można analizować śledzenia nie jest potrzebne do otwierania pliku całego śledzenia. Zamiast tego należy załadować śladów w przedziale czasu, gdy może wystąpić błąd. Ponieważ zakres jest mniejszy, narzędzie przeglądarki danych śledzenia usługi można wczytać pliku — szybciej i można zidentyfikować błędy przy użyciu mniejszy zestaw danych.

#### <a name="enabling-partial-loading"></a>Włączenie ładowania częściowego

Nie musisz ręcznie włączyć ładowania częściowego. Jeśli całkowity rozmiar plików śledzenia, który podejmie próbę załadowania przekracza 40 MB, przeglądarki danych śledzenia usługi automatycznie wyświetla ładowania częściowego okno dialogowe umożliwiające wybranie part, który chcesz załadować.

> [!NOTE]
> Ponieważ dane śledzenia nie mogą być rozproszone równomiernie w czasie zakresu, długość okresu, który określisz częściowe ładowania narzędzi może nie być proporcjonalny do rozmiaru ładowania widocznego. Rozmiar rzeczywisty ładowanie może być mniejszy niż szacowany rozmiar w oknie dialogowym ładowania częściowego.

#### <a name="adjusting-partial-loading"></a>Dostosowywanie ładowania częściowego

Po załadowaniu częściowo pliku śledzenia, można zmienić ładowany zestaw danych. Aby to zrobić przez dostosowanie narzędzi ładowania częściowego, u góry okna podglądu.

1. Przesuń pasek narzędzi, myszy, lub wprowadź godzinę rozpoczęcia i zakończenia.

2. Kliknij przycisk **Dostosuj** przycisku.

## <a name="understanding-trace-icons"></a>Omówienie śledzenia ikon

Poniżej przedstawiono listę ikon używanych przez narzędzie przeglądarki danych śledzenia usługi w **działania** widoku **wykres** widoku i **śledzenia** reprezentują różne elementy w okienku.

> [!NOTE]
> Niektóre dane śledzenia, które nie są podzielone (na przykład, "komunikat zostanie zamknięte") ma nie ikony.

### <a name="activity-tracing-traces"></a>Działania śledzenia śladów

|Ikona|Opis|
|----------|-----------------|
|![Ostrzeżenie śledzenia](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Ostrzeżenie śledzenia: Śledzenia, który jest emitowane na poziomie ostrzeżenia|
|![Błąd śledzenia](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Błąd śledzenia: Śledzenie, który jest emitowane na poziomie błędu.|
|![Działanie Rozpocznij śledzenie:](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Ślad rozpoczęcia działania: Śledzenie, która oznacza początek działania. Zawiera on nazwę działania. Projektant aplikacji lub dla deweloperów należy zdefiniować jedno działanie, Rozpocznij śledzenie na identyfikator działania na proces lub wątek.<br /><br /> Jeśli identyfikator działania są propagowane przez źródła śledzenia do śledzenia korelacji, następnie widać wielu rozpoczyna się dla tego samego identyfikatora aktywności (po jednej na źródła śledzenia). Rozpocznij śledzenie jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![Działanie Zatrzymaj śledzenie](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Działanie Zatrzymaj śledzenie: Śledzenie, który oznacza koniec działania. . Zawiera on nazwę działania. Projektant aplikacji lub dla deweloperów należy zdefiniować jedno działanie Zatrzymaj śledzenie według identyfikatorów aktywności dla źródła śledzenia. Nie śladów ze źródła śledzenia danego są wyświetlane po działaniu Stop emitowane przez to źródło śledzenia, z wyjątkiem, jeśli stopień szczegółowości czasu śledzenia nie jest wystarczająco mała. Jeśli tak się stanie, być przemieszane dwóch ślady z tym samym czasie, w tym zatrzymania, podczas wyświetlania. Jeśli identyfikator działania są propagowane przez źródła śledzenia do śledzenia korelacji, zostanie wyświetlony wielu zatrzyma się na tym samym identyfikatorze aktywności (po jednej na źródła śledzenia). Zatrzymaj śledzenie jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![Działanie Suspend śledzenia](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Działanie Suspend śledzenia: Śledzenie oznaczający razem, gdy działanie zostało wstrzymane. Ślady są emitowane w działanie wstrzymaną, dopóki nie wznawia działania. Działanie wstrzymaną oznacza działań wykonywanych w działania w zakresie źródła śledzenia nie przetwarzania. Wstrzymywanie/wznawianie ślady są przydatne do profilowania. Wstrzymaj śledzenia jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![Działanie wznowienia śledzenia](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4e0a-9988-cdc2f7030f17")|Ślad wznowienie działania: Śledzenie, oznaczający czas działania zostanie wznowione po jego została wstrzymana. Ślady mogą ponownie wyemitowane w tym działaniu. Wstrzymywanie/wznawianie ślady są przydatne do profilowania. Wznów śledzenia jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![Transfer](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Transfer: Śledzenie, który jest emitowane, gdy przepływ sterowania logicznych jest przenoszona z jednego działania na inny. Działanie, które pochodzi transfer może w dalszym ciągu wykonują pracę równolegle do działania, których przeniesienie przechodzi do. Transfer śledzenia jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![Transfer From](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Przenosić: Śledzenie, definiujący transfer z innego działania do bieżącego działania.|
|![Transfer To](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Przenieś do: Śledzenie, definiujący przeniesienia przepływu sterowania logicznych z bieżącego działania do kolejnego działania.|

### <a name="wcf-traces"></a>Dane śledzenia WCF

|Ikona|Opis|
|----------|-----------------|
|![Komunikat śledzenia dziennika](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Śledzenie dziennik komunikatów: Śledzenia, które są emitowane po wiadomości WCF jest rejestrowane za pomocą funkcji rejestrowania komunikatów podczas `System.ServiceModel.MessageLogging` źródła śledzenia jest włączona. Kliknięcie tego powoduje wyświetlenie komunikatu. Istnieją cztery punkty rejestrowania można skonfigurować wiadomości: ServiceLevelSendRequest, TransportSend, TransportReceive i ServiceLevelReceiveRequest, który może być również określony przez `messageSource` atrybutu w śledzenie dziennik komunikatów.|
|![Komunikat śledzenia odebrane](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Śledzenie odebranych komunikatów: Śledzenia, które są emitowane po odebraniu wiadomości WCF, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie informacji lub pełne. Ślad ma zasadnicze znaczenie dla wyświetlanie strzałek korelacji wiadomości w działaniu **wykres** widoku.|
|![Komunikat śledzenia wysłane](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Śledzenie wysłanych komunikatów: Śledzenia, który jest emitowane po wysłaniu wiadomości WCF, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie informacji lub pełne. Ślad ma zasadnicze znaczenie dla wyświetlanie strzałek korelacji wiadomości w działaniu **wykres** widoku.|

### <a name="activities"></a>Kategoria Activities

|Ikona|Opis|
|----------|-----------------|
|![Activity](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Działania: Wskazuje, że bieżące działanie jest ogólne działanie.|
|![Główny działania](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Działania głównego: Wskazuje działania głównego procesu.|

### <a name="wcf-activities"></a>Działania usługi WCF

|Ikona|Opis|
|----------|-----------------|
|![Działanie środowiska](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Działanie środowiska: Działanie, które umożliwia tworzenie, spowoduje otwarcie lub zamknięcie klienta lub hosta usługi WCF. Błędy, które wystąpiło podczas tych faz pojawi się w przypadku tego działania.|
|![Nasłuchiwanie działania](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Nasłuchiwanie działania: Działanie, które dzienniki śledzenia związane z odbiornika. Wewnątrz tego działania możemy wyświetlić żądania informacji i połączenie odbiornika.|
|![Odbieranie bajtów działania](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Odbieranie bajtów działania: Działanie, który grupuje wszystkie ślady dotyczące odbierania Bajty przychodzące połączenia między dwoma punktami końcowymi. To działanie jest niezbędne do korelacji z działaniami transportu, które propagowania ich identyfikator działania, takie jak sterownik http.sys. Błędy połączeń, takie jak przerwań pojawi się w przypadku tego działania.|
|![Przetwarzanie komunikatu działania](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Proces działania komunikatu: Działanie, które grupy danych śledzenia dotyczących tworzenia komunikatów WCF. Błędy z powodu nieprawidłowych koperty lub nieprawidłowo sformułowany komunikat pojawi się w działania. Wewnątrz tego działania możemy sprawdzić nagłówki wiadomości, aby zobaczyć, jeśli identyfikator działania został rozpropagowany od elementu wywołującego. Jeśli jest to wartość true, w przypadku, gdy przekazywane do procesu akcji działania (dalej), firma Microsoft można także przypisać do tego działania propagowany działania identyfikator korelacji między obiektami wywołującym i śladów funkcji.|
|![Komunikat śledzenia dziennika](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Działanie działania procesu: Działanie, który grupuje wszystkie ślady związane z żądaniem WCF między dwoma punktami końcowymi. Jeśli `propagateActivity` ustawiono `true` zarówno punkty końcowe w konfiguracji wszystkie ślady z obu punktów końcowych są scalane w jedno działanie, aby uzyskać bezpośredni wpływ. Takie działanie będzie zawierać błędy spowodowane transportu lub zabezpieczeń, przetwarzanie, rozszerzając na granicy kod użytkownika i utworzyć kopię (jeśli istnieje odpowiedzi).|
|![Przetwarzanie komunikatu działania](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Wykonaj działania użytkownika kodu: Działanie, który grupuje ślady kod użytkownika do przetworzenia żądania.|

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli nie masz uprawnień do zapisu w rejestrze, otrzymasz następujący komunikat o błędzie "Microsoft Service przeglądarka śledzenia nie został zarejestrowany w systemie" Kiedy używać "`svctraceviewer /register`" polecenie, aby zarejestrować narzędzia. W takiej sytuacji należy rejestrować przy użyciu konta które ma dostęp do zapisu do rejestru.

Ponadto narzędzie przeglądarki danych śledzenia usługi zapisuje niektóre ustawienia (na przykład niestandardowe filtry i opcje filtrowania) do pliku SvcTraceViewer.exe.settings w folderze zestawu. Jeśli nie masz uprawnień do odczytu dla pliku, nadal można uruchomić narzędzie, ale nie można załadować ustawień.

Jeśli otrzymasz komunikat o błędzie "Wystąpił nieznany błąd podczas przetwarzania śladów co najmniej jeden" podczas otwierania pliku etl, oznacza to, że format plik etl jest nieprawidłowy.

Po otwarciu dziennika śledzenia utworzone za pomocą arabskim systemie operacyjnym, możesz zauważyć, że nie działa filtr czasu. Na przykład roku 2005 odnosi się do roku 1427 w języku arabskim kalendarzu. Zakres czasu, obsługiwane przez przeglądarki danych śledzenia usługi filtr narzędzie nie obsługuje jednak daty wcześniejszej niż 1752. To oznacza, że nie jest możliwe wybrać poprawną datę w filtrze. Aby rozwiązać ten problem, należy utworzyć filtr niestandardowy (**widok/niestandardowe filtry**) za pomocą wyrażenia XPath do uwzględnienia w określonym zakresie czasu.

## <a name="see-also"></a>Zobacz także

- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Konfigurowanie śledzenia](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Kompleksowe śledzenie](./diagnostics/tracing/end-to-end-tracing.md)
