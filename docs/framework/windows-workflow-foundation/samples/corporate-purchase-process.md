---
title: Proces zakupów firmowych
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: 346d4b58d8d59c416fbdd51f5fbe02b54f9e078f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313336"
---
# <a name="corporate-purchase-process"></a>Proces zakupów firmowych
W tym przykładzie przedstawiono sposób tworzenia bardzo podstawowe żądania dla procesu zakupu propozycji (RFP) na podstawie z automatycznego najlepszym wyborem propozycji. Łączy ona <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>, i <xref:System.Activities.Statements.ForEach%601> i niestandardowe działanie, aby utworzyć przepływ pracy, który reprezentuje proces.

 Ten przykład zawiera [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikację kliencką, która umożliwia wchodzenie w interakcje z procesem jako uczestnicy różnych (jako oryginalnego zleceniodawcy lub określonego dostawcy).

## <a name="requirements"></a>Wymagania

-   Visual Studio 2012.

-   [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Demonstracje

-   Działania niestandardowe.

-   Kompozycja działań.

-   Zakładki.

-   Trwałość.

-   Trwałość informatycznych.

-   Śledzenie.

-   Do śledzenia.

-   Hosting [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w różnych klientów ([!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji sieci Web i aplikacji formularzy WinForms).

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Opis procesu  
 Niniejszy przykład pokazuje implementację programu Windows Workflow Foundation (WF) w celu zbierania propozycji od dostawców na potrzeby ogólnego firmy.  
  
1. Pracownik firmy X tworzy żądanie propozycji (RFP).  
  
    1.  Typy pracowników RFP tytuł i opis.  
  
    2.  Pracownik wybiera dostawców, które chce zaprosić do przesyłania propozycji.  
  
2. Pracownik przesyła propozycji.  
  
    1.  Tworzone jest wystąpienie przepływu pracy.  
  
    2.  Przepływ pracy czeka, aż wszyscy dostawcy do przedstawienia ich propozycji.  
  
3. Po otrzymaniu wszystkich propozycji przepływ pracy wykonuje iterację przez wszystkie odebrane propozycje i wybiera najlepszą z nich.  
  
    1.  Każdy dostawca ma reputację (w tym przykładzie są przechowywane na liście reputację w VendorRepository.cs).  
  
    2.  Łączna wartość propozycji jest określana przez (wartość wpisana w przez dostawcę) * (Dostawca w zarejestrowany reputacji) / 100.  
  
4. Oryginalny osoby żądającej widoczne przesłane propozycji. Najlepszą propozycję są prezentowane w specjalnej sekcji w raporcie.  
  
## <a name="process-definition"></a>Definicji procesu  
 Podstawowe zasady logiczne próbki używa <xref:System.Activities.Statements.ParallelForEach%601> działanie, które oczekuje na oferty z każdego dostawcy (przy użyciu niestandardowego działania, który tworzy zakładki) i rejestruje propozycji dostawcy jako RFP (przy użyciu <xref:System.Activities.Statements.InvokeMethod> działanie).  
  
 Przykład następnie iterację przez wszystkie odebrane propozycji przechowywane w `RfpRepository`, obliczania skorygowany wartości (przy użyciu <xref:System.Activities.Statements.Assign> działania i <xref:System.Activities.Expressions> działania), i jeśli skorygowaną wartość jest lepsza niż poprzedniej ofercie najlepsze, Przypisuje nową wartość jako najlepszą ofertę (przy użyciu <xref:System.Activities.Statements.If> i <xref:System.Activities.Statements.Assign> działań).  
  
## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie  
 Ten przykład zawiera następujące projekty.  
  
|Projekt|Opis|  
|-------------|-----------------|  
|Wspólne|Obiekty jednostki, używane w ramach procesu (żądanie propozycji, dostawcy i propozycje dostawcy).|  
|WfDefinition|Definicja procesu (jako [!INCLUDE[wf1](../../../../includes/wf1-md.md)] program) i host (`PurchaseProcessHost`) używane przez aplikacje klienckie do tworzenia i używania wystąpienia przepływu pracy procesu zakupu.|  
|Klient sieci Web|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Aplikację kliencką, która umożliwia użytkownikom tworzenia i uczestniczyć w procesie zakupu wystąpień. Używa innych utworzonych niestandardowo hosta do interakcji z aparatu przepływu pracy.|  
|WinFormsClient|Aplikacja kliencka Windows Forms, który umożliwia użytkownikom tworzenia i uczestniczyć w procesie zakupu wystąpień. Używa innych utworzonych niestandardowo hosta do interakcji z aparatu przepływu pracy.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Poniższa tabela zawiera opis najważniejszych pliki w projekcie WfDefinition.  
  
|Plik|Opis|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Interfejs dla hosta przepływu pracy.|  
|PurchaseProcessHost.cs|Implementacja hosta przepływu pracy. Host abstrakcję szczegółów środowiska wykonawczego przepływów pracy i jest używany w aplikacjach klienckich do ładowania, uruchamiania i interakcję z `PurchaseProcess` wystąpienia przepływu pracy.|  
|PurchaseProcessWorkflow.cs|Działanie, które zawiera definicję przepływu pracy procesu zakupu (pochodzi od klasy <xref:System.Activities.Activity>).<br /><br /> Działania, które wynikają z <xref:System.Activities.Activity> compose funkcji przez łączenie istniejących niestandardowe działania i działania z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] biblioteki działań. Złożenia te działania to najprostszy sposób tworzenia funkcji niestandardowych.|  
|WaitForVendorProposal.cs|To niestandardowe działanie jest pochodną <xref:System.Activities.NativeActivity> i tworzy nazwany zakładki, która musi zostać wznowiony później przez dostawcę podczas przesyłania propozycji.<br /><br /> Działań, które wynikają z <xref:System.Activities.NativeActivity>, podobne do tych, które wynikają z <xref:System.Activities.CodeActivity>, utworzenia imperatywne funkcji przez zastąpienie <xref:System.Activities.NativeActivity.Execute%2A>, również ma dostęp do wszystkich funkcji środowiska wykonawczego przepływów pracy za pośrednictwem <xref:System.Activities.ActivityContext> , które pobiera przekazany do `Execute` metody. Ten kontekst obsługuje planowanie i anulowanie podrzędnych utrwalić nie działań, Konfigurowanie strefy (w których środowisko uruchomieniowe nie pozostania danych przepływu pracy, takich jak transakcje niepodzielne bloki wykonywania), a <xref:System.Activities.Bookmark> obiektów (uchwyty wznawianie wstrzymana przepływów pracy).|  
|TrackingParticipant.cs|A <xref:System.Activities.Tracking.TrackingParticipant> który odbiera wszystkie zdarzenia śledzenia i zapisuje je do pliku tekstowego.<br /><br /> Śledzenie uczestników są dodawane do wystąpienia przepływu pracy jako rozszerzenia.|  
|XmlWorkflowInstanceStore.cs|Niestandardowy <xref:System.Runtime.DurableInstancing.InstanceStore> który zapisuje aplikacji przepływu pracy z plikami XML.|  
|XmlPersistenceParticipant.cs|Niestandardowy <xref:System.Activities.Persistence.PersistenceParticipant> wystąpienia żądania dla propozycji który zapisuje do pliku XML.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Klasy pomocnika do implementowania wzorca asynchronicznego w składnikach trwałości.|  
  
### <a name="common"></a>Wspólne  
 Poniższa tabela zawiera opis najważniejszych klasy w projekcie wspólnej.  
  
|Class|Opis|  
|-----------|-----------------|  
|Dostawcy|Dostawca, który przesyła propozycje propozycji w żądaniu.|  
|RequestForProposal|Żądanie do składania wniosków (RFP) to zaproszenie dla dostawców, którzy mają możliwość przesyłania propozycji dla określonego produktu lub usługi.|  
|VendorProposal|Wniosek dostawcy do konkretnych RFP.|  
|VendorRepository|Repozytorium dostawców. Ta implementacja zawiera kolekcję w pamięci wystąpień dostawcy i metod udostępniania tych wystąpień.|  
|RfpRepository|Repozytorium żądania do składania wniosków. Ta implementacja zawiera używa Linq to XML w pliku XML żądania dla propozycji generowane przez informatycznych trwałości kwerendy. |  
|IOHelper|Ta klasa obsługuje wszystkie problemy I dotyczących wejścia/wyjścia (folderów, ścieżek i itd.)|  
  
### <a name="web-client"></a>Klient sieci Web  
 Poniższa tabela zawiera opis najważniejszych stron sieci Web w projekcie sieci Web klienta.  
  
|Plik|Opis|  
|-|-|  
|CreateRfp.aspx|Tworzy i przesyła nowe żądanie do składania wniosków.|  
|Default.aspx|Pokazuje wszystkich aktywnych i zakończonych żądań do składania wniosków.|  
|GetVendorProposal.aspx|Pobiera propozycji od dostawcy w żądaniu konkretnych propozycji. Ta strona jest używane tylko przez dostawców.|  
|ShowRfp.aspx|Pokaż wszystkie informacje o żądaniu konkurs (propozycji odebrane, dat, wartości i innych informacji). Ta strona jest używana tylko przez autora żądania dla propozycji.|  
  
### <a name="winforms-client"></a>Klient WinForms  
 Poniższa tabela zawiera opis najważniejszych formularze w projekcie Windows Forms.  
  
|Formularz|Opis|  
|-|-|  
|NewRfp|Tworzy i przesyła nowe żądanie do składania wniosków.|  
|ShowProposals|Pokaż wszystkich aktywnych i zakończonych żądań do składania wniosków. **Uwaga:**  Może być konieczne kliknięcie **Odśwież** przycisku w interfejsie użytkownika, aby zobaczyć zmiany w tym ekranie, po utworzeniu lub zmodyfikować żądanie dla propozycji.|  
|SubmitProposal|Uzyskać propozycji od dostawcy w żądaniu konkretnych propozycji. To okno jest używane tylko przez dostawców.|  
|ViewRfp|Pokaż wszystkie informacje o żądaniu konkurs (propozycji odebrane, dat, wartości i innych informacji). To okno jest używana tylko przez autora żądania do składania wniosków.|  
  
### <a name="persistence-files"></a>Trwałe pliki  
 W poniższej tabeli przedstawiono pliki generowane przez dostawcę trwałości (`XmlPersistenceProvider`) znajdują się w ścieżce folderu tymczasowego bieżącego systemu (przy użyciu <xref:System.IO.Path.GetTempPath%2A>). Plik śledzenia jest tworzony w bieżącej ścieżce wykonywania.  
  
|Nazwa pliku|Opis|Ścieżka|  
|-|-|-|  
|rfps.xml|Plik XML z wszystkich aktywnych i zakończonych żądań do składania wniosków.|<xref:System.IO.Path.GetTempPath%2A>|  
|[identyfikator instanceid]|Ten plik zawiera wszystkie informacje na temat wystąpienia przepływu pracy.<br /><br /> Ten plik został wygenerowany przez implementację informatycznych trwałości (PersistenceParticipant w XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceId].tracking|Plik tekstowy, wszystkie zdarzenia, które wystąpiły w ciągu konkretne wystąpienie.<br /><br /> Ten plik jest generowany przez TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|Plik śledzenia generowane przez przepływ pracy na podstawie parametrów konfiguracji w pliku App.config lub Web.config plików.|Bieżąca ścieżka wykonywania|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania PurchaseProcess.sln.  
  
2. Aby wykonać projektu sieci Web klienta, otwórz **Eksploratora rozwiązań** i kliknij prawym przyciskiem myszy **klienta sieci Web** projektu. Wybierz **Ustaw jako projekt startowy**.  
  
3. Aby wykonać projekt klienta WinForms, otwórz **Eksploratora rozwiązań** i kliknij prawym przyciskiem myszy **WinForms klienta** projektu. Wybierz **Ustaw jako projekt startowy**.  
  
4. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
5. Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
### <a name="web-client-options"></a>Opcje klienta sieci Web  
  
-   **Utwórz nowy RFP**: Tworzy nowe żądanie propozycji (RFP) i rozpoczyna proces zakupu przepływu pracy.  
  
-   **Odśwież**: Odświeża listę aktywnych i RFPs zostało zakończone w głównym oknie.  
  
-   **Widok**: Zostanie wyświetlona zawartość istniejącego RFP. Dostawcy mogą przesyłać propozycje ich (Jeśli zaproszenie lub RFP nie zostało zakończone.).  
  
-   Wyświetl jako: Użytkownik ma dostęp RFP przy użyciu różnych tożsamości, wybierając odpowiednią uczestnikiem **Wyświetl jako** pola kombi w siatce RFPs active.  
  
### <a name="winforms-client-options"></a>Opcje klienta WinForms  
  
-   **Utwórz RFP**: Tworzy nowe żądanie propozycji (RFP) i rozpoczyna proces zakupu przepływu pracy.  
  
-   **Odśwież**: Odświeża listę aktywnych i RFPs zostało zakończone w głównym oknie.  
  
-   **Wyświetl RFP**: Zostanie wyświetlona zawartość istniejącego RFP. Dostawcy mogą przesyłać propozycje ich (Jeśli zaproszenie lub RFP nie zostało zakończone.)  
  
-   **Połącz się jako**: Użytkownik ma dostęp RFP przy użyciu różnych tożsamości, wybierając odpowiednią uczestnikiem **Wyświetl jako** pola kombi w siatce RFPs active.
