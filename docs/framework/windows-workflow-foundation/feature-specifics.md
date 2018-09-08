---
title: Charakterystyka funkcji programu Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: b18c6dd76762f4495ac475cd3dfa4e1995733b59
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140882"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Charakterystyka funkcji programu Windows Workflow Foundation
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] dodaje wiele funkcji do systemu Windows Workflow Foundation. W tym dokumencie opisano kilka nowych funkcji i zwraca szczegółowe informacje na temat scenariuszy, w których mogą być przydatne.  
  
## <a name="messaging-activities"></a>Działania dotyczące komunikatów  
 Działań dotyczących komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) są używane do wysyłania i odbierania komunikatów WCF z przepływu pracy.  <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania są używane w celu utworzenia operacji usługi Windows Communication Foundation (WCF), który jest uwidaczniany za pomocą języka WSDL, podobnie jak standardowy usług sieci web WCF.  <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> są używane do korzystania z usługi sieci web podobnych do programu WCF <xref:System.ServiceModel.ChannelFactory>; **Dodaj odwołanie do usługi** istnieje również środowisko dla programu Workflow Foundation, generujący wstępnie skonfigurowane działania.  
  
### <a name="getting-started-with-messaging-activities"></a>Wprowadzenie do działań dotyczących komunikatów  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], Utwórz projekt aplikacji usługi przepływu pracy WCF. A <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> pary zostaną umieszczone na kanwie.  
  
-   Kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj odwołanie do usługi**.  Wskaż istniejącą usługę sieci web WSDL, a następnie kliknij przycisk **OK**.  Skompilować projekt, aby pokazać wygenerowane działania (implementowane przy użyciu <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply>) z przybornika.  
  
-   Przykłady te działania można znaleźć w następujących sekcjach:  
  
    -   Basic: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scenariusze: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
-   [Dokumentacja koncepcyjna](https://go.microsoft.com/fwlink/?LinkId=204801)  
  
-   [Działania projektanta dokumentacja dotycząca komunikatów](https://go.microsoft.com/fwlink/?LinkId=204802)  
  
### <a name="messaging-activities-example-scenario"></a>Obsługa wiadomości działania przykładowy scenariusz  
 A `BestPriceFinder` usługi wywołuje wiele usług linii lotniczych, można znaleźć najlepsze ceny biletu dla określonej trasy.  Realizacji tego scenariusza wymaga przy użyciu działań komunikatów do otrzymają żądanie cena, pobrać ceny z usługami zaplecza i odpowiadania na żądania ceny za pomocą najlepsze ceny.  Również wymaga używania innych działań, out-of-box do tworzenia logiki biznesowej do obliczania najlepsze ceny.  
  
## <a name="workflowservicehost"></a>Elementu WorkflowServiceHost  
 <xref:System.ServiceModel.WorkflowServiceHost> Jest hostem out-of-box przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i komunikatów WCF (mimo że przepływy pracy nie są wymagane do obsługi komunikatów można hostować).  Integruje się również z trwałości, śledzenia i kontrolowania wystąpienia za pomocą zestawu zachowania usługi.  Podobnie jak w przypadku firmy WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> mogą być samodzielnie hostowane w aplikacji konsoli/WinForms/WPF lub usługa Windows lub hostowanych w sieci web (w formacie .xamlx) w usługach IIS i WAS.  
  
### <a name="getting-started-with-workflow-service-host"></a>Wprowadzenie do hosta usługi przepływu pracy  
  
-   W programie Visual Studio 2010, należy utworzyć projekt aplikacji usługi przepływu pracy WCF: ten projekt zostanie skonfigurowana do użycia <xref:System.ServiceModel.WorkflowServiceHost> w środowisku hosta sieci web.  
  
-   Aby hostować przepływ pracy-messaging, Dodaj niestandardowego <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> spowoduje to utworzenie wystąpienia na podstawie wiadomości.  
  
-   Wystąpienia przepływu pracy mogą być kontrolowane (np. wstrzymane lub przerwane), dodając <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> do <xref:System.ServiceModel.WorkflowServiceHost> , a następnie używając <xref:System.ServiceModel.Activities.WorkflowControlClient>.  
  
-   Przykłady dla <xref:System.ServiceModel.WorkflowServiceHost> można znaleźć w następujących sekcjach:  
  
    -   [Wykonanie](../../../docs/framework/windows-workflow-foundation/samples/execution.md)  
  
    -   Basic: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scenariusze: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Aplikacja: [zawieszone Zarządzanie wystąpieniami](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)  
  
-   [Dokumentacja koncepcyjna elementu WorkflowServiceHost](https://go.microsoft.com/fwlink/?LinkId=204807)  
  
### <a name="workflowservicehost-scenario"></a>Scenariusz elementu WorkflowServiceHost  
 Usługa BestPriceFinder wywołuje wiele usług linii lotniczych, można znaleźć najlepsze ceny biletu dla określonej trasy.  Realizacji tego scenariusza wymaga hostowanie przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost>.  Go również użyć działań komunikatów, otrzymają żądanie ceny, pobrać ceny z usługami zaplecza i odpowiadać na żądania ceny za pomocą najlepsze ceny.  
  
## <a name="correlation"></a>Korelacja  
 Korelacja jest jedna z następujących czynności:  
  
-   Sposób grupowania wiadomości razem; oznacza to, że relacja między komunikatu żądania i odpowiedzi.  
  
-   Sposób mapowania elementu danych na wystąpienie usługi  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   Aby rozpocząć pracę z korelacją, Utwórz nowy projekt w programie Visual Studio. Utwórz zmienną typu <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
-   Przykład korelacji używane do grupowania wiadomości razem jest korelacji "żądanie-odpowiedź", który umożliwia grupowanie komunikatów.  
  
    -   Na <xref:System.ServiceModel.Activities.Receive> działania, kliknij pozycję <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości i dodać <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> przy użyciu CorrelationHandle utworzony w pierwszym kroku powyżej.  
  
    -   Utwórz <xref:System.ServiceModel.Activities.SendReply> działanie, klikając prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> i klikając przycisk "Utwórz SendReply". Wklej go do pracy po <xref:System.ServiceModel.Activities.Receive> działania.  
  
-   Przykładem mapowania elementu danych na wystąpienie usługi jest oparte na zawartości korelacji, który mapuje element danych (na przykład identyfikator zamówienia) wystąpienia określonego przepływu pracy.  
  
    -   Dla każdego działania, obsługi komunikatów, kliknij `CorrelationInitializers` właściwości i dodać <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> przy użyciu <xref:System.ServiceModel.Activities.CorrelationHandle> zmiennej utworzonej powyżej. Kliknij dwukrotnie żądaną właściwość w komunikacie (np. OrderID) z menu rozwijanego. Ustaw `CorrelatesWith` właściwość <xref:System.ServiceModel.Activities.CorrelationHandle> zmiennej powyżej.  
  
-   Przykłady:  
  
    -   Basic: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scenariusze: [usług](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   [Dokumentacja koncepcyjna korelacji](https://go.microsoft.com/fwlink/?LinkId=204939)  
  
### <a name="correlation-scenario"></a>Scenariusz korelacji  
 Przepływ pracy przetwarzania zamówień jest używany do obsługi tworzenia nowego zamówienia i aktualizowanie istniejących zamówień, które jest obecnie w toku.  Realizacji tego scenariusza wymaga hostowanie przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> i używanie działań dotyczących komunikatów.  Również wymagałoby korelacji na podstawie `orderId` aby upewnić się, że aktualizacje zostały wprowadzone poprawne przepływ pracy.  
  
## <a name="simplified-configuration"></a>Uproszczona konfiguracja  
 Schemat konfiguracji programu WCF jest złożona i zapewnia użytkownikom z wieloma trudno znaleźć funkcji. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], koncentrowaliśmy się na ułatwienia dla użytkowników usługi WCF, skonfiguruj swoje usługi z następującymi funkcjami:  
  
-   Usuwanie potrzebę jawnego konfiguracji dla usługi. Jeśli nie skonfigurujesz dowolne \<usługi > elementy usługi i usługi nie definiuje programowo dowolnego punktu końcowego, a następnie zestaw punktów końcowych zostaną automatycznie dodane do usługi, jeden na każdy adres podstawowy usługi i na umowę zaimplementowane przez usługę.  
  
-   Umożliwia użytkownikowi na definiowanie wartości domyślnych dla wiązania WCF i zachowań, które będą stosowane do usług bez konieczności jawnej konfiguracji.  
  
-   Standardowe punkty końcowe zdefiniować wielokrotnego użytku wstępnie skonfigurowanymi punktami końcowymi, które mają stałe wartości dla co najmniej jednej właściwości punktu końcowego (adresu, powiązania i umowy) i umożliwiają definiowanie właściwości niestandardowych.  
  
-   Na koniec <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umożliwia centralne zarządzanie Konfiguracja klienta programu WCF, przydatne w scenariuszach, w których konfiguracja jest wybrane lub zmienić po utworzeniu czas ładowania domen aplikacji.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   [Przewodnik dla deweloperów do programu WCF 4.0](https://go.microsoft.com/fwlink/?LinkId=204940)  
  
-   [Fabryka kanałów konfiguracji](https://go.microsoft.com/fwlink/?LinkId=204941)  
  
-   [Standardowy punkt końcowy elementu](https://go.microsoft.com/fwlink/?LinkId=204942)  
  
-   [Usługa ulepszenia konfiguracji w programie .net Framework 4](https://go.microsoft.com/fwlink/?LinkId=204943)  
  
-   [Powszechnym użytkownika na platformie .NET 4: błędne Nazwa konfiguracji usługi WF/WCF](https://go.microsoft.com/fwlink/?LinkId=204944)  
  
### <a name="simplified-configuration-scenarios"></a>Uproszczona konfiguracja scenariuszy  
  
-   Doświadczeni projektanci ASMX chce rozpocząć korzystanie z usługi WCF. Jednak WCF jest prawdopodobnie zbyt skomplikowane! Te informacje, wymagających do zapisu w pliku konfiguracji, co to jest? W .NET 4 możesz nawet zdecydujesz się zrezygnować w każdym pliku konfiguracji.  
  
-   Istniejącego zestawu usług WCF są bardzo trudne, konfigurowania i konserwacji. Plik konfiguracji zawiera tysięcy wierszy kodu XML, które są bardzo niebezpieczne touch. Zmniejszenie tej ilości kodu do coś, co jest łatwiejsze w zarządzaniu jest potrzebna pomoc.  
  
## <a name="data-contract-resolver"></a>Mechanizmu rozpoznawania kontraktów danych  
 W .NET 3.5 wystąpiły pewne ograniczenia w projekcie znanych typów:  
  
-   Dynamiczne dodawanie znanych typów, podczas serializacji lub deserializacji, nie było możliwe.  
  
-   Serializatory może nie dotyczyć informacji nieznany typ xsi: type.  
  
-   Nie było możliwe dla użytkowników określić, jaki typ xsi: type chciałby pojawiał się na przewodowej, na przykład zmniejszyć rozmiar wystąpienia serializacji w sieci.  
  
 [Obiektu DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md) rozwiązuje te problemy w programie .NET 4.5.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   [Dokumentacja interfejsu API rozpoznawania nazw kontraktu danych](https://go.microsoft.com/fwlink/?LinkId=204946)  
  
-   [Wprowadzenie do mechanizmu rozpoznawania kontraktów danych](https://go.microsoft.com/fwlink/?LinkId=204947)  
  
-   Przykłady:  
  
    -   [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md)  
  
    -   [KnownAssemblyAttribute](../../../docs/framework/wcf/samples/knownassemblyattribute.md)  
  
### <a name="data-contract-resolver-scenarios"></a>Scenariusze programu rozpoznawania nazw kontraktu danych  
  
-   Uniknięcie konieczności zadeklarować dziesiątki <xref:System.Runtime.Serialization.KnownTypeAttribute> obiektów w usłudze.  
  
-   Zmniejszenie rozmiaru obiektów blob XML.  
  
## <a name="flowchart"></a>Schemat blokowy  
 Schemat blokowy jest dobrze znanego modelu do reprezentowania wizualnie problemów domeny. To nowy styl przepływu sterowania, które wprowadzamy w .NET 4. Podstawowa charakterystycznych dla schematu blokowego jest, że tylko jedno działanie jest wykonywany w danym momencie. Blokowe można wyrazić w pętli i alternatywne wyników, ale nie może natywnie express wykonania wielu węzłów.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], Utwórz aplikację konsoli przepływu pracy. Dodawanie schematu blokowego w Projektancie przepływu pracy.  
  
-   Funkcja schemat blokowy wykorzystuje następujące klasy:  
  
    -   <xref:System.Activities.Statements.Flowchart>  
  
    -   <xref:System.Activities.Statements.FlowNode>  
  
    -   <xref:System.Activities.Statements.FlowDecision>  
  
    -   <xref:System.Activities.Statements.FlowStep>  
  
    -   <xref:System.Activities.Statements.FlowSwitch%601>  
  
-   Przykłady:  
  
    -   [Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    -   [Scenariusz StateMachine używający kombinacji obiektów FlowChart i Pick](../../../docs/framework/windows-workflow-foundation/samples/statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)  
  
    -   [Proces zatrudniania](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
-   Dokumentacja projektanta:  
  
    -   [Projektanci działań Flowchart](/visualstudio/workflow-designer/flowchart-activity-designers)  
  
### <a name="flowchart-scenarios"></a>Schemat blokowy scenariuszy  
 Działania może służyć do implementowania odgadnięcia gry. Gra odgadnięcia jest bardzo prosta: komputer wybiera losową liczbę, a gracz ma odgadnąć tę liczbę. Gdy gracz przesyła każdego odgadnięcia, komputer pokazuje mu wskazówką (czyli "try mniejszą liczbę"). Jeśli gracz znajdzie numer w przypadku prób ataków mniej niż 7, odbiera on specjalnych Gratulacje z komputera. Ta gra może być implementowany przy użyciu kombinacji następujących działań proceduralnych:  
  
-   <xref:System.Activities.Statements.Sequence>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.TryCatch>  
  
-   <xref:System.Activities.Statements.Assign%601>  
  
-   <xref:System.Activities.Statements.If>  
  
## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Działań proceduralnych (sekwencji, jeśli ForEach, przełącznika, przypisywanie, DoWhile, podczas gdy)  
 Działań proceduralnych udostępniają mechanizm przepływu sterowania sekwencyjnego modelu przy użyciu pojęcia, które są znane programistów. Te działania tradycyjnie Włącz konstrukcji języka programowania ze strukturą i, gdy jest to konieczne, udostępniać parzystości języka procedurach języków, takich jak C# / VB.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], Utwórz aplikację konsoli przepływu pracy. Dodawanie działań proceduralnych w Projektancie przepływu pracy.  
  
-   Przykłady:  
  
    -   [Proces zatrudniania](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
    -   [Proces zakupów firmowych](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)  
  
-   Dokumentacja projektanta:  
  
    -   [Parallel, projektant działań](/visualstudio/workflow-designer/parallel-activity-designer)  
  
    -   [ParallelForEach\<T > Projektant działań](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)  
  
### <a name="procedural-activity-scenarios"></a>Scenariusze działań proceduralnych  
  
-   <xref:System.Activities.Statements.Parallel>: System zarządzania dokumentami intranet ma przepływu pracy zatwierdzania dokumentów. Dokumenty należy zatwierdzić dla osób z kilku wydziałów, zanim mogą być publikowane z intranetem. Nie ma zamówienie ustanowionych dla zatwierdzeń; mogą one występować w dowolnym momencie, dokument jest w fazie "oczekuje na zatwierdzenie". Gdy użytkownik przesyła dokumentu do przeglądu muszą zostać zatwierdzone przez swojemu menedżerowi bezpośrednich, administrator sieci intranet i Menedżera komunikacji wewnętrznej.  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>Aplikacja WF zarządza firmowych kupuje w dużej firmie. Firmowe zasady określają, że przed zaplanowaniem każdej operacji zakupu, wyceny trzech różnych dostawców jest wymagana. Pracownik działu zakupów wybiera trzech dostawców z listy dostawców firmy. Po tych dostawców zostało zaznaczone, a powiadomienia, firma będzie czekać na ich ekonomicznych propozycji. Propozycje może występować w dowolnej kolejności. Aby wdrożyć ten scenariusz w WF, użyjemy <xref:System.Activities.Statements.ParallelForEach%601> , będzie iterację naszych kolekcji dostawców i poprosić o ich ekonomicznych propozycji. Wszystkie wszystkie oferty są zbierane, najlepszą z nich jest wybrane i wyświetlane.  
  
## <a name="invokemethod"></a>InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> Działanie umożliwia wywoływanie metod publicznych w obiektach lub typów w zakresie. Go obsługuje wywoływania wystąpienie i metody statyczne z lub bez parametrów (w tym tablice parametrów) i metod ogólnych. Umożliwia także wykonanie metody synchronicznie i asynchronicznie.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], Utwórz aplikację konsoli przepływu pracy. Dodaj <xref:System.Activities.Statements.InvokeMethod> działania w Projektancie przepływów pracy i skonfigurować statyczne lub wystąpienie metody na nim.  
  
-   Przykłady:  
  
    -   [InvokeMethod](../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
  
-   Dokumentacja projektanta: [InvokeMethod, Projektant działań](/visualstudio/workflow-designer/invokemethod-activity-designer)  
  
### <a name="invokemethod-scenarios"></a>Scenariusze InvokeMethod  
  
-   Metoda w obiekcie w zakresie musi być wywoływane. Na przykład wartość musi zostać dodane do słownika. Wywoływana jest metoda Add wystąpienia słownika i klucza i wartości są dostarczane.  
  
-   Metody musi być wywołana na starszą wersję obiektu CLR. Zamiast tworzyć niestandardowe działanie, aby opakować wywołanie tej starszej wersji klasy, jeśli znajduje się w zakresie podczas wykonywania przepływu pracy <xref:System.Activities.Statements.InvokeMethod> mogą być używane.  
  
## <a name="error-handling-activities"></a>Działania obsługi błędu  
 <xref:System.Activities.Statements.TryCatch> Działania udostępnia mechanizm przechwytywanie wyjątków, które występują podczas wykonywania zbioru zawarte działania (podobne do konstrukcji Try/Catch w języku C# /VB). <xref:System.Activities.Statements.TryCatch> zapewnia obsługę na poziomie przepływu pracy wyjątków. Gdy nieobsługiwany wyjątek jest zgłaszany, przepływu pracy zostało przerwane i na koniec bloku nie będzie można wykonać. To zachowanie jest zgodne z C#.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], Utwórz aplikację konsoli przepływu pracy. Dodaj <xref:System.Activities.Statements.TryCatch> działania w Projektancie przepływu pracy.  
  
-   Przykłady:  
  
    1.  [Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    2.  [Używanie działań proceduralnych](../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
  
-   Dokumentacja projektanta: [Projektanci działań Error Handling](/visualstudio/workflow-designer/error-handling-activity-designers)  
  
### <a name="error-handling-scenarios"></a>Scenariusze obsługi błędów  
 Zbiór działań musi być wykonywane, i logikę specyficzną dla musi być wykonywany po wystąpieniu błędu. Jeśli podczas tej logiki obsługi błędów okaże się, że błąd nie jest możliwe do odzyskania, wyjątek będzie zgłaszany ponownie i działania nadrzędnego (lub host) poradzi sobie z tym problemem.  
  
## <a name="pick-activity"></a>Wybieranie działania  
 <xref:System.Activities.Statements.Pick> Działania zapewnia modelowanie w WF przepływu sterowania opartego na zdarzeniach. <xref:System.Activities.Statements.Pick> zawiera wiele gałęzi, w którym każdej gałęzi czeka na konkretne zdarzenie występuje przed uruchomieniem. W tej konfiguracji <xref:System.Activities.Statements.Pick> zachowuje się podobnie jak <xref:System.Activities.Statements.Switch%601> na które działania będą wykonywane tylko jeden zestaw zdarzeń odbywa się nasłuchiwanie. Każda gałąź jest oparte na zdarzeniach i zdarzenia, które wystąpiło działa odpowiednia gałąź, najpierw. Wszystkie inne gałęzie Anuluj i Zatrzymaj nasłuchiwanie zdarzeń.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], Utwórz aplikację konsoli przepływu pracy. Dodaj <xref:System.Activities.Statements.Pick> działania w Projektancie przepływu pracy.  
  
-   Przykład: [używanie działania Pick](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
  
-   Dokumentacja projektanta: [wybrać Projektant działań](/visualstudio/workflow-designer/pick-activity-designer)  
  
### <a name="pick-scenario"></a>Wybierz scenariusz  
 Użytkownik musi się monit o podanie danych wejściowych. W normalnych warunkach, deweloper wykorzystany do wywołania metody, takie jak <xref:System.Console.ReadLine%2A> na wybór opcji Monituj o wejściowych użytkownika. Problem za pomocą tego Instalatora polega na tym, że program czeka, aż użytkownik wprowadza coś. W tym scenariuszu upływu limitu czasu jest potrzebny do odblokowania działanie blokujące. Typowy scenariusz to taki, który wymaga to zadanie można wykonać w ramach danego czas trwania. Działanie blokujące — limit czasu jest scenariusz, w którym pobrania dodaje wiele wartości.  
  
## <a name="wcf-routing-service"></a>Usługa routingu WCF  
 Usługa routingu jest zaprojektowane jako ogólnego oprogramowania routera, który pozwala na kontrolowanie przepływ WCFmessages Between klientów i usług.  Usługa routingu umożliwia rozdzielenie klientów z usług, co daje znacznie większą swobodę w zakresie konfiguracji, może obsługiwać i elastyczność masz podczas wybierania sposobu hostowania usług.  W .NET 3.5 klientów i usługi zostały ściśle; Klient ma wiedzieć o wszystkich usług potrzebny na komunikowanie się, gdzie znajduje się. Ponadto usługi WCF w programie .net Framework 3.5 ma następujące ograniczenia:  
  
-   Obsługa błędów została skomplikowane, ponieważ musiały być ustalone do klienta tę logikę.  
  
-   Klientów i usług było zawsze używaj tego samego powiązania.  
  
-   Usługi rzadko dobrze była brana pod uwagę: jest łatwiejsze do klienta, zwróć się do jednej usługi, która implementuje wszystko, a nie wymagających, aby wybrać wiele usług.  
  
 Usługa routingu na platformie .net 4 zaprojektowano w celu ułatwienia rozwiązywania tych problemów. Nowa usługa routingu ma następujące cechy:  
  
1.  Routing na podstawie zawartości (<xref:System.ServiceModel.Dispatcher.MessageFilter> obiektów zbadać wiadomości, aby określić, gdzie mają być wysyłane.)  
  
2.  Protokół mostkowanie (transportu ko & munikat)  
  
3.  Obsługa błędów (router przechwytuje wyjątki komunikacji i awaryjnie do tworzenia kopii zapasowych punktów końcowych)  
  
4.  Aktualizacja dynamiczna (w pamięci) <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> i konfiguracji routingu.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
1.  Dokumentacja: [routingu](../../../docs/framework/wcf/feature-details/routing.md)  
  
2.  Przykłady: [usługi routingu &#91;przykłady WCF&#93;](../../../docs/framework/wcf/samples/routing-services.md)  
  
3.  Blog: [reguł routingu!](https://go.microsoft.com/fwlink/?LinkId=204956)  
  
### <a name="routing-scenarios"></a>Scenariusze routingu  
 Usługa routingu jest przydatne w następujących scenariuszach:  
  
-   Klienci skontaktować się z wieloma usługami bez konieczności ich bezpośrednio adres.  
  
-   Klienci mogą wykonywać dodatkowej logiki na żądanie klienta w celu określenia, gdzie w celu kierowania go  
  
-   Rozłóż operacje, które klient wykonuje w wielu wdrożeniach usługi bez refaktoryzacji klienta.  
  
-   Klienci i usługi mogą mówić różnych powiązania o różnych typach ustawień zabezpieczeń.  
  
-   Klientów można włączyć w taki sposób, aby być bardziej niezawodne przed awarią lub niedostępności usługi.  
  
## <a name="wcf-discovery"></a>Odnajdywanie w programie WCF  
 Odnajdywanie w programie WCF jest technologią framework, która umożliwia włączenie mechanizmu odnajdywania infrastruktury aplikacji. Można użyć tej funkcji do usługi stał się wykrywalny i skonfigurowania klientów do wyszukiwania usług. Klienci nie muszą już być trudne kodowanego z punktem końcowym, wybierając odpornego na błędy aplikacji bardziej niezawodne i błędów. Odnajdywanie jest doskonałą platformę do tworzenia funkcji automatycznej konfiguracji w aplikacji.  
  
 Produkt jest oparty na standardowego protokołu WS Discovery. Ustalono, aby być międzyoperacyjnych, rozszerzalne i ogólnych. Produkt obsługuje dwa tryby działania:  
  
1.  Zarządzane: w przypadku jednostki w sieci odpowiednią wiedzę na temat istniejące usługi, klienci wykonuje zapytania bezpośrednio do informacji. Jest to analogiczne do usługi Active Directory.  
  
2.  Ad hoc: gdy klienci używają komunikaty multiemisji do lokalizowania usługi.  
  
 Ponadto komunikaty odnajdywania są niezależne od protokołu sieciowego; używając ich na górze dowolny protokół, który obsługuje wymagania trybu. Na przykład odnajdywania mogą być wysyłane komunikaty multiemisji za pośrednictwem kanału protokołu UDP lub innych sieci, który obsługuje komunikaty multiemisji.  Zaprojektuj te punkty, w połączeniu z elastycznością funkcji umożliwiają dostosowanie odnajdywania specjalnie w celu rozwiązania.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
-   Dokumentacja: [odnajdywanie w programie WCF](../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
  
-   Przykłady: [odnajdywanie (przykłady)](../../../docs/framework/wcf/samples/discovery-samples.md)  
  
### <a name="discovery-scenarios"></a>Scenariusze odnajdywania  
 Projektant nie chce punktów końcowych twardych kodu, ponieważ jest nieznany, gdy moja usługa będzie dostępna. Zamiast tego Deweloper chce, aby wybrać usługę w czasie wykonywania. Więcej oddzielenie, niezawodności i automatyczna konfiguracja jest wymagana między składnikami aplikacji.  
  
## <a name="tracking"></a>Śledzenie  
 Śledzenie przepływu pracy zapewnia wgląd w wykonywania wystąpienia przepływu pracy.  Zdarzenia śledzenia są emitowane z przepływu pracy na poziomie wystąpienia przepływu pracy i wykonywania działań w ramach przepływu pracy. Uczestnikiem śledzenia przepływu pracy musi zostać dodane do hosta przepływu pracy do subskrybowania śledzenie rekordów. Rekordy śledzenia są filtrowane przy użyciu profilu śledzenia. .Net Framework oferuje uczestnika śledzenia zdarzeń systemu Windows (Event Tracing for Windows), a podstawowy profil jest zainstalowany w pliku machine.config.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
1.  W [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], Utwórz projekt aplikacji usługi przepływu pracy WCF. A <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> pary zostaną umieszczone na kanwie w taki sposób, aby rozpocząć.  
  
2.  Otwórz plik web.config, a następnie dodaj sposób za pomocą żadnego profilu śledzenia funkcji ETW.  
  
    1.  Domyślny profil jest używany.  
  
    2.  Otwórz Podgląd zdarzeń i włączanie kanał analityczne w następujący węzeł: **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows** , **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.  
  
    3.  Uruchom usługę przepływu pracy.  
  
    4.  Obserwuj przepływ pracy zdarzenia śledzenia w Podglądzie zdarzeń.  
  
3.  Przykłady: [śledzenia](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)  
  
4.  Dokumentacja koncepcyjna: [przepływu pracy i śledzenie](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
  
## <a name="sql-workflow-instance-store"></a>Store wystąpienia przepływu pracy SQL  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Jest implementacją magazyn wystąpienia oparte na programie SQL Server. Magazyn wystąpień przechowuje stan uruchomionego wystąpienia oraz wszystkie dane niezbędne do ładowania i wznowić tego wystąpienia. Host usługi powoduje, że magazyn wystąpienia ma być zapisany stan wystąpienia, jeśli przepływ pracy będzie się powtarzać, a następnie go powoduje, że magazyn wystąpienia można załadować stanu wystąpienia, po umieszczeniu komunikatu dla tego wystąpienia lub wygasa działanie opóźnienia.  
  
### <a name="getting-started"></a>Wprowadzenie  
  
1.  W [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], tworzenie przepływu pracy, który zawiera niejawny lub jawny <xref:System.Activities.Statements.Persist> działania. Dodaj <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachowanie do hosta usługi przepływu pracy. Można to zrobić w kodzie lub w pliku konfiguracyjnym aplikacji.  
  
2.  Przykłady: [trwałości](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)  
  
3.  Dokumentacja koncepcyjna: [Store wystąpienia przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).
