---
title: Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 543b0e714343cdb8078861ceb31e4f8035e20afd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321213"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)

Narzędzie Podgląd śledzenia usługi Windows Communication Foundation (WCF) ułatwia analizowanie śladów diagnostycznych generowanych przez funkcję WCF. Przeglądarka śledzenia usługi umożliwia łatwe scalanie, wyświetlanie i filtrowanie komunikatów śledzenia w dzienniku, co umożliwia diagnozowanie, naprawianie i weryfikowanie problemów z usługą WCF.

## <a name="configuring-tracing"></a>Konfigurowanie śledzenia

Ślady diagnostyczne zawierają informacje, które pokazują, co dzieje się w całej operacji aplikacji. Jak nazywa się to, można wykonać operacje ze źródła do miejsca docelowego i również za pośrednictwem punktów pośrednich.

Śledzenie można skonfigurować przy użyciu pliku konfiguracji aplikacji — plik Web. config dla aplikacji hostowanych w sieci Web lub pliku *nazwa_aplikacji*. config dla aplikacji samodzielnych. Oto przykład:

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

W tym przykładzie określono nazwę i typ odbiornika śledzenia. Odbiornik ma nazwę `sdt`, a w polu Typ należy dodać odbiornik śledzenia standardowego .NET Framework (System. Diagnostics. XmlWriterTraceListener). Atrybut `initializeData` służy do ustawiania nazwy pliku dziennika dla tego odbiornika jako `SdrConfigExample.e2e`. W przypadku pliku dziennika można zastąpić w pełni kwalifikowaną ścieżkę dla prostej nazwy pliku.

Przykład tworzy plik w katalogu głównym o nazwie SdrConfigExample. e2e. W przypadku używania podglądu śledzenia do otwierania pliku zgodnie z opisem w sekcji "Otwieranie i przeglądanie plików śledzenia WCF" można zobaczyć wszystkie wysłane komunikaty.

Poziom śledzenia jest kontrolowany przez ustawienie `switchValue`. Dostępne poziomy śledzenia są opisane w poniższej tabeli.

|Poziom śledzenia|Opis|
|-----------------|-----------------|
|Krytyczny|-Rejestruje błędy i wpisy dziennika zdarzeń, a następnie śledzi informacje o korelacji. Poniżej przedstawiono kilka przykładów sytuacji, w których można użyć poziomu krytycznego:<br />-Twoja domena aplikacji powiodła się z powodu nieobsługiwanego wyjątku.<br />-Nie można uruchomić aplikacji.<br />-Komunikat, który spowodował błąd pochodzący z procesu MojaApl. exe.|
|Błąd|-Rejestruje wszystkie wyjątki. Poziomu błędu można użyć w następujących sytuacjach:<br />-Twój kod uległ awarii z powodu nieprawidłowego wyjątku rzutowania.<br />-"Nie można utworzyć punktu końcowego" powoduje niepowodzenie aplikacji podczas uruchamiania.|
|Ostrzeżenie|-Istnieje warunek, który może spowodować błąd lub krytyczny błąd. Tego poziomu można użyć w następujących sytuacjach:<br />-Aplikacja otrzymuje więcej żądań, niż pozwala na to jej ustawienia ograniczania.<br />-Kolejka otrzymująca jest 98 procent skonfigurowanej pojemności.|
|Informacje|— Komunikaty przydatne do monitorowania i diagnozowania stanu systemu, mierzenia wydajności lub profilowania. Te informacje można wykorzystać do planowania pojemności i zarządzania wydajnością. Tego poziomu można użyć w następujących sytuacjach:<br />-Wystąpił błąd, gdy wiadomość dotarła do domeny AppDomain i została przeprowadzona deserializacji.<br />-Wystąpił błąd podczas tworzenia powiązania HTTP.|
|Pełny|— Śledzenie na poziomie debugowania zarówno dla kodu użytkownika, jak i obsługi. Ustaw ten poziom w następujący sposób:<br />— Nie masz pewności, która metoda w kodzie została wywołana w przypadku wystąpienia błędu.<br />-Masz skonfigurowany nieprawidłowy punkt końcowy i nie można uruchomić usługi, ponieważ wpis w magazynie rezerwacji jest zablokowany.|
|ActivityTracing|Przepływ zdarzeń między działaniami przetwarzania i składnikami.<br /><br /> Na tym poziomie Administratorzy i deweloperzy mogą skorelować aplikacje w tej samej domenie aplikacji.<br /><br /> -Ślady dla granic działania: Uruchamianie/zatrzymywanie.<br />— Ślady dla transferów.|

 Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W przykładowej konfiguracji odbiornik ma nazwę `sdt` i odbiornik standardowego .NET Framework śledzenia (`System.Diagnostics.XmlWriterTraceListener`) jest dodawany jako typ. Użyj `initializeData`, aby ustawić nazwę pliku dziennika dla tego odbiornika. Ponadto można zastąpić w pełni kwalifikowaną ścieżkę dla prostej nazwy pliku.

Począwszy od .NET Framework 4,8, kontrolki ComboBox w niektórych kompozycjach o dużym kontraście są wyświetlane w prawidłowym kolorze. Tę zmianę można wyłączyć, usuwając następujące ustawienie z pliku *svcTraceViewer. exe. config* :

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

## <a name="using-the-service-trace-viewer-tool"></a>Korzystanie z narzędzia Podgląd śledzenia usług

### <a name="opening-and-viewing-wcf-trace-files"></a>Otwieranie i przeglądanie plików śledzenia WCF

Przeglądarka śledzenia usług obsługuje trzy typy plików:

- Plik śledzenia WCF (. svcLog)

- Plik śledzenia zdarzeń (ETL)

- Plik śledzenia użycie Crismon

 Przeglądarka śledzenia usługi umożliwia otwieranie dowolnego obsługiwanego pliku śledzenia, Dodawanie i integrowanie dodatkowych plików śledzenia lub otwieranie i scalanie grup plików śledzenia jednocześnie.

##### <a name="to-open-a-trace-file"></a>Aby otworzyć plik śledzenia

1. Uruchom podgląd śledzenia usługi przy użyciu okna wiersza polecenia, aby przejść do lokalizacji instalacji programu WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin), a następnie wpisz `SvcTraceViewer.exe`.

> [!NOTE]
> Narzędzie Podgląd śledzenia usług można skojarzyć z dwoma typami plików:. svclog i. stvproj. Aby zarejestrować i wyrejestrować rozszerzenia plików, można użyć dwóch parametrów w wierszu polecenia.
>
> /Register: Zarejestruj skojarzenie rozszerzeń plików ". svclog" i ". stvproj" z SvcTraceViewer. exe
>
> /Unregister: Wyrejestrowywanie skojarzenia rozszerzeń plików ". svclog" i ". stvproj" z plikiem SvcTraceViewer. exe

1. Po uruchomieniu podglądu śledzenia usług kliknij pozycję **plik** , a następnie wskaż polecenie **Otwórz**. Przejdź do lokalizacji, w której są przechowywane pliki śledzenia.

2. Kliknij dwukrotnie plik śledzenia, który chcesz otworzyć.

    > [!NOTE]
    > Naciśnij klawisz SHIFT podczas klikania wielu plików śledzenia, aby wybrać i otworzyć je jednocześnie. Podgląd śledzenia usług Scala zawartość wszystkich plików i wyświetla jeden widok. Można na przykład otworzyć pliki śledzenia zarówno klienta, jak i usługi. Jest to przydatne, gdy włączono rejestrowanie komunikatów i propagację działań w konfiguracji. W ten sposób można przeanalizować wymianę komunikatów między klientem i usługą. Możesz również przeciągnąć wiele plików do przeglądarki lub użyć karty **projekt** . Aby uzyskać więcej informacji, zobacz sekcję Zarządzanie projektem.

3. Aby dodać więcej plików śledzenia do kolekcji, która jest otwarta, kliknij pozycję **plik** , a następnie wskaż polecenie **Dodaj**. W otwartym oknie przejdź do lokalizacji plików śledzenia i kliknij dwukrotnie plik, który chcesz dodać.

> [!CAUTION]
> Nie zaleca się ładowania pliku dziennika śledzenia większego niż 200 MB. Jeśli spróbujesz załadować plik większy niż ten limit, proces ładowania może zająć dużo czasu, w zależności od zasobu komputera. Narzędzie przeglądarka śledzenia usługi może nie reagować przez dłuższy czas lub może spowodować wyczerpanie pamięci maszyny. Zaleca się skonfigurowanie ładowania częściowego w celu uniknięcia tego. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz sekcję "Ładowanie dużych plików śledzenia".

#### <a name="event-tracing-and-crimson-tracing"></a>Śledzenie zdarzeń i śledzenie użycie Crismon

Format natywny przeglądarki jest formatem śledzenia aktywności, który emituje WCF. Ślady emitowane w innym formacie muszą zostać przekonwertowane przed wyświetleniem ich przez przeglądarkę. Obecnie oprócz formatu śledzenia działania przeglądarka obsługuje śledzenie zdarzeń i śledzenie użycie Crismon.

Po otwarciu pliku, który nie zawiera śladów aktywności, przeglądarka próbuje skonwertować plik. Należy określić nazwę i lokalizację pliku, który będzie zawierać skonwertowane dane śledzenia. Po przeprowadzeniu konwersji danych przeglądarka wyświetli zawartość nowego pliku.

> [!NOTE]
> Konwersja wymaga miejsca na dysku do przechowywania przekonwertowanych danych śledzenia. Upewnij się, że na dysku jest dostępna wystarczająca ilość miejsca do przechowywania danych przed rozpoczęciem konwersji. W przeciwnym razie konwersja nie powiedzie się.

### <a name="managing-projects"></a>Zarządzanie projektami

Przeglądarka obsługuje projekty w celu ułatwienia wyświetlania wielu plików śledzenia. Na przykład jeśli masz plik śledzenia klienta i plik śledzenia usługi, możesz dodać je do projektu. Następnie przy każdym otwarciu projektu wszystkie pliki śledzenia w projekcie są ładowane jednocześnie.

Istnieją dwa sposoby zarządzania projektami:

- W menu **plik** można otworzyć, zapisać i zamknąć projekty.

- Na karcie **projekt** można dodać pliki do projektu.

### <a name="viewing-wcf-traces"></a>Wyświetlanie śladów WCF

Funkcja WCF emituje ślady przy użyciu formatu śledzenia działań. W modelu śledzenia aktywności poszczególne ślady są pogrupowane w działania zgodnie z ich przeznaczeniem. Przepływ kontroli logicznej jest przesyłany między działaniami. Na przykład w okresie istnienia aplikacji wiele pojawiających się i znikających działań wysyłania komunikatów. Aby uzyskać więcej informacji o wyświetlaniu śladów i działań oraz interfejsie użytkownika przeglądarki śledzenia usługi, zobacz [Używanie przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](./diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).

#### <a name="switching-to-different-views"></a>Przełączanie do różnych widoków

Podgląd śledzenia usług udostępnia następujące różne widoki. Są one wyświetlane jako karty w lewym okienku przeglądarki i dostępne również z menu **Widok** .

- Widok działania

- Widok projektu

- Widok komunikatów

- Widok wykresu

##### <a name="activity-view"></a>Widok działania

Po otwarciu plików śledzenia można zobaczyć ślady pogrupowane w działania i wyświetlane w widoku **działania** w okienku po lewej stronie.

W widoku **działania** są wyświetlane nazwy działań, liczba śladów w działaniu, czas trwania, godzina rozpoczęcia i godzina zakończenia.

Po kliknięciu dowolnego z wymienionych działań ślady w tym działaniu są wyświetlane w okienku śledzenia po prawej stronie. Następnie możesz wybrać ślad, aby wyświetlić jego szczegóły.

Możesz wybrać wiele działań, naciskając klawisz **Ctrl** lub **SHIFT** i klikając odpowiednie działania. W okienku śledzenia zostaną wyświetlone wszystkie ślady wybranych działań.

Możesz kliknąć dwukrotnie działanie, aby wyświetlić je w widoku **wykresu** . Alternatywnym sposobem jest wybranie działania i przełączenie do widoku **wykresu** .

> [!NOTE]
> Działanie "000000000000" to działanie specjalne, którego nie można wyświetlić w widoku wykresu. Ze względu na to, że wszystkie inne działania są z nim powiązane, wyświetlanie tego działania ma poważny wpływ na wydajność.

Możesz kliknąć tytuł kolumny, aby posortować listę działań. Działania zawierające ślady ostrzeżeń mają żółte tło, a te, które zawierają ślady błędów, mają kolor czerwony.

Istnieją różne rodzaje działań i każdy typ odpowiada ikonie po lewej stronie każdego działania. W tym celu można zapoznać się z sekcją Omówienie ikon śledzenia.

##### <a name="project-view"></a>Widok projektu

Ten widok umożliwia zarządzanie plikami śledzenia w bieżącym projekcie. Aby uzyskać więcej informacji, zobacz sekcję Zarządzanie projektem.

##### <a name="message-view"></a>Widok komunikatów

Ten widok umożliwia wyświetlenie wszystkich śladów dzienników komunikatów, w tym akcji, daty/godziny, procesu, aktywności i od/do, a następnie przejście do szczegółów skojarzonego śledzenia dziennika komunikatów. Można grupować ślady dziennika komunikatów według granicy działania, procesu/wątku lub wysyłania & odbierania w celu łatwiejszego nawigowania w przepływie komunikatów.

##### <a name="graph-view"></a>Widok wykresu

Ten widok przedstawia dane śledzenia dla danego działania w formularzu wykresu. Formularz wykresu pozwala zobaczyć krokowe wykonywanie zdarzeń oraz współzależności między wieloma działaniami, ponieważ dane są przenoszone między nimi.

Aby przełączyć się do widoku **wykresu** , wybierz działanie w widoku **działania** , a następnie kliknij kartę **działanie** lub śledzenie dziennika komunikatów w widoku **komunikatów** . W przypadku załadowania wielu plików śledzenia, gdy działanie obejmuje ślady z więcej niż jednego pliku, wszystkie odpowiednie ślady są wyświetlane w widoku wykresu. Dwukrotne kliknięcie działań i ślady dziennika komunikatów również prowadzi do widoku **wykresu** .

W widoku **wykresu** każda pionowa kolumna reprezentuje działanie, a każdy blok w kolumnie reprezentuje wynik śledzenia. Działania są pogrupowane według procesu (lub wątku). Małe strzałki między działaniami reprezentują transfery. Duże strzałki między procesami reprezentują wymianę komunikatów. Działanie w zaznaczeniu jest zawsze żółte.

###### <a name="selecting-traces-in-the-graph"></a>Wybieranie śladów na wykresie

1. Kliknij blok na grafie.

2. Użyj klawiszy w górę i w dół, aby wybrać swoje sąsiednie ślady.

3. Obserwuj informacje o śledzeniu w okienku śledzenia i okienku szczegółów.

###### <a name="expanding-or-collapsing-activity-transfers"></a>Rozszerzanie lub zwijanie transferów działań

Można rozwinąć transfery działań, gdy działanie w obszarze wybór zostanie przetransferowane do innego działania. Dzięki temu można postępować zgodnie z transferami.

Aby rozwinąć lub zwinąć transfery działań,

1. Znajdź ślad transferu ze znakiem "+" po lewej stronie ikony transferu.

2. Kliknij "+" lub naciśnij **klawisze CTRL** i "+" przy użyciu klawiatury.

3. Następne działanie pojawia się na wykresie.

4. "-" Pojawia się po lewej stronie ikony transferu. Kliknij znak "-" lub naciśnij klawisze CTRL i "-", aby przenieść działanie.

> [!NOTE]
> Gdy działanie ma wiele transferów, i zostanie rozwinięte jedno z transferów, zostaną wyświetlone działania, które prowadzą do nowego działania z działania głównego. Te nowe działania są wyświetlane w zwiniętym formularzu. Jeśli chcesz zobaczyć szczegóły tych działań, rozwiń je pionowo, klikając ikonę rozwijania w nagłówku wykresu.

###### <a name="expanding-or-collapsing-activities-vertically"></a>Rozwijanie lub zwijanie działań w pionie

Przeglądarka ukrywa niepotrzebne szczegóły na grafie aktywności przez zwijanie działań. W działaniu zwiniętym pojedyncze ślady nie są wyświetlane. Wyświetlane są tylko ślady transferu. Aby wyświetlić wszystkie ślady w działaniu, rozwiń aktywność w pionie, klikając symbol rozwinięcia działania w nagłówku grafu.

Aby rozwinąć lub zwinąć działania w pionie,

1. Kliknij ikonę "+" w nagłówku działania, aby rozwinąć aktywność w pionie.

2. Zauważ, że wszystkie ślady są wyświetlane na wykresie.

3. Kliknij ikonę "-" w nagłówku działania, aby zwinąć aktywność w pionie.

4. Należy zauważyć, że w działaniu są wyświetlane tylko ważne transfery, dzienniki komunikatów, ostrzeżenia i ślady wyjątków.

###### <a name="options"></a>Opcje

Możesz wybrać dwie opcje z menu **opcji** w widoku wykresu.

- Pokaż ślady granicy działania, które po usunięciu zaznaczenia ignorują ślady granicy działania na wykresie.

- Pokaż pełne ślady niebędące wiadomościami, które po usunięciu zaznaczenia opcji Ignoruj pełne ślady poziomu, z wyjątkiem śladów komunikatów. W większości przypadków ślady poziomu verbose są mniej ważne dla analizy. Ta opcja jest przydatna, gdy nie chcesz analizować śladów pełnego poziomu i chcesz skupić się tylko na bardziej ważnych śladach.

###### <a name="layout-mode"></a>Tryb układu

Przeglądarka ma dwa tryby układu: **proces** i **wątek**. To ustawienie definiuje największą jednostkę organizacji. Domyślnym trybem układu jest **proces**, co oznacza, że działania są pogrupowane według procesów na grafie.

###### <a name="execution-list"></a>Lista wykonywania

Możesz wybrać proces lub wątek, który ma być wyświetlany na wykresie z tej listy rozwijanej. Na przykład, jeśli masz pliki śledzenia dwóch klientów (a i B), a jedna usługa została otwarta i chcesz tylko wyświetlić usługę i klienta A na grafie, możesz usunąć z listy opcję Klient B.

#### <a name="viewing-trace-details"></a>Wyświetlanie szczegółów śledzenia

Aby wyświetlić szczegóły śledzenia, wybierz śledzenie w okienku śledzenie. Szczegóły są wyświetlane w okienku szczegółów.

##### <a name="trace-pane"></a>Okienko śledzenia

Górne okienko w podglądzie śledzenia usługi jest okienkiem śledzenia. Wyświetla on wszystkie ślady w wybranym działaniu z dodatkowymi informacjami, na przykład poziom śledzenia, identyfikator wątku i nazwa procesu.

Możesz skopiować nieprzetworzony kod XML śledzenia do schowka, klikając prawym przyciskiem myszy ślad i wybierając **Kopiuj ślad do schowka**.

##### <a name="detail-pane"></a>Okienko szczegółów

Lewe dolne okienko w podglądzie śledzenia usługi jest okienkiem szczegółowym. Zawiera trzy karty do wyświetlania szczegółów śledzenia.

W widoku **sformatowanym** są wyświetlane informacje w bardziej zorganizowany sposób. Zawiera listę wszystkich znanych elementów XML w tabelach i drzewach, ułatwiając odczytywanie i zrozumienie informacji.

W widoku **XML** zostanie wyświetlony kod XML odpowiadający wybranemu śledzeniu. Obsługuje ona podświetlanie i kolor składni. W przypadku używania **Find** do wyszukiwania ciągów wyróżniane są wyniki wyszukiwania.

Widok **komunikatów** wyświetla część wiadomości XML w obszarze ślady dziennika komunikatów. Jest on niewidoczny w przypadku wybrania śledzenia bez komunikatów.

### <a name="filtering-wcf-traces"></a>Filtrowanie śladów WCF

Aby ułatwić analizę śledzenia, można je filtrować w następujący sposób:

- Pasek narzędzi filtru zapewnia dostęp do wstępnie zdefiniowanych i niestandardowych filtrów. Można ją włączyć za pomocą menu **Widok** .

- Wstępnie zdefiniowany filtr podglądu może służyć do selektywnego filtrowania części śladów WCF. Domyślnie jest ono ustawione tak, aby zezwalać na przekazywanie wszystkich śladów infrastruktury. Ustawienia tego filtru są zdefiniowane w podmenu **Opcje filtru** w menu **Widok** .

- Niestandardowe filtry XPath zapewniają użytkownikom pełną kontrolę nad filtrowaniem. Można je zdefiniować w **filtrze niestandardowym** w menu **Widok** .

Wyświetlane są tylko ślady przekazywane przez wszystkie filtry.

#### <a name="using-the-filter-toolbar"></a>Korzystanie z paska narzędzi filtru

Pasek narzędzi filtru pojawia się u góry narzędzia. Jeśli nie istnieje, możesz ją aktywować w menu **Widok** . Pasek ma trzy składniki:

- Wyszukaj: **Wyszukiwanie** definiuje temat, który ma być wyszukiwany w operacji filtrowania. Na przykład jeśli chcesz znaleźć wszystkie ślady, które były emitowane w kontekście procesu X, ustaw to pole na X i pole **wyszukiwania w** polu Nazwa procesu. To pole jest zmieniane na Kontrolka selektora daty/godziny, gdy jest wybrany filtr oparty na czasie.

- Wyszukaj w: to pole definiuje typ filtru, który ma zostać zastosowany.

- Poziom: ustawienie poziomu definiuje minimalny poziom śledzenia dozwolony przez filtr. Na przykład, jeśli poziom jest ustawiony na błąd i w górę, wyświetlane są tylko ślady na poziomie błędu i krytycznym. Ten filtr łączy z kryteriami określonymi przez wyszukiwanie i wyszukiwanie.

Przycisk **Filtruj teraz** uruchamia operację filtrowania. Niektóre filtry, zwłaszcza gdy są stosowane do dużego zestawu danych, potrwają dużo czasu. Możesz anulować operację filtrowania, naciskając przycisk **Zatrzymaj** , który pojawia się na pasku stanu w menu **operacje** .

Przycisk **Wyczyść** resetuje wstępnie zdefiniowane i niestandardowe filtry, aby umożliwić przekazywanie wszystkich śladów.

#### <a name="filter-options"></a>Opcje filtru

Przeglądarka może automatycznie usuwać dane śledzenia WCF z widoku. Umożliwia selektywne usuwanie śladów emitowanych przez określone obszary programu WCF, na przykład usuwanie śladów związanych z transakcjami z widoku.

Ustawienia tego filtru są zdefiniowane w podmenu **Opcje filtru** w menu **Widok** .

#### <a name="custom-filters"></a>Filtry niestandardowe

Jeśli znasz język ścieżki XML (XPath), możesz użyć go do skonstruowania filtrów niestandardowych, aby przeszukiwać dane śledzenia dowolnego interesującego elementu XML. Filtry są dostępne za pomocą paska narzędzi filtru.

Filtry niestandardowe mogą zawierać parametry. Można również zaimportować istniejące wcześniej filtry niestandardowe.

##### <a name="creating-a-custom-filter"></a>Tworzenie filtru niestandardowego

Filtry można tworzyć na dwa sposoby:

###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Tworzenie niestandardowego filtru przy użyciu Kreatora szablonu

Możesz kliknąć istniejący ślad i utworzyć filtr oparty na strukturze śledzenia. Ten przykład umożliwia utworzenie niestandardowego filtru na podstawie identyfikatora wątku.

1. W okienku śledzenie w prawym górnym rogu okna podglądu wybierz ślad zawierający element, którego ma dotyczyć filtr.

2. Kliknij przycisk **Utwórz filtr niestandardowy** znajdujący się w górnej części okienka śledzenia.

3. W wyświetlonym oknie dialogowym wprowadź nazwę filtru. W tym przykładzie wprowadź `Thread ID`. Możesz również podać opis filtra.

4. Widok drzewa po lewej stronie wyświetla strukturę rekordu śledzenia wybranego w kroku 1. Przejdź do elementu, dla którego chcesz utworzyć warunek. W tym przykładzie przejdź do ThreadID, który ma znajdować się w węźle XPath: /E2ETraceEvent/System/Execution/@ThreadID. Kliknij dwukrotnie atrybut ThreadID w widoku drzewa. Spowoduje to utworzenie wyrażenia dla atrybutu po prawej stronie okna dialogowego.

5. Zmień wartość pola Parameter dla warunku ThreadID z none na "{0}". Ten krok umożliwia skonfigurowanie wartości ThreadID podczas stosowania filtru. (Zobacz sekcję jak zastosować filtr) Można zdefiniować maksymalnie cztery parametry. Warunki są łączone za pomocą operatora OR.

6. Kliknij przycisk **OK** , aby utworzyć filtr.

> [!NOTE]
> Po utworzeniu filtru za pomocą Kreatora szablonu można go edytować tylko ręcznie. Nie można aktywować kreatora dla filtru, który został wcześniej utworzony. Ponadto warunki filtru XPath utworzonego w Kreatorze szablonów są łączone za pomocą operatora OR. Jeśli wymagana jest operacja i, można edytować wyrażenie filtru po jego utworzeniu.

###### <a name="creating-a-custom-filter-manually"></a>Ręczne tworzenie filtru niestandardowego

Menu Filtry niestandardowe pozwala na ręczne wprowadzanie filtrów XPath.

1. W menu Widok kliknij element menu **filtry niestandardowe** .

2. W wyświetlonym oknie dialogowym kliknij pozycję **Nowy.**

3. Określ nazwę filtru i wyrażenie XPath przy minimalnej wartości.

4. Kliknij przycisk **OK**.

###### <a name="applying-a-custom-filter"></a>Stosowanie filtru niestandardowego

Po utworzeniu filtru niestandardowego jest on dostępny za pośrednictwem paska narzędzi filtru. Wybierz filtr, który ma zostać zastosowany w polu **Wyszukaj w** pasku narzędzi filtru. W poprzednim przykładzie wybierz pozycję "Identyfikator wątku".

1. Określ wartość, której szukasz, w polu **Znajdź** . W naszym przykładzie wprowadź identyfikator wątku, który chcesz wyszukać.

2. Kliknij pozycję **Filtruj teraz**i obserwuj wynik operacji.

Jeśli filtr używa wielu parametrów, wprowadź je za pomocą znaku ";" jako separatora w polu **Znajdź** . Na przykład następujący ciąg definiuje 3 parametry: ' 1; findValue; text '. Przeglądarka stosuje wartość "1" do parametru {0} filtru. wartości "findValue" i "text" są stosowane odpowiednio do {1} i {2}.

###### <a name="sharing-custom-filters"></a>Udostępnianie filtrów niestandardowych

Filtry niestandardowe mogą być współużytkowane między różnymi sesjami i różnymi użytkownikami. Możesz wyeksportować filtry do pliku definicji i zaimportować ten plik w innej lokalizacji.

 Aby zaimportować filtr niestandardowy:

1. W menu **Widok** kliknij pozycję **filtry niestandardowe**.

2. W otwartym oknie dialogowym kliknij przycisk **Importuj** .

3. Przejdź do pliku filtru niestandardowego (. stvcf), kliknij plik, a następnie kliknij przycisk **Otwórz** .

Aby wyeksportować filtr niestandardowy:

1. W menu Widok kliknij pozycję **filtry niestandardowe**.

2. W otwartym oknie dialogowym Wybierz filtr, który chcesz wyeksportować.

3. Kliknij przycisk **Eksportuj** .

4. Określ nazwę i lokalizację pliku definicji filtru niestandardowego (. stvcf), a następnie kliknij przycisk **Zapisz** .

> [!NOTE]
> Te filtry niestandardowe można importować i eksportować tylko z przeglądarki śledzenia usługi. Nie mogą być odczytane przez inne narzędzia.

### <a name="finding-data"></a>Znajdowanie danych

Przeglądarka udostępnia następujące metody znajdowania danych:

- Pasek narzędzi Znajdź zapewnia szybki dostęp do najczęściej używanych opcji znajdowania.

- Okno dialogowe znajdowania zawiera więcej opcji znajdowania. Jest dostępny za pomocą menu **Edytuj** lub przez krótki klawisz Ctrl + F.

Pasek narzędzi Znajdź pojawia się u góry okna podglądu. Jeśli nie istnieje, możesz ją aktywować w menu **Widok** . Pasek ma dwa składniki:

- Znajdź: umożliwia wprowadzenie słowa kluczowego wyszukiwania.

- Szukaj w: umożliwia wprowadzenie zakresu wyszukiwania. Można wybrać, czy mają być wyszukiwane wszystkie działania, czy tylko bieżące działanie.

W oknie dialogowym Znajdowanie dostępne są dwie dodatkowe opcje:

- Znajdź element docelowy:

  - Opcja "nieprzetworzone dane dziennika" przeszukuje słowo kluczowe we wszystkich danych pierwotnych.

  - Opcje "tekst XML" i "atrybut XML" przeszukują tylko elementy XML.

  - Opcja "zalogowany komunikat" przeszukuje słowo kluczowe tylko w komunikatach.

- Ignoruj działanie główne: wyszukiwanie ignoruje ślady w działaniu "000000000000". Poprawia to wydajność w dużych plikach śledzenia, gdy działanie główne ma tysiące śladów, z których większość jest transferowana.

### <a name="navigating-traces"></a>Nawigowanie po śladach

Ponieważ ślady są rejestrowane krok po kroku w czasie wykonywania aplikacji, przechodzenie między śladami może ułatwić debugowanie aplikacji. Przeglądarka śledzenia usługi oferuje różne sposoby nawigowania w śladach.

#### <a name="step-forward-or-backward"></a>Krok do przodu lub do tyłu

Jeśli wszystkie ślady są rozpatrywane jako wiersz kodu w programie, przechodzenie do przodu jest bardzo podobne do "krok po kroku" w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio. Różnica polega na tym, że można również przejść do tyłu w śladach. Przechodzenie do przodu oznacza przejście do następnego śladu w działaniu.

- Przejdź do przodu: Użyj menu **działania** lub naciśnij klawisz "F10". W okienku śledzenia można także użyć klawisza Strzałka w dół.

- Przejdź do tyłu: Użyj menu **działania** lub naciśnij klawisz F9. W okienku śledzenia można także użyć klawisza Strzałka w górę.

> [!NOTE]
> Może to potrwać do działania w innym procesie lub nawet na innym komputerze, ponieważ komunikaty programu WCF mogą zawierać identyfikatory działań, które obejmują maszyny.

#### <a name="follow-transfer"></a>Postępuj zgodnie z transferem

Ślady transferu to specjalne ślady w pliku śledzenia. Działanie może zostać przeniesione do innego działania przez śledzenie transferu. Na przykład "działanie A" może zostać przeniesione do "Activity B". W takim przypadku istnieje śledzenie transferu w "Activity A" o nazwie "to: Activity" i ikonie transferu. Ten ślad transferu jest łączem między dwoma śladami. W obszarze "aktywność B" może być również śledzony transfer na końcu działania, aby można było przesłać z powrotem do "działania A". Jest to podobne do wywołań funkcji w programach: wywołania B, a następnie B zwracają.

"Śledź transfer" przypomina "krok po kroku" w debugerze. Następuje przeniesienie od A do B. Nie ma żadnego wpływu na inne ślady.

Istnieją dwa sposoby postępowania z transferem: według myszy lub klawiatury:

- Za pomocą myszy: kliknij dwukrotnie ślad transferu w okienku śledzenie.

- Za pomocą klawiatury: Wybierz śledzenie transferu i użyj polecenia "śledź transfer" w menu **działania** lub naciśnij klawisz "F11"

> [!NOTE]
> W wielu przypadkach, gdy działanie przenosi do działania B, aktywność A oczekuje do momentu, aż aktywność B przeniesie z powrotem do działania A. Oznacza to, że działanie A nie ma śledzenia rejestrowane w okresie, gdy działanie B jest aktywnie śledzone. Jednak jest to możliwe również, że działanie A nie czeka i kontynuuje rejestrowanie śladów. Istnieje również możliwość, że działanie B nie przeniesie z powrotem do działania A. W związku z tym transfery aktywności nadal różnią się od wywołań funkcji w tym sensie. W widoku wykresu można lepiej zrozumieć transfery działań.

#### <a name="jump-to-next-or-previous-transfer"></a>Przejdź do następnego lub poprzedniego transferu

Podczas analizowania bieżącego działania lub wybranych działań w przypadku wybrania wielu działań warto szybko znaleźć działania, do których są przesyłane. "Przeskocz do następnego transferu" pozwala zlokalizować następny ślad transferu w działaniu. Po znalezieniu śledzenia transferu można użyć polecenia "śledź transfer", aby przejść do następnego działania.

- Przejdź do następnego transferu: Użyj menu **działania** lub naciśnij klawisze "CTRL + F10".

- Przejdź do poprzedniego transferu: Użyj menu **działania** lub naciśnij klawisze "Ctrl + F9".

#### <a name="navigate-in-graph-view"></a>Nawigowanie w widoku wykresu

Chociaż nawigowanie w okienku działanie i w okienku śledzenia jest podobne do debugowania, Używanie widoku **wykresu** zapewnia znacznie lepsze środowisko nawigacji. Aby uzyskać więcej informacji, zobacz sekcję "widok wykresu".

### <a name="loading-large-trace-files"></a>Ładowanie dużych plików śledzenia

Pliki śledzenia mogą być bardzo duże. Na przykład, jeśli włączysz śledzenie na poziomie "verbose", wynikowy plik śledzenia do uruchomienia kilku minut może być w łatwy w użyciu setki megabajtów lub nawet większy, w zależności od szybkości sieci i wzorca komunikacji.

Po otwarciu bardzo dużego pliku śledzenia w podglądzie śledzenia usług może to mieć negatywny wpływ na wydajność systemu. Szybkość ładowania i czas odpowiedzi po załadowaniu mogą być wolne. Rzeczywista szybkość różni się od czasu do czasu, w zależności od konfiguracji sprzętowej. W większości komputerów ładowanie pliku śledzenia większego niż 200M ma poważny wpływ na wydajność. W przypadku śledzenia plików większych niż 1G narzędzie może korzystać z całej dostępnej pamięci lub przestać odpowiadać przez bardzo długi czas.

Aby uniknąć wolnego czasu ładowania i odpowiedzi podczas analizowania dużych plików śledzenia, przeglądarka śledzenia usług udostępnia funkcję o nazwie "częściowe ładowanie", która ładuje jedynie niewielką część śledzenia w danym momencie. Na przykład może istnieć plik śledzenia o rozmiarze 1 GB, uruchomiony przez kilka dni na serwerze. Gdy wystąpią jakieś błędy i chcesz analizować ślad, nie trzeba otwierać całego pliku śledzenia. Zamiast tego można załadować ślady w określonym czasie, gdy wystąpi błąd. Ze względu na to, że zakres jest mniejszy, narzędzie Podgląd śledzenia usługi może załadować plik szybciej i można zidentyfikować błędy przy użyciu mniejszego zestawu danych.

#### <a name="enabling-partial-loading"></a>Włączanie ładowania częściowego

Nie jest konieczne ręczne włączenie ładowania częściowego. Jeśli łączny rozmiar plików śledzenia, które próbujesz załadować, przekracza 40MB, przeglądarka śledzenia usługi automatycznie wyświetli okno dialogowe ładowania częściowego umożliwiające wybranie części, która ma zostać załadowana.

> [!NOTE]
> Ponieważ ślady nie mogą być dystrybuowane równomiernie w przedziale czasu, długość okresu określonego na pasku narzędzi do częściowego ładowania może nie być proporcjonalna do pokazanego rozmiaru ładowania. Rzeczywisty rozmiar ładowania może być mniejszy niż szacowany rozmiar w oknie dialogowym częściowego ładowania.

#### <a name="adjusting-partial-loading"></a>Dostosowywanie ładowania częściowego

Po załadowaniu pliku śledzenia częściowo można zmienić ładowany zestaw danych. Można to zrobić, dopasowując częściowy pasek narzędzi ładowania w górnej części okna podglądu.

1. Przenieś pasek narzędzi według myszy lub wprowadź godzinę rozpoczęcia i zakończenia.

2. Kliknij przycisk **Dostosuj** .

## <a name="understanding-trace-icons"></a>Omówienie ikon śledzenia

Poniżej znajduje się lista ikon używanych przez narzędzie Podgląd śledzenia usług w widoku **działania** , widoku **wykresu** i w okienku **śledzenia** do reprezentowania różnych elementów.

> [!NOTE]
> Niektóre ślady, które nie zostały skategoryzowane (na przykład "komunikat jest zamknięty") nie ma ikony.

### <a name="activity-tracing-traces"></a>Ślady śledzenia działań

|Ikona|Opis|
|----------|-----------------|
|![Ostrzeżenie śledzenia](./media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Śledzenie ostrzeżeń: ślad, który jest emitowany na poziomie ostrzeżenia|
|![Śledzenie błędów](./media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Śledzenie błędów: ślad, który jest emitowany na poziomie błędu.|
|![Śledzenie rozpoczęcia działania:](./media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Śledzenie rozpoczęcia działania: ślad, który oznacza początek działania. Zawiera nazwę działania. Jako projektant aplikacji lub deweloper, należy zdefiniować jedno śledzenie uruchamiania działań dla każdego procesu lub wątku.<br /><br /> Jeśli identyfikator działania jest propagowany między źródłami śledzenia dla korelacji śledzenia, można zobaczyć wiele uruchomień dla tego samego identyfikatora działania (jeden na źródło śledzenia). Śledzenie uruchamiania jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![Śledzenie zatrzymania działania](./media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Śledzenie zatrzymania działania: ślad, który oznacza koniec działania. . Zawiera nazwę działania. Jako projektant aplikacji lub deweloper należy zdefiniować jeden ślad zatrzymania działania dla każdego identyfikatora działania dla źródła śledzenia. Po zatrzymaniu działania przez to źródło śledzenia nie są wyświetlane żadne ślady z danego źródła śledzenia, z wyjątkiem tego, czy stopień szczegółowości czasu śledzenia nie jest wystarczająco mały. W takim przypadku dwa ślady z tym samym czasem, łącznie z zatrzymaniem, mogą zostać przeplatane po wyświetleniu. Jeśli identyfikator działania jest propagowany między źródłami śledzenia dla korelacji śledzenia, można zobaczyć wiele zatrzymań dla tego samego identyfikatora działania (jeden na źródło śledzenia). Śledzenie zatrzymania jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|(./media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32") ![śledzenia wstrzymania działania]|Śledzenie wstrzymania działania: ślad, który oznacza czas wstrzymania działania. Żadne ślady nie są emitowane w zawieszonej aktywności do momentu wznowienia działania. Działanie zawieszone oznacza, że żadne przetwarzanie nie odbywa się w tym działaniu w zakresie źródła śledzenia. Śledzenie zawieszania/wznawiania jest przydatne do profilowania. Śledzenie wstrzymania jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![Śledzenie wznowienia działania](./media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4E0A-9988-cdc2f7030f17")|Śledzenie wznawiania działania: ślad oznaczający czas wznowienia działania po jego wstrzymaniu. Ślady mogą być emitowane ponownie w ramach tego działania. Śledzenie zawieszania/wznawiania jest przydatne do profilowania. Ślad wznawiania jest emitowany, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![](./media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "B2d9850e-f362-4ae5-bb8d-9f6f3ca036a5") transferu|Transfer: ślad, który jest emitowany, gdy przepływ kontroli logicznej jest transferowany z jednego działania do innego. Działanie, z którego pochodzi transfer, może nadal wykonywać pracę równolegle do działania, do którego przejdzie transfer. Śledzenie transferu jest emitowane, jeśli ActivityTracing jest włączona dla źródła śledzenia.|
|![Transfer z](./media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Prześlij z: ślad, który definiuje transfer z innego działania do bieżącego działania.|
|![Przenieś do](./media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Prześlij do: ślad, który definiuje transfer przepływu sterowania logicznego z bieżącego działania do innego działania.|

### <a name="wcf-traces"></a>Ślady WCF

|Ikona|Opis|
|----------|-----------------|
|(./media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197") ![śledzenia dziennika komunikatów]|Śledzenie dziennika komunikatów: ślad, który jest emitowany, gdy komunikat WCF jest rejestrowany przez funkcję rejestrowania komunikatów, gdy włączone jest źródło śledzenia `System.ServiceModel.MessageLogging`. Kliknięcie tego śladu wyświetla komunikat. Istnieją cztery konfigurowalne punkty rejestrowania dla wiadomości: ServiceLevelSendRequest, TransportSend, TransportReceive i ServiceLevelReceiveRequest, które mogą być również określane przez atrybut `messageSource` w śladie dziennika komunikatów.|
|![Komunikat](./media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c") śledzenia|Komunikat otrzymany ślad: ślad, który jest emitowany po odebraniu komunikatu WCF, jeśli źródło śledzenia `System.ServiceModel` jest włączone na poziomie informacji lub szczegółowości. Ten ślad jest istotny do wyświetlania strzałki korelacji komunikatów w widoku **wykresu** aktywności.|
|![Wysłany komunikat](./media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4C12-9405-677e995ac387") śledzenia|Komunikat wysłany do śledzenia: ślad, który jest emitowany, gdy zostanie wysłany komunikat WCF, jeśli źródło śledzenia `System.ServiceModel` jest włączone na poziomie informacji lub szczegółowości. Ten ślad jest istotny do wyświetlania strzałki korelacji komunikatów w widoku **wykresu** aktywności.|

### <a name="activities"></a>Kategoria Activities

|Ikona|Opis|
|----------|-----------------|
|![](./media/wcfc-defaultactivityc.gif "Wcfc_defaultActivityc") działania|Działanie: wskazuje, że bieżące działanie jest działaniem ogólnym.|
|(./media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9") ![działania głównego]|Działanie główne: wskazuje działanie główne procesu.|

### <a name="wcf-activities"></a>Działania WCF

|Ikona|Opis|
|----------|-----------------|
|(./media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1") ![działania środowiska]|Działanie środowiska: działanie, które tworzy, otwiera lub zamyka hosta lub klienta WCF. W tym działaniu pojawią się błędy, które wystąpiły w trakcie tych faz.|
|(./media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "D7b135f6-ec7d-45d7-9913-037ab30e4c26") ![aktywności nasłuchiwania]|Działanie nasłuchiwania: działanie, które rejestruje ślady związane z odbiornikiem. Wewnątrz tego działania możemy wyświetlać informacje o odbiorniku i żądania połączeń.|
|(./media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e") ![aktywności odbierania bajtów]|Aktywność odbierania bajtów: działanie grupujące wszystkie ślady związane z odbieraniem przychodzących bajtów w ramach połączenia między dwoma punktami końcowymi. To działanie jest niezbędne do skorelowania z działaniami transportowymi, które propagują ich identyfikator działania, takich jak http. sys. W tym działaniu będą wyświetlane błędy połączeń, takie jak przerwania.|
|![Proces działania komunikatu](./media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Działanie przetwarzania komunikatu: działanie grupujące dane śledzenia związane z tworzeniem komunikatów WCF. Błędy spowodowane złą kopertą lub źle sformułowany komunikat pojawi się w tym działaniu. Wewnątrz tego działania możemy sprawdzić nagłówki wiadomości, aby sprawdzić, czy identyfikator działania został rozpropagowany z obiektu wywołującego. Jeśli ta wartość jest równa true, w przypadku przechodzenia do działania dotyczącego akcji (kolejnej ikony) można także przypisać do tego działania propagowany identyfikator działania dla korelacji między ślady wywołujące i wywoływane.|
|(./media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197") ![śledzenia dziennika komunikatów]|Działanie działania procesu: działanie grupujące wszystkie ślady związane z żądaniem programu WCF w dwóch punktach końcowych. Jeśli `propagateActivity` jest ustawiona na `true` dla obu punktów końcowych w konfiguracji, wszystkie ślady z obu punktów końcowych zostaną scalone w jedno działanie dla bezpośredniej korelacji. Takie działanie będzie zawierać błędy spowodowane transportem lub przetwarzaniem zabezpieczeń, rozszerzając do granicy kodu użytkownika i z powrotem (Jeśli odpowiedź istnieje).|
|![Proces działania komunikatu](./media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Działanie wykonywania kodu użytkownika: działanie grupujące dane śledzenia kodu użytkownika na potrzeby przetwarzania żądania.|

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli użytkownik nie ma uprawnień do zapisu w rejestrze, zostanie wyświetlony następujący komunikat o błędzie "w przypadku użycia polecenia" `svctraceviewer /register` "Podgląd śledzenia usługi firmy Microsoft nie został zarejestrowany w systemie, gdy do zarejestrowania tego narzędzia jest używane polecenie" {0} ". W takim przypadku należy zalogować się przy użyciu konta, które ma dostęp do zapisu w rejestrze.

Ponadto narzędzie Podgląd śledzenia usług zapisuje niektóre ustawienia (na przykład filtry niestandardowe i opcje filtru) do pliku SvcTraceViewer. exe. Settings w folderze zestawu. Jeśli nie masz uprawnienia do odczytu pliku, możesz nadal uruchamiać narzędzie, ale nie można załadować ustawień.

Jeśli zostanie wyświetlony komunikat o błędzie "Wystąpił nieznany błąd podczas przetwarzania co najmniej jednego śladu" podczas otwierania pliku. etl, oznacza to, że format pliku ETL jest nieprawidłowy.

Jeśli otworzysz dziennik śledzenia utworzony przy użyciu arabskiej systemu operacyjnego, możesz zauważyć, że filtr czasu nie działa. Na przykład rok 2005 odpowiada roku 1427 w kalendarzu arabskim. Jednak zakres czasu obsługiwany przez filtr narzędzia Podgląd śledzenia usług nie obsługuje daty wcześniejszej niż 1752. Może to oznaczać, że nie można wybrać prawidłowej daty w filtrze. Aby rozwiązać ten problem, można utworzyć filtr niestandardowy (**Widok/filtry niestandardowe**) przy użyciu wyrażenia XPath, aby uwzględnić określony zakres czasu.

## <a name="see-also"></a>Zobacz także

- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](./diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Konfigurowanie śledzenia](./diagnostics/tracing/configuring-tracing.md)
- [Kompleksowe śledzenie](./diagnostics/tracing/end-to-end-tracing.md)
