---
title: Proces zatrudniania
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: c6f542cef8e1417ed9c8d3a185252a91062e2161
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313154"
---
# <a name="hiring-process"></a>Proces zatrudniania
Ten przykład demonstruje sposób implementacji procesu biznesowego, przy użyciu działań dotyczących komunikatów i dwa przepływy pracy hostowany jako usług przepływu pracy. Te przepływy pracy są częścią infrastruktury IT w fikcyjnej firmy o nazwie Contoso, Inc.  
  
 `HiringRequest` Procesu przepływu pracy (zaimplementowane jako <xref:System.Activities.Statements.Flowchart>) poprosi o podanie autoryzacji z kilku menedżerów w organizacji. Aby osiągnąć ten cel, przepływ pracy używa innych istniejących usług w organizacji (w naszym przypadku skrzynki odbiorczej usługi i usługi danych organizacji, zaimplementowane jako zwykły usług Windows Communication Foundation (WCF)).  
  
 `ResumeRequest` Przepływu pracy (zaimplementowane jako <xref:System.Activities.Statements.Sequence>) publikuje zadania opublikowanie w witrynie sieci Web kariery zewnętrznych firmy Contoso i zarządza nimi przejęcia wznawia. Publikowanie zadań jest dostępna w zewnętrznej sieci Web, witryny w ustalonym czasie (aż do wygaśnięcia limitu czasu) lub do momentu pracownika z firmy Contoso decyduje o jej usunięcie.  
  
 W tym przykładzie przedstawiono następujące funkcje [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
-   <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Sequence> przepływów pracy na potrzeby modelowania procesów biznesowych.  
  
-   Usługi przepływu pracy.  
  
-   Działania dotyczące komunikatów.  
  
-   Korelacja oparta na zawartości.  
  
-   Działania niestandardowe (deklaratywne i oparte na kodzie).  
  
-   Dostarczane przez system server stanów trwałych programu SQL.  
  
-   Niestandardowe <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
-   Niestandardowe śledzenia.  
  
-   Śledzenie zdarzeń dla zdarzeń śledzenia Windows (ETW).  
  
-   Kompozycja działań.  
  
-   <xref:System.Activities.Statements.Parallel> działania.  
  
-   <xref:System.Activities.Statements.CancellationScope> działanie.  
  
-   Czasomierze trwałe (<xref:System.Activities.Statements.Delay> działanie).  
  
-   Transakcje.  
  
-   Więcej niż jeden przepływ pracy w tym samym rozwiązaniu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Opis procesu  
 Contoso, Inc. chce, aby mieć ścisłą kontrolę nad zatrudnionych w każdym z jego działów. W związku z tym w dowolnym momencie każdy pracownik chce, aby rozpocząć nowy proces zatrudniania, muszą przejść przez zatrudniania zatwierdzenia proces żądania, zanim rekrutacji może rzeczywiście wystąpi. Ten proces jest nazywany zatrudniania żądanie procesu (zdefiniowane w projekcie HiringRequestService) i składa się z następujących czynności:  
  
1. Pracownik (osoby żądającej) uruchamia zatrudniania żądanie procesu.  
  
2. Menedżer żądającego musi zatwierdzić żądanie:  
  
    1.  Menedżer może odrzucić żądanie.  
  
    2.  Menedżer może zwrócić żądania do zleceniodawcy, aby uzyskać dodatkowe informacje:  
  
        1.  Osoby żądającej przeglądów i wysyła żądanie do menedżera.  
  
    3.  Menedżer może zatwierdzić.  
  
3. Po Menedżera żądającego zatwierdza, właściciel działu, musisz zatwierdzić żądanie:  
  
    1.  Właściciel działu może odrzucić.  
  
    2.  Właściciel działu mogą zatwierdzać.  
  
4. Po zatwierdzeniu przez właściciela działu, ten proces wymaga zatwierdzenia menedżerów 2 h lub dyrektora generalnego:  
  
    1.  Ten proces można przejść do stanu zaakceptowane lub odrzucone.  
  
    2.  Jeśli proces zostanie zaakceptowana, nowe wystąpienie klasy `ResumeRequest` uruchamiania przepływu pracy (`ResumeRequest` jest połączony z HiringRequest.csproj poprzez odwołanie do usługi.)  
  
 Po zatwierdzić menedżerowie zatrudniania nowych pracowników działu KADR muszą znaleźć odpowiednim kandydatem. Ten proces odbywa się przez drugi przepływu pracy (`ResumeRequest`zdefiniowaną w ResumeRequestService.csproj). Ten przepływ pracy definiuje proces przesyłania zadania publikowanie za pomocą kariery możliwość zewnętrznej witryny sieci Web kariery firmy Contoso, otrzyma wznawia od kandydatów, a następnie monitoruje stan delegowania zadań. Pozycje są dostępne przez stały okres (aż do czasu wygaśnięcia) lub dopóki pracownika z firmy Contoso decyduje go usunąć. `ResumeRequest` Przepływu pracy składa się z następujących czynności:  
  
1. Pracownika z firmy Contoso typów w informacje na temat pozycji i okres limitu czasu. Gdy typy pracowników te informacje, pozycja jest publikowany w witrynie sieci Web kariery.  
  
2. Po opublikowaniu informacji zainteresowane strony mogą przesyłać wznawia ich. Po przesłaniu życiorysu znajduje się w rekordzie połączone do otwarcia zadania.  
  
3. Kandydaci mogą przesyłać wznawia, do momentu wygaśnięcia limitu czasu lub ktoś z działu KADR Contoso jawnie postanowi usunąć delegowania zatrzymywania procesu.  
  
## <a name="projects-in-the-sample"></a>Projekty w przykładzie  
 W poniższej tabeli przedstawiono projektów w przykładowym rozwiązaniu.  
  
|Projekt|Opis|  
|-------------|-----------------|  
|ContosoHR|Zawiera klasy repozytorium, obiektów biznesowych i kontrakty danych.|  
|HiringRequestService|Zawiera definicję przepływu pracy, proces zatrudniania żądania.<br /><br /> Ten projekt jest wdrażany jako aplikację konsolową, która samodzielnie obsługuje przepływu pracy (plik xaml) jako usługę.|  
|ResumeRequestService|Usługi przepływu pracy, która gromadzi wznawia z kandydatów, dopóki nie upłynie limit czasu wygaśnięcia lub ktoś decyduje o tym, że proces musi zostać zatrzymana.<br /><br /> Ten projekt jest wdrażany jako usługa deklaracyjnego przepływu pracy (xamlx).|  
|OrgService|To usługa, która udostępnia informacje organizacyjne (pracownicy, pozycje, PositionTypes i działów). Tę usługę można traktować jako moduł organizacji firmy z zasobów przedsiębiorstwa Plan (ERP).<br /><br /> Ten projekt jest wdrażany jako aplikację konsolową, która udostępnia usługi Windows Communication Foundation (WCF).|  
|InboxService|Skrzynka odbiorcza, zawierający informacje z możliwością działania zadania dla pracowników.<br /><br /> Ten projekt jest wdrażany jako aplikację konsolową, która udostępnia usługi WCF.|  
|InternalClient|Aplikacja sieci Web do interakcji z procesu. Użytkownicy mogą uruchomić, udział i przeglądać ich HiringProcess przepływów pracy. Za pomocą tej aplikacji, mogą także uruchomić i monitorować procesy ResumeRequest.<br /><br /> Ta witryna jest implementowany jako wewnętrzne sieci intranet firmy Contoso. Ten projekt jest wdrażany jako witryny sieci Web ASP.NET.|  
|CareersWebSite|Zewnętrznej witryny sieci Web, która udostępnia stanowiska w firmie Contoso. Wszelkie potencjalne Release candidate można przejść do tej witryny i przesłać życiorysu.|  
  
## <a name="feature-summary"></a>Podsumowanie funkcji  
 W poniższej tabeli opisano, jak każda funkcja jest używana w tym przykładzie.  
  
|Funkcja|Opis|Projekt|  
|-------------|-----------------|-------------|  
|Schemat blokowy|Proces biznesowy jest przedstawiana jako schematu blokowego. Opis ten schemat blokowy przedstawia proces w taki sam sposób, w którym firma będzie narysuje je w tablicy.|HiringRequestService|  
|Usługi przepływu pracy|Schemat blokowy z definicji procesu znajduje się w usłudze (w tym przykładzie usługa znajduje się w aplikacji konsoli).|HiringRequestService|  
|Działania dotyczące komunikatów|Schemat blokowy używa działań komunikatów na dwa sposoby:<br /><br /> -Aby uzyskać informacje od użytkownika (Aby odbierać decyzje i powiązane informacje w każdym kroku zatwierdzenia).<br />-Aby wchodzić w interakcje z innymi usługami istniejących (InboxService i OrgDataService, używane za pośrednictwem odwołań do usług).|HiringRequestService|  
|Korelacja na podstawie zawartości|Korelowanie komunikatów zatwierdzenia na właściwość ID zatrudniania żądania:<br /><br /> -Rozpoczęcie procesu, uchwyt korelacji jest inicjowany z identyfikator żądania.<br />— Komunikaty przychodzące zatwierdzenia skorelować na ich ID (identyfikator żądania jest pierwszy parametr każdy komunikat zatwierdzenia).|HiringRequestService / ResumeRequestService|  
|Działania niestandardowe (deklaratywne i kodu na podstawie)|Istnieje kilka niestandardowych działań w tym przykładzie:<br /><br /> -   `SaveActionTracking`: To działanie wyemituje niestandardowego <xref:System.Activities.Tracking.TrackingRecord> (przy użyciu <xref:System.Activities.NativeActivityContext.Track%2A>). To działanie został utworzony przy użyciu kodu imperatywnego rozszerzanie <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: To działanie odbiera listę typie stanowisk identyfikatory i zwraca listę osób, które mają tej pozycji w firmie Contoso. To działanie został utworzony w sposób deklaratywny (z wykorzystaniem projektanta działań).<br />-   `SaveHiringRequestInfo`: To działanie zapisuje informacje o `HiringRequest` (przy użyciu `HiringRequestRepository.Save`). To działanie został utworzony przy użyciu kodu imperatywnego rozszerzanie <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Trwałość serwera SQL dostarczane przez system|<xref:System.ServiceModel.Activities.WorkflowServiceHost> Wystąpienie, schemat blokowy definicji procesu jest skonfigurowany do używania dostarczane przez system stanów trwałych programu SQL Server.|HiringRequestService / ResumeRequestService|  
|Niestandardowe śledzenie|Przykład obejmuje uczestnikiem niestandardowe śledzenia, która zapisuje historii `HiringRequestProcess` (to rekordy, jakie działania zostały wykonane, przez kogo i kiedy). Kod źródłowy jest w folderze śledzenia HiringRequestService.|HiringRequestService|  
|Śledzenie zdarzeń systemu Windows|Dostarczane przez system śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku App.config w usłudze HiringRequestService.|HiringRequestService|  
|Kompozycja działań|Definicja proces używa bezpłatnego skład <xref:System.Activities.Activity>. Schemat blokowy zawiera kilka sekwencji i działania równoległe, zawierające w tym samym czasie inne działania (i tak dalej).|HiringRequestService|  
|Działania równoległe|-   <xref:System.Activities.Statements.ParallelForEach%601> Służy do rejestrowania w skrzynce odbiorczej, Dyrektor Generalny i menedżerów działu KADR równolegle (oczekiwanie na krok zatwierdzenia menedżerów dwóch HR).<br />-   <xref:System.Activities.Statements.Parallel> Służy do wykonywania niektórych zadań oczyszczania w krokach ukończone i odrzucony|HiringRequestService|  
|Unieważnieniu modelu|Schemat blokowy używa <xref:System.Activities.Statements.CancellationScope> utworzyć zachowanie anulowania (w tym przypadku nie niektóre oczyszczanie.)|HiringRequestService|  
|Klient uczestnika stanów trwałych|`HiringRequestPersistenceParticipant` zapisuje dane ze zmiennej przepływu pracy do tabeli w bazie danych HR firmy Contoso.|HiringRequestService|  
|Usługi przepływu pracy|`ResumeRequestService` jest implementowany przy użyciu usług przepływu pracy. Informacje o definicji i usługi przepływu pracy znajduje się w ResumeRequestService.xamlx. Usługa jest skonfigurowana do użycia, trwałość i śledzenia.|ResumeRequestService|  
|Czasomierze trwałe|`ResumeRequestService` używa czasomierzy trwałe, aby zdefiniować czas trwania zadania księgowania (po wygaśnięciu limitu czasu, publikowanie zadania zostanie zamknięte).|ResumeRequestService|  
|Transakcje|<xref:System.Activities.Statements.TransactionScope> Służy do zapewnienia spójności danych w ramach wykonania kilku czynności (po odebraniu nowych resume).|ResumeRequestService|  
|Transakcje|Niestandardowego uczestnika stanów trwałych (`HiringRequestPersistenceParticipant`) i niestandardowego uczestnika śledzenia (`HistoryFileTrackingParticipant`) Użyj tej samej transakcji.|HiringRequestService|  
|Za pomocą [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.|Przepływy pracy są dostępne z dwóch [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Data Storage  
 Dane są przechowywane w bazie danych programu SQL Server o nazwie `ContosoHR` (skryptu do tworzenia tej bazy danych znajduje się w `DbSetup` folder). Wystąpienia przepływu pracy są przechowywane w bazie danych programu SQL Server o nazwie `InstanceStore` (skrypty służące do tworzenia magazyn wystąpienia są częścią [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] dystrybucji).  
  
 Obu bazach danych są tworzone przez uruchomienie skryptu plik Setup.cmd z wiersza polecenia dla deweloperów programu Visual Studio.  
  
## <a name="running-the-sample"></a>Działa aplikacja przykładowa  
  
#### <a name="to-create-the-databases"></a>Do tworzenia baz danych  
  
1. Otwórz wiersz polecenia dla deweloperów programu Visual Studio.  
  
2. Przejdź do folderu przykładu.  
  
3. Uruchom plik Setup.cmd.  
  
4. Sprawdź, czy dwie bazy danych `ContosoHR` i `InstanceStore` zostały utworzone w programie SQL Express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Aby skonfigurować rozwiązanie do wykonania  
  
1. Uruchom program Visual Studio jako administrator. Otwórz HiringRequest.sln.  
  
2. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
3. Wybierz opcję **wiele projektów startowych** i ustaw **CareersWebSite**, **InternalClient**, **HiringRequestService**, i **ResumeRequestService** do **Start**. Pozostaw **ContosoHR**, **InboxService**, i **OrgService** None.  
  
4. Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B. Sprawdź, czy kompilacja zakończyła się pomyślnie.  
  
#### <a name="to-run-the-solution"></a>Aby uruchomić rozwiązanie  
  
1. Po kompilacji rozwiązania, naciśnij klawisze CTRL + F5, aby uruchomić bez debugowania. Sprawdź, czy wszystkie usługi zostały uruchomione.  
  
2. Kliknij prawym przyciskiem myszy **InternalClient** w rozwiązaniu, a następnie wybierz **Pokaż w przeglądarce**. Domyślna strona dla `InternalClient` jest wyświetlana. Upewnij się, że usługi są uruchomione, a następnie kliknij łącze.  
  
3. **HiringRequest** modułu jest wyświetlana. Możesz wykonać scenariusz przedstawione w tym miejscu.  
  
4. Gdy `HiringRequest` jest zakończone, możesz rozpocząć `ResumeRequest`. Możesz wykonać scenariusz przedstawione w tym miejscu.  
  
5. Gdy `ResumeRequest` jest opublikowana, jest dostępna w publicznej witrynie sieci Web (witryna sieci Web kariery firmy Contoso). Aby zobaczyć, publikując zadania (i zastosować dla pozycji), przejdź do witryny sieci Web kariery.  
  
6. Kliknij prawym przyciskiem myszy **CareersWebSite** w rozwiązaniu i wybierz **Pokaż w przeglądarce**.  
  
7. Przejdź z powrotem do `InternalClient` przez kliknięcie prawym przyciskiem myszy **InternalClient** w rozwiązaniu i wybierając polecenie **Pokaż w przeglądarce**.  
  
8. Przejdź do **JobPostings** sekcji, klikając **zadań** link w menu u góry skrzynki odbiorczej. Możesz wykonać scenariusz przedstawione w tym miejscu.  
  
## <a name="scenarios"></a>Scenariusze  
  
### <a name="hiring-request"></a>Żądanie zatrudniania  
  
1. Jan Alexander (inżynier oprogramowania) chce zażądać nowego położenia zatrudnienia programista testu (SDET) działu inżynierii, który ma co najmniej 3 lata doświadczenia w języku C#.  
  
2. Utworzone żądanie pojawi się w skrzynce odbiorczej przez Michaela (kliknij **Odśwież** Jeśli nie widzisz żądania) oczekuje na zatwierdzenie Peter Brehm, kto jest kierownikiem firmy Michael.  
  
3. Peter chce działać na żądanie przez Michaela. ADAM sądzą zapotrzebowanie pozycji 5 lat środowisko C#, a nie 3, więc użytkownik wysyła swoje komentarze, wróć do przeglądu.  
  
4. Michael zobaczy komunikat w swojej Skrzynce odbiorczej z menedżerowi i chce działać. Michael widzi historię żądań pozycji i zgadza się z Peter. Michael modyfikuje opis, który wymaga 5 lat doświadczenia w języku C# i akceptuje modyfikacji.  
  
5. Peter działa na żądanie zmodyfikowane przez Michaela i akceptuje je. Żądanie musi zostać zatwierdzone, Dyrektor ds. inżynierii, Reiterowi Tsvi firmy.  
  
6. Reiterowi Tsvi firmy chce, aby przyspieszyć żądania, dlatego umieszcza się on w komentarzu powiedzieć, że żądanie jest pilne i akceptuje je.  
  
7. Żądanie zawiera teraz zostać zatwierdzone przez dwa HR menedżerowie lub dyrektora Generalnego. Dyrektor Generalny, Brian Richard Goldstein, widzi nagłe żądanie przez Tsvi. On działa na żądanie, akceptując, związku z czym pomijany zatwierdzenia przez menedżerów dwóch HR.  
  
8. Żądanie zostanie usunięty ze skrzynki odbiorczej Michael firmy, a teraz rozpoczął proces zatrudniania specjalistów SDET.  
  
### <a name="start-resume-request"></a>Rozpocznij żądanie wznowienia  
  
1. Teraz, pozycja zadanie oczekuje na zostać opublikowane do zewnętrznej witryny sieci Web, w którym użytkownicy mogą stosować (można to sprawdzić kliknięcie **zadań** link). Obecnie pozycji zadania znajdują się z przedstawicielem działu KADR, który jest odpowiedzialny za finalizowanie pozycji zadania i opublikuj go.  
  
2. HR chce edytować tej pozycji zadania (klikając **Edytuj** link), ustawiając limit czasu 60 minut (w realnym, może to być dni lub tygodni). Limit czasu umożliwia pozycji zadania, aby zdjąć zewnętrznej witryny sieci Web zgodnie z określonym czasie.  
  
3. Po zapisaniu edytowanego stanowisko, zostanie on wyświetlony na **odbieranie wznawia** karcie (w wyniku odświeżenia strony sieci Web, aby zobaczyć nowe położenie zadania).  
  
### <a name="collecting-resumes"></a>Wznawia zbieranie  
  
1. Pozycja zadania powinny pojawić się na zewnętrznej witryny sieci Web. Jako osoba zainteresowani zastosowanie dla zadania możesz poprosić o tej pozycji i Prześlij swój życiorys.  
  
2. Jeśli możesz wrócić do usługi listy ogłoszeń zadania, możesz "wyświetlić wznawia", zostały zebrane do tej pory.  
  
3. GODZ. je również zatrzymać zbieranie wznawia (np. Po zidentyfikowaniu prawo Release candidate).  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
  
1. Upewnij się, że używasz programu Visual Studio z uprawnieniami administratora.  
  
2. Jeśli rozwiązanie nie twórz, sprawdź następujące informacje:  
  
    -   Odwołanie do `ContosoHR` nie brakuje `InternalClient` lub `CareersWebSite` projektów.  
  
3. Jeśli rozwiązanie wykonanie nie powiedzie się, sprawdź następujące informacje:  
  
    1.  Wszystkie usługi są uruchomione.  
  
    2.  Odwołania do usług są aktualizowane.  
  
        1.  Otwórz App_WebReferences folder  
  
        2.  Kliknij prawym przyciskiem myszy **Contoso** i wybierz **aktualizacja odwołań sieci Web/usługi**.  
  
        3.  Ponownie skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B w programie Visual Studio.  
  
## <a name="uninstalling"></a>Odinstalowywanie  
  
1. Usuń magazyn wystąpienia programu SQL Server, uruchamiając Cleanup.bat, znajdujący się w folderze Program DbSetup.  
  
2. Usuń w formie kodu źródłowego na dysku twardym.