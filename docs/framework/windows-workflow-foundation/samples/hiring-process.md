---
title: Proces zatrudniania
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: 16975aaa56c8fde09fa6f57781f13280c147e73e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038158"
---
# <a name="hiring-process"></a>Proces zatrudniania
Ten przykład pokazuje, jak zaimplementować proces biznesowy przy użyciu działań związanych z obsługą komunikatów i dwóch przepływów pracy hostowanych jako usługi przepływu pracy. Te przepływy pracy są częścią infrastruktury IT fikcyjnej firmy o nazwie contoso, Inc.  
  
 Proces przepływu pracy (zaimplementowany <xref:System.Activities.Statements.Flowchart>jako) prosi o autoryzację od kilku menedżerów w organizacji. `HiringRequest` Aby osiągnąć ten cel, przepływ pracy używa innych istniejących usług w organizacji (w naszym przypadku usługa Skrzynka odbiorcza i usługa danych organizacji zaimplementowana jako usługi w postaci zwykłego Windows Communication Foundation (WCF)).  
  
 Przepływ pracy (zaimplementowany <xref:System.Activities.Statements.Sequence>jako) publikuje w witrynie sieci Web opiekę zewnętrzną firmy Contoso i zarządza nabyciem życiorysów. `ResumeRequest` Okresowe Księgowanie zadania jest dostępne w zewnętrznej witrynie sieci Web przez ustalony czas (do czasu wygaśnięcia limitu czasu) lub do momentu, gdy pracownik od firmy Contoso zdecyduje się go usunąć.  
  
 Ten przykład ilustruje następujące funkcje programu [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
- <xref:System.Activities.Statements.Flowchart>i <xref:System.Activities.Statements.Sequence> przepływy pracy do modelowania procesów biznesowych.  
  
- Usługi przepływu pracy.  
  
- Działania dotyczące komunikatów.  
  
- Korelacja oparta na zawartości.  
  
- Działania niestandardowe (deklaracyjne i oparte na kodzie).  
  
- Trwałość serwera SQL dostarczona przez system.  
  
- Niestandardowe <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
- Śledzenie niestandardowe.  
  
- Śledzenie zdarzeń systemu Windows (ETW) śledzenie.  
  
- Kompozycja działań.  
  
- <xref:System.Activities.Statements.Parallel>demonstracj.  
  
- <xref:System.Activities.Statements.CancellationScope>interakcyjn.  
  
- Trwałe czasomierze<xref:System.Activities.Statements.Delay> (Activity).  
  
- Akcja.  
  
- Więcej niż jeden przepływ pracy w tym samym rozwiązaniu.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Opis procesu  
 Firma Contoso, Inc. chce mieć ścisłą kontrolę nad liczbami pracowników w poszczególnych działach. W związku z tym kiedykolwiek każdy pracownik chce rozpocząć nowy proces zatrudniania, musi przejść przez zatwierdzenie procesu zatrudniania, zanim nastąpi faktyczne przeprowadzenie rekrutacji. Ten proces jest nazywany żądaniem procesu zatrudniania (zdefiniowanym w projekcie HiringRequestService) i składa się z następujących kroków:  
  
1. Pracownik (osoba żądająca) uruchamia żądanie procesu zatrudniania.  
  
2. Menedżer osoby żądającej musi zatwierdzić żądanie:  
  
    1. Menedżer może odrzucić żądanie.  
  
    2. Menedżer może zwrócić żądanie do żądającego, aby uzyskać dodatkowe informacje:  
  
        1. Obiekt żądający przegląda i wysyła żądanie z powrotem do Menedżera.  
  
    3. Menedżer może zatwierdzić.  
  
3. Po zatwierdzeniu Menedżera żądającego właściciel działu musi zatwierdzić żądanie:  
  
    1. Właściciel działu może odrzucić.  
  
    2. Właściciel działu może zatwierdzić.  
  
4. Po zatwierdzeniu przez właściciela działu proces wymaga zatwierdzenia 2 menedżerów kadr lub dyrektora naczelnego:  
  
    1. Proces może przejść do stanu zaakceptowane lub odrzucone.  
  
    2. Jeśli proces zostanie zaakceptowany, zostanie uruchomione nowe wystąpienie `ResumeRequest` przepływu pracy (`ResumeRequest` jest ono połączone z HiringRequest. csproj przez odwołanie do usługi).  
  
 Gdy menedżerowie zatwierdzą zatrudnienie nowego pracownika, HR musi znaleźć odpowiedniego kandydata. Ten proces jest wykonywany przez drugi przepływ pracy (`ResumeRequest`zdefiniowany w ResumeRequestService. csproj). Ten przepływ pracy definiuje proces przesyłania zadań związanych z pracą w trybie kariery do zewnętrznej witryny sieci Web Opieky firmy Contoso, odbiera wznowień od kandydatów i monitoruje stan księgowania zadania. Stanowiska są dostępne przez ustalony okres (do czasu wygaśnięcia) lub do momentu, gdy pracownik od firmy Contoso zdecyduje się go usunąć. `ResumeRequest` Przepływ pracy składa się z następujących kroków:  
  
1. Pracownik z typów Contoso w informacjach o pozycji i przekroczeniu limitu czasu. Gdy pracownik wpisze te informacje, pozycja jest ogłaszana w witrynie kariery w sieci Web.  
  
2. Po opublikowaniu informacji zainteresowane strony mogą przesłać życiorysy. Po przesłaniu wznowienie jest przechowywane w rekordzie połączonym z otwieranym zadaniem.  
  
3. Wnioskodawcy mogą przesyłać wznowienia do momentu wygaśnięcia limitu czasu lub ktoś z działu kadr firmy Contoso nie będzie jawnie decydował o usunięciu księgowania, zatrzymując proces.  
  
## <a name="projects-in-the-sample"></a>Projekty w przykładzie  
 W poniższej tabeli przedstawiono projekty w przykładowym rozwiązaniu.  
  
|Projekt|Opis|  
|-------------|-----------------|  
|ContosoHR|Zawiera Kontrakty danych, obiekty biznesowe i klasy repozytorium.|  
|HiringRequestService|Zawiera definicję przepływu pracy procesu zatrudniania zlecenia.<br /><br /> Ten projekt jest implementowany jako Aplikacja konsolowa, która automatycznie udostępnia przepływ pracy (plik XAML) jako usługę.|  
|ResumeRequestService|Usługa przepływu pracy, która zbiera dane z kandydatów do momentu wygaśnięcia limitu czasu lub ktoś zdecyduje, że proces musi zostać zatrzymany.<br /><br /> Ten projekt jest zaimplementowany jako usługa deklaracyjnego przepływu pracy (xamlx).|  
|OrgService|Usługa, która ujawnia informacje organizacji (pracownicy, stanowiska, PositionTypes i działy). Tę usługę można traktować jako moduł organizacji firmowej planu zasobów przedsiębiorstwa (ERP).<br /><br /> Ten projekt jest implementowany jako Aplikacja konsolowa, która uwidacznia usługę Windows Communication Foundation (WCF).|  
|InboxService|Skrzynka odbiorcza, która zawiera zadania funkcjonalne dla pracowników.<br /><br /> Ten projekt jest implementowany jako Aplikacja konsolowa, która uwidacznia usługę WCF.|  
|InternalClient|Aplikacja sieci Web do współpracy z procesem. Użytkownicy mogą uruchamiać, uczestniczyć i przeglądać przepływy pracy HiringProcess. Korzystając z tej aplikacji, można również uruchamiać i monitorować procesy ResumeRequest.<br /><br /> Ta witryna jest zaimplementowana jako wewnętrzna z intranetem firmy Contoso. Ten projekt jest zaimplementowany jako witryna sieci Web ASP.NET.|  
|CareersWebSite|Zewnętrzna witryna sieci Web, która udostępnia otwarte stanowiska w firmie Contoso. Każdy potencjalny kandydat może przejść do tej witryny i przesłać wznowienie.|  
  
## <a name="feature-summary"></a>Podsumowanie funkcji  
 W poniższej tabeli opisano, w jaki sposób każda funkcja jest używana w tym przykładzie.  
  
|Funkcja|Opis|Projekt|  
|-------------|-----------------|-------------|  
|Schemat blokowy|Proces biznesowy jest reprezentowany jako schemat blokowy. Ten opis schematu blokowego reprezentuje proces w taki sam sposób, w jaki firma zostałaby narysowana w tablicy.|HiringRequestService|  
|Usługi przepływu pracy|Schemat blokowy z definicją procesu jest hostowany w usłudze (w tym przykładzie usługa jest hostowana w aplikacji konsoli).|HiringRequestService|  
|Działania dotyczące komunikatów|Schemat blokowy używa działań obsługi komunikatów na dwa sposoby:<br /><br /> — Aby uzyskać informacje od użytkownika (aby otrzymywać decyzje i powiązane informacje w każdym kroku zatwierdzenia).<br />— Aby współdziałać z innymi istniejącymi usługami (InboxService i OrgDataService, używanymi przez odwołania do usługi).|HiringRequestService|  
|Korelacja na podstawie zawartości|Komunikaty o zatwierdzaniu są skorelowane z właściwością ID żądania zatrudniania:<br /><br /> — Po rozpoczęciu procesu dojście korelacji jest inicjowane z IDENTYFIKATORem żądania.<br />-Przychodzące komunikaty zatwierdzenia są skorelowane względem ich identyfikatora (pierwszy parametr każdego komunikatu zatwierdzenia jest IDENTYFIKATORem żądania).|HiringRequestService / ResumeRequestService|  
|Działania niestandardowe (na podstawie deklaracyjne i kodu)|W tym przykładzie istnieje kilka działań niestandardowych:<br /><br /> -   `SaveActionTracking`: To działanie emituje niestandardowe <xref:System.Activities.Tracking.TrackingRecord> (przy użyciu <xref:System.Activities.NativeActivityContext.Track%2A>). To działanie zostało utworzone przy użyciu bezwzględnego rozszerzania <xref:System.Activities.NativeActivity>kodu.<br />-   `GetEmployeesByPositionTypes`: To działanie odbiera listę identyfikatorów typu pozycji i zwraca listę osób, które mają tę pozycję w firmie Contoso. To działanie zostało utworzone deklaratywnie (przy użyciu projektanta działań).<br />-   `SaveHiringRequestInfo`: To działanie zapisuje informacje `HiringRequest` o (przy użyciu `HiringRequestRepository.Save`). To działanie zostało utworzone przy użyciu bezwzględnego rozszerzania <xref:System.Activities.CodeActivity>kodu.|HiringRequestService|  
|Trwałość SQL Server dostarczana przez system|<xref:System.ServiceModel.Activities.WorkflowServiceHost> Wystąpienie, które obsługuje definicję procesu Flowchart, jest skonfigurowane tak, aby korzystało z trwałości SQL Server dostarczonej przez system.|HiringRequestService / ResumeRequestService|  
|Niestandardowe śledzenie|Przykład obejmuje niestandardowego uczestnika śledzenia, który zapisuje historię `HiringRequestProcess` (czyli to rejestruje czynność, przez kogo zostało wykonane). Kod źródłowy znajduje się w folderze śledzenia elementu HiringRequestService.|HiringRequestService|  
|Śledzenie ETW|Śledzenie ETW dostarczone przez system jest konfigurowane w pliku App. config w usłudze HiringRequestService.|HiringRequestService|  
|Składanie działań|W definicji procesu jest stosowana bezpłatna kompozycja <xref:System.Activities.Activity>programu. Schemat blokowy zawiera kilka równoległych działań, które w tym samym czasie zawierają inne działania (itd.).|HiringRequestService|  
|Działania równoległe|-   <xref:System.Activities.Statements.ParallelForEach%601>służy do rejestrowania w skrzynce odbiorczej kierowników dyrektorów naczelnych i KADRy (w oczekiwaniu na krok zatwierdzenia dwóch menedżerów kadr).<br />-   <xref:System.Activities.Statements.Parallel>służy do wykonywania niektórych zadań oczyszczania w zakończonych i odrzuconych krokach|HiringRequestService|  
|Anulowanie modelu|Schemat blokowy <xref:System.Activities.Statements.CancellationScope> używa do tworzenia zachowań anulowania (w tym przypadku jest to oczyszczane).|HiringRequestService|  
|Uczestnik trwałości klienta|`HiringRequestPersistenceParticipant`zapisuje dane ze zmiennej przepływu pracy w tabeli przechowywanej w bazie danych contoso HR.|HiringRequestService|  
|Usługi przepływu pracy|`ResumeRequestService`jest zaimplementowany przy użyciu usług Workflow Services. Definicja przepływu pracy i informacje o usłudze są zawarte w ResumeRequestService. xamlx. Usługa jest skonfigurowana do korzystania z trwałości i śledzenia.|ResumeRequestService|  
|Trwałe czasomierze|`ResumeRequestService`używa trwałych czasomierzy do zdefiniowania czasu trwania księgowania zadania (po upływie limitu czasu, gdy zadanie zostanie zamknięte).|ResumeRequestService|  
|Transakcje|<xref:System.Activities.Statements.TransactionScope>służy do zapewnienia spójności danych w ramach wykonywania kilku działań (po odebraniu nowej życiorysu).|ResumeRequestService|  
|Transakcje|Niestandardowy uczestnik trwałości (`HiringRequestPersistenceParticipant`) i uczestnik śledzenia niestandardowego (`HistoryFileTrackingParticipant`) używają tej samej transakcji.|HiringRequestService|  
|Używanie [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w aplikacjach ASP.NET.|Przepływy pracy są dostępne z poziomu dwóch aplikacji ASP.NET.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Magazyn danych  
 Dane są przechowywane w SQL Server Database o nazwie `ContosoHR` (skrypt służący do tworzenia tej bazy danych znajduje się `DbSetup` w folderze). Wystąpienia przepływu pracy są przechowywane w bazie danych SQL Server `InstanceStore` o nazwie (skrypty do tworzenia magazynu wystąpień są częścią [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] dystrybucji).  
  
 Obie bazy danych są tworzone przez uruchomienie skryptu Setup. cmd z wiersz polecenia dla deweloperów dla programu Visual Studio.  
  
## <a name="running-the-sample"></a>Uruchamianie przykładu  
  
#### <a name="to-create-the-databases"></a>Aby utworzyć bazy danych  
  
1. Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio.  
  
2. Przejdź do przykładowego folderu.  
  
3. Uruchom program Setup. cmd.  
  
4. Sprawdź, czy dwie bazy `ContosoHR` danych `InstanceStore` i zostały utworzone w programie SQL Express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Aby skonfigurować rozwiązanie do wykonania  
  
1. Uruchom program Visual Studio jako administrator. Otwórz HiringRequest. sln.  
  
2. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.  
  
3. Wybierz opcję **wiele projektów startowych** i ustaw **CareersWebSite**, **InternalClient**, **HiringRequestService**i **ResumeRequestService** do **uruchomienia**. Pozostaw wartości **ContosoHR**, **InboxService**i **OrgService** jako none.  
  
4. Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B. Sprawdź, czy kompilacja zakończyła się pomyślnie.  
  
#### <a name="to-run-the-solution"></a>Aby uruchomić rozwiązanie  
  
1. Po skompilowaniu rozwiązania naciśnij kombinację klawiszy CTRL + F5, aby uruchomić bez debugowania. Sprawdź, czy wszystkie usługi zostały uruchomione.  
  
2. Kliknij prawym przyciskiem myszy pozycję **InternalClient** w rozwiązaniu, a następnie wybierz pozycję **Wyświetl w przeglądarce**. Zostanie wyświetlona `InternalClient` strona domyślna dla. Upewnij się, że usługi są uruchomione, a następnie kliknij link.  
  
3. Zostanie wyświetlony moduł **HiringRequest** . W tym miejscu możesz wykonać opisany tutaj scenariusz.  
  
4. Po zakończeniu można `ResumeRequest`uruchomić polecenie. `HiringRequest` W tym miejscu możesz wykonać opisany tutaj scenariusz.  
  
5. `ResumeRequest` Po opublikowaniu jest on dostępny w publicznej witrynie sieci Web (w witrynie sieci Web opieka firmy Contoso). Aby zobaczyć Księgowanie zadania (i zastosować je do pozycji), przejdź do witryny sieci Web usługi Kariers.  
  
6. Kliknij prawym przyciskiem myszy pozycję **CareersWebSite** w rozwiązaniu, a następnie wybierz pozycję **Widok w przeglądarce**.  
  
7. Przejdź z powrotem do `InternalClient` strony, klikając prawym przyciskiem myszy pozycję **InternalClient** w rozwiązaniu, a następnie wybierając pozycję **Widok w przeglądarce**.  
  
8. Przejdź do sekcji **jobpostings** , klikając link **zapisy dotyczące zadań** w górnym menu skrzynki odbiorczej. W tym miejscu możesz wykonać opisany tutaj scenariusz.  
  
## <a name="scenarios"></a>Scenariusze  
  
### <a name="hiring-request"></a>Zlecenie zatrudniania  
  
1. Michael Alexander (inżynier oprogramowania) chce zażądać nowej pozycji do zatrudniania inżyniera oprogramowania w teście (SDET) w dziale inżynierów, którzy mają co najmniej 3 lata doświadczenia C#w.  
  
2. Po utworzeniu żądanie pojawia się w skrzynce odbiorczej firmy Michael (kliknij przycisk **Odśwież** , jeśli żądanie nie zostanie wyświetlone) oczekujące na zatwierdzenie przez Menedżera firmy Piotr Brehm.  
  
3. Piotr chce działać na żądanie Jan. Uważa, że pozycja wymaga 5 lat C# doświadczenia, a nie 3, dlatego wysyła swoje komentarze z powrotem do przeglądu.  
  
4. Michael widzi komunikat w swojej skrzynce odbiorczej przez jego Menedżera i chce działać. Michael widzi historię żądania umieszczenia i zgadza się z Peterowi. Michael modyfikuje opis, aby wymagać 5 lat C# doświadczenia i akceptuje modyfikację.  
  
5. Piotr działa w przypadku zmodyfikowanego żądania Michael i akceptuje je. Żądanie musi być zatwierdzone przez dyrektora inżynieryjnego, Tsvi Reiter.  
  
6. Tsvi Reiter chce przyspieszyć żądanie, dzięki czemu otrzymuje komentarz, aby powiedzieć, że żądanie jest pilne i akceptuje je.  
  
7. Żądanie musi być zatwierdzone przez dwóch menedżerów kadr lub dyrektora naczelnego. Dyrektor naczelny, Brian Richard Goldstein, widzi pilne żądanie przez Tsvi. Działa na żądanie, akceptując go, w ten sposób pomijając zatwierdzenie przez dwóch menedżerów kadr.  
  
8. Żądanie zostało usunięte z skrzynki odbiorczej firmy Jan i proces zatrudniania usługi SDET został rozpoczęty.  
  
### <a name="start-resume-request"></a>Uruchom żądanie wznowienia  
  
1. Teraz pozycja zadania oczekuje na opublikowanie w zewnętrznej witrynie sieci Web, w której mogą być stosowane inne osoby (zobaczysz łącze do pozycji **Księgowanie zadania** ). Obecnie pozycja zadania jest nadana przedstawicielowi KADRy, który jest odpowiedzialny za finalizowanie stanowiska zadania i jego opublikowanie.  
  
2. HR chce edytować tę pozycję zadania (przez kliknięcie linku **edycji** ), ustawiając limit czasu wynoszący 60 minut (w czasie rzeczywistym). Limit czasu pozwala na wyjęcie stanowiska zadania poza zewnętrzną witrynę sieci Web zgodnie z określonym czasem.  
  
3. Po zapisaniu edytowanej pozycji zadania zostanie ona wyświetlona na karcie **otrzymywanie wznowień** (Odśwież stronę sieci Web, aby zobaczyć nową pozycję zadania).  
  
### <a name="collecting-resumes"></a>Zbieranie wznowień  
  
1. Pozycja zadania powinna pojawić się w zewnętrznej witrynie sieci Web. Osoby zainteresowane zastosowaniem do zadania mogą być stosowane do tej pozycji i przesłać wznowienie.  
  
2. Jeśli wrócisz do usługi lista księgowań zadań, możesz "wyświetlić wznowienia", które zostały zebrane do tej pory.  
  
3. HR może również zatrzymać zbieranie wznowień (na przykład po zidentyfikowaniu odpowiedniego kandydata).  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
  
1. Upewnij się, że używasz programu Visual Studio z uprawnieniami administratora.  
  
2. Jeśli kompilacja nie powiedzie się, sprawdź następujące kwestie:  
  
    - Brak odwołania do `ContosoHR` nie istnieje `InternalClient` w projektach lub `CareersWebSite` .  
  
3. Jeśli nie można wykonać rozwiązania, sprawdź następujące kwestie:  
  
    1. Wszystkie usługi są uruchomione.  
  
    2. Odwołania do usług zostały zaktualizowane.  
  
        1. Otwórz folder App_WebReferences  
  
        2. Kliknij prawym przyciskiem myszy pozycję **contoso** i wybierz pozycję **Aktualizuj odwołania sieci Web/usług**.  
  
        3. Skompiluj ponownie rozwiązanie, naciskając klawisze CTRL + SHIFT + B w programie Visual Studio.  
  
## <a name="uninstalling"></a>Powiązane  
  
1. Usuń magazyn wystąpień SQL Server, uruchamiając polecenie Oczyść. bat znajdujące się w folderze DbSetup.  
  
2. Usuń kod źródłowy z dysku twardego.
