---
title: Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 215e34a3e7b075463ceeaa15386d3a347ffff064
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809020"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)
Narzędzia podglądu śledzenia usługi Windows Communication Foundation (WCF) pomaga analizować dane śledzenia diagnostycznego, które są generowane przez usługę WCF. Przeglądarki danych śledzenia usługi umożliwia łatwe scalania, widoków i filtrować komunikaty śledzenia w dzienniku, tak aby zdiagnozować, naprawy i sprawdź problemów dotyczących usługi WCF.  
  
## <a name="configuring-tracing"></a>Konfigurowanie śledzenia  
 Dane śledzenia diagnostycznego udostępnić informacje, które wskazują na to, co dzieje się w całej aplikacji operacji. Jak nazwa wskazuje, można wykonać operacji z ich źródła do miejsca docelowego, a także pośrednich punktów.  
  
 Można skonfigurować przy użyciu pliku konfiguracji aplikacji śledzenie — którejkolwiek Web.config dla aplikacji hostowanych w sieci Web, lub *Appname*.config własnym obsługiwanych aplikacji. Oto przykład:  
  
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
  
 W tym przykładzie określono nazwę i typ obiektu nasłuchującego śledzenia. Odbiornik o nazwie `sdt` i standardowe nasłuchującego śledzenia .NET Framework (System.Diagnostics.XmlWriterTraceListener) jest dodawana jako typu. `initializeData` Atrybut służy do ustawiania nazwy pliku dziennika dla tego odbiornika jako `SdrConfigExample.e2e`. Dla pliku dziennika można użyć w pełni kwalifikowaną ścieżkę dla nazwy pliku prostego.  
  
 W przykładzie jest tworzony plik w katalogu głównym o nazwie SdrConfigExample.e2e. Po podglądzie śledzenia można otworzyć pliku, zgodnie z opisem w sekcji "Otwieranie i wyświetlanie WCF pliki śledzenia", można wyświetlić wszystkie komunikaty, które zostały wysłane.  
  
 Poziom śledzenia jest kontrolowany przez `switchValue` ustawienie. Poziomy śledzenia dostępne są opisane w poniższej tabeli.  
  
|Poziom śledzenia|Opis|  
|-----------------|-----------------|  
|Krytyczny|-Rejestruje wpisy Fast kończyć się niepowodzeniem i dziennik zdarzeń i informacje o śledzeniu korelacji. Oto kilka przykładów sytuacji, należy zastosować poziom krytyczny:<br />-AppDomain zakończył działanie z powodu nieobsługiwanego wyjątku.<br />-Aplikacji nie powiedzie się.<br />-Komunikat, który spowodował błąd pochodzi z procesu MyApp.exe.|  
|Błąd|— Rejestruje wszystkie wyjątki. Możesz użyć poziom błędów w następujących sytuacjach:<br />-Awaria kodu ze względu na nieprawidłowe rzutowanie wyjątek.<br />Wyjątek "nie można utworzyć punktu końcowego" powoduje niepowodzenie podczas uruchamiania aplikacji.|  
|Ostrzeżenie|-Istnieje warunek, który następnie może spowodować błąd lub błąd krytyczny. Możesz użyć tego poziomu w następujących sytuacjach:<br />-Aplikacja odbiera żądania więcej niż umożliwia jego ustawienia ograniczenia przepustowości.<br />-Odbierania kolejka jest w 98 procent jego skonfigurowaną pojemność.|  
|Informacje|-Przydatne do monitorowania i diagnozowania stan systemu, pomiaru wydajności lub profilowania komunikaty są generowane. Może wykorzystywać takie informacje dotyczące planowania i wydajności zarządzanie wydajnością. Możesz użyć tego poziomu w następujących sytuacjach:<br />— Po wiadomości osiągnął elementu AppDomain i wykonano deserializacji wystąpił błąd.<br />-Błąd wystąpił podczas tworzenia wiązania HTTP.|  
|Pełny|-Debugowania poziomu śledzenie dla obu kod użytkownika i obsługi. Ustaw poziom po:<br />— Nie ma pewności wywołano metodę, które w kodzie, gdy wystąpił błąd.<br />-Jest niepoprawny punkt końcowy skonfigurowany i usługi nie powiodło się, ponieważ wpis w magazynie rezerwacji jest zablokowany.|  
|ActivityTracing|Przepływ zdarzenia między działaniami przetwarzania i składniki.<br /><br /> Ten poziom umożliwia Administratorzy i deweloperzy służące do skorelowania aplikacji w tej samej domenie aplikacji.<br /><br /> -Dane śledzenia granice działania: uruchamiania i zatrzymywania.<br />-Ślady transferów.|  
  
 Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W konfiguracji przykład odbiornik o nazwie `sdt` i standardowe nasłuchującego śledzenia .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jest dodawana jako typu. Użyj `initializeData` można ustawić nazwy pliku dziennika dla tego odbiornika. Ponadto można użyć w pełni kwalifikowaną ścieżkę dla nazwy pliku prostego.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Za pomocą narzędzia podglądu śledzenia usługi  
  
### <a name="opening-and-viewing-wcf-trace-files"></a>Otwieranie i wyświetlanie plików śledzenia WCF  
 Przeglądarka śledzenia usługi obsługuje trzy typy plików:  
  
-   Usługi WCF (.svcLog) pliku śledzenia  
  
-   Zdarzenia śledzenia w pliku (ETL)  
  
-   Plik śledzenia crismon  
  
 Podgląd śledzenia usługi umożliwia otwierania plików obsługiwanych śledzenia, Dodaj i integrowanie śledzenia dodatkowe pliki, lub Otwórz i jednocześnie scalania grupy plików śledzenia.  
  
##### <a name="to-open-a-trace-file"></a>Aby otworzyć plik śledzenia  
  
1.  Uruchom Podgląd śledzenia usługi za pomocą okna polecenia przejdź do lokalizacji instalacji usługi WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin), a następnie wpisz `SvcTraceViewer.exe`.  
  
> [!NOTE]
>  Narzędzia podglądu śledzenia usługi można skojarzyć z dwóch typów plików: .svclog i .stvproj. Dwa parametry wiersza polecenia umożliwia rejestrowanie i wyrejestrowywanie rozszerzenia pliku.  
>   
>  / register: Zarejestruj skojarzenia pliku rozszerzenia ".svclog" i ".stvproj" SvcTraceViewer.exe  
>   
>  / unregister: wyrejestrować skojarzenia pliku rozszerzenia ".svclog" i ".stvproj" z SvcTraceViewer.exe  
  
1.  Podczas uruchamiania przeglądarki danych śledzenia usługi, kliknij przycisk **pliku** , a następnie wskaż polecenie **Otwórz**. Przejdź do lokalizacji, w którym są przechowywane pliki śledzenia.  
  
2.  Kliknij dwukrotnie plik śledzenia, który chcesz otworzyć.  
  
    > [!NOTE]
    >  Naciśnij klawisz SHIFT podczas klikania wiele plików śledzenia, wybierz i otwórz je jednocześnie. Przeglądarki danych śledzenia usługi Scala zawartość wszystkich plików i przedstawia jeden widok. Na przykład można otworzyć pliki śledzenia zarówno klient, jak i usługi. Jest to przydatne, gdy włączono rejestrowanie i działania propagacji komunikat w konfiguracji. W ten sposób można sprawdzić w wymianie wiadomości między klientem a usługą. Można także przeciągnąć wielu plików do podglądu lub użyj **projektu** kartę. W sekcji Zarządzanie projektu więcej szczegółów.  
  
3.  Aby dodać pliki śledzenia dodatkowe do kolekcji, która jest otwarta, kliknij przycisk **pliku** , a następnie wskaż polecenie **Dodaj**. W otwartym oknie przejdź do lokalizacji plików śledzenia, a następnie kliknij dwukrotnie plik, który chcesz dodać.  
  
> [!CAUTION]
>  Nie zaleca się załadowanie pliku dziennika śledzenia większe niż 200MB. Próba załadowania pliku większego niż to ograniczenie proces ładowania może zająć dużo czasu, w zależności od zasobu komputera. Narzędzia podglądu śledzenia usługi mogą nie odpowiadać przez długi czas lub może on zużywa pamięć komputera. Zalecane jest skonfigurowanie częściowe ładowania Aby tego uniknąć. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz sekcję "Pliki ładowania dużych śledzenia".  
  
#### <a name="event-tracing-and-crimson-tracing"></a>Śledzenie zdarzeń i śledzenia Crismon  
 Podgląd formatu macierzystego to format śledzenie działania, który emituje WCF. Przed przeglądarka wyświetli je, należy przekonwertować śladów emitowanych w innym formacie. Obecnie oprócz format śledzenie działania, przeglądarka obsługuje śledzenie zdarzeń i śledzenia crismon.  
  
 Po otwarciu pliku, który nie zawiera działania śledzenia Podgląd próbuje przekonwertować pliku. Należy określić nazwę i lokalizację pliku, który będzie zawierać dane śledzenia przekonwertowany. Po konwersji danych przeglądarka wyświetla zawartość nowego pliku.  
  
> [!NOTE]
>  Konwersja wymaga miejsca na dysku do przechowywania danych śledzenia przekonwertowany. Upewnij się, że masz wystarczającą ilość miejsca na dysku do przechowywania danych, przed rozpoczęciem konwersji. W przeciwnym razie niepowodzenia konwersji.  
  
### <a name="managing-projects"></a>Zarządzanie projektami  
 Przeglądarka obsługuje projektów, ułatwia przeglądanie wielu plików śledzenia. Na przykład jeśli plik śledzenia klienta i plik śledzenia usługi, można je dodać do projektu. Następnie w każdym otwarciu projektu, wszystkie pliki śledzenia w projekcie są ładowane jednocześnie.  
  
 Istnieją dwa sposoby zarządzania projektami:  
  
-   W **pliku** menu, można otworzyć, zapisać i zamknąć projektów.  
  
-   W **projektu** karcie, możesz dodać pliki do projektu.  
  
### <a name="viewing-wcf-traces"></a>Wyświetlanie śledzenia WCF  
 Usługi WCF emituje danych śledzenia przy użyciu formatu śledzenie działania. W modelu śledzenie działania indywidualnych ślady są pogrupowane w działania zgodnie z ich przeznaczenie. Przepływ sterowania logiczne są przesyłane między działaniami. Na przykład przez cały okres istnienia aplikacji, wiele "działania wysyłania komunikatu" pojawiają się i znikają. Aby uzyskać więcej informacji o wyświetlaniu zbyt śladów i działań i interfejsu użytkownika podglądu śledzenia usługi, zobacz [przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
#### <a name="switching-to-different-views"></a>Przełączanie do innych widoków  
 Przeglądarka śledzenia usługi udostępnia następujące widoki. Są wyświetlane jako karty w lewym okienku Podgląd i mogą również uzyskiwać z **widoku** menu.  
  
-   Wyświetl działania  
  
-   Widok projektu  
  
-   Widok komunikatów  
  
-   Widok wykresu  
  
##### <a name="activity-view"></a>Wyświetl działania  
 Po otwarciu plików śledzenia są widoczne ślady zgrupowane w działań i wyświetlane w **działania** widoku w okienku po lewej stronie.  
  
 **Działania** nazwy działań Wyświetla widok, liczba dane śledzenia w działaniu, czas trwania, godzina rozpoczęcia, godziny zakończenia.  
  
 Klikając jedną z wymienionych działań, ślady tego działania są wyświetlane w okienku śledzenia po prawej stronie. Następnie możesz wybrać śledzenia, aby wyświetlić jego szczegóły.  
  
 Możesz wybrać wiele działań przez naciśnięcie przycisku **Ctrl** lub **Shift** klucza i klikając odpowiednie działania. Okienko śledzenia wyświetla wszystkie ślady wybranego działania.  
  
 Możesz kliknąć dwukrotnie działanie, aby wyświetlić je w **wykres** widoku. Alternatywną metodą jest wybierz działanie, a następnie przejdź do **wykres** widoku.  
  
> [!NOTE]
>  Działanie "000000000000" jest specjalnym działaniu, które nie mogą być wyświetlane w widoku wykresu. Ponieważ wszystkie inne działania są z nim połączone, wyświetlanie to działanie ma wpływ na wydajność poważny.  
  
 Możesz kliknąć tytuł kolumny, aby posortować listę działania. Działania, które zawierają zapisy ostrzeżeń mają żółty tła i tymi, które zawierają dane śledzenia błędów ma jeden czerwony.  
  
 Istnieją różne typy działań i każdego typu odpowiada ikony po lewej stronie każdego działania. Może się odwoływać do sekcji ikony śledzenia opis ich znaczenia.  
  
##### <a name="project-view"></a>Widok projektu  
 Ten widok umożliwia zarządzanie plikami śledzenia w bieżącym projekcie. W sekcji Zarządzanie projektu więcej szczegółów.  
  
##### <a name="graph-view"></a>Widok wykresu  
 Jedną z najbardziej zaawansowanych funkcji przeglądarki danych śledzenia usługi jest **wykres** widoku, który wyświetla dane śledzenia dla danego działania w postaci wykresu. Formularz wykres umożliwia podgląd wykonywania stopniowym zdarzeń i wzajemne relacje między kilka działań, jak dane są przenoszone między nimi.  
  
 Aby przełączyć się do **wykres** wyświetlić, wybierz działanie w **działania** wyświetlić, a następnie kliknij przycisk **działania** tabulatorem ani wiadomości dziennika śledzenia w **komunikat**Widoku. Jeśli pliki śledzenia zostały załadowane, a działanie obejmuje śladów pochodzących z więcej niż jeden plik, wszystkie odpowiednie dane śledzenia są wyświetlane w widoku wykresu. Dwukrotne kliknięcie działań i ślady dziennika komunikatów również prowadzi do **wykres** widoku.  
  
 W **wykres** widoku w poszczególnych kolumnach reprezentuje działanie, a każdy blok w kolumnie — śledzenia. Działania są pogrupowane według proces (lub wątek). Małe strzałki między działaniami reprezentują transferów. Duży strzałki między procesami reprezentują wymiany wiadomości. Działania w zaznaczenie jest zawsze żółty.  
  
###### <a name="selecting-traces-in-the-graph"></a>Wybieranie ślady na wykresie  
  
1.  Kliknij przycisk blokiem na wykresie.  
  
2.  W górę i w dół kluczy, aby wybrać jej sąsiednich śladów.  
  
3.  Sprawdź informacje o śledzeniu w okienku śledzenia i okienka szczegółów.  
  
###### <a name="expanding-or-collapsing-activity-transfers"></a>Rozwijanie lub zwijanie transferów działań  
 Możesz rozszerzyć transferów działania podczas działania w zaznaczeniu się na inne działanie. Umożliwia ona wykonaj transferów.  
  
 Aby rozwinąć lub zwinąć transferów działań  
  
1.  Zlokalizuj śledzenia transfer ze znakiem "+", po lewej stronie ikony transferu.  
  
2.  Kliknij przycisk "+" lub naciśnij klawisz **Ctrl** i "+" za pomocą klawiatury.  
  
3.  Następne działanie zostanie wyświetlone na wykresie.  
  
4.  A "-" pojawia się po lewej stronie ikony transferu. Kliknij przycisk "-" podpisywania lub naciśnij klawisz Ctrl i "-", zwija transfer działania.  
  
> [!NOTE]
>  Po działanie ma wiele przesyłania do niej i rozwiń jeden przeniesień, działania, które spowodować nowe działanie działania głównego są wyświetlane. Te nowe działania są wyświetlane w postaci zwinięte. Jeśli chcesz wyświetlić szczegóły tych działań, powiększyć je w pionie, klikając ikonę rozwijania w nagłówku wykresu.  
  
###### <a name="expanding-or-collapsing-activities-vertically"></a>Rozwijanie lub zwijanie działań w pionie  
 Podgląd komunikatów o Ukrywa niepotrzebne szczegóły na wykresie działań, zwijając działań. W działaniu zwinięte nie są wyświetlane poszczególne śladów. Są wyświetlane tylko transferów śledzenia. Jeśli chcesz wyświetlić wszystkie dane śledzenia w działaniu, rozwiń węzeł działania w pionie, klikając symbol rozwiń działania w nagłówku wykresu.  
  
 Aby rozwinąć lub zwinąć działań w pionie  
  
1.  Kliknij ikonę "+" w nagłówku działania, aby rozwinąć działania w pionie.  
  
2.  Zwróć uwagę, że wszystkie dane śledzenia są wyświetlane na wykresie.  
  
3.  Kliknij przycisk "-" ikonę w nagłówku działania, aby zwinąć działania w pionie.  
  
4.  Powiadomienia czy tylko ważne w przypadku transferów komunikatów dzienników, ostrzeżenie i śledzenia wyjątków są wyświetlane w działaniu.  
  
###### <a name="options"></a>Opcje  
 Można wybrać dwie opcje z **opcja** menu w widoku wykresu.  
  
-   Pokaż działania granic ślady po usunięciu zaznaczenia Ignoruj śladów granic działania na wykresie.  
  
-   Pokaż komunikat nie pełne dane śledzenia, której po usunięciu zaznaczenia Ignoruj pełnych śladów poziomu, z wyjątkiem śledzenia wiadomości. W większości przypadków pełne dane śledzenia poziomu są mniej ważne w przypadku analizy. Ta opcja jest pomocna, jeśli nie chcesz przeanalizować pełne dane śledzenia poziomu i chcesz tylko skupić się na bardziej ważne ślady.  
  
###### <a name="layout-mode"></a>Tryb układu  
 Podgląd ma dwa tryby układu: **procesu** i **wątku**. To ustawienie określa Największa jednostka organizacji. Wartość domyślna jest w trybie układu **procesu**, co oznacza, że działania są pogrupowane według procesów na wykresie.  
  
###### <a name="execution-list"></a>Wykonanie listy  
 Można wybrać, który proces lub wątek, który będzie wyświetlany na wykresie z tej listy rozwijanej. Na przykład jeśli masz pliki śledzenia dwóch klientów (A i B) i jedną usługę otworzyć i tylko mają być wyświetlane na wykresie usługa i klient A, możesz wyłączyć klienta B z listy.  
  
#### <a name="viewing-trace-details"></a>Wyświetlanie szczegółów śledzenia  
 Aby wyświetlić szczegóły śledzenia, należy wybrać śledzenia w okienku śledzenia. Szczegóły są wyświetlane w okienku szczegółów.  
  
##### <a name="trace-pane"></a>Okienko śledzenia  
 Górnym prawym okienku podglądu śledzenia usługi to okienko śledzenia. Wyświetlane są wszystkie dane śledzenia w wybranych działania o dodatkowe informacje, na przykład poziom śledzenia, identyfikator wątku i nazwę procesu.  
  
 Nieprzetworzona XML śledzenia można skopiować do Schowka, prawym przyciskiem myszy śledzenia i wybierając **śledzenia kopiowania do Schowka**.  
  
##### <a name="detail-pane"></a>W okienku szczegółów  
 Dolne okienko po lewej stronie w przeglądarce śledzenia usługi jest w okienku szczegółów. Udostępnia trzy karty, aby wyświetlić szczegółowe informacje śledzenia.  
  
 **Sformatowany** widoku są wyświetlane informacje w sposób bardziej zorganizowany. Wyświetla listę znanych elementów XML w tabelach i drzewa, dzięki czemu łatwiej odczytywać i zrozumienie informacji.  
  
 **XML** XML odpowiadający wybranej śledzenia zostaną wyświetlone. Obsługuje ona składnię i wyróżnianie kolorów. Jeśli używasz **znaleźć** do wyszukiwania ciągów, zawiera opis wyników wyszukiwania.  
  
 **Komunikat** widok zawiera część komunikatu XML ślady dziennika komunikatów. Jest niewidoczne po wybraniu śledzenia bez wiadomości.  
  
### <a name="filtering-wcf-traces"></a>Filtrowanie danych śledzenia WCF  
 Aby ułatwić analizę śledzenia, można filtrować je w następujący sposób:  
  
-   Filtr narzędzi zapewnia dostęp do wstępnie zdefiniowanych i niestandardowych filtrów. Można ją włączyć za pomocą **widoku** menu.  
  
-   Wstępnie zdefiniowany filtr podglądu może służyć do filtrowania selektywnie części śledzenia WCF. Domyślnie jest ustawiona zezwalająca na wszystkie ślady infrastruktury do przekazywania. Ustawienia tego filtru są definiowane w **opcje filtrowania** podmenu w obszarze **widoku** menu.  
  
-   Filtry niestandardowe XPath zapewniają użytkownikom pełną kontrolę nad filtrowania. Może być zdefiniowana w **niestandardowy filtr** w obszarze **widoku** menu.  
  
 Tylko dane śledzenia, które przechodzą przez wszystkie filtry, które są wyświetlane.  
  
#### <a name="using-the-filter-toolbar"></a>Za pomocą narzędzi filtru  
 Pasek narzędzi filtru jest wyświetlany w górnej części narzędzia. Jeśli nie jest obecny, możesz to zrobić w **widoku** menu. Pasek ma trzy składniki:  
  
-   Wyszukaj: **Wyszukaj** definiuje podmiotu, który ma zostać wyszukane w operacji filtru. Na przykład, jeśli chcesz znaleźć wszystkie dane śledzenia, które zostały wyemitowane w kontekście procesu X, ustaw ten pola X i **wyszukiwania w** pole "Proces name". Wybrano tej zmiany do formantu selektora daty i godziny, gdy filtr na podstawie czasu.  
  
-   Wyszukaj w: to pole określa typ filtrów do zastosowania.  
  
-   Poziom: Ustawienie poziomu określa minimalny poziom śledzenia dozwolone przez filtr. Na przykład jeśli poziom jest ustawiona na błędy i zapasowej, są wyświetlane tylko dane śledzenia na poziomie błąd i krytyczne. Ten filtr łączy się z kryteriami wyszukiwania i wyszukaj w.  
  
 **Filtru teraz** przycisk rozpoczyna operację filtru. Niektóre filtry, szczególnie w przypadku, gdy są one stosowane do dużych zestawów danych, potrwać bardzo długo. Operacja filtru można anulować, naciskając klawisz **zatrzymać** przycisku, który jest wyświetlany w pasku stanu w obszarze **operacji** menu.  
  
 **Wyczyść** przycisk resetuje filtry wstępnie zdefiniowanych i niestandardowych zezwalająca na wszystkie ślady do przekazywania.  
  
#### <a name="filter-options"></a>Opcje filtru  
 Podgląd może automatycznie usunąć śledzenia WCF z widoku. Można selektywnie usunąć śladów emitowane przez określone obszary WCF, na przykład usunięcie transakcji powiązanego z śladów z widoku.  
  
 Ustawienia tego filtru są definiowane w **opcje filtrowania** podmenu w obszarze **widoku** menu.  
  
#### <a name="custom-filters"></a>Filtry niestandardowe  
 Jeśli znasz język XML Path Language (XPath), można użyć go do utworzenia filtrów niestandardowych do wyszukiwania danych śledzenia dla każdego elementu XML zainteresowań. Filtry są dostępne za pośrednictwem narzędzi filtru.  
  
 Filtry niestandardowe mogą zawierać parametrów. Możesz również zaimportować istniejące filtry niestandardowe.  
  
##### <a name="creating-a-custom-filter"></a>Tworzenie niestandardowego filtru  
 Filtry można utworzyć na dwa sposoby:  
  
###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Utworzenie filtru niestandardowego za pomocą Kreatora szablonów  
 Można kliknąć istniejących śledzenia i utworzyć filtr na podstawie struktury śledzenia. W tym przykładzie tworzy niestandardowy filtr na podstawie identyfikatora wątku.  
  
1.  W okienku śledzenia w prawy górny obszar podglądu wybierz śledzenia, który zawiera element, który chcesz filtrować.  
  
2.  Kliknij przycisk **utworzyć niestandardowy filtr** przycisk znajdujący się w górnej części okienka śledzenia.  
  
3.  W oknie dialogowym Wprowadź nazwę filtru. W tym przykładzie wprowadź `Thread ID`. Można też podać opis filtru.  
  
4.  Widok drzewa po lewej stronie wyświetla strukturę rekord śledzenia, który wybrano w kroku 1. Przejdź do elementu, aby utworzyć warunek. W tym przykładzie, przejdź do ThreadID się znajdować w wyrażeniu XPath: /E2ETraceEvent/System/Execution/@ThreadID węzła. Kliknij dwukrotnie atrybut Identyfikator wątku w widoku drzewa. Spowoduje to utworzenie wyrażenia dla atrybutu po prawej stronie okna dialogowego.  
  
5.  Zmiany w tym polu parametru warunek identyfikator wątku z Brak, aby "{0}". Ten krok powoduje włączenie identyfikator wątku wartość do skonfigurowania, gdy jest stosowany filtr. (Zobacz porady Zastosuj filtr sekcji) Można określić maksymalnie cztery parametry. Warunki są łączone przy użyciu operatora OR.  
  
6.  Kliknij przycisk **Ok** do tworzenia filtru.  
  
> [!NOTE]
>  Po utworzeniu filtru przy użyciu Kreatora szablonów, można jej edytować tylko ręcznie. Nie jest możliwe uruchomić Kreatora tworzenia filtru, który został utworzony wcześniej. Ponadto warunki filtr XPath w Kreatorze szablonu są łączone przy użyciu operatora OR. Jeśli potrzebujesz operacja oraz można edytować wyrażenie filtru, po jego utworzeniu.  
  
###### <a name="creating-a-custom-filter-manually"></a>Ręczne tworzenie niestandardowego filtru  
 Menu Filtry niestandardowe umożliwia ręczne wprowadzenie filtrach XPath.  
  
1.  W menu Widok, kliknij przycisk **filtry niestandardowe** elementu menu.  
  
2.  W oknie dialogowym, kliknij przycisk **nowy.**  
  
3.  Co najmniej Określ nazwę filtru i XPath wyrażenia.  
  
4.  Kliknij przycisk **OK**.  
  
###### <a name="applying-a-custom-filter"></a>Stosowanie filtru niestandardowego  
 Po utworzeniu niestandardowego filtru nie jest dostępny jednak narzędzi filtru. Wybierz filtr, który chcesz zastosować w **wyszukiwania w** pole narzędzi filtru. W poprzednim przykładzie wybierz identyfikator wątku.  
  
1.  Określ wartość, którego szukasz w **Znajdź** pola. W tym przykładzie wprowadź identyfikator wątku, który chcesz wyszukać.  
  
2.  Kliknij przycisk **filtru teraz**i obserwować wyniki operacji.  
  
 Jeśli z filtrem używa wiele parametrów, wprowadź je za pomocą ";" jako separator w **Znajdź** pola. Na przykład, następujący ciąg definiuje 3 parametry: "1; findValue tekst". Podgląd komunikatów o zastosowanie '1' {0} parametr filtru. 'findValue' i 'text' są stosowane do {1} i {2} odpowiednio.  
  
###### <a name="sharing-custom-filters"></a>Udostępnianie filtry niestandardowe  
 Filtry niestandardowe mogą udostępniać różne sesje i różnych użytkowników. Można wyeksportować do pliku definicji filtrów i zaimportować ten plik w innej lokalizacji.  
  
 Aby zaimportować niestandardowy filtr:  
  
1.  W **widoku** menu, kliknij przycisk **filtry niestandardowe**.  
  
2.  W wyświetlonym oknie dialogowym kliknij **importu** przycisku.  
  
3.  Przejdź do pliku filtru niestandardowego (.stvcf), kliknij plik, a następnie kliknij przycisk **Otwórz** przycisku.  
  
 Aby wyeksportować niestandardowy filtr:  
  
1.  W menu Widok, kliknij przycisk **filtry niestandardowe**.  
  
2.  W otwartym oknie dialogowym Wybierz filtr, który ma zostać wykonane eksportowanie.  
  
3.  Kliknij przycisk **wyeksportować** przycisku.  
  
4.  Określ nazwę i lokalizację pliku definicji filtru niestandardowego (.stvcf), a następnie kliknij przycisk **zapisać** przycisku.  
  
> [!NOTE]
>  Te filtry niestandardowe można tylko zaimportowane i wyeksportowane z przeglądarki danych śledzenia usługi. Nie można ich odczytać za pomocą innych narzędzi.  
  
### <a name="finding-data"></a>Wyszukiwanie danych  
 Podgląd komunikatów o oferuje następujące sposoby wyszukiwania danych:  
  
-   Na pasku narzędzi Znajdź zapewnia szybki dostęp do najbardziej typowe opcje wyszukiwania.  
  
-   Okno dialogowe znajdowania zawiera więcej dostępne opcje. Nie jest dostępny za pośrednictwem **Edytuj** menu lub przez krótki klawisze Ctrl + F.  
  
 Pasek narzędzi Znajdź pojawia się u góry okna podglądu. Jeśli nie jest obecny, możesz to zrobić w **widoku** menu. Pasek zawiera dwa składniki:  
  
-   Znajdź: Pozwala na wprowadzenie słowa kluczowe do wyszukania.  
  
-   Szukaj w: Pozwala na wprowadzenie zakres wyszukiwania. Można wybrać, czy do wyszukania wszystkich działań lub bieżącego działania.  
  
 Okno dialogowe znajdowania zawiera dwie dodatkowe opcje:  
  
-   Znajdź element docelowy:  
  
    -   Opcji "danych pierwotnych dziennika" przeszukuje wszystkie nieprzetworzone dane słowo kluczowe.  
  
    -   Opcji "Tekstu XML" i "Atrybutu XML" Wyszukiwanie tylko w elementach XML.  
  
    -   Opcja "Rejestrowany komunikat" przeszukuje kluczowego tylko w wiadomości.  
  
-   Ignoruj działania głównego: wyszukiwanie ignoruje dane śledzenia w działaniu "000000000000". Poprawia to wydajność w śledzenia dużych plików, gdy działanie główne ma tysiące ślady, z których większość są transferów.  
  
### <a name="navigating-traces"></a>Nawigowanie po danych śledzenia  
 Ponieważ dane śledzenia są zapisywane krok po kroku w czasie wykonywania aplikacji, nawigacja śladów może pomóc debugowania aplikacji. Przeglądarka śledzenia usługi udostępnia różne sposoby nawigowanie w danych śledzenia.  
  
#### <a name="step-forward-or-backward"></a>Krok do przodu i do tyłu  
 Jeśli należy wziąć pod uwagę każdego śledzenia jako wiersz kodu w programie, wykonywanie krok po kroku do przodu jest bardzo podobny do "Przekrocz nad" w programie Visual Studio programowanie środowiska IDE (Integrated). Różnica polega na tym, że można również przejść do tyłu w dane śledzenia. Wykonywanie krok po kroku do przodu oznacza przechodzenia do następnego śledzenia w działaniu.  
  
-   Krok do przodu: Używanie **działania** menu lub naciśnij przycisk "F10". Umożliwia także strzałka "w dół" w okienku śledzenia.  
  
-   Kroku Backward: Użyj **działania** menu lub naciśnij przycisk "F9". Umożliwia także strzałka "w górę" w okienku śledzenia.  
  
> [!NOTE]
>  Może to zająć należy do działania wykonywane w ramach innego procesu lub na innym komputerze, ponieważ wiadomości WCF może przenosić identyfikatorów, które obejmują maszyny działania.  
  
#### <a name="follow-transfer"></a>Wykonaj transferu  
 Transfer danych śledzenia są specjalne dane śledzenia w pliku śledzenia. Działanie może przenieść do innego działania śledzenia transferu. Na przykład "Działania A", mogą przesyłać do "Działania B". W takim przypadku Brak śledzenia transfer w ikonie "Działania A" o nazwie "Działania:" i transferu. Ślad transfer jest powiązanie tych dwóch zapisów śledzenia. W "Działania B" może być również śledzenia transferu na koniec działania powrotem do "Działania A". Jest to podobne do wywołania funkcji w programach: A wywołuje B, a następnie zwraca B.  
  
 "Wykonaj transfer" jest podobna do "Wkrocz do" w debugerze. Wynika transfer z zakresu od A do b Nie ma wpływu na inne dane śledzenia.  
  
 Istnieją dwa sposoby przeniesienia wykonaj: myszy lub klawiatury:  
  
-   Przy myszy: Kliknij dwukrotnie śledzenia transfer w okienku śledzenia.  
  
-   Klawiatury: Wybierz śledzenia transfer i użyj "Wykonaj Transfer" w **działania** menu lub naciśnij przycisk "F11"  
  
> [!NOTE]
>  W wielu przypadkach podczas działania A na B działania działania A czeka, aż działania B przesyła do działania A. Oznacza to, że działania A ma śladów rejestrowane w okresie podczas działania B aktywnie jest śledzenie. Jednak istnieje również możliwość, że działanie, A nie oczekuje i ślady dziennika w dalszym ciągu. Możliwe jest również B działania nie są przekazywane do działania A. W związku z tym transferów działań nadal różnią się od wywołania funkcji, w tym sensie. Można zrozumieć działanie transferów w widoku wykresu.  
  
#### <a name="jump-to-next-or-previous-transfer"></a>Przejście do następnej lub poprzedniej transferu  
 Podczas konfigurowania bieżące działanie lub wybranych działań po wybraniu wielu działań, możesz szybko znaleźć działań, które przekazuje do. "Skok do transferu obok" umożliwia Znajdź następny śledzenia transfer w działaniu. Po znalezieniu śledzenia transfer umożliwia "Wykonaj transfer" Wkrocz do następnego działania.  
  
-   Przejście do następnego transferu: Użyj **działania** menu lub naciśnij przycisk "Ctrl + F10".  
  
-   Przejście do poprzedniego Transfer: Użyj **działania** menu lub naciśnij przycisk "Kombinację klawiszy Ctrl + F9".  
  
#### <a name="navigate-in-graph-view"></a>Przejdź w widoku wykresu  
 Mimo że nawigowanie po okienka działania i śledzenia jest podobny do debugowania, za pomocą **wykres** widok zawiera wiele lepsze środowisko w nawigacji. Zobacz sekcję "Widok wykresu", aby uzyskać więcej informacji.  
  
### <a name="loading-large-trace-files"></a>Ładowanie plików dużych śledzenia  
 Pliki śledzenia mogą być bardzo duże. Na przykład jeśli włączysz śledzenie na poziomie "Pełne" utworzonego pliku śledzenia dla uruchomione kilka minut można łatwo można setki megabajtów lub jeszcze większym, w zależności od szybkości i komunikacji wzorca sieci.  
  
 Po otwarciu pliku śledzenia bardzo dużych podglądu śledzenia usługi wydajność systemu może być negatywnego wpływu na. Szybkość ładowania i czas odpowiedzi po załadowaniu może działać powoli. Rzeczywista szybkość różni się od czasu do czasu, w zależności od konfiguracji sprzętowej. W większości komputerów podczas ładowania pliku śledzenia, które jest większe niż 200M ma negatywny wpływ na wydajność poważny. Ślady plików większych niż 1 GB/S narzędzie może użyć wszystkich dostępną pamięć, lub przestać odpowiadać bardzo długi czas.  
  
 Aby uniknąć powolne ładowanie i czas odpowiedzi w analizowanie śledzenia dużych plików, przeglądarki śledzenia usługi zawiera funkcję "Częściowe ładowania", który jest ładowany przez tylko niewielką częścią śledzenia w czasie. Na przykład może mieć plik śledzenia ponad 1GB, uruchomione przez kilka dni na serwerze. Jeśli wystąpiły błędy i do przeanalizowania śledzenia, nie jest potrzebne do otwierania pliku śledzenia całego. Zamiast tego można ładować dane śledzenia w przedziale czasu, gdy mógł wystąpić błąd. Ponieważ zakres jest mniejszy, narzędzia podglądu śledzenia usługi można załadować pliku szybciej i można zidentyfikować błędy przy użyciu mniejszy zestaw danych.  
  
#### <a name="enabling-partial-loading"></a>Włączenie ładowania częściowe  
 Nie musisz ręcznie włączyć ładowanie częściowej. Jeśli całkowity rozmiar plików śledzenia, które próba załadowania przekroczy 40 MB, przeglądarki danych śledzenia usługi automatycznie wyświetla okna dialogowego ładowanie częściowe do wyboru element, który chcesz załadować.  
  
> [!NOTE]
>  Ponieważ dane śledzenia nie mogą być dystrybuowane równomiernie w czasie zakresu, długość okresu, który określić częściowego ładowania paska narzędzi nie może być proporcjonalny do rozmiaru ładowania pokazano. Rozmiar rzeczywisty ładowania może być mniejszy niż rozmiar szacowany w oknie dialogowym z częściowa ładowania.  
  
#### <a name="adjusting-partial-loading"></a>Ładowanie częściowe dopasowanie  
 Po załadowaniu częściowo pliku śledzenia, możesz zmienić ładowany zestaw danych. Można to zrobić, dostosowując narzędzi ładowania częściowe u góry okna podglądu.  
  
1.  Przenieś pasek narzędzi za pomocą myszy lub wprowadzić godzinę rozpoczęcia i zakończenia.  
  
2.  Kliknij przycisk **Dostosuj** przycisku.  
  
## <a name="understanding-trace-icons"></a>Opis śledzenia ikon  
 Poniżej przedstawiono listę ikony, które używa narzędzia podglądu śledzenia usługi **działania** widoku **wykres** widoku i **śledzenia** okienko, aby reprezentować różne elementy.  
  
> [!NOTE]
>  Niektóre dane śledzenia, które nie są podzielone (na przykład, "wiadomość jest zamknięte") nie ikona.  
  
### <a name="activity-tracing-traces"></a>Działania śledzenia śledzenia  
  
|Ikona|Opis|  
|----------|-----------------|  
|![Ostrzeżenie śledzenia](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Ostrzeżenie śledzenia: emitowanego na poziomie ostrzeżenia śledzenia|  
|![Błąd podczas śledzenia](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Błąd podczas śledzenia: emitowanego na poziomie Błąd śledzenia.|  
|![Śledzenie działań Start:](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Śledzenie działań Start: śledzenia, która oznacza początek działania. Zawiera nazwę działania. Jako projektanta aplikacji lub deweloperem należy zdefiniować jedno działanie Rozpocznij śledzenie na identyfikator działania na proces lub wątek.<br /><br /> Jeśli identyfikator działania są propagowane w źródła śledzenia dla korelacji śledzenia, zostanie wyświetlony wielu uruchamia dla tego samego identyfikatora aktywności (po jednym dla każdego źródła śledzenia). Rozpocznij śledzenie jest emitowany, jeśli ActivityTracing jest włączony dla źródła śledzenia.|  
|![Działanie Zatrzymaj śledzenie](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Działanie Zatrzymaj śledzenie: śledzenia, która oznacza koniec działania. . Zawiera nazwę działania. Jako projektanta aplikacji lub deweloperem należy zdefiniować jedno działanie Zatrzymaj śledzenie na identyfikator działania na źródła śledzenia. Ślady z danego źródła są wyświetlane po działaniu Stop emitowane przez to źródło śledzenia, z wyjątkiem Jeśli różnica czasu śledzenia nie jest wystarczająco mała. W takim przypadku dwa śladów z tym samym czasie, w tym Stop, może przeplotu podczas wyświetlania. Jeśli identyfikator działania są propagowane w źródła śledzenia dla korelacji śledzenia, zobaczysz wielu zatrzyma się na tym samym identyfikatorze aktywności (po jednym dla każdego źródła śledzenia). Zatrzymaj śledzenie jest emitowany, jeśli ActivityTracing jest włączony dla źródła śledzenia.|  
|![Działanie Suspend śledzenia](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Działanie Suspend śledzenia: ślad oznacza czas działania jest wstrzymana. Ślady są emitowane w działaniu zawieszone, dopóki nie wznawia działania. Zawieszone działanie oznacza, że żadne przetwarzanie się nie dzieje tego działania w zakresie źródła śledzenia. Wstrzymanie/wznowienie dane śledzenia są przydatne do profilowania. Wstrzymaj śledzenia jest emitowany Jeśli ActivityTracing jest włączony dla źródła śledzenia.|  
|![Działanie wznowienia śledzenia](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4e0a-9988-cdc2f7030f17")|Działanie wznowienia śledzenia: ślad oznacza czas działania zostanie wznowione po jego została wstrzymana. Śladów może wyemitować ponownie w danego działania. Wstrzymanie/wznowienie dane śledzenia są przydatne do profilowania. Wznów śledzenia jest emitowany Jeśli ActivityTracing jest włączony dla źródła śledzenia.|  
|![Transfer](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Transfer: Śledzenia emitowanego podczas przepływu sterowania logicznej jest przenoszona z jednego działania do drugiego. Działanie, które transferu pochodzi z może kontynuować wykonywania równoległe działanie, gdy transfer przejdzie do pracy. Śledzenie Transfer jest emitowany Jeśli ActivityTracing jest włączony dla źródła śledzenia.|  
|![Transfer From](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Przesyłanie z: Śledzenia definiujący transfer z innego działania do bieżącego działania.|  
|![Transfer To](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Przesyłanie danych do: Śledzenia definiujący przeniesienia przepływu sterowania logicznych z bieżącego działania do innego działania.|  
  
### <a name="wcf-traces"></a>Dane śledzenia WCF  
  
|Ikona|Opis|  
|----------|-----------------|  
|![Komunikat dziennika śledzenia](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Komunikat dziennika śledzenia: emitowanego podczas rejestrowania wiadomości WCF przez funkcję rejestrowanie komunikatów śledzenia podczas `System.ServiceModel.MessageLogging` źródła śledzenia jest włączona. Kliknięcie tego śledzenia powoduje wyświetlenie komunikatu. Istnieją cztery punkty można skonfigurować rejestrowanie wiadomości: ServiceLevelSendRequest, TransportSend TransportReceive i ServiceLevelReceiveRequest, który można również określić przez `messageSource` atrybutu w wiadomości dziennika śledzenia.|  
|![Komunikat śledzenia odebrane](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Komunikat śledzenia odebrane: śledzenia emitowanego po odebraniu wiadomości WCF, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie informacji lub pełne. Ślad jest niezbędne do wyświetlania strzałkę korelacji wiadomości w działaniu **wykres** widoku.|  
|![Komunikat śledzenia wysłane](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Komunikat śledzenia wysłane: śledzenia emitowanego po wysłaniu wiadomości WCF, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie informacji lub pełne. Ślad jest niezbędne do wyświetlania strzałkę korelacji wiadomości w działaniu **wykres** widoku.|  
  
### <a name="activities"></a>Kategoria Activities  
  
|Ikona|Opis|  
|----------|-----------------|  
|![Działanie](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Działanie: Wskazuje, że bieżące działanie jest ogólne działanie.|  
|![Działanie główne](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Działania głównego: wskazuje działania głównego procesu.|  
  
### <a name="wcf-activities"></a>Działania programu WCF  
  
|Ikona|Opis|  
|----------|-----------------|  
|![Działanie środowiska](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Działanie środowiska: działanie, które umożliwia tworzenie, powoduje otwarcie lub zamknięcie klienta lub hosta usługi WCF. Błędy, które wystąpiło podczas fazy te będą wyświetlane w tego działania.|  
|![Nasłuchiwanie działania](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Nasłuchiwanie działania: działanie, które dzienniki śledzenia związane z odbiornik. Wewnątrz tego działania możemy wyświetlić żądania odbiornika informacji i połączenia.|  
|![Odbieranie bajtów działania](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Działanie bajtów odbierania: działania, który grupuje wszystkie ślady dotyczące odbierania bajtów przychodzących na połączenie między dwoma punktami końcowymi. To działanie ma zasadnicze znaczenie korelacji z działaniami transportu, propagujące ich identyfikator działania, takie jak sterownik http.sys. Błędy połączenia, takie jak przerwań pojawi się tego działania.|  
|![Przetwarzanie komunikatów działania](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Przetwarzanie działania komunikatu: działania, który grupuje dane śledzenia dotyczących tworzenia wiadomości WCF. Błędy z powodu nieprawidłowych koperty lub źle sformułowane wiadomości będą wyświetlane w tym działania. Wewnątrz tego działania możemy sprawdzić nagłówki komunikatów, aby sprawdzić, czy identyfikator działania pochodzi z obiektu wywołującego. Jeśli to PRAWDA, gdy przekazywane do procesu akcji działania (dalej), firma Microsoft można także przypisać dla danego działania propagowany działania identyfikator korelacji między wywołującego i ślady wywołującej.|  
|![Komunikat dziennika śledzenia](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Przetwarzanie działanie Action: działania, który grupuje wszystkie ślady dotyczące żądania WCF między dwoma punktami końcowymi. Jeśli `propagateActivity` ma ustawioną wartość `true` dla obu punktów końcowych w konfiguracji wszystkie ślady z oba punkty końcowe są scalane w jedno działanie dla bezpośredniego korelacji. Takie działanie będzie zawierać błędy z powodu transportu lub zabezpieczeń przetwarzania, rozszerzanie do granicy kod użytkownika i (jeśli istnieje odpowiedzi).|  
|![Przetwarzanie komunikatów działania](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Wykonanie działania kodu użytkownika: śledzi działania, który grupuje kod użytkownika do przetworzenia żądania.|  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Jeśli nie masz uprawnień do zapisu w rejestrze, otrzymasz następujący komunikat o błędzie "Microsoft Service podglądu śledzenia nie został zarejestrowany w systemie" Kiedy używać "`svctraceviewer /register`" polecenie, aby zarejestrować narzędzia. W takim przypadku należy Zaloguj się za pomocą konta, które ma dostęp do zapisu do rejestru.  
  
 Ponadto narzędzia podglądu śledzenia usługi zapisuje niektórych ustawień (na przykład filtry niestandardowe i opcje filtrowania) do pliku SvcTraceViewer.exe.settings w folderze jej zestawu. Jeśli nie masz uprawnienia do odczytu pliku, nadal można uruchomić narzędzie, ale nie można załadować ustawień.  
  
 Jeśli zostanie wyświetlony komunikat o błędzie "Wystąpił nieznany błąd podczas przetwarzania śladów co najmniej jeden" podczas otwierania pliku etl, oznacza to, że format pliku etl jest nieprawidłowy.  
  
 Jeśli możesz otworzyć dziennika śledzenia utworzone za pomocą Arabic systemu operacyjnego, można zauważyć, że czas filtru nie działa. Na przykład roku 2005 odpowiada roku 1427 Arabic kalendarza. Jednak zakres czasu obsługiwane przez filtr narzędzia podglądu śledzenia usługi nie obsługuje starszych niż 1752 daty. Może to oznaczać, że nie jesteś w stanie wybierz poprawną datę w filtrze. Aby rozwiązać ten problem, należy utworzyć niestandardowego filtru (**widoku/niestandardowe filtry**) za pomocą wyrażenia XPath do uwzględnienia w określonym zakresie czasu.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Konfigurowanie śledzenia](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Propagacja dla korelacji śledzenia End-To-End i śledzenie działań](http://msdn.microsoft.com/library/2c11a905-64f8-47b5-bae5-a74fc666137e)
