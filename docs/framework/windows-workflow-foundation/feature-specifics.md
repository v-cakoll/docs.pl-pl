---
title: "Windows Workflow Foundation funkcji charakterystykę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e7a223248b574e30c266c3c9ac66bf317f1d19f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation funkcji charakterystykę
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]Dodaje liczbę funkcji do systemu Windows Workflow Foundation. Ten dokument opisano kilka nowych funkcji i zwraca szczegółowe informacje o scenariuszach, w których mogą być przydatne.  
  
## <a name="messaging-activities"></a>Działania dotyczące komunikatów  
 Działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) są używane do wysyłania i odbierania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] komunikaty z przepływu pracy.  <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.SendReply> działania są używane do formularza [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] operacja uwidocznionego za pośrednictwem WSDL, podobnie jak standardowy usługi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług sieci web.  <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.ReceiveReply> są używane do pracy z usługą sieci web podobny do programu WCF <xref:System.ServiceModel.ChannelFactory>; **Dodaj odwołanie do usługi** istnieje również środowiska dla programu Workflow Foundation generuje wstępnie skonfigurowane działania.  
  
### <a name="getting-started-with-messaging-activities"></a>Wprowadzenie do działania obsługi wiadomości  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], Utwórz projekt aplikacji usługi przepływu pracy WCF. A <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> pary zostaną umieszczone w obszarze roboczym.  
  
-   Kliknij prawym przyciskiem myszy na projekt i wybierz **Dodaj odwołanie do usługi**.  Wskaż istniejący opis WSDL usługi sieci web, a następnie kliknij przycisk **OK**.  Skompilowanie projektu do wyświetlenia wygenerowanego działania (implementowane za pomocą <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply>) z przybornika.  
  
-   Przykłady dotyczące tych działań można znaleźć w następujących sekcjach:  
  
    -   Basic: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scenariusze: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
-   [Dokumentacja koncepcyjna](http://go.microsoft.com/fwlink/?LinkId=204801)  
  
-   [Dokumentacja projektanta działań do obsługi komunikatów](http://go.microsoft.com/fwlink/?LinkId=204802)  
  
### <a name="messaging-activities-example-scenario"></a>Działania przykładowy scenariusz do obsługi komunikatów  
 A `BestPriceFinder` usługi uwidacznia do wielu linii lotniczych usług można znaleźć najlepszej biletów dla określonej trasy.  Realizacji tego scenariusza wymaga przy użyciu działań komunikat mógł odebrać żądanie cen, pobrać ceny z usługami zaplecza i odpowiadania na żądania cen o najlepszej.  On również wymagają można używać do tworzenia logiki biznesowej obliczania najlepszej innych działań out-of-box.  
  
## <a name="workflowservicehost"></a>Obiekt WorkflowServiceHost  
 <xref:System.ServiceModel.WorkflowServiceHost> Jest host out-of-box przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] wiadomości (mimo że przepływy pracy nie są wymagane do obsługi komunikatów znajdować).  Integruje się również z utrwalania, śledzenia i kontroli wystąpienia za pomocą zestawu zachowania usługi.  Podobnie jak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]w <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> mogą być samodzielnie hostowana w aplikacji console/WinForms/WPF lub usługa systemu Windows lub hostowanych w sieci web (w formacie .xamlx) w usługach IIS lub WAS.  
  
### <a name="getting-started-with-workflow-service-host"></a>Wprowadzenie do korzystania z hosta usługi przepływu pracy  
  
-   W programie Visual Studio 2010, należy utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projekt aplikacji usługi przepływu pracy: ten projekt będzie można skonfigurować do używania <xref:System.ServiceModel.WorkflowServiceHost> w środowisku hosta sieci web.  
  
-   Aby hosta przepływu pracy z systemem innym niż wiadomości, Dodaj niestandardowy <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> który spowoduje utworzenie wystąpienia na podstawie wiadomości.  
  
-   Wystąpienia przepływu pracy mogą być kontrolowane (np. wstrzymane lub przerwane) przez dodanie <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> do <xref:System.ServiceModel.WorkflowServiceHost> , a następnie użyć <xref:System.ServiceModel.Activities.WorkflowControlClient>.  
  
-   Przykłady dla <xref:System.ServiceModel.WorkflowServiceHost> można znaleźć w następujących sekcjach:  
  
    -   [Wykonanie](../../../docs/framework/windows-workflow-foundation/samples/execution.md)  
  
    -   Basic: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scenariusze: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Aplikacja: [zawieszone Zarządzanie wystąpieniami](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)  
  
-   [Dokumentacja koncepcyjna WorkflowServiceHost](http://go.microsoft.com/fwlink/?LinkId=204807)  
  
### <a name="workflowservicehost-scenario"></a>Scenariusz WorkflowServiceHost  
 Usługa BestPriceFinder uwidacznia do wielu linii lotniczych usług można znaleźć najlepszej biletów dla określonej trasy.  Realizacji tego scenariusza należy hosta przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost>.  On również używać działań wiadomości, otrzymają żądanie cen, pobrać ceny z usługami zaplecza i odpowiadania na żądania cen o najlepszej.  
  
## <a name="correlation"></a>Korelacja  
 Korelacji jest jedną z następujących operacji:  
  
-   Sposób grupowania wiadomości razem; oznacza to, że relacja między komunikatu żądania i odpowiedzi.  
  
-   Sposób mapowania elementu danych do wystąpienia usługi  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   Aby rozpocząć pracę z korelacją, Utwórz nowy projekt w programie Visual Studio. Utwórz zmienną typu <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
-   Przykład korelacji używane do grupowania wiadomości razem to korelacja żądań i odpowiedzi, który umożliwia grupowanie komunikatów.  
  
    -   Na <xref:System.ServiceModel.Activities.Receive> działania, kliknij polecenie <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości i dodać <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> za pomocą obiektu CorrelationHandle utworzony w pierwszym kroku powyżej.  
  
    -   Utwórz <xref:System.ServiceModel.Activities.SendReply> działania, klikając prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> i klikając przycisk "Utwórz SendReply". Wklej go do przepływu pracy po <xref:System.ServiceModel.Activities.Receive> działania.  
  
-   Przykład mapowania elementu danych na wystąpienie usługi to korelacji na podstawie zawartości, która mapuje element danych (na przykład identyfikator zamówienia) na wystąpienie określonego przepływu pracy.  
  
    -   W żadnej aktywności obsługi komunikatów, kliknij `CorrelationInitializers` właściwości i dodać <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> przy użyciu <xref:System.ServiceModel.Activities.CorrelationHandle> zmiennej utworzone powyżej. Kliknij dwukrotnie odpowiednią właściwość komunikat (np. OrderID) z menu rozwijanego. Ustaw `CorrelatesWith` właściwości <xref:System.ServiceModel.Activities.CorrelationHandle> zmiennej używanej powyżej.  
  
-   Przykłady:  
  
    -   Basic: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scenariusze: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   [Dokumentacja koncepcyjna korelacji](http://go.microsoft.com/fwlink/?LinkId=204939)  
  
### <a name="correlation-scenario"></a>Scenariusz korelacji  
 Kolejność przetwarzania przepływu pracy jest używane do obsługi tworzenia nowego kolejności i aktualizowanie istniejące zlecenia, które są w toku.  Realizacji tego scenariusza należy hosta przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> i działania obsługi wiadomości.  Będzie to również wymagać korelacji na podstawie `orderId` aby upewnić się, że aktualizacje zostały wprowadzone poprawne przepływu pracy.  
  
## <a name="simplified-configuration"></a>Uproszczona konfiguracja  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Schemat konfiguracji jest złożony i udostępnia użytkownikom wiele trudne do znalezienia funkcji. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], firma Microsoft skupia się na myśl [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] użytkowników skonfiguruj swoje usługi przy użyciu następujących funkcji:  
  
-   Usuwanie konieczności jawnego konfiguracji dla usługi. Jeśli nie skonfigurujesz żadnego \<usługi > dla usługi i usługi nie definiuje programowo dowolnego punktu końcowego, a następnie zestaw punktów końcowych zostanie automatycznie dodany do usługi, jeden dla poszczególnych adres podstawowy usługi i kontraktu zaimplementowane przez usługę.  
  
-   Umożliwia użytkownikowi na definiowanie wartości domyślnych dla powiązań WCF i zachowania, które będą stosowane do usług za pomocą jawnego konfiguracji.  
  
-   Standardowe punkty końcowe zdefiniuj wielokrotnego użytku wstępnie skonfigurowanymi punktami końcowymi, które wartości dla co najmniej jednej właściwości punktu końcowego (address, binding i contract) stałe i umożliwiają definiowanie właściwości niestandardowych.  
  
-   Na koniec <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umożliwia centralne zarządzanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfiguracji klienta, przydatne w scenariuszach, w których konfiguracja jest wybrane lub zmienione od czasu ładowania domeny aplikacji.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   [Przewodnik dewelopera usługi WCF 4.0](http://go.microsoft.com/fwlink/?LinkId=204940)  
  
-   [Fabryka kanałów konfiguracji](http://go.microsoft.com/fwlink/?LinkId=204941)  
  
-   [Standardowy punkt końcowy elementu](http://go.microsoft.com/fwlink/?LinkId=204942)  
  
-   [Usługa konfiguracji ulepszeń w programie .net Framework 4](http://go.microsoft.com/fwlink/?LinkId=204943)  
  
-   [Powszechnym błędem użytkownika w programie .NET 4: błędne Nazwa konfiguracji usługi WF/WCF](http://go.microsoft.com/fwlink/?LinkId=204944)  
  
### <a name="simplified-configuration-scenarios"></a>Uproszczona konfiguracja scenariuszy  
  
-   Doświadczony developer ASMX chce rozpocząć korzystanie z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Jednak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] prawdopodobnie zbyt skomplikowany! Co to jest tych informacji, który należy zapisać w pliku konfiguracji? W .NET 4 nawet można nie ma pliku konfiguracji na wszystkich.  
  
-   Istniejącego zestawu usług WCF są bardzo trudne do konfigurowania i konserwacji. Plik konfiguracji ma tysięcy wierszy kodu XML, które są bardzo niebezpieczne touch. Pomoc jest potrzebny do skrócić ten kod inny łatwiejsze w zarządzaniu.  
  
## <a name="data-contract-resolver"></a>Mechanizmu rozpoznawania kontraktów danych  
 Program .NET 3.5 wystąpiły kilka ograniczeń w projekcie znanych typów:  
  
-   Dynamiczne dodawanie ze znanych typów, podczas serializacji lub deserializacji, nie było możliwe.  
  
-   Serializatorów może nie uwzględniać informacji nieznany typ xsi: type.  
  
-   Nie można dla użytkowników określić, które chciałby mieć są wyświetlane w sieci, aby na przykład zmniejszyć rozmiar instancji serializacji umieszczonego w wartość xsi: type.  
  
 [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md) pozwala rozwiązać te problemy w programie .NET 4.5.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   [Dokumentacja interfejsu API programu rozpoznawania nazw kontraktu danych](http://go.microsoft.com/fwlink/?LinkId=204946)  
  
-   [Wprowadzenie do mechanizmu rozpoznawania kontraktów danych](http://go.microsoft.com/fwlink/?LinkId=204947)  
  
-   Przykłady:  
  
    -   [Obiektu DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md)  
  
    -   [KnownAssemblyAttribute](../../../docs/framework/wcf/samples/knownassemblyattribute.md)  
  
### <a name="data-contract-resolver-scenarios"></a>Scenariusze programu rozpoznawania nazw kontraktu danych  
  
-   Co pozwala uniknąć konieczności zadeklarować dziesiątki <xref:System.Runtime.Serialization.KnownTypeAttribute> obiektów w usłudze.  
  
-   Zmniejszenie rozmiaru obiektu blob XML.  
  
## <a name="flowchart"></a>Schemat blokowy  
 Schemat blokowy jest dobrze znanego modelu do wizualnego reprezentowania problemów domeny. Jest nowy styl przepływu sterowania związku w .NET 4. Podstawowa charakterystycznych dla schematu blokowego jest, że tylko jedno działanie jest uruchomione w danym momencie. Blokowe można wyrazić w pętli i alternatywne wyników, ale nie można natywnie express równoczesne wykonywanie wielu węzłów.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], tworzenie aplikacji konsolowej przepływu pracy. Dodaj schemat blokowy w Projektancie przepływów pracy.  
  
-   Schemat blokowy funkcji używa następujących klas:  
  
    -   <xref:System.Activities.Statements.Flowchart>  
  
    -   <xref:System.Activities.Statements.FlowNode>  
  
    -   <xref:System.Activities.Statements.FlowDecision>  
  
    -   <xref:System.Activities.Statements.FlowStep>  
  
    -   <xref:System.Activities.Statements.FlowSwitch%601>  
  
-   Przykłady:  
  
    -   [Obsługa w działaniu Flowchart przy użyciu TryCatch błędów](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    -   [Obiekt StateMachine scenariusz przy użyciu kombinacji schematu blokowego i pobrania](../../../docs/framework/windows-workflow-foundation/samples/statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)  
  
    -   [Zatrudniania procesu](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
-   Projektanta dokumentacji:  
  
    -   [Schemat blokowy projektantów działań](/visualstudio/workflow-designer/flowchart-activity-designers)  
  
### <a name="flowchart-scenarios"></a>Schemat blokowy scenariuszy  
 Schemat blokowy działania może służyć do zaimplementowania guessing gier. Gry guessing jest bardzo prosta: komputer wybiera liczbę losową i odtwarzacz ma odgadnąć ten numer. Gdy odtwarzacz przesyła każdy wynik, komputer pokazuje mu wskazówkę (tj. "try mniejszą liczbę"). Odtwarzacz znajdzie numer w mniej niż 7 prób, on odbiera specjalne Gratulacje z komputera. Gry może być realizowane za kombinację procedurach następujących działań:  
  
-   <xref:System.Activities.Statements.Sequence>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.TryCatch>  
  
-   <xref:System.Activities.Statements.Assign%601>  
  
-   <xref:System.Activities.Statements.If>  
  
## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Procedurach działania (sekwencji, jeśli, ForEach, przełącznika, Przypisz, DoWhile, podczas gdy)  
 Działania procedurach udostępniają mechanizm przepływu sterowania sekwencyjnych modelu przy użyciu pojęcia, które są znane dla programistów. Te działania włączyć tradycyjnie konstrukcji języka programowania structured i, gdy jest to konieczne, należy zapewnić zgodność języka z typowych procedurach języków, takich jak C# / VB.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], tworzenie aplikacji konsolowej przepływu pracy. Dodaj działania procedurach w Projektancie przepływów pracy.  
  
-   Przykłady:  
  
    -   [Zatrudniania procesu](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
    -   [Proces zakupu firmowych](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)  
  
-   Projektanta dokumentacji:  
  
    -   [Projektant działań równoległych](/visualstudio/workflow-designer/parallel-activity-designer)  
  
    -   [Działania ParallelForEach\<T > Projektant działań](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)  
  
### <a name="procedural-activity-scenarios"></a>Scenariusze procedurach działania  
  
-   <xref:System.Activities.Statements.Parallel>: System zarządzania dokument intranetowych ma procedury zatwierdzania dokumentu. Dokumenty wymagają zatwierdzenia przez osoby w kilku działów można było opublikować z intranetem. Nie ma ustalony porządek zatwierdzeń; może ona występować w dowolnym momencie, dokument jest w fazie "zatwierdzania oczekujących". Gdy użytkownik prześle dokument musi być zatwierdzony przez jej bezpośrednie menedżera, administrator sieci intranet i Menedżera komunikacji wewnętrznej.  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>Aplikacja WF zarządza firmowej kupuje w dużej firmie. Firmowe zasady określają, że przed zaplanowaniem żadnej operacji zakupu, wyceny trzech różnych dostawców jest wymagana. Pracowników z działu kupowania wybiera dostawców trzy z listy dostawców firmy. Po tych dostawców zostały zaznaczone i powiadomienia, firma będzie oczekiwał na ich gospodarczego propozycji. Propozycje są dostępne w dowolnej kolejności. Aby wdrożyć ten scenariusz w WF, używamy <xref:System.Activities.Statements.ParallelForEach%601> które iterację naszych kolekcji dostawców i poproś o ich gospodarczego propozycji. Po zebraniu są wszystkie oferty, najlepszy jest zaznaczone i wyświetlane.  
  
## <a name="invokemethod"></a>InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> Działania umożliwia wywoływania metod publicznych w obiektach lub typów w zakresie. Go obsługuje wywoływania wystąpienie i metod statycznych lub bez parametrów (w tym tablice parametrów) i metody ogólne. Umożliwia także wykonanie metody synchronicznego i asynchronicznego.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], tworzenie aplikacji konsolowej przepływu pracy. Dodaj <xref:System.Activities.Statements.InvokeMethod> działania w Projektancie przepływów pracy i skonfigurować statyczne i wystąpienie metody w nim.  
  
-   Przykłady:  
  
    -   [InvokeMethod](../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
  
-   Dokumentacja projektanta: [InvokeMethod Projektant działań](/visualstudio/workflow-designer/invokemethod-activity-designer)  
  
### <a name="invokemethod-scenarios"></a>Scenariusze InvokeMethod  
  
-   Metody w obiekt w zakresie musi być wywoływane. Na przykład wartość musi zostać dodany do słownika. Wywoływana jest metoda Add wystąpienia słownika, a klucz i wartość.  
  
-   Metoda musi wywoływanej na starszą wersję obiektu CLR. Zamiast tworzenia działań niestandardowych do opakowywania wywołanie tej klasy starszej wersji, jeśli znajduje się w zakresie podczas wykonywania przepływu pracy <xref:System.Activities.Statements.InvokeMethod> mogą być używane.  
  
## <a name="error-handling-activities"></a>Błąd obsługi działań  
 <xref:System.Activities.Statements.TryCatch> Działania udostępnia mechanizm przechwytywanie wyjątków występujących podczas wykonywania zbiór działań zawartych w niej (podobnie jak konstrukcja Try/Catch w C# /VB). <xref:System.Activities.Statements.TryCatch>zapewnia obsługi na poziomie przepływu pracy wyjątków. Gdy jest nieobsługiwany wyjątek, przepływu pracy zostało przerwane i nie można wykonać na koniec bloku. To zachowanie jest zgodne z C#.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], tworzenie aplikacji konsolowej przepływu pracy. Dodaj <xref:System.Activities.Statements.TryCatch> działania w Projektancie przepływów pracy.  
  
-   Przykłady:  
  
    1.  [Obsługa w działaniu Flowchart przy użyciu TryCatch błędów](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    2.  [Przy użyciu procedur działań](../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
  
-   Dokumentacja projektanta: [projektantów działań Obsługa błędów](/visualstudio/workflow-designer/error-handling-activity-designers)  
  
### <a name="error-handling-scenarios"></a>Scenariusze obsługi błędów  
 Zbiór działań ma zostać wykonana, a logika charakterystyczna musi być wykonywana w przypadku wystąpienia błędu. Jeśli podczas tego błędu obsługi logiki okaże się, że błąd nie jest możliwe do odzyskania, zostanie zgłoszony wyjątek i działania nadrzędnego (lub hosta) będzie rozwiązać problem.  
  
## <a name="pick-activity"></a>Wybierz działanie  
 <xref:System.Activities.Statements.Pick> Działania udostępnia modelowanie w WF przepływu sterowania opartego na zdarzeniach. <xref:System.Activities.Statements.Pick>zawiera wiele gałęzi, w której każda gałąź czeka na wystąpienie określonego zdarzenia wystąpić przed uruchomieniem. W tej konfiguracji <xref:System.Activities.Statements.Pick> działa podobnie do <xref:System.Activities.Statements.Switch%601> do której działanie będzie wykonywane tylko jeden zestaw zdarzeń odbywa się nasłuchiwanie. Każda gałąź jest zdarzeniami i zdarzenia, które wystąpiło uruchamia odpowiednie gałęzi najpierw. Wszystkie inne gałęzie Anuluj i Zatrzymaj nasłuchiwanie zdarzeń.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], tworzenie aplikacji konsolowej przepływu pracy. Dodaj <xref:System.Activities.Statements.Pick> działania w Projektancie przepływów pracy.  
  
-   Przykład: [przy użyciu działaniu wybierz](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
  
-   Dokumentacja projektanta: [wybierz Projektant działań](/visualstudio/workflow-designer/pick-activity-designer)  
  
### <a name="pick-scenario"></a>Wybierz scenariusz  
 Użytkownik powinien zostać wyświetlony monit o podanie danych wejściowych. W normalnych okolicznościach dewelopera użyje wywołania metody, takie jak <xref:System.Console.ReadLine%2A> monitowanie dla danych wejściowych użytkownika. Problem z tej instalacji jest, czy program oczekuje, aż użytkownik wprowadza coś. W tym scenariuszu limit czasu jest potrzebny do odblokowania działania blokujące. Typowy scenariusz obejmuje wymaga to zadanie można wykonać w ramach danego czas trwania. Czas blokowania działalność jest scenariusz, gdzie pobrania dodaje wiele wartości.  
  
## <a name="wcf-routing-service"></a>Usługa routingu WCF  
 Usługa routingu została zaprojektowana jako ogólnego oprogramowania routera, który umożliwia kontrolowanie sposobu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]komunikatów przepływu Between klientów i usług.  Usługa routingu umożliwia oddziel klientów z usług, co pozwala na większą swobodę pod względem konfiguracje czy może obsługiwać i elastyczność, czy masz podczas określania, jak udostępniać swoje usługi.  W .NET 3.5 klientów i usług ściśle zostały powiązane; Klient ma informacje o wszystkich usług, aby komunikować się i gdzie znajduje się. Ponadto usługi WCF w programie .net Framework 3.5 ma następujące ograniczenia:  
  
-   Obsługa błędów była złożoną, jak tę logikę musiały być ustalony do klienta.  
  
-   Zawsze używaj tego samego powiązania mają klientów i usług.  
  
-   Usługi rzadko również była brana pod uwagę: jest łatwiej klienta rozmawiać z jedną usługę, która implementuje wszystko, zamiast wymagających wybranie wielu usług.  
  
 Usługa routingu w .net 4 zaprojektowano w celu ułatwienia rozwiązywania tych problemów. Nowa usługa routingu zawiera następujące funkcje:  
  
1.  Routing na podstawie zawartości (<xref:System.ServiceModel.Dispatcher.MessageFilter> obiektów Sprawdź wiadomość w celu określenia, gdzie mają być wysyłane.)  
  
2.  Protokół mostkowanie (transportu & wiadomości)  
  
3.  Obsługa błędów (router przechwytuje komunikację wyjątki i awaryjnie do tworzenia kopii zapasowej punktów końcowych)  
  
4.  Aktualizacja dynamiczna (w pamięci) z <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> i konfigurację routingu.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
1.  Dokumentacja: [routingu](../../../docs/framework/wcf/feature-details/routing.md)  
  
2.  Przykłady: [routingu usługi &#91; Przykłady WCF &#93;](../../../docs/framework/wcf/samples/routing-services.md)  
  
3.  Blog: [reguły routingu!](http://go.microsoft.com/fwlink/?LinkId=204956)  
  
### <a name="routing-scenarios"></a>Scenariusze routingu  
 Usługa routingu jest przydatne w następujących scenariuszach:  
  
-   Klienci może komunikować się wiele usług bez konieczności rozwiąż je bezpośrednio.  
  
-   Klienci mogą wykonywać dodatkową logikę na żądanie klienta, aby określić, dokąd w celu kierowania go  
  
-   Rozłóż operacje, które klient wykonuje na wiele implementacji usługi bez refaktoryzacji klienta.  
  
-   Klienci i usługi można mowy różnych powiązania z innych ustawień zabezpieczeń.  
  
-   Klientów można włączyć być bardziej niezawodne, Niepowodzenie lub niedostępności usługi.  
  
## <a name="wcf-discovery"></a>Odnajdywanie w programie WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Odnajdywanie to technologia framework, która umożliwia włączenie mechanizmu odnajdywania infrastruktury aplikacji. Służy do utworzenia usługi wykrywalny i skonfiguruj klientów do wyszukiwania usług. Klienci nie muszą już trudno kodowanego z punktem końcowym, tworzenie aplikacji bardziej niezawodne i odporność na uszkodzenia. Odnajdywanie jest idealna platforma do tworzenia funkcji automatycznej konfiguracji do aplikacji.  
  
 Produkt jest oparty na standard WS-Discovery. Ma ona być interoperacyjne, rozszerzalne i rodzajowy. Produkt obsługuje dwa tryby działania:  
  
1.  Zarządzany: w przypadku jednostki w sieci odpowiednią wiedzę na temat istniejących usług, klienci wyszukiwać go bezpośrednio informacje. To jest analogiczne do usługi Active Directory.  
  
2.  Ad hoc: gdy klienci używają komunikatów multiemisji do lokalizowania usług.  
  
 Ponadto komunikaty odnajdywania zależą od protokołu sieciowego; używając ich w górnej części każdego protokołu, który spełnia wymagania dotyczące trybu. Przykładowo odnajdowanie za pośrednictwem kanału UDP i innych sieci obsługującej multiemisji wiadomości można wysyłać komunikatów multiemisji.  Te projektowe punktów, w połączeniu z funkcji elastyczności, umożliwiają dostosowanie odnajdywania specjalnie do rozwiązania.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   Dokumentacja: [odnajdywania WCF](../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
  
-   Przykłady: [odnajdywanie (przykłady)](../../../docs/framework/wcf/samples/discovery-samples.md)  
  
### <a name="discovery-scenarios"></a>Scenariusze odnajdywania  
 Deweloper nie chce punktów końcowych twardych kodu, ponieważ jest nieznany, gdy mój usługa będzie dostępna. Zamiast tego Deweloper chce wybrać usługę w czasie wykonywania. Więcej oddzielenie, niezawodności i automatycznej konfiguracji jest potrzebne między składnikami aplikacji.  
  
## <a name="tracking"></a>Śledzenie  
 Śledzenia przepływu pracy zapewnia wgląd w działania wystąpienia przepływu pracy.  Zdarzenia śledzenia są emitowane z przepływu pracy na poziomie wystąpienia przepływu pracy i wykonywania działań w przepływie pracy. Uczestnik śledzenia przepływu pracy musi mają zostać dodane do hosta przepływu pracy, aby subskrybować śledzenie rekordów. Rejestruje śledzenia są filtrowane, za pomocą profilu śledzenia. .Net Framework zapewnia uczestnika śledzenia funkcji ETW (zdarzenia śledzenia dla systemu Windows), i podstawowy profil jest instalowany w pliku machine.config.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
1.  W [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], Utwórz projekt aplikacji usługi przepływu pracy WCF. A <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> pary zostaną umieszczone w obszarze roboczym, aby rozpocząć.  
  
2.  Otwórz plik web.config, a następnie dodaj ETW śledzenia zachowanie w przypadku żadnego profilu.  
  
    1.  Domyślny profil jest używany.  
  
    2.  Otwórz Podgląd zdarzeń i włączyć kanału analityczne w następującego węzła: **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **systemu Windows** , **Aplikacji serwerowych aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.  
  
    3.  Uruchamianie usługi przepływu pracy.  
  
    4.  Sprawdź przepływ pracy zdarzenia śledzenia w Podglądzie zdarzeń.  
  
3.  Przykłady: [śledzenia](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)  
  
4.  Dokumentacja koncepcyjna: [przepływu pracy śledzenia i śledzenia](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
  
## <a name="sql-workflow-instance-store"></a>Magazyn wystąpienia przepływu pracy SQL  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Jest implementacją serwera SQL magazynu wystąpienia. Magazyn wystąpienia zapisuje stan uruchomionego wystąpienia oraz wszystkie dane niezbędne do ładowania i wznowić tego wystąpienia. Host usługi powoduje, że w magazynie wystąpień, aby zapisać stan wystąpienia, jeśli przepływ pracy będzie się powtarzać, a zleca w magazynie wystąpień załadować stan wystąpienia nadejścia wiadomości dla danego wystąpienia lub wygaśnie w działaniu delay.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
1.  W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], utworzenia przepływu pracy, który zawiera niejawne lub jawne <xref:System.Activities.Statements.Persist> działania. Dodaj <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachowania do hosta usługi przepływu pracy. Można to zrobić w kodzie, lub w pliku konfiguracyjnym aplikacji.  
  
2.  Przykłady: [trwałości](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)  
  
3.  Dokumentacja koncepcyjna: [magazyn wystąpienia przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).
