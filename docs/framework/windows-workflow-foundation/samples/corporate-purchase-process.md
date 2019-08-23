---
title: Proces zakupów firmowych
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: d019c1915e691fcba00fa8f1b0884a898ce02fab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951527"
---
# <a name="corporate-purchase-process"></a>Proces zakupów firmowych
Ten przykład pokazuje, jak utworzyć bardzo podstawowe żądania zakupu na podstawie oferty (RFP) z automatycznym najlepszym wyborem oferty. Łączy <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>i iniestandardowąaktywnośćdotworzeniaprzepływupracy,któryreprezentujeproces.<xref:System.Activities.Statements.ForEach%601>

 Ten przykład zawiera aplikację kliencką ASP.NET, która umożliwia współpracę z procesem jako różnych uczestników (jako oryginalny obiekt żądający lub określony dostawca).

## <a name="requirements"></a>Wymagania

- Visual Studio 2012.

- [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Demonstracje

- Działania niestandardowe.

- Kompozycja działań.

- Zakładki.

- Trwałość.

- Trwałość schematized.

- Pochodzenia.

- Funkcja.

- Hosting [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w różnych klientach (ASP.NET aplikacje sieci Web i aplikacje WinForms).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Opis procesu  
 Ten przykład pokazuje implementację programu Windows Workflow Foundation (WF) do zbierania propozycji od dostawców dla firmy ogólnej.  
  
1. Pracownik firmy X tworzy żądanie oferty (RFP).  
  
    1. Typy pracowników w tytule i opisie RFP.  
  
    2. Pracownik wybiera dostawców, którzy chcą zaprosić do przesyłania propozycji.  
  
2. Pracownik przesyła propozycję.  
  
    1. Tworzone jest wystąpienie przepływu pracy.  
  
    2. Przepływ pracy czeka, aż wszyscy dostawcy przesłali swoje propozycje.  
  
3. Po otrzymaniu wszystkich propozycji przepływ pracy iteruje przez wszystkie otrzymane propozycje i wybiera najlepszy.  
  
    1. Każdy dostawca ma reputację (ten przykład zapisuje listę reputacji w VendorRepository.cs).  
  
    2. Łączna wartość propozycji jest określana przez (wartość wpisaną przez dostawcę) * (zarejestrowana reputacja dostawcy)/100.  
  
4. Oryginalny obiekt żądający może zobaczyć wszystkie przesłane wnioski. Najlepsza propozycja jest przedstawiona w specjalnej sekcji w raporcie.  
  
## <a name="process-definition"></a>Definicja procesu  
 Podstawowa logika przykładu używa <xref:System.Activities.Statements.ParallelForEach%601> działania, które czeka na oferty od każdego dostawcy (przy użyciu niestandardowego działania, które tworzy zakładkę), i rejestruje propozycję dostawcy jako RFP ( <xref:System.Activities.Statements.InvokeMethod> przy użyciu działania).  
  
 Następnie próbka wykonuje iterację we wszystkich odebranych propozycjach przechowywanych `RfpRepository`w, obliczaniu wartości skorygowanej ( <xref:System.Activities.Statements.Assign> przy użyciu <xref:System.Activities.Expressions> działania i działań), a jeśli skorygowana wartość jest lepsza niż poprzednia Najlepsza oferta, przypisuje nową wartość jako najlepszą ofertę (przy użyciu <xref:System.Activities.Statements.If> i <xref:System.Activities.Statements.Assign> działania).  
  
## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie  
 Ten przykład zawiera następujące projekty.  
  
|Projekt|Opis|  
|-------------|-----------------|  
|Wspólne|Obiekty jednostek używane w procesie (żądanie oferty, dostawcy i propozycja dostawcy).|  
|WfDefinition|Definicja procesu (jako [!INCLUDE[wf1](../../../../includes/wf1-md.md)] program) i hosta (`PurchaseProcessHost`) używanego przez aplikacje klienckie do tworzenia i używania wystąpień przepływu pracy procesu zakupu.|  
|Klient sieci Web|Aplikacja kliencka ASP.NET, która umożliwia użytkownikom tworzenie i uczestnictwo w wystąpieniach procesu zakupu. Używa niestandardowego hosta, aby móc korzystać z aparatu przepływu pracy.|  
|WinFormsClient|Windows Forms aplikacji klienckiej, która umożliwia użytkownikom tworzenie wystąpień procesu zakupu i uczestnictwo w nich. Używa niestandardowego hosta, aby móc korzystać z aparatu przepływu pracy.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Poniższa tabela zawiera opis najważniejszych plików w projekcie WfDefinition.  
  
|Plik|Opis|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Interfejs hosta przepływu pracy.|  
|PurchaseProcessHost.cs|Implementacja hosta dla przepływu pracy. Host stanowi streszczenie szczegółów środowiska uruchomieniowego przepływu pracy i jest używany we wszystkich aplikacjach klienckich do ładowania, uruchamiania i współdziałania z `PurchaseProcess` wystąpieniami przepływu pracy.|  
|PurchaseProcessWorkflow.cs|Działanie, które zawiera definicję przepływu pracy procesu zakupu (pochodzi z <xref:System.Activities.Activity>).<br /><br /> Działania, które pochodzą <xref:System.Activities.Activity> od funkcji redagowania przez złożenie istniejących działań niestandardowych i działań [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] z biblioteki działań. Montaż tych działań jest najbardziej podstawowym sposobem na tworzenie funkcji niestandardowych.|  
|WaitForVendorProposal.cs|To działanie niestandardowe pochodzi z <xref:System.Activities.NativeActivity> i tworzy nazwę zakładki, która musi zostać wznowiona później przez dostawcę podczas przesyłania propozycji.<br /><br /> Działania, które pochodzą <xref:System.Activities.NativeActivity>z, takie jak te, <xref:System.Activities.CodeActivity>które pochodzą z, tworzą bezwzględne funkcje przez zastępowanie <xref:System.Activities.NativeActivity.Execute%2A>, ale również mają dostęp do wszystkich funkcji środowiska uruchomieniowego przepływu pracy za pośrednictwem <xref:System.Activities.ActivityContext> , który pobiera przeszedł do `Execute` metody. Ten kontekst obsługuje planowanie i anulowanie działań podrzędnych, Konfigurowanie stref braku trwałego (bloków wykonywania, w których środowisko uruchomieniowe nie utrwala danych przepływu pracy, takich jak transakcje niepodzielne), oraz <xref:System.Activities.Bookmark> obiektów (uchwytów dla wznawianie wstrzymanych przepływów pracy).|  
|TrackingParticipant.cs|A <xref:System.Activities.Tracking.TrackingParticipant> który odbiera wszystkie zdarzenia śledzenia i zapisuje je w pliku tekstowym.<br /><br /> Śledzenie uczestników jest dodawane do wystąpienia przepływu pracy jako rozszerzenia.|  
|XmlWorkflowInstanceStore.cs|Niestandardowa <xref:System.Runtime.DurableInstancing.InstanceStore> , która zapisuje aplikacje przepływu pracy w plikach XML.|  
|XmlPersistenceParticipant.cs|Niestandardowa <xref:System.Activities.Persistence.PersistenceParticipant> , która zapisuje wystąpienie żądania zaprojektowania w pliku XML.|  
|AsyncResult.cs/CompletedAsyncResult.cs|Klasy pomocnika do implementowania wzorca asynchronicznego w składnikach trwałości.|  
  
### <a name="common"></a>Wspólne  
 Poniższa tabela zawiera opis najważniejszych klas w projekcie wspólnym.  
  
|Class|Opis|  
|-----------|-----------------|  
|Dostawcy|Dostawca, który przesyła wnioski w żądaniach dotyczących propozycji.|  
|RequestForProposal|Prośba o propozycje propozycji (RFP) to zaproszenie dla dostawców do przesyłania wniosków dotyczących określonego asortymentu lub usługi.|  
|VendorProposal|Propozycja przedstawiona przez dostawcę do konkretnej RFPu.|  
|VendorRepository|Repozytorium dostawców. Ta implementacja zawiera kolekcję wystąpień dostawcy i metod w celu udostępnienia tych wystąpień w pamięci.|  
|RfpRepository|Repozytorium żądań dla propozycji. Ta implementacja zawiera użycie LINQ to XML do wysyłania zapytań do pliku XML żądań dotyczących propozycji wygenerowanych przez trwałość schematized. |  
|IOHelper|Ta klasa obsługuje wszystkie problemy związane z we/wy (foldery, ścieżki itd.).|  
  
### <a name="web-client"></a>Klient sieci Web  
 Poniższa tabela zawiera opis najważniejszych stron sieci Web w projekcie klienta sieci Web.  
  
|Plik|Opis|  
|-|-|  
|CreateRfp.aspx|Tworzy i przesyła nowe żądanie dotyczące propozycji.|  
|Default.aspx|Pokazuje wszystkie aktywne i zakończone żądania dla propozycji.|  
|GetVendorProposal.aspx|Pobiera propozycję od dostawcy w konkretnym żądaniu na potrzeby składania propozycji. Ta strona jest używana tylko przez dostawców.|  
|ShowRfp.aspx|Pokaż wszystkie informacje na temat żądania propozycji (odebrane propozycje, daty, wartości i inne informacje). Ta strona jest używana tylko przez twórcę żądania propozycji.|  
  
### <a name="winforms-client"></a>Klient WinForms  
 Poniższa tabela zawiera opis najważniejszych formularzy w projekcie win Forms.  
  
|Formularz|Opis|  
|-|-|  
|NewRfp|Tworzy i przesyła nowe żądanie dotyczące propozycji.|  
|ShowProposals|Pokaż wszystkie aktywne i zakończone żądania dla propozycji. **Uwaga:**  Może być konieczne kliknięcie przycisku **Odśwież** w interfejsie użytkownika, aby zobaczyć zmiany na tym ekranie po utworzeniu lub zmodyfikowaniu żądania dla propozycji.|  
|SubmitProposal|Uzyskaj propozycję od dostawcy w konkretnym żądaniu na potrzeby składania ofert. To okno jest używane tylko przez dostawców.|  
|ViewRfp|Pokaż wszystkie informacje na temat żądania propozycji (odebrane propozycje, daty, wartości i inne informacje). To okno jest używane tylko przez twórcę żądania do składania wniosków.|  
  
### <a name="persistence-files"></a>Pliki trwałości  
 W poniższej tabeli przedstawiono pliki wygenerowane przez dostawcę trwałości (`XmlPersistenceProvider`) znajdują się w ścieżce do tymczasowego folderu systemowego (przy użyciu programu <xref:System.IO.Path.GetTempPath%2A>). Plik śledzenia jest tworzony w bieżącej ścieżce wykonania.  
  
|Nazwa pliku|Opis|Ścieżka|  
|-|-|-|  
|RFPs. XML|Plik XML ze wszystkimi aktywnymi i zakończonymi żądaniami dotyczącymi propozycji.|<xref:System.IO.Path.GetTempPath%2A>|  
|Identyfikator wystąpienia|Ten plik zawiera wszystkie informacje dotyczące wystąpienia przepływu pracy.<br /><br /> Ten plik jest generowany przez implementację trwałości schematized (PersistenceParticipant w XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceId].tracking|Plik tekstowy ze wszystkimi zdarzeniami, które wystąpiły w konkretnym wystąpieniu.<br /><br /> Ten plik jest generowany przez TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess. Tracing. TraceLog. txt|Plik śledzenia generowany przez przepływ pracy na podstawie parametrów konfiguracyjnych w plikach App. config lub Web. config.|Bieżąca ścieżka wykonywania|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania PurchaseProcess. sln.  
  
2. Aby wykonać projekt klienta sieci Web, Otwórz **Eksplorator rozwiązań** i kliknij prawym przyciskiem myszy projekt **klienta sieci Web** . Wybierz pozycję **Ustaw jako projekt startowy**.  
  
3. Aby wykonać projekt klienta WinForms, Otwórz **Eksplorator rozwiązań** i kliknij prawym przyciskiem myszy projekt **WinForms Client** . Wybierz pozycję **Ustaw jako projekt startowy**.  
  
4. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
5. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
### <a name="web-client-options"></a>Opcje klienta sieci Web  
  
- **Utwórz nowy RFP**: Tworzy nowe żądanie dotyczące propozycji (RFP) i uruchamia przepływ pracy procesu zakupu.  
  
- **Odśwież**: Odświeża listę aktywnych i zakończonych RFPs w oknie głównym.  
  
- **Widok**: Pokazuje zawartość istniejącego RFP. Dostawcy mogą przesyłać swoje propozycje (jeśli zaproszeni lub RFP nie zostały zakończone).  
  
- Wyświetl jako: Użytkownik może uzyskać dostęp do RFP przy użyciu różnych tożsamości, wybierając żądanego uczestnika w **widoku** pole kombi w aktywnej siatce RFPs.  
  
### <a name="winforms-client-options"></a>Opcje klienta WinForms  
  
- **Utwórz RFP**: Tworzy nowe żądanie dotyczące propozycji (RFP) i uruchamia przepływ pracy procesu zakupu.  
  
- **Odśwież**: Odświeża listę aktywnych i zakończonych RFPs w oknie głównym.  
  
- **Wyświetl RFP**: Pokazuje zawartość istniejącego RFP. Dostawcy mogą przesyłać swoje propozycje (jeśli nie zakończył się zaproszenie lub RFP)  
  
- **Połącz jako**: Użytkownik może uzyskać dostęp do RFP przy użyciu różnych tożsamości, wybierając żądanego uczestnika w **widoku** pole kombi w aktywnej siatce RFPs.
