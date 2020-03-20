---
title: Proces zakupów firmowych
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: 93cfc3546fc312f046c4a5e1dd63dfb357f143c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182868"
---
# <a name="corporate-purchase-process"></a>Proces zakupów firmowych
W tym przykładzie pokazano, jak utworzyć bardzo podstawowy proces zakupu oparty na zaproszeniu do składania wniosków (RFP) z automatycznym wyborem najlepszych propozycji. Łączy <xref:System.Activities.Statements.Parallel>program <xref:System.Activities.Statements.ParallelForEach%601>, <xref:System.Activities.Statements.ForEach%601> i działanie niestandardowe, aby utworzyć przepływ pracy, który reprezentuje proces.

 Ten przykład zawiera ASP.NET aplikacji klienckiej, która umożliwia interakcję z procesem jako różnych uczestników (jako oryginalny żądający lub określonego dostawcy).

## <a name="requirements"></a>Wymagania

- Visual Studio 2012.

- [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Demonstracje

- Działania niestandardowe.

- Skład działalności.

- Zakładki.

- Trwałości.

- Schematyczna trwałość.

- Śledzenia.

- Śledzenia.

- Hosting [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w różnych klientach (ASP.NET aplikacji sieci Web i aplikacji WinForms).

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Opis procesu  
 W tym przykładzie przedstawiono implementację programu Windows Workflow Foundation (WF) w celu zebrania propozycji od dostawców dla firmy ogólnej.  
  
1. Pracownik firmy X tworzy wniosek o propozycję (RFP).  
  
    1. Typy pracownika w tytule i opisie rfp.  
  
    2. Pracownik wybiera dostawców, których chce zaprosić do przesyłania propozycji.  
  
2. Pracownik składa propozycję.  
  
    1. Zostanie utworzone wystąpienie przepływu pracy.  
  
    2. Przepływ pracy oczekuje na wszystkich dostawców do przesłania swoich propozycji.  
  
3. Po otrzymaniu wszystkich propozycji przepływ pracy iteruje przez wszystkie otrzymane propozycje i wybiera najlepszą.  
  
    1. Każdy dostawca ma reputację (ten przykład przechowuje listę reputacji w VendorRepository.cs).  
  
    2. Całkowita wartość propozycji jest określana przez (Wartość wpisywany przez dostawcę) * (Zarejestrowana reputacja dostawcy) / 100.  
  
4. Pierwotny wnioskodawca może zobaczyć wszystkie złożone wnioski. Najlepsza propozycja przedstawiona jest w specjalnej sekcji sprawozdania.  
  
## <a name="process-definition"></a>Definicja procesu  
 Podstawowa logika przykładu <xref:System.Activities.Statements.ParallelForEach%601> używa działania, które czeka na oferty od każdego dostawcy (przy użyciu działania niestandardowego, które tworzy <xref:System.Activities.Statements.InvokeMethod> zakładkę) i rejestruje propozycję dostawcy jako rfp (przy użyciu działania).  
  
 Następnie próbka iteruje wszystkie otrzymane propozycje `RfpRepository`przechowywane w , obliczając <xref:System.Activities.Statements.Assign> skorygowaną <xref:System.Activities.Expressions> wartość (przy użyciu działania i działań), a jeśli skorygowana wartość jest <xref:System.Activities.Statements.If> lepsza <xref:System.Activities.Statements.Assign> niż poprzednia najlepsza oferta, przypisuje nową wartość jako najlepszą ofertę (przy użyciu i działaniach).  
  
## <a name="projects-in-this-sample"></a>Projekty w tej próbie  
 Ten przykład zawiera następujące projekty.  
  
|Project|Opis|  
|-------------|-----------------|  
|Wspólne|Obiekty encji używane w ramach procesu (Żądanie propozycji, Dostawca i Propozycja dostawcy).|  
|WfDefinition (WfDefinition)|Definicja procesu (jako [!INCLUDE[wf1](../../../../includes/wf1-md.md)] programu) i`PurchaseProcessHost`hosta ( ) używanego przez aplikacje klienckie do tworzenia i używania wystąpień przepływu pracy procesu zakupu.|  
|Webclient|ASP.NET aplikacja kliencka, która umożliwia użytkownikom tworzenie i uczestniczenie w wystąpieniach procesu zakupu. Używa hosta utworzonego na zamówienie do interakcji z aparatem przepływu pracy.|  
|WinFormsClient (WinFormsClient)|Aplikacja kliencka Windows Forms, która umożliwia użytkownikom tworzenie i uczestniczenie w wystąpieniach procesu zakupu. Używa hosta utworzonego na zamówienie do interakcji z aparatem przepływu pracy.|  
  
### <a name="wfdefinition"></a>WfDefinition (WfDefinition)  
 Poniższa tabela zawiera opis najważniejszych plików w projekcie WfDefinition.  
  
|Plik|Opis|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Interfejs dla hosta przepływu pracy.|  
|PurchaseProcessHost.cs|Implementacja hosta dla przepływu pracy. Host abstrakcji szczegóły środowiska wykonawczego przepływu pracy i jest używany we wszystkich aplikacjach `PurchaseProcess` klienckich do ładowania, uruchamiania i interakcji z wystąpień przepływu pracy.|  
|PurchaseProcessWorkflow.cs|Działanie zawierające definicję przepływu pracy Proces zakupu (pochodzi od <xref:System.Activities.Activity>).<br /><br /> Działania, które wynikają z <xref:System.Activities.Activity> funkcji tworzenia przez łączenie istniejących działań [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] niestandardowych i działań z biblioteki działań. Składanie tych działań jest najbardziej podstawowym sposobem tworzenia funkcji niestandardowych.|  
|WaitForVendorProposal.cs|To działanie niestandardowe <xref:System.Activities.NativeActivity> pochodzi z i tworzy nazwany zakładki, które muszą zostać wznowione później przez dostawcę podczas przesyłania propozycji.<br /><br /> Działania, które wynikają z <xref:System.Activities.NativeActivity>, jak <xref:System.Activities.CodeActivity>te, które wynikają <xref:System.Activities.NativeActivity.Execute%2A>z , tworzenie funkcji imperatywu przez zastąpienie , <xref:System.Activities.ActivityContext> ale również `Execute` mają dostęp do wszystkich funkcji środowiska wykonawczego przepływu pracy za pośrednictwem, który zostanie przekazany do metody. Ten kontekst obsługuje planowanie i anulowanie działań podrzędnych, konfigurowanie stref bez utrwalenia (bloków wykonywania, podczas których środowisko wykonawcze <xref:System.Activities.Bookmark> nie utrwali danych przepływu pracy, takich jak w ramach transakcji niepodzielnych) i obiektów (dojścia do ponownego uruchamiania wstrzymanych przepływów pracy).|  
|TrackingParticipant.cs|A, <xref:System.Activities.Tracking.TrackingParticipant> który odbiera wszystkie zdarzenia śledzenia i zapisuje je w pliku tekstowym.<br /><br /> Uczestnicy śledzenia są dodawane do wystąpienia przepływu pracy jako rozszerzenia.|  
|XmlWorkflowInstanceStore.cs|Niestandardowy, <xref:System.Runtime.DurableInstancing.InstanceStore> który zapisuje aplikacje przepływu pracy w plikach XML.|  
|XmlPersistenceParticipant.cs|Niestandardowe, <xref:System.Activities.Persistence.PersistenceParticipant> które zapisuje wystąpienie żądania propozycji w pliku XML.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Klasy pomocnicze do implementowania wzorca asynchroniczne w składnikach trwałości.|  
  
### <a name="common"></a>Wspólne  
 Poniższa tabela zawiera opis najważniejszych klas w projekcie Wspólne.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|Dostawca|Dostawca, który przesyła propozycje w żądaniu propozycji.|  
|WniosekZapropozycję|Wniosek o propozycje (RFP) jest zaproszeniem dla dostawców do składania propozycji dotyczących określonego towaru lub usługi.|  
|DostawcaPropozycja|Wniosek złożony przez sprzedawcę do konkretnej rfp.|  
|DostawcaPozycja|Repozytorium dostawców. Ta implementacja zawiera kolekcję w pamięci wystąpień dostawcy i metody insektowania tych wystąpień.|  
|RfpRepository|Repozytorium wniosków o propozycje. Ta implementacja zawiera używa Linq do XML do kwerendy pliku XML żądań propozycji generowanych przez schematyzowany trwałości. |  
|IOHelper|Ta klasa obsługuje wszystkie problemy związane z we/wy (foldery, ścieżki i tak dalej.)|  
  
### <a name="web-client"></a>Klient sieci Web  
 Poniższa tabela zawiera opis najważniejszych stron sieci Web w projekcie klienta sieci Web.  
  
|Plik|Opis|  
|-|-|  
|CreateRfp.aspx|Tworzy i przesyła nowe żądanie propozycji.|  
|Default.aspx|Pokazuje wszystkie aktywne i ukończone wnioski o propozycje.|  
|GetVendorProposal.aspx|Pobiera propozycję od dostawcy w konkretnym żądaniu propozycji. Ta strona jest używana tylko przez dostawców.|  
|ShowRfp.aspx|Pokaż wszystkie informacje o żądaniu propozycji (otrzymane propozycje, daty, wartości i inne informacje). Ta strona jest używana tylko przez twórcę żądania propozycji.|  
  
### <a name="winforms-client"></a>Klient WinForms  
 Poniższa tabela zawiera opis najważniejszych formularzy w projekcie Formularze win.  
  
|Formularz|Opis|  
|-|-|  
|Okręg wyborczy NewRfp|Tworzy i przesyła nowe żądanie propozycji.|  
|Propozycje pokazów|Pokaż wszystkie aktywne i gotowe żądania propozycji. **Uwaga:**  Może być konieczne kliknięcie przycisku **Odśwież** w interfejsie użytkownika, aby zobaczyć zmiany na tym ekranie po utworzeniu lub zmodyfikowaniu żądania propozycji.|  
|SubmitProposal|Uzyskaj propozycję od dostawcy w konkretnym żądaniu propozycji. To okno jest używane tylko przez dostawców.|  
|ViewRfp (WidokRfp)|Pokaż wszystkie informacje o żądaniu propozycji (otrzymane propozycje, daty, wartości i inne informacje). To okno jest używane tylko przez twórcę żądania propozycji.|  
  
### <a name="persistence-files"></a>Pliki trwałości  
 W poniższej tabeli przedstawiono pliki`XmlPersistenceProvider`generowane przez dostawcę trwałości ( ) znajdują <xref:System.IO.Path.GetTempPath%2A>się w ścieżce folderu tymczasowego bieżącego systemu (za pomocą ). Plik obrysowywania jest tworzony w bieżącej ścieżce wykonywania.  
  
|Nazwa pliku|Opis|Ścieżka|  
|-|-|-|  
|plik rfps.xml|Plik XML ze wszystkimi aktywnymi i gotowymi żądaniami propozycji.|<xref:System.IO.Path.GetTempPath%2A>|  
|[instancja]|Ten plik zawiera wszystkie informacje o wystąpieniu przepływu pracy.<br /><br /> Ten plik jest generowany przez implementacji trwałości schematyzowanej (PersistenceParticipant w XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceId].śledzenie|Plik tekstowy ze wszystkimi zdarzeniami, które wystąpiły w konkretnym wystąpieniu.<br /><br /> Ten plik jest generowany przez TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|Plik śledzenia wygenerowany przez przepływ pracy na podstawie parametrów konfiguracji w plikach App.config lub Web.config.|Bieżąca ścieżka wykonywania|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tej próbki  
  
1. Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania PurchaseProcess.sln.  
  
2. Aby wykonać projekt klienta sieci Web, otwórz **Eksploratora rozwiązań** i kliknij prawym przyciskiem myszy projekt **klienta sieci Web.** Wybierz **pozycję Ustaw jako projekt startowy**.  
  
3. Aby wykonać projekt Klienta WinForms, otwórz **Eksploratora rozwiązań** i kliknij prawym przyciskiem myszy projekt **Klienta WinForms.** Wybierz **pozycję Ustaw jako projekt startowy**.  
  
4. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.  
  
5. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.  
  
### <a name="web-client-options"></a>Opcje klienta sieci Web  
  
- **Utwórz nową rfp:** Tworzy nowe żądanie propozycji (RFP) i uruchamia przepływ pracy procesu zakupu.  
  
- **Odśwież :** Odświeża listę aktywnych i gotowych RPP w oknie głównym.  
  
- **Widok**: Pokazuje zawartość istniejącego rfp. Dostawcy mogą przesyłać swoje propozycje (jeśli zaproszenie lub rfp nie jest zakończona).  
  
- Widok jako: Użytkownik może uzyskać dostęp do rfp przy użyciu różnych tożsamości, wybierając żądanego uczestnika w **polu Widok jako** kombi w aktywnej siatce RPP.  
  
### <a name="winforms-client-options"></a>Opcje klienta WinForms  
  
- **Tworzenie rfp:** Tworzy nowe żądanie propozycji (RFP) i uruchamia przepływ pracy procesu zakupu.  
  
- **Odśwież :** Odświeża listę aktywnych i gotowych RPP w oknie głównym.  
  
- **Wyświetl RFP**: Pokazuje zawartość istniejącego rfp. Dostawcy mogą składać swoje propozycje (jeśli zaproszenie lub rfp nie jest zakończona)  
  
- **Połącz jako:** Użytkownik może uzyskać dostęp do rfp przy użyciu różnych tożsamości, wybierając żądanego uczestnika w **polu Widok jako** kombi w aktywnej siatce RPP.
