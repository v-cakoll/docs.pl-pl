---
title: Zatrudniania procesu
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: 87327692e35e9386dab4cf906ab33cbe08d73fdd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519766"
---
# <a name="hiring-process"></a>Zatrudniania procesu
W tym przykładzie pokazano, jak zaimplementować proces biznesowy przy użyciu działań obsługi wiadomości i dwóch przepływów pracy hostowany jako usługi przepływu pracy. Te przepływy pracy są częścią infrastruktury IT fikcyjnej firmy o nazwie Contoso, Inc.  
  
 `HiringRequest` Procesu przepływu pracy (zaimplementowane jako <xref:System.Activities.Statements.Flowchart>) żąda autoryzacji z kilku menedżerów w organizacji. Na osiągnięcie tego celu, przepływ pracy używa innych istniejących usług w organizacji (w tym przypadku usługa skrzynki odbiorczej i Usługa danych organizacji zaimplementowane jako zwykły usług Windows Communication Foundation (WCF)).  
  
 `ResumeRequest` Przepływu pracy (zaimplementowane jako <xref:System.Activities.Statements.Sequence>) publikuje zadania w witrynie sieci Web firmy Contoso zewnętrznych możliwości podnoszenia kwalifikacji i zarządza nabycie wznawia. Publikowanie zadania jest dostępny w sieci Web zewnętrznej witryny na czas (dopóki nie zostanie przekroczony został limit wygasa) lub do pracownika z firmy Contoso decyduje o tym, aby usunąć go.  
  
 W tym przykładzie pokazano poniższe funkcje [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
-   <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Sequence> przepływy pracy dla modelowania procesów biznesowych.  
  
-   Usługi przepływu pracy.  
  
-   Działania dotyczące komunikatów.  
  
-   Na podstawie zawartości korelacji.  
  
-   Działania niestandardowe (deklaratywne i opartych na kodzie).  
  
-   Dostarczane przez system trwałości serwera SQL.  
  
-   Niestandardowe <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
-   Niestandardowe śledzenia.  
  
-   Zdarzenia śledzenia do śledzenia systemu Windows (ETW).  
  
-   Skład działań.  
  
-   <xref:System.Activities.Statements.Parallel> działania.  
  
-   <xref:System.Activities.Statements.CancellationScope> działanie.  
  
-   Czasomierze trwałe (<xref:System.Activities.Statements.Delay> działania).  
  
-   Transakcje.  
  
-   Więcej niż jeden przepływ pracy w tym samym rozwiązaniu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Opis procesu  
 Firmy Contoso, Inc. chce mieć ścisłej kontroli nad zatrudnionych w każdej jego działów. W związku z tym w dowolnym momencie każdy pracownik chce uruchomić nowego procesu zatrudniania, muszą przejść przez zatrudniania zatwierdzenia procesu żądania przed rekrutacji zdarzyć faktycznie. Ten proces jest nazywany zatrudniania przetworzyć żądania (zdefiniowany w projekcie HiringRequestService) i obejmuje następujące kroki:  
  
1.  Pracownik (obiektu żądającego) uruchamia zatrudniania przetworzyć żądania.  
  
2.  Menedżer żądającego musi zatwierdzić żądanie:  
  
    1.  Menedżer może odrzucać żądania.  
  
    2.  Menedżer może zwracać żądania do zleceniodawcy, aby uzyskać dodatkowe informacje:  
  
        1.  Żądający monitoruje i wysyła żądanie z powrotem do menedżera.  
  
    3.  Menedżer może zatwierdzić.  
  
3.  Po Menedżera żądającego zatwierdza, właściciel działu musi zatwierdzić żądanie:  
  
    1.  Właściciel działu można odrzucić.  
  
    2.  Właściciel działu mogą zatwierdzać.  
  
4.  Po zatwierdza właściciela działu, proces wymaga zatwierdzenia menedżerów 2 h lub Dyrektora:  
  
    1.  Proces może przejść w stan zatwierdzone lub odrzucone.  
  
    2.  Jeśli proces jest akceptowany, nowe wystąpienie klasy `ResumeRequest` przepływ pracy jest uruchomiony (`ResumeRequest` jest połączony z HiringRequest.csproj za pomocą odwołania do usługi.)  
  
 Po menedżerów zatwierdzenie zatrudnienia pracownika, HR musi znaleźć odpowiednie kandydata. Ten proces odbywa się w drugim przepływu pracy (`ResumeRequest`zdefiniowanej w ResumeRequestService.csproj). Ten przepływ pracy definiuje proces przesyłania zadania Księgowanie za pomocą zawodowych możliwość zewnętrznej witryny sieci Web możliwości podnoszenia kwalifikacji firmy Contoso, odbiera wznawia z kandydatów i monitoruje stan delegowania zadania. Pozycje są dostępne w danym okresie ustalonym (do czasu wygaśnięcia) lub do momentu pracownika z firmy Contoso decyduje o tym usunąć go. `ResumeRequest` Przepływ pracy składa się z następujących czynności:  
  
1.  Pracownika z firmy Contoso typy informacje dotyczące pozycji i okres limitu czasu. Gdy typy pracowników w tych informacji, pozycja jest opublikowana w witrynie sieci Web możliwości podnoszenia kwalifikacji.  
  
2.  Po opublikowaniu informacji zainteresowanych stron można przesłać wznawia ich. Po przesłaniu wznowienia, znajduje się w rekordzie powiązany otwierania zadania.  
  
3.  Kandydaci mogą przesyłać wznawia, dopóki przekroczeniu limitu czasu lub ktoś z działu Contoso HR jawnie postanowi usunąć delegowania zatrzymywania procesu.  
  
## <a name="projects-in-the-sample"></a>Projekty w próbce.  
 W poniższej tabeli przedstawiono projektów w rozwiązaniu próbki.  
  
|Projekt|Opis|  
|-------------|-----------------|  
|ContosoHR|Zawiera klasy repozytorium, obiektów biznesowych i kontraktów danych.|  
|HiringRequestService|Zawiera definicję przepływu pracy zatrudnienia proces żądania.<br /><br /> Ten projekt jest wdrażany jako aplikacji konsoli własnym obsługującego przepływu pracy (plik xaml) jako usługa.|  
|ResumeRequestService|Usługi przepływu pracy, która gromadzi wznawia z kandydatów do chwili osiągnięcia limitu czasu lub inna decyduje o tym, że proces musi zostać zatrzymana.<br /><br /> Ten projekt jest wdrażany jako usługa deklaracyjnego przepływu pracy (xamlx).|  
|OrgService|Usługa, która udostępnia informacje organizacyjne (pracowników, pozycje PositionTypes i działów). Tę usługę można traktować jako modułu organizacji firmy z zasobów przedsiębiorstwa planowanie (ERP).<br /><br /> Ten projekt jest wdrażany jako aplikacja konsolowa, która udostępnia usługi Windows Communication Foundation (WCF).|  
|InboxService|Skrzynka odbiorcza zawiera zadań dla pracowników.<br /><br /> Ten projekt jest wdrażany jako aplikacja konsolowa, która udostępnia usługi WCF.|  
|InternalClient|Aplikacji sieci Web do interakcji z procesem. Użytkownicy mogą uruchomić, udziału i przeglądać ich HiringProcess przepływów pracy. Za pomocą tej aplikacji, mogą także uruchomić i monitorować procesy ResumeRequest.<br /><br /> Ta lokacja jest implementowany jako wewnętrzne sieci intranet firmy Contoso. Ten projekt jest wdrażany jako witryny sieci Web ASP.NET.|  
|CareersWebSite|Zewnętrznej witryny sieci Web, który ujawnia Otwórz pozycje w firmie Contoso. Wszelkie potencjalne kandydata można przejść do tej witryny i przesłać Wznów.|  
  
## <a name="feature-summary"></a>Podsumowanie funkcji  
 W poniższej tabeli opisano, jak każdej funkcji jest używany w tym przykładzie.  
  
|Funkcja|Opis|Projekt|  
|-------------|-----------------|-------------|  
|Schemat blokowy|Proces biznesowy jest reprezentowany jako blokowego. Ten opis schemat blokowy przedstawia proces w taki sam sposób, w którym firma będzie mieć narysowana go w tablicy.|HiringRequestService|  
|usługi przepływu pracy|Schemat blokowy procesu definicji znajduje się w usłudze (w tym przykładzie usługa znajduje się w aplikacji konsoli).|HiringRequestService|  
|Działania dotyczące komunikatów|Schemat blokowy używa działania obsługi komunikatów na dwa sposoby:<br /><br /> — Aby uzyskać informacje od użytkownika (Aby odbierać decyzje i powiązane informacje w każdym kroku zatwierdzenia).<br />— W celu wchodzenia w interakcje z innymi usługami istniejących (InboxService i OrgDataService używane za pośrednictwem odwołania do usług).|HiringRequestService|  
|Korelacja na podstawie zawartości|Korelowanie zatwierdzenia wiadomości o właściwości ID zatrudniania żądania:<br /><br /> — Po uruchomieniu procesu dojścia korelacji jest zainicjowany przy użyciu Identyfikatora żądania.<br />-Korelowanie przychodzących komunikatów zatwierdzenia na ich ID (pierwszy parametr każdy komunikat zatwierdzenia jest identyfikatorem żądania).|HiringRequestService / ResumeRequestService|  
|Działania niestandardowe (deklaratywne i kod na podstawie)|Istnieje kilka niestandardowych działań w tym przykładzie:<br /><br /> -   `SaveActionTracking`: Działanie emituje niestandardowego <xref:System.Activities.Tracking.TrackingRecord> (przy użyciu <xref:System.Activities.NativeActivityContext.Track%2A>). To działanie został utworzony przy użyciu kodu konieczne rozszerzenie <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: To działanie odbiera listę pozycji typu identyfikatorów i zwraca listę użytkowników, którzy mają tej pozycji w firmie Contoso. To działanie został utworzony deklaratywnie (przy użyciu narzędzia Projektant działań).<br />-   `SaveHiringRequestInfo`: Działanie zapisuje informacje o `HiringRequest` (przy użyciu `HiringRequestRepository.Save`). To działanie został utworzony przy użyciu kodu konieczne rozszerzenie <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Trwałość serwera SQL dostarczane przez system|<xref:System.ServiceModel.Activities.WorkflowServiceHost> Wystąpienie, schemat blokowy procesu definicji jest skonfigurowana do używania trwałości programu SQL Server dostarczane przez system.|HiringRequestService / ResumeRequestService|  
|Niestandardowe śledzenia|Przykład obejmuje uczestnika niestandardowych śledzenia, który zapisuje historię `HiringRequestProcess` (to rejestruje czynności zostały wykonane, kto i kiedy). Kod źródłowy jest w folderze śledzenia HiringRequestService.|HiringRequestService|  
|Śledzenie zdarzeń systemu Windows|Dostarczane przez system śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku App.config w usłudze HiringRequestService.|HiringRequestService|  
|Kompozycja działań|Definicja proces używa wolnego skład <xref:System.Activities.Activity>. Schemat blokowy zawiera kilka sekwencji i działania równoległe, które jednocześnie zawierać innych działań (i tak dalej).|HiringRequestService|  
|Działania równoległe|-   <xref:System.Activities.Statements.ParallelForEach%601> Służy do rejestrowania w skrzynce odbiorczej Prezes i menedżerów HR równoległe (oczekiwanie na menedżerów dwóch HR zatwierdzenia kroku).<br />-   <xref:System.Activities.Statements.Parallel> Służy do wykonywania niektórych zadań oczyszczania w krokach ukończone i odrzucone|HiringRequestService|  
|Anulowanie modelu|Schemat blokowy używa <xref:System.Activities.Statements.CancellationScope> można utworzyć zachowania anulowania (w tym przypadku nie niektórych oczyszczania.)|HiringRequestService|  
|Uczestnika trwałości klienta|`HiringRequestPersistenceParticipant` zapisuje dane z zmiennej przepływu pracy do tabeli w bazie danych Contoso HR.|HiringRequestService|  
|Usługi przepływu pracy|`ResumeRequestService` zaimplementowano przy użyciu usługi przepływu pracy. Informacje o definicji i usługi przepływu pracy znajduje się w ResumeRequestService.xamlx. Usługa jest skonfigurowana do używania trwałości i śledzenia.|ResumeRequestService|  
|Czasomierze trwałych|`ResumeRequestService` używa czasomierze trwałe, aby zdefiniować czas trwania księgowej zlecenia (po przekroczeniu limitu czasu, księgowanie zadania jest zamknięty).|ResumeRequestService|  
|Transakcje|<xref:System.Activities.Statements.TransactionScope> Służy do zapewnienia spójności danych w ramach wykonania kilku czynności (po odebraniu nowego resume).|ResumeRequestService|  
|Transakcje|Uczestnika trwałości niestandardowe (`HiringRequestPersistenceParticipant`) i uczestnika niestandardowych śledzenia (`HistoryFileTrackingParticipant`) Użyj tej samej transakcji.|HiringRequestService|  
|Przy użyciu [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.|Przepływy pracy są dostępne z dwóch [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Magazyn danych  
 Dane są przechowywane w bazie danych programu SQL Server o nazwie `ContosoHR` (skrypt służący do tworzenia tej bazy danych znajduje się w `DbSetup` folderu). Wystąpienia przepływu pracy są przechowywane w bazie danych programu SQL Server o nazwie `InstanceStore` (skrypty służące do tworzenia w magazynie wystąpień są częścią [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] dystrybucji).  
  
 Obie bazy danych są tworzone przez uruchomienie skryptu Setup.cmd z wiersza polecenia programu Visual Studio.  
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
  
#### <a name="to-create-the-databases"></a>Do tworzenia baz danych  
  
1.  Otwórz wiersz polecenia programu Visual Studio.  
  
2.  Przejdź do folderu próbki.  
  
3.  Uruchom Setup.cmd.  
  
4.  Sprawdź, czy dwie bazy danych `ContosoHR` i `InstanceStore` zostały utworzone w programie SQL Express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Aby skonfigurować rozwiązanie do wykonania  
  
1.  Uruchom program Visual Studio jako administrator. Otwórz HiringRequest.sln.  
  
2.  Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
3.  Wybierz opcję **wiele projektów startowych** i ustaw **CareersWebSite**, **InternalClient**, **HiringRequestService**, i **ResumeRequestService** do **Start**. Pozostaw **ContosoHR**, **InboxService**, i **OrgService** None.  
  
4.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B. Sprawdź, czy kompilacja powiodła się.  
  
#### <a name="to-run-the-solution"></a>Aby uruchomić rozwiązanie  
  
1.  Po rozwiązaniu kompilacje, naciśnij kombinację klawiszy CTRL + F5, aby uruchomić bez debugowania. Sprawdź, czy wszystkie usługi zostały uruchomione.  
  
2.  Kliknij prawym przyciskiem myszy **InternalClient** w rozwiązaniu, a następnie wybierz **Wyświetl w przeglądarce**. Domyślna strona dla `InternalClient` jest wyświetlany. Upewnij się, że usługi są uruchomione i kliknij łącze.  
  
3.  **HiringRequest** modułu jest wyświetlany. Możesz wykonać scenariusz szczegółowo w tym miejscu.  
  
4.  Raz `HiringRequest` jest zakończone, można uruchomić `ResumeRequest`. Możesz wykonać scenariusz szczegółowo w tym miejscu.  
  
5.  Gdy `ResumeRequest` jest opublikowane, jest dostępna w publicznej witryny sieci Web (witryna sieci Web firmy Contoso możliwości podnoszenia kwalifikacji). Aby zobaczyć, księgowanie zadania (i zastosować dla pozycji), przejdź do witryny sieci Web możliwości podnoszenia kwalifikacji.  
  
6.  Kliknij prawym przyciskiem myszy **CareersWebSite** rozwiązania i wybierz **Wyświetl w przeglądarce**.  
  
7.  Przejdź z powrotem do `InternalClient` przez kliknięcie prawym przyciskiem myszy **InternalClient** w rozwiązaniu i wybierając **Wyświetl w przeglądarce**.  
  
8.  Przejdź do **JobPostings** sekcji klikając **zadań** łącze w menu u góry skrzynki odbiorczej. Możesz wykonać scenariusz szczegółowo w tym miejscu.  
  
## <a name="scenarios"></a>Scenariusze  
  
### <a name="hiring-request"></a>Zatrudniania żądania  
  
1.  Jan Alexander (inżynier oprogramowania) chce, aby zażądać nowego położenia zatrudnienia inżyniera testowego (SDET) oprogramowania działu inżynierii, który ma co najmniej 3 latach doświadczeń w języku C#.  
  
2.  Utworzone żądanie pojawia się w skrzynce odbiorczej na Michael (kliknij **Odśwież** Jeśli nie widzisz żądania) oczekujące na zatwierdzenie Peterowi Brehm, będącego jego Michael menedżera.  
  
3.  Peterowi potrzebuje do działania w jego Michael żądania. Wymagania pozycji z C# obsługi zamiast 3, 5 lat on sądzi, wysyła on jego komentarze wstecz do przeglądu.  
  
4.  Jan zobaczy komunikat w swojej Skrzynce odbiorczej z menedżerowi i chce działania. Jan widzi historii żądania pozycji i jest zgodna z Peterowi. Jan modyfikuje opis, aby wymagać 5 latach doświadczeń C# i akceptuje modyfikacji.  
  
5.  Peterowi działa na żądanie zmodyfikowane przez Michael i akceptuje on. Żądanie musi zostać zatwierdzone przez dyrektora z zespołu inżynieryjnego, Reiterowi Tsvi firmy.  
  
6.  Reiterowi Tsvi firmy chce przyspieszyć żądania, więc on umieszcza w komentarz oznacza, że żądanie jest pilnych i akceptuje on.  
  
7.  Żądanie zawiera teraz zatwierdzenia przez dwa HR menedżerów lub Dyrektora. Dyrektora Richard Goldstein Brianowi, widzi wniosku przez Tsvi. On działa na żądanie, akceptując związku z czym pomijany zatwierdzenia przez dwa HR menedżerów.  
  
8.  Żądanie zostanie usunięty ze skrzynki odbiorczej w Michael i procesu zatrudnienia SDET zostało teraz uruchomione.  
  
### <a name="start-resume-request"></a>Uruchom żądanie wznowienia  
  
1.  Teraz, pozycja zadanie oczekuje na można opublikować do zewnętrznej witryny sieci Web, w którym użytkownicy mogą stosować (można to sprawdzić kliknięcie **zadań** link). Obecnie pozycji zadania znajduje się z przedstawicielem HR, kto jest odpowiedzialny za finalizowanie pozycji zadania i przesłanie go.  
  
2.  HR chce edytować tej pozycji zadania (klikając **Edytuj** link) przez ustawienie limitu czasu 60 minut (w rzeczywistych, może to być dni lub tygodni). Limit czasu umożliwia stanowisko podejmowane poza zewnętrznej witryny sieci Web zgodnie z określonym czasie.  
  
3.  Po zapisaniu edytowanego stanowisko, prawdopodobnie w **odbieranie wznawia** kartę (odświeżania strony sieci Web, aby zobaczyć nowe położenie zadania).  
  
### <a name="collecting-resumes"></a>Wznawia zbieranie  
  
1.  Pozycja zadania powinna pojawić się w zewnętrznej witryny sieci Web. Osoby zainteresowane stosowania zadania mogą odnoszą się do tej pozycji i przesłać Twojej wznowienia.  
  
2.  Jeśli możesz powrócić do listy wpisów zadań usługi, możesz "wyświetlić wznawia" do tej pory które zostały zebrane.  
  
3.  HR można też zatrzymać zbieranie wznawia (na przykład po wykryto prawo candidate).  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
  
1.  Upewnij się, że używasz programu Visual Studio z uprawnieniami administratora.  
  
2.  W przypadku niepowodzenia rozwiązania do tworzenia sprawdzić następujące kwestie:  
  
    -   Odwołanie do `ContosoHR` nie brakuje `InternalClient` lub `CareersWebSite` projektów.  
  
3.  Jeśli rozwiązania wykonanie nie powiedzie się, sprawdź następujące informacje:  
  
    1.  Wszystkie usługi są uruchomione.  
  
    2.  Odwołania do usług są aktualizowane.  
  
        1.  Otwórz App_WebReferences folder  
  
        2.  Kliknij prawym przyciskiem myszy **Contoso** i wybierz **odwołania sieci Web/usługa aktualizacji**.  
  
        3.  Ponownie skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B w programie Visual Studio.  
  
## <a name="uninstalling"></a>Odinstalowanie  
  
1.  Usuń magazyn wystąpienia programu SQL Server, uruchamiając Cleanup.bat znajdujący się w folderze Program DbSetup.  
  
2.  Usuń dysk twardy w formie kodu źródłowego.