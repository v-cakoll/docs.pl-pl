---
title: Proces zakupu firmowych
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: 34d9280fb1d4009aa729cb2eba55b817db9fff56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520045"
---
# <a name="corporate-purchase-process"></a>Proces zakupu firmowych
W tym przykładzie przedstawiono sposób tworzenia żądanie bardzo proste propozycje (RFP) na podstawie procesu zakupu z automatycznego najlepszym wyborem propozycji. Łączy <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>, i <xref:System.Activities.Statements.ForEach%601> i działań niestandardowych do tworzenia przepływu pracy, który reprezentuje procesu.  
  
 Ten przykład zawiera [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji klienckiej, która umożliwia interakcję z procesem jako uczestnicy różnych (jako oryginalnego żądający lub określonego dostawcy).  
  
## <a name="requirements"></a>Wymagania  
  
-   [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
-   [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Działania niestandardowe.  
  
-   Skład działań.  
  
-   Zakładki.  
  
-   Trwałość.  
  
-   Informatycznych trwałości.  
  
-   Śledzenie.  
  
-   Śledzenie.  
  
-   Hosting [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w różnych klientów ([!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sieci Web, aplikacji i WinForms aplikacji).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Opis procesu  
 Ten przykład przedstawia implementację programu Windows Workflow Foundation (WF) do zbierania propozycje od dostawców dla ogólnych firmy.  
  
1.  Pracownik X firmy tworzy żądanie propozycji (RFP).  
  
    1.  Typy pracowników RFP tytuł i opis.  
  
    2.  Pracownik wybiera dostawców, które chce zaprosić do przedstawienia propozycji.  
  
2.  Pracownik przesyła propozycji.  
  
    1.  Tworzone jest wystąpienie przepływu pracy.  
  
    2.  Przepływ pracy oczekuje dla wszystkich dostawców do przedstawienia ich propozycji.  
  
3.  Po otrzymaniu wszystkich propozycji, przepływ pracy iteruje odebrane propozycji i wybiera najlepszy.  
  
    1.  Każdy dostawca ma reputacji (w tym przykładzie przechowuje listę reputacji w VendorRepository.cs).  
  
    2.  Łączna wartość propozycji jest określana przez (wartość wpisana przez dostawcę) * (Dostawca użytkownika zarejestrowany reputacji) / 100.  
  
4.  Oryginalny żądający widoczny przesłanych propozycji. Najlepsze wniosku jest podana w specjalnej sekcji w raporcie.  
  
## <a name="process-definition"></a>Definicja procesu  
 Logika core próbki używa <xref:System.Activities.Statements.ParallelForEach%601> działanie, które oczekuje na ofert od poszczególnych dostawców (przy użyciu niestandardowego działania, która tworzy zakładki) i rejestruje propozycji dostawcy jako RFP (przy użyciu <xref:System.Activities.Statements.InvokeMethod> działania).  
  
 Próbka następnie iterację wszystkich odebranych propozycji przechowywane w `RfpRepository`, obliczanie skorygowaną wartość (przy użyciu <xref:System.Activities.Statements.Assign> działania i <xref:System.Activities.Expressions> działania), i jeśli skorygowaną wartość jest lepszym rozwiązaniem niż poprzednie najlepszą ofertę, Przypisuje nową wartość jako najlepsze oferty (przy użyciu <xref:System.Activities.Statements.If> i <xref:System.Activities.Statements.Assign> działań).  
  
## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie  
 Ten przykład zawiera następujące projekty.  
  
|Projekt|Opis|  
|-------------|-----------------|  
|Wspólne|Obiekty obiektów używane w ramach procesu (żądanie propozycji, dostawcy i propozycje dostawcy).|  
|WfDefinition|Definicja procesu (jako [!INCLUDE[wf1](../../../../includes/wf1-md.md)] program) i host (`PurchaseProcessHost`) używany przez aplikacje klienckie za tworzenie i używanie wystąpienia przepływu pracy procesu zakupu.|  
|Klient sieci Web|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Aplikacji klienckiej, która umożliwia użytkownikom tworzenie i brać udziału w wystąpień procesu zakupu. Niestandardowe hosta używa do interakcji z aparatu przepływu pracy.|  
|WinFormsClient|Aplikacja kliencka formularzy systemu Windows, który umożliwia użytkownikom tworzenie i brać udziału w wystąpień procesu zakupu. Niestandardowe hosta używa do interakcji z aparatu przepływu pracy.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Poniższa tabela zawiera opis najważniejszych pliki w projekcie WfDefinition.  
  
|Plik|Opis|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Interfejs dla hosta przepływu pracy.|  
|PurchaseProcessHost.cs|Implementacja hosta przepływu pracy. Host abstracts szczegóły środowiska uruchomieniowego przepływu pracy i jest używany we wszystkich aplikacjach klienta do ładowania, uruchomić i interakcyjnie `PurchaseProcess` wystąpienia przepływu pracy.|  
|PurchaseProcessWorkflow.cs|To działanie, które zawiera definicję przepływu pracy procesu zakupu (pochodną <xref:System.Activities.Activity>).<br /><br /> Działania, które pochodzą z <xref:System.Activities.Activity> tworzą funkcji przez łączenie istniejącego niestandardowe działania i działania z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Biblioteka działań. Składanie te działania jest najprostszym sposobem tworzenia funkcji niestandardowych.|  
|WaitForVendorProposal.cs|To niestandardowe działanie jest pochodną <xref:System.Activities.NativeActivity> i tworzy zakładki o nazwie, która musi zostać wznowiony później przez dostawcę podczas przesyłania propozycji.<br /><br /> Działań, które pochodzą z <xref:System.Activities.NativeActivity>, podobne do tych, które pochodzą z <xref:System.Activities.CodeActivity>, utworzenia ważnych funkcji przez zastąpienie <xref:System.Activities.NativeActivity.Execute%2A>, ale mają także dostęp do wszystkich funkcji środowiska uruchomieniowego przepływu pracy za pośrednictwem <xref:System.Activities.ActivityContext> który pobiera przekazany `Execute` metody. Ten kontekst został obsługę planowania i anulowanie podrzędnych utrwalić nie działań, Konfigurowanie strefy (w których środowisko uruchomieniowe nie zmieniają danych przepływu pracy, takich jak w obrębie transakcji atomic blokuje wykonywania), i <xref:System.Activities.Bookmark> (dojść do obiektów wznawianie wstrzymanych przepływów pracy).|  
|TrackingParticipant.cs|A <xref:System.Activities.Tracking.TrackingParticipant> czy odbiera wszystkie zdarzenia śledzenia i zapisuje je w pliku tekstowym.<br /><br /> Uczestników śledzenia są dodawane do wystąpienia przepływu pracy jako rozszerzenia.|  
|XmlWorkflowInstanceStore.cs|Niestandardowy <xref:System.Runtime.DurableInstancing.InstanceStore> który zapisuje aplikacji przepływu pracy do plików XML.|  
|XmlPersistenceParticipant.cs|Niestandardowy <xref:System.Activities.Persistence.PersistenceParticipant> wystąpienia żądania dla propozycji który zapisuje do pliku XML.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Klasy pomocy dla implementacji wzorca asynchronicznego w składnikach trwałości.|  
  
### <a name="common"></a>Wspólne  
 Poniższa tabela zawiera opis najważniejszych klas w typowych projektu.  
  
|Class|Opis|  
|-----------|-----------------|  
|Dostawcy|Dostawca, który przesyła propozycje propozycje w żądaniu.|  
|RequestForProposal|Żądanie propozycje (RFP) jest zaproszenie dla dostawców można przesyłać propozycje dotyczące określonego produktu lub usługi.|  
|VendorProposal|Wniosek dostawcy do konkretnych RFP.|  
|VendorRepository|Repozytorium dostawców. Ta implementacja zawiera kolekcję wystąpień dostawcy i metody udostępnianie tych wystąpień w pamięci.|  
|RfpRepository|Repozytorium żądania propozycji. Ta implementacja zawiera używa Linq do XML w pliku XML żądania dla propozycji generowane przez informatycznych trwałości kwerendy. Ta klasa implementuje [System.Runtime.Persistence.IDataViewMapper](https://msdn.microsoft.com/library/system.runtime.persistence.idataviewmapper(v=vs.110).aspx).|  
|IOHelper|Ta klasa obsługuje wszystkie problemy I O powiązanych z / (folderów, ścieżek itd.)|  
  
### <a name="web-client"></a>Klient sieci Web  
 Poniższa tabela zawiera opis najważniejszych stron sieci Web w projekcie sieci Web klienta.  
  
|Plik|Opis|  
|-|-|  
|CreateRfp.aspx|Tworzy i żąda nowej propozycji.|  
|Default.aspx|Przedstawia wszystkie aktywne i ukończone żądania propozycji.|  
|GetVendorProposal.aspx|Pobiera propozycję od dostawcy w żądaniu konkretnych propozycji. Ta strona jest używany tylko przez dostawców.|  
|ShowRfp.aspx|Pokaż wszystkie informacje dotyczące żądania propozycje (propozycje odebrane, dat, wartości i inne informacje). Ta strona jest używana tylko przez autora żądania dla propozycji.|  
  
### <a name="winforms-client"></a>WinForms klienta  
 Poniższa tabela zawiera opis najważniejszych formularzy w projekcie Win formularzy.  
  
|Formularz|Opis|  
|-|-|  
|NewRfp|Tworzy i żąda nowej propozycji.|  
|ShowProposals|Pokaż wszystkie aktywne i gotowe żądania propozycji. **Uwaga:** może zajść potrzeba kliknięcia przycisku **Odśwież** przycisk w interfejsie użytkownika, aby zobaczyć zmiany na tym ekranie po tworzenia lub modyfikowania żądania dla propozycji.|  
|SubmitProposal|Uzyskać propozycję od dostawcy w żądaniu konkretnych propozycji. To okno jest używany tylko przez dostawców.|  
|ViewRfp|Pokaż wszystkie informacje dotyczące żądania propozycje (propozycje odebrane, dat, wartości i inne informacje). To okno jest używana tylko przez autora żądania dla propozycji.|  
  
### <a name="persistence-files"></a>Trwałe pliki  
 W poniższej tabeli przedstawiono pliki wygenerowane przez dostawca trwałości (`XmlPersistenceProvider`) znajdują się w ścieżce folderu tymczasowego bieżący system (przy użyciu <xref:System.IO.Path.GetTempPath%2A>). Plik śledzenia jest tworzony w bieżącej ścieżce wykonywania.  
  
|Nazwa pliku|Opis|Ścieżka|  
|-|-|-|  
|rfps.XML|Plik XML z wszystkich żądań aktywne i gotowe do propozycji.|<xref:System.IO.Path.GetTempPath%2A>|  
|[identyfikator wystąpienia]|Ten plik zawiera wszystkie informacje dotyczące wystąpienia przepływu pracy.<br /><br /> Ten plik został wygenerowany przez implementację informatycznych trwałości (PersistenceParticipant w XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|.tracking [instanceId]|Plik tekstowy z wszystkich zdarzeń, które wystąpiły w konkretne wystąpienie.<br /><br /> Ten plik jest generowany przez TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|Plik śledzenia, generowane przez przepływ pracy, na podstawie parametrów konfiguracji w pliku App.config lub Web.config.|Bieżącej ścieżki wykonywania|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania PurchaseProcess.sln.  
  
2.  Aby wykonać projektu sieci Web klienta, otwórz **Eksploratora rozwiązań** i kliknij prawym przyciskiem myszy **klienta sieci Web** projektu. Wybierz **Ustaw jako projekt startowy**.  
  
3.  Aby wykonać projektu WinForms klienta, otwórz **Eksploratora rozwiązań** i kliknij prawym przyciskiem myszy **klienta WinForms** projektu. Wybierz **Ustaw jako projekt startowy**.  
  
4.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
5.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
### <a name="web-client-options"></a>Opcje klienta sieci Web  
  
-   **Utwórz nowy RFP**: tworzy nowe żądanie propozycje (RFP) i uruchomienie procesu zakupu przepływ pracy.  
  
-   **Odśwież**: Odświeża listę aktywnych i RFPs zostało zakończone w głównym oknie.  
  
-   **Widok**: Pokazuje zawartość RFP istniejących. Dostawcy mogą przesyłać propozycje ich (Jeśli zaproszenie lub nie została zakończona RFP).  
  
-   Widoku w postaci: Użytkownik ma dostęp RFP przy użyciu różnych tożsamości, wybierając odpowiednią uczestnika **wyświetlić jako** pola kombi w siatce RFPs aktywne.  
  
### <a name="winforms-client-options"></a>Opcje WinForms klienta  
  
-   **Utwórz RFP**: tworzy nowe żądanie propozycje (RFP) i uruchomienie procesu zakupu przepływ pracy.  
  
-   **Odśwież**: Odświeża listę aktywnych i RFPs zostało zakończone w głównym oknie.  
  
-   **Wyświetl RFP**: Pokazuje zawartość RFP istniejących. Dostawcy mogą przesyłać propozycje ich (Jeśli zaproszenie lub nie została zakończona RFP)  
  
-   **Połącz jako**: użytkownik ma dostęp RFP przy użyciu różnych tożsamości, wybierając odpowiednią uczestnika **wyświetlić jako** pola kombi w siatce RFPs aktywne.