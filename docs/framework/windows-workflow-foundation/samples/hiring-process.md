---
title: Proces zatrudniania
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: ade72422d29d170e9c80f602f151ce765a1a00f7
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291688"
---
# <a name="hiring-process"></a>Proces zatrudniania
W tym przykładzie pokazano, jak zaimplementować proces biznesowy przy użyciu działań obsługi wiadomości i dwa przepływy pracy hostowane jako usługi przepływu pracy. Te przepływy pracy są częścią infrastruktury IT fikcyjnej firmy o nazwie Contoso, Inc.  
  
 Proces `HiringRequest` przepływu pracy (zaimplementowany jako) prosi o autoryzację <xref:System.Activities.Statements.Flowchart>od kilku menedżerów w organizacji. Aby osiągnąć ten cel, przepływ pracy korzysta z innych istniejących usług w organizacji (w naszym przypadku usługi skrzynki odbiorczej i organizacyjnej usługi danych zaimplementowanych jako zwykłe usługi Windows Communication Foundation (WCF).  
  
 Przepływ `ResumeRequest` pracy (zaimplementowany <xref:System.Activities.Statements.Sequence>jako) publikuje ogłoszenie o pracę w zewnętrznej witrynie firmy Contoso w sieci Web kariery i zarządza pozyskiwaniem życiorysów. Ogłoszenie o pracę jest dostępne w zewnętrznej witrynie sieci Web przez określony czas (do momentu wygaśnięcia limitu czasu) lub do czasu, gdy pracownik firmy Contoso zdecyduje się go usunąć.  
  
 W tym przykładzie przedstawiono następujące [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]cechy:  
  
- <xref:System.Activities.Statements.Flowchart>i <xref:System.Activities.Statements.Sequence> przepływów pracy do modelowania procesów biznesowych.  
  
- Usługi przepływu pracy.  
  
- Działania związane z wiadomościami.  
  
- Korelacja oparta na zawartości.  
  
- Działania niestandardowe (deklaratywne i oparte na kodzie).  
  
- Trwałość serwera SQL zapewnianą przez system.  
  
- Niestandardowe <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
- Śledzenie niestandardowe.  
  
- Śledzenie zdarzeń dla systemu Windows (ETW) Śledzenie.  
  
- Skład działalności.  
  
- <xref:System.Activities.Statements.Parallel>Działania.  
  
- <xref:System.Activities.Statements.CancellationScope>Działania.  
  
- Trwałe czasomierze (<xref:System.Activities.Statements.Delay> aktywność).  
  
- Transakcji.  
  
- Więcej niż jeden przepływ pracy w tym samym rozwiązaniu.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Opis procesu  
 Contoso, Inc chce mieć ścisłą kontrolę nad zatrudnieniem w każdym z jego działów. W związku z tym, w każdej chwili każdy pracownik chce rozpocząć nowy proces rekrutacji, muszą przejść przez zatwierdzenie procesu żądania zatrudnienia, zanim rekrutacja może rzeczywiście się zdarzyć. Ten proces jest nazywany żądaniem procesu rekrutacji (zdefiniowanym w projekcie HiringRequestService) i składa się z następujących kroków:  
  
1. Pracownik (z żądaniem) rozpoczyna żądanie procesu rekrutacji.  
  
2. Menedżer osoby ubiegającej się o zgodę musi zatwierdzić żądanie:  
  
    1. Menedżer może odrzucić żądanie.  
  
    2. Menedżer może zwrócić żądanie do osoby ubiegaczej o dodatkowe informacje:  
  
        1. Żądający przegląda i wysyła żądanie z powrotem do menedżera.  
  
    3. Menedżer może zatwierdzić.  
  
3. Po zatwierdzeniu przez menedżera z żądaniem właściciel działu musi zatwierdzić żądanie:  
  
    1. Właściciel działu może odrzucić.  
  
    2. Właściciel działu może zatwierdzić.  
  
4. Po zatwierdzeniu przez właściciela działu proces wymaga zgody 2 menedżerów HR lub dyrektora generalnego:  
  
    1. Proces może przejść do stanu akceptowane lub odrzucone.  
  
    2. Jeśli proces jest zaakceptowany, zostanie `ResumeRequest` uruchomione nowe wystąpienie przepływu pracy (`ResumeRequest` jest połączone z HiringRequest.csproj za pośrednictwem odwołania do usługi).  
  
 Gdy menedżerowie zatwierdzą zatrudnienie nowego pracownika, kadr musi znaleźć odpowiedniego kandydata. Ten proces jest wykonywany przez`ResumeRequest`drugi przepływ pracy ( , zdefiniowany w resumerequestService.csproj). Ten przepływ pracy definiuje proces przesyłania oferty pracy z możliwością kariery do zewnętrznej witryny firmy Contoso w sieci Web Kariera, otrzymuje życiorysy od kandydatów i monitoruje stan księgowania ofert pracy. Stanowiska są dostępne przez określony czas (do upływu czasu) lub do czasu, gdy pracownik firmy Contoso zdecyduje się go usunąć. Przepływ `ResumeRequest` pracy składa się z następujących kroków:  
  
1. Pracownik firmy Contoso wpisuje informacje o stanowisku i czasie trwania. Po wpisywaniu przez pracownika tych informacji stanowisko jest księgowane w witrynie sieci Web Kariera.  
  
2. Po opublikowaniu informacji zainteresowane strony mogą przedłożyć swoje życiorysy. Po przesłaniu życiorysu jest on przechowywany w rekordzie połączonym z otwarciem zadania.  
  
3. Wnioskodawcy mogą przesyłać życiorysy do czasu wygaśnięcia limit czasu lub ktoś z działu hr contoso wyraźnie zdecyduje się usunąć delegowania, zatrzymując proces.  
  
## <a name="projects-in-the-sample"></a>Projekty w próbie  
 W poniższej tabeli przedstawiono projekty w przykładowym rozwiązaniu.  
  
|Project|Opis|  
|-------------|-----------------|  
|ContosoHR (właso)|Zawiera kontrakty danych, obiekty biznesowe i klasy repozytorium.|  
|Usługa HiringRequestService|Zawiera definicję przepływu pracy procesu żądania rekrutacji.<br /><br /> Ten projekt jest implementowany jako aplikacja konsoli, która samodzielnie hostuje przepływ pracy (plik xaml) jako usługę.|  
|Usługa cvrequestservice|Usługa przepływu pracy, która zbiera życiorysy od kandydatów, dopóki upłynie limit czasu lub ktoś zdecyduje, że proces musi zostać zatrzymany.<br /><br /> Ten projekt jest implementowany jako deklaratywna usługa przepływu pracy (xamlx).|  
|Usługa orgia|Usługa, która udostępnia informacje o organizacji (Pracownicy, Stanowiska, PositionTypes i Działy). Tę usługę można potraktować jako moduł Organizacji firmy planu zasobów przedsiębiorstwa (ERP).<br /><br /> Ten projekt jest implementowany jako aplikacja konsoli, która udostępnia usługę Windows Communication Foundation (WCF).|  
|Usługa skrzynka odbiorcza|Skrzynka odbiorcza zawierająca zadania, które mogą być wykonywane przez pracowników.<br /><br /> Ten projekt jest implementowany jako aplikacja konsoli, która udostępnia usługę WCF.|  
|Wewnętrznyklient|Aplikacja sieci Web do interakcji z procesem. Użytkownicy mogą uruchamiać, uczestniczyć i wyświetlać swoje przepływy pracy HiringProcess. Za pomocą tej aplikacji, mogą również uruchamiać i monitorować procesy ResumeRequest.<br /><br /> Ta witryna jest implementowana jako wewnętrzna w intranecie firmy Contoso. Ten projekt jest realizowany jako ASP.NET witryny sieci Web.|  
|KarieraWebSite|Zewnętrzna witryna sieci Web, która udostępnia otwarte pozycje w aplikacji Contoso. Każdy potencjalny kandydat może przejść do tej witryny i przesłać życiorys.|  
  
## <a name="feature-summary"></a>Podsumowanie funkcji  
 W poniższej tabeli opisano, jak każda funkcja jest używana w tym przykładzie.  
  
|Funkcja|Opis|Project|  
|-------------|-----------------|-------------|  
|Schemat blokowy|Proces biznesowy jest reprezentowany jako schemat blokowy . Ten opis schematu blokowego reprezentuje proces w taki sam sposób, w jaki firma narysowałaby go na tablicy.|Usługa HiringRequestService|  
|Usługi przepływu pracy|Schemat blokowy z definicją procesu jest obsługiwany w usłudze (w tym przykładzie usługa jest hostowana w aplikacji konsoli).|Usługa HiringRequestService|  
|Działania związane z wiadomościami|Schemat blokowy używa działań obsługi wiadomości na dwa sposoby:<br /><br /> - Aby uzyskać informacje od użytkownika (aby otrzymać decyzje i powiązane informacje w każdym kroku zatwierdzania).<br />- Do interakcji z innymi istniejącymi usługami (InboxService i OrgDataService, używane za pośrednictwem odwołań do usługi).|Usługa HiringRequestService|  
|Korelacja oparta na zawartości|Komunikaty zatwierdzenia są skorelowane na właściwości identyfikatora żądania wynajmu:<br /><br /> - Po uruchomieniu procesu dojście korelacji jest inicjowane z identyfikatorem żądania.<br />- Przychodzące komunikaty zatwierdzenia korelują ze swoim identyfikatorem (pierwszym parametrem każdego komunikatu zatwierdzenia jest identyfikator żądania).|HiringRequestService / ResumeRequestService|  
|Działania niestandardowe (deklaratywne i oparte na kodzie)|W tym przykładzie istnieje kilka działań niestandardowych:<br /><br /> -   `SaveActionTracking`: To działanie emituje <xref:System.Activities.Tracking.TrackingRecord> <xref:System.Activities.NativeActivityContext.Track%2A>niestandardowe (za pomocą ). To działanie zostało naliczone przy <xref:System.Activities.NativeActivity>użyciu kodu imperatywu rozszerzającego .<br />-   `GetEmployeesByPositionTypes`: To działanie otrzymuje listę identyfikatorów typów stanowisk i zwraca listę osób, które mają tę pozycję w aplikacji Contoso. To działanie zostało autorem deklaratywnie (przy użyciu projektanta działań).<br />-   `SaveHiringRequestInfo`: To działanie zapisuje `HiringRequest` informacje `HiringRequestRepository.Save`o (za pomocą ). To działanie zostało naliczone przy <xref:System.Activities.CodeActivity>użyciu kodu imperatywu rozszerzającego .|Usługa HiringRequestService|  
|Trwałość programu SQL Server zapewniana przez system|Wystąpienie, <xref:System.ServiceModel.Activities.WorkflowServiceHost> które obsługuje definicję procesu schematu blokowego jest skonfigurowany do korzystania z trwałości programu SQL Server dostarczonych przez system.|HiringRequestService / ResumeRequestService|  
|Niestandardowe śledzenie|Przykład zawiera niestandardowego uczestnika śledzenia, który `HiringRequestProcess` zapisuje historię a (rejestruje, jaka akcja została wykonana, przez kogo i kiedy). Kod źródłowy znajduje się w folderze Śledzenie HiringRequestService.|Usługa HiringRequestService|  
|Śledzenie ETW|Śledzenie ETW dostarczane przez system jest skonfigurowane w pliku App.config w usłudze HiringRequestService.|Usługa HiringRequestService|  
|Skład działalności|Definicja procesu wykorzystuje wolny <xref:System.Activities.Activity>skład . Schemat blokowy zawiera kilka sequence i parallel działania, które w tym samym czasie zawierają inne działania (i tak dalej).|Usługa HiringRequestService|  
|Działania równoległe|-   <xref:System.Activities.Statements.ParallelForEach%601>służy do równoległej rejestracji w skrzynce odbiorczej dyrektora generalnego i menedżerów HR (oczekiwanie na krok zatwierdzania dwóch menedżerów HR).<br />-   <xref:System.Activities.Statements.Parallel>służy do wykonywania niektórych zadań oczyszczania w krokach Zakończone i Odrzucone|Usługa HiringRequestService|  
|Anulowanie modelu|Schemat blokowy używa <xref:System.Activities.Statements.CancellationScope> do tworzenia zachowania anulowania (w tym przypadku wykonuje pewne oczyszczanie.)|Usługa HiringRequestService|  
|Uczestnik trwałości klienta|`HiringRequestPersistenceParticipant`zapisuje dane ze zmiennej przepływu pracy do tabeli przechowywanej w bazie danych contoso HR.|Usługa HiringRequestService|  
|Usługi przepływu pracy|`ResumeRequestService`jest implementowana przy użyciu usług przepływu pracy. Definicja przepływu pracy i informacje o usłudze są zawarte w pliku ResumeRequestService.xamlx. Usługa jest skonfigurowana do używania trwałości i śledzenia.|Usługa cvrequestservice|  
|Trwałe zegary|`ResumeRequestService`używa trwałych czasomierzy do zdefiniowania czasu trwania stanowiska pracy (po upływie określonego czasu księgowanie zlecenia jest zamykany).|Usługa cvrequestservice|  
|Transakcje|<xref:System.Activities.Statements.TransactionScope>służy do zapewnienia spójności danych w ramach wykonywania kilku działań (po odebraniu nowego życiorysu).|Usługa cvrequestservice|  
|Transakcje|Uczestnik trwałości niestandardowej (`HiringRequestPersistenceParticipant`)`HistoryFileTrackingParticipant`i niestandardowy uczestnik śledzenia ( ) używają tej samej transakcji.|Usługa HiringRequestService|  
|Korzystanie [!INCLUDE[wf1](../../../../includes/wf1-md.md)] z aplikacji ASP.NET.|Przepływy pracy są dostępne z dwóch ASP.NET aplikacji.|InternalClient / KarieraWebSite|  
  
## <a name="data-storage"></a>Magazyn danych  
 Dane są przechowywane w bazie `ContosoHR` danych programu SQL Server o nazwie `DbSetup` (skrypt do tworzenia tej bazy danych znajduje się w folderze). Wystąpienia przepływu pracy są przechowywane w `InstanceStore` bazie danych programu SQL Server o nazwie [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] (skrypty do tworzenia magazynu wystąpień są częścią dystrybucji).  
  
 Obie bazy danych są tworzone przez uruchomienie skryptu Setup.cmd z wiersza polecenia dewelopera dla programu Visual Studio.  
  
## <a name="running-the-sample"></a>Uruchamianie przykładowej aplikacji  
  
#### <a name="to-create-the-databases"></a>Aby utworzyć bazy danych  
  
1. Otwórz wiersz polecenia dewelopera dla programu Visual Studio.  
  
2. Przejdź do folderu przykładów.  
  
3. Uruchom plik Setup.cmd.  
  
4. Sprawdź, czy dwie `ContosoHR` `InstanceStore` bazy danych i zostały utworzone w programie SQL Express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Aby skonfigurować rozwiązanie do wykonania  
  
1. Uruchom program Visual Studio jako administrator. Otwórz HiringRequest.sln.  
  
2. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**.  
  
3. Wybierz opcję **Wiele projektów startowych** i ustaw **careersWebSite**, **InternalClient**, **HiringRequestService**i **ResumeRequestService** na **Start**. Pozostaw **ContosoHR**, **InboxService**i **OrgService** jako Brak.  
  
4. Zbuduj rozwiązanie, naciskając klawisze CTRL+SHIFT+B. Sprawdź, czy kompilacja powiodła się.  
  
#### <a name="to-run-the-solution"></a>Aby uruchomić rozwiązanie  
  
1. Po kompilacji rozwiązania naciśnij klawisze CTRL+F5, aby uruchomić bez debugowania. Sprawdź, czy wszystkie usługi zostały uruchomione.  
  
2. Kliknij prawym przyciskiem myszy **pozycję InternalClient** w rozwiązaniu, a następnie wybierz polecenie **Wyświetl w przeglądarce**. Zostanie wyświetlona `InternalClient` strona domyślna. Upewnij się, że usługi są uruchomione, a następnie kliknij łącze.  
  
3. Zostanie wyświetlony moduł **HiringRequest.** Możesz śledzić scenariusz szczegółowo tutaj.  
  
4. Po `HiringRequest` zakończeniu można uruchomić plik `ResumeRequest`. Możesz śledzić scenariusz szczegółowo tutaj.  
  
5. Po `ResumeRequest` opublikowaniu jest on dostępny w publicznej witrynie sieci Web (Contoso Careers Web Site). Aby wyświetlić listę ofert pracy (i ubiegać się o stanowisko), przejdź do witryny sieci Web Kariera.  
  
6. Kliknij prawym przyciskiem myszy **careersWebSite** w rozwiązaniu i wybierz pozycję **Wyświetl w przeglądarce**.  
  
7. Przejdź z `InternalClient` powrotem do tego przycisku, klikając prawym przyciskiem myszy **InternalClient** w rozwiązaniu i wybierając **pozycję Wyświetl w przeglądarce**.  
  
8. Przejdź do sekcji **JobPostings,** klikając **łącze Oferty pracy** w górnym menu skrzynki odbiorczej. Możesz śledzić scenariusz szczegółowo tutaj.  
  
## <a name="scenarios"></a>Scenariusze  
  
### <a name="hiring-request"></a>Wniosek o zatrudnienie  
  
1. Michael Alexander (Software Engineer) chce poprosić o nowe stanowisko w zakresie zatrudniania inżyniera oprogramowania w teście (SDET) w dziale inżynierii, który ma co najmniej 3-letnie doświadczenie w języku C#.  
  
2. Po utworzeniu żądanie pojawia się w skrzynce odbiorczej Michała (kliknij **przycisk Odśwież,** jeśli nie widzisz żądania) w oczekiwaniu na zatwierdzenie Przez Petera Brehma, który jest menedżerem Michaela.  
  
3. Piotr chce działać na prośbę Michaela. Uważa, że stanowisko wymaga 5 lat doświadczenia c# zamiast 3, więc wysyła swoje komentarze z powrotem do przeglądu.  
  
4. Michael widzi wiadomość w swojej skrzynce odbiorczej od swojego menedżera i chce działać. Michael widzi historię prośby o stanowisko i zgadza się z Piotrem. Michael modyfikuje opis, aby wymagać 5 lat doświadczenia w języku C# i akceptuje modyfikację.  
  
5. Peter działa na zmodyfikowaną prośbę Michaela i akceptuje ją. Wniosek musi teraz zostać zatwierdzony przez dyrektora inżynierii, Tsvi Reiter.  
  
6. Tsvi Reiter chce przyspieszyć wniosek, więc umieszcza w komentarzu powiedzieć, że wniosek jest pilny i akceptuje go.  
  
7. Wniosek musi teraz zostać zatwierdzony przez dwóch menedżerów HR lub dyrektora generalnego. Dyrektor generalny, Brian Richard Goldstein, widzi pilną prośbę Tsvi. Działa on na wniosek, akceptując go, omijając w ten sposób zatwierdzenie przez dwóch menedżerów HR.  
  
8. Żądanie zostanie usunięte ze skrzynki odbiorczej Michaela i proces zatrudniania SDET już się rozpoczął.  
  
### <a name="start-resume-request"></a>Uruchom żądanie wznowienia  
  
1. Teraz stanowisko pracy oczekuje na zaksięgowanie w zewnętrznej witrynie sieci Web, w której można złożyć wniosek (można je zobaczyć klikając **łącze Oferty pracy).** Obecnie stanowisko to znajduje się u przedstawiciela DZIAŁU KADR, który jest odpowiedzialny za sfinalizowanie stanowiska i jego delegowanie.  
  
2. Hr chce edytować to stanowisko (klikając **łącze Edytuj),** ustawiając limit czasu 60 minut (w prawdziwym życiu może to być dni lub tygodnie). Limit czasu umożliwia wyjęcie stanowiska zadania z zewnętrznej witryny sieci Web zgodnie z określonym czasem.  
  
3. Po zapisaniu edytowane stanowisko pracy, pojawia się na **odbieranie wznawia** kartę (odśwież stronę sieci Web, aby zobaczyć nowe stanowisko pracy).  
  
### <a name="collecting-resumes"></a>Zbieranie życiorysów  
  
1. Stanowisko zadania powinno pojawić się w zewnętrznej witrynie sieci Web. Jako osoba zainteresowana ubieganiem się o pracę, możesz ubiegać się o to stanowisko i złożyć życiorys.  
  
2. Jeśli wrócisz do usługi Lista ofert pracy, możesz "wyświetlić życiorysy", które zostały zebrane do tej pory.  
  
3. Kadr może również przestać zbierać życiorysy (na przykład po zidentyfikowaniu właściwego kandydata).  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
  
1. Upewnij się, że używasz programu Visual Studio z uprawnieniami administratora.  
  
2. Jeśli rozwiązanie nie powiedzie się do kompilacji, sprawdź następujące czynności:  
  
    - Odwołanie do `ContosoHR` nie brakuje `InternalClient` w `CareersWebSite` projektach lub.  
  
3. Jeśli rozwiązanie nie zostanie wykonane, sprawdź następujące kwestie:  
  
    1. Wszystkie usługi są uruchomione.  
  
    2. Odwołania do usługi są aktualizowane.  
  
        1. Otwieranie folderu App_WebReferences  
  
        2. Kliknij prawym przyciskiem myszy pozycję **Contoso** i wybierz polecenie **Aktualizuj odwołania do sieci Web/usługi**.  
  
        3. Przebuduj rozwiązanie, naciskając klawisze CTRL+SHIFT+B w programie Visual Studio.  
  
## <a name="uninstalling"></a>Odinstalowywanie  
  
1. Usuń magazyn wystąpień programu SQL Server, uruchamiając plik Cleanup.bat, znajdujący się w folderze DbSetup.  
  
2. Usuń kod źródłowy z dysku twardego.
