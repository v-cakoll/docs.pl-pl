---
title: Charakterystyka funkcji programu Windows Workflow Foundation
description: W tym artykule opisano nowe funkcje, które .NET Framework 4 dodaje do Windows Workflow Foundation i scenariuszy, w których funkcje mogą być przydatne.
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: fb490b3dd368710bf2ed98f7c53b7b184fa15b0b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419957"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Charakterystyka funkcji programu Windows Workflow Foundation

.NET Framework 4 dodaje wiele funkcji do Windows Workflow Foundation. W tym dokumencie opisano szereg nowych funkcji i przedstawiono szczegółowe informacje na temat scenariuszy, w których mogą być przydatne.

## <a name="messaging-activities"></a>Działania dotyczące komunikatów

Działania obsługi komunikatów ( <xref:System.ServiceModel.Activities.Receive> , <xref:System.ServiceModel.Activities.SendReply> ,,) służą <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> do wysyłania i odbierania komunikatów WCF z przepływu pracy. <xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.SendReply>działania są używane do tworzenia Windows Communication Foundation (WCF) operacji usługi, która jest udostępniana za pośrednictwem WSDL, podobnie jak w przypadku standardowych usług sieci Web WCF. <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.ReceiveReply> są używane do korzystania z usługi sieci Web podobnej do WCF <xref:System.ServiceModel.ChannelFactory> ; istnieje również **Dodaj odwołanie do usługi** środowiska Workflow Foundation, które generuje wstępnie skonfigurowane działania.

### <a name="getting-started-with-messaging-activities"></a>Wprowadzenie z działaniami związanymi z obsługą komunikatów

- W programie Visual Studio 2012 Utwórz projekt aplikacji usługi przepływu pracy WCF. <xref:System.ServiceModel.Activities.Receive>Para i <xref:System.ServiceModel.Activities.SendReply> zostanie umieszczona na kanwie.

- Kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj odwołanie do usługi**. Wskaż istniejący WSDL usługi sieci Web i kliknij przycisk **OK**. Skompiluj projekt, aby wyświetlić wygenerowane działania (zaimplementowane przy użyciu <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> ) w przyborniku.

- [Dokumentacja usług przepływu pracy](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Przykładowy scenariusz działań związanych z przesyłaniem komunikatów

`BestPriceFinder`Usługa wywołuje wiele usług lotniczych, aby znaleźć najlepszą cenę biletów dla określonej trasy. Wdrożenie tego scenariusza wymagało użycia komunikatów o działaniach w celu uzyskania żądania ceny, pobrania cen z usług zaplecza i odpowiedzi na żądanie ceny przy użyciu najlepszej ceny. Wymaga to również użycia innych działań poza biurem do tworzenia logiki biznesowej do obliczania najlepszej ceny.

## <a name="workflowservicehost"></a>Obiektu

<xref:System.ServiceModel.WorkflowServiceHost>Jest hostem przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i komunikatów WCF (chociaż przepływy pracy nie są wymagane do obsługi komunikatów, aby były hostowane). Integruje się ona również z zachowaniem trwałości, śledzenia i kontroli wystąpienia za pomocą zestawu zachowań usługi. Podobnie jak w przypadku platformy WCF <xref:System.ServiceModel.ServiceHost> , <xref:System.ServiceModel.WorkflowServiceHost> może to być samodzielne środowisko w konsoli/WinForms/aplikacji WPF lub usłudze systemu Windows lub w sieci Web (jako plik. xamlx) w usługach IIS lub was.

### <a name="getting-started-with-workflow-service-host"></a>Wprowadzenie z hostem usługi przepływu pracy

- W programie Visual Studio 2010 Utwórz projekt aplikacji usługi przepływu pracy WCF: ten projekt zostanie skonfigurowany do użycia <xref:System.ServiceModel.WorkflowServiceHost> w środowisku hosta sieci Web.

- Aby hostować przepływ pracy bez obsługi komunikatów, należy dodać niestandardowy, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> który utworzy wystąpienie na podstawie komunikatu.

- Wystąpienia przepływu pracy mogą być kontrolowane (np. zawieszone lub zakończone) przez dodanie <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> do <xref:System.ServiceModel.WorkflowServiceHost> i za pomocą <xref:System.ServiceModel.Activities.WorkflowControlClient> .

- Przykłady dla programu <xref:System.ServiceModel.WorkflowServiceHost> można znaleźć w następujących sekcjach:

  - [Wykonanie](./samples/execution.md)

  - Aplikacja: [Zarządzanie wystąpieniami zawieszonymi](./samples/suspended-instance-management.md)

- [Hostowanie usług przepływu pracy — Omówienie](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>Scenariusz obiektu WorkflowServiceHost

Usługa BestPriceFinder odwołuje się do wielu usług lotniczych, aby znaleźć najlepszą cenę biletów dla określonej trasy. Wdrożenie tego scenariusza wymaga hostowania przepływu pracy w programie <xref:System.ServiceModel.WorkflowServiceHost> . Będzie ona również używać działań komunikatów do otrzymywania żądania ceny, pobierania cen z usług zaplecza i odpowiadania na żądanie ceny przy użyciu najlepszej ceny.

## <a name="correlation"></a>Korelacja

Korelacja jest jedną z dwóch rzeczy:

- Sposób grupowania komunikatów ze sobą; to jest relacja między komunikatem żądania a jego odpowiedzią.

- Sposób mapowania danych na wystąpienie usługi

### <a name="getting-started"></a>Getting Started

- Aby rozpocząć pracę z korelacją, Utwórz nowy projekt w programie Visual Studio. Utwórz zmienną typu <xref:System.ServiceModel.Activities.CorrelationHandle> .

- Przykładem korelacji używanym do grupowania komunikatów jest korelacja typu żądanie-odpowiedź, która powoduje grupowanie komunikatów.

  - Na <xref:System.ServiceModel.Activities.Receive> działanie, kliknij <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Właściwość i Dodaj <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> przy użyciu obiekt CorrelationHandle utworzonych w pierwszym kroku powyżej.

  - Utwórz <xref:System.ServiceModel.Activities.SendReply> działanie, klikając je prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> i klikając polecenie "Utwórz działanie SendReply". Wklej je do przepływu pracy po <xref:System.ServiceModel.Activities.Receive> działaniu.

- Przykładem mapowania danych do wystąpienia usługi jest korelacja oparta na zawartości, która mapuje dane (na przykład identyfikator zamówienia) do określonego wystąpienia przepływu pracy.

  - Na wszystkich działaniach związanych z obsługą wiadomości kliknij `CorrelationInitializers` Właściwość i Dodaj <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle> zmienną using utworzoną powyżej. Kliknij dwukrotnie odpowiednią właściwość wiadomości (np. IDZamówienia) z menu rozwijanego. Ustaw `CorrelatesWith` Właściwość na <xref:System.ServiceModel.Activities.CorrelationHandle> zmienną użytą powyżej.

- [Dokumentacja koncepcyjna korelacji](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Scenariusz korelacji

Przepływ pracy przetwarzania zamówień jest używany do obsługi nowego zamówienia i aktualizowania istniejących zamówień, które są w toku. Wdrożenie tego scenariusza wymaga hostowania przepływu pracy w programie <xref:System.ServiceModel.WorkflowServiceHost> i korzystania z działań związanych z przesyłaniem komunikatów. Wymaga również korelacji opartej na `orderId` usłudze, aby upewnić się, że aktualizacje są wykonywane w prawidłowym przepływie pracy.

## <a name="simplified-configuration"></a>Uproszczona konfiguracja

Schemat konfiguracji programu WCF jest skomplikowany i oferuje użytkownikom wiele trudnych do znalezienia funkcji. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] systemie firma Microsoft koncentruje się na konfigurowaniu usług przez użytkowników usługi WCF przy użyciu następujących funkcji:

- Usuwanie potrzeby jawnej konfiguracji dla poszczególnych usług. Jeśli nie skonfigurujesz żadnych \<> usługi dla usługi, a usługa nie będzie definiować programistycznie żadnych punktów końcowych, zestaw punktów końcowych zostanie automatycznie dodany do usługi, jeden na adres podstawowy usługi i dla kontraktu wdrożonego przez usługę.

- Umożliwia użytkownikowi Definiowanie wartości domyślnych dla powiązań i zachowań programu WCF, które będą stosowane do usług bez wyraźnej konfiguracji.

- Standardowe punkty końcowe definiują wstępnie skonfigurowane punkty końcowe wielokrotnego użytku, które mają ustalone wartości dla co najmniej jednej właściwości punktu końcowego (adresu, powiązania i kontraktu) i umożliwiają definiowanie właściwości niestandardowych.

- Na koniec program <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umożliwia centralne zarządzanie konfiguracją klienta programu WCF, przydatną w scenariuszach, w których konfiguracja jest wybierana lub zmieniana po upływie czasu ładowania domeny aplikacji.

### <a name="getting-started"></a>Getting Started

- [Przewodnik dewelopera dotyczący programu WCF 4,0](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [Fabryka kanałów konfiguracji](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [Standardowy element punktu końcowego](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [Ulepszenia konfiguracji usługi w .NET Framework 4](https://docs.microsoft.com/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [Typowy błąd użytkownika w programie .NET 4: wpisywanie nazwy konfiguracji WF/WCF usługi](https://docs.microsoft.com/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a>Uproszczone scenariusze konfiguracji

- Doświadczony programista może rozpocząć korzystanie z programu WCF. Jednak program WCF wygląda zbyt skomplikowany. Jakie są wszystkie informacje potrzebne do zapisu w pliku konfiguracji? W programie .NET 4 można nawet zdecydować, aby nie mieć pliku konfiguracji.

- Konfigurowanie i konserwowanie istniejącego zestawu usług WCF jest bardzo trudne. Plik konfiguracji zawiera tysiące wierszy kodu XML, które są niezwykle niebezpieczne do dotknięcia. Pomoc jest wymagana w celu zmniejszenia ilości kodu do łatwiejszego zarządzania.

## <a name="data-contract-resolver"></a>Program rozpoznawania kontraktu danych

W programie .NET 3,5 istniały pewne ograniczenia dotyczące projektowania znanych typów:

- Dynamiczne dodawanie znanych typów podczas serializacji lub deserializacji nie było możliwe.

- Serializatory nie mogą zajmować się nieznanymi informacjami typu xsi: Type.

- Użytkownicy mogą określić, jakie dane xsi: Type mają być wyświetlane w sieci, na przykład, aby rozmiar wystąpienia serializacji w sieci był mniejszy.

[Obiektu DataContractResolver](../wcf/samples/datacontractresolver.md) rozwiązuje te problemy w programie .NET 4,5.

### <a name="getting-started"></a>Getting Started

- [Dokumentacja interfejsu API programu rozpoznawania kontraktów danych](xref:System.Runtime.Serialization.DataContractResolver)

- [Wprowadzenie do programu rozpoznawania kontraktu danych](https://docs.microsoft.com/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- Badan

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Scenariusze dotyczące programu rozpoznawania kontraktów danych

- Unikanie konieczności deklarowania dziesiątek <xref:System.Runtime.Serialization.KnownTypeAttribute> obiektów w usłudze.

- Zmniejszenie rozmiaru obiektu BLOB XML.

## <a name="flowchart"></a>Schemat blokowy

Schemat blokowy jest dobrze znanym modelem, aby wizualnie reprezentować problemy z domeną. Jest to nowy styl przepływu sterowania wprowadzany w programie .NET 4. Podstawowa charakterystyka schematu blokowego polega na tym, że w danym momencie wykonywane jest tylko jedno działanie. Schematy blokowe mogą wyznaczać pętle i alternatywne wyniki, ale nie mogą natywnie wyrażać jednoczesnego wykonywania wielu węzłów.

### <a name="getting-started"></a>Getting Started

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodaj schemat blokowy do projektanta przepływu pracy.

- Funkcja Flowchart używa następujących klas:

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- Badan

  - [Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [Proces zatrudniania](./samples/hiring-process.md)

- Dokumentacja projektanta:

  - [Projektanci działań Flowchart](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Scenariusze schematów blokowych

Działanie Flowchart może służyć do implementowania gry do odgadnięcia. Gra do odgadnięcia jest bardzo prosta: komputer wybiera liczbę losową i gracz musi odgadnąć ten numer. Gdy gracz przesyła każde odgadnięcie, komputer wyświetli wskazówkę (tj. "Wypróbuj mniejszą liczbę"). Jeśli gracz znajdzie liczbę w krótszym niż 7 próbach, otrzyma specjalny Congratulation z komputera. Tę grę można zaimplementować przy użyciu kombinacji następujących działań proceduralnych:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Działania proceduralne (sekwencja, if, ForEach, Switch, Assign, DoWhile, while)

Działania proceduralne zapewniają mechanizm modelowania sekwencyjnego przepływu sterowania przy użyciu koncepcji, które są znane dla programistów. Działania te umożliwiają tradycyjną strukturę programowania strukturalnego i, w razie potrzeby, zapewniają parzystość języka za pomocą wspólnych języków proceduralnych, takich jak C# i Visual Basic.

### <a name="getting-started"></a>Getting Started

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodaj działania proceduralne w Projektancie przepływu pracy.

- Badan

  - [Proces zatrudniania](./samples/hiring-process.md)

  - [Proces zakupów firmowych](./samples/corporate-purchase-process.md)

- Dokumentacja projektanta:

  - [Parallel, projektant działań](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach \< T> — Projektant działań](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Scenariusze działań proceduralnych

- <xref:System.Activities.Statements.Parallel>: System zarządzania dokumentami w intranecie ma przepływ pracy zatwierdzania dokumentów. Dokumenty muszą zostać zatwierdzone przez osoby w kilku działach, zanim będą mogły zostać opublikowane w intranecie. Nie ma ustalonej kolejności dla zatwierdzeń; mogą one występować w dowolnym momencie, gdy dokument jest w fazie "Oczekiwanie na zatwierdzenie". Gdy użytkownik przesyła dokument do przeglądu, musi zostać zatwierdzony przez Menedżera bezpośredniego, administratora intranetu i wewnętrznego menedżera komunikacji.

- <xref:System.Activities.Statements.ParallelForEach%601>: Aplikacja WF zarządza kupowaniem firmy w ramach dużej firmy. Reguły firmowe określają, że przed zaplanowaniem jakiejkolwiek operacji zakupu wymagane jest przeprowadzenie oceny dla trzech różnych dostawców. Pracownik działu zakupów wybiera trzech dostawców z listy dostawców firmy. Po wybraniu i powiadomieniu tych dostawców firma będzie czekać na swoje propozycje gospodarcze. Propozycje mogą występować w dowolnej kolejności. Aby zaimplementować ten scenariusz w programie WF, używamy, <xref:System.Activities.Statements.ParallelForEach%601> Aby wykonać iterację w ramach naszej kolekcji dostawców i poprosił o ich propozycje gospodarcze. Po zebraniu wszystkich ofert zostanie wybrana i wyświetlona Najlepsza.

## <a name="invokemethod"></a>InvokeMethod

<xref:System.Activities.Statements.InvokeMethod>Działanie umożliwia wywoływanie metod publicznych w obiektach lub typach w zakresie. Obsługuje ona wywoływanie wystąpień i metod statycznych z parametrami lub bez parametrów (w tym tablicami parametrów) i metodami ogólnymi. Umożliwia również wykonywanie synchronicznie i asynchronicznie metody.

### <a name="getting-started"></a>Getting Started

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodawanie <xref:System.Activities.Statements.InvokeMethod> działania w Projektancie przepływu pracy i Konfigurowanie na nim metod statycznych i wystąpień.

- Dokumentacja projektanta: [Projektant działań InvokeMethod](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>Scenariusze Metody InvokeMethod

- Należy wywołać metodę w obiekcie w zakresie. Na przykład należy dodać wartość do słownika. Wywoływana jest metoda Add wystąpienia słownika, a podano klucz i wartość.

- Metoda musi zostać wywołana dla starszego obiektu CLR. Zamiast tworzyć działanie niestandardowe, aby otoczyć wywołanie tej starszej klasy, jeśli jest w zakresie podczas wykonywania przepływu pracy, <xref:System.Activities.Statements.InvokeMethod> można użyć.

## <a name="error-handling-activities"></a>Działania obsługi błędów

<xref:System.Activities.Statements.TryCatch>Działanie zapewnia mechanizm przechwytywania wyjątków, które występują podczas wykonywania zestawu zawartych działań (podobnie jak konstrukcja try/catch w języku C# i Visual Basic). <xref:System.Activities.Statements.TryCatch>zapewnia obsługę wyjątków na poziomie przepływu pracy. Gdy zostanie zgłoszony nieobsługiwany wyjątek, przepływ pracy zostanie przerwany i blok finally nie zostanie wykonany. To zachowanie jest spójne z językiem C#.

### <a name="getting-started"></a>Getting Started

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodawanie <xref:System.Activities.Statements.TryCatch> działania w Projektancie przepływu pracy.

- Przykład: [Obsługa błędów w działaniu Flowchart przy użyciu TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Dokumentacja projektanta: Tworzenie [obsługi błędów projektantów działań](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Scenariusze obsługi błędów

Należy wykonać zestaw działań i należy wykonać konkretną logikę w przypadku wystąpienia błędu. Jeśli podczas tej logiki obsługi błędów okaże się, że błąd nie jest możliwy do odzyskania, wyjątek zostanie ponownie wygenerowany, a działanie nadrzędne (lub hosta) będzie rozwiązywać problem.

## <a name="pick-activity"></a>Wybierz działanie

<xref:System.Activities.Statements.Pick>Działanie zapewnia modelowanie przepływu sterowania opartego na zdarzeniach w WF. <xref:System.Activities.Statements.Pick>zawiera wiele gałęzi, w których poszczególne gałęzie czekają na wystąpienie określonego zdarzenia przed uruchomieniem. W tej konfiguracji zachowanie jest <xref:System.Activities.Statements.Pick> podobne do, <xref:System.Activities.Statements.Switch%601> do którego działanie wykona tylko jeden z zestawów zdarzeń, które nasłuchuje. Każda gałąź jest sterowana zdarzeniami, a zdarzenie, które występuje, uruchamia najpierw odpowiadającą gałąź. Wszystkie inne gałęzie anulują i przerywają nasłuchiwanie zdarzeń.

### <a name="getting-started"></a>Getting Started

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodawanie <xref:System.Activities.Statements.Pick> działania w Projektancie przepływu pracy.

- Przykład: [Korzystanie z działania pobrania](./samples/using-the-pick-activity.md)

- Dokumentacja projektanta: [Wybierz projektanta działań](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Wybierz scenariusz

Użytkownik musi zostać poproszony o podanie danych wejściowych. W normalnych warunkach deweloper użyje wywołania metody, na przykład w <xref:System.Console.ReadLine%2A> celu wyświetlenia monitu o wprowadzenie danych przez użytkownika. Problem z tą konfiguracją polega na tym, że program czeka, aż użytkownik wprowadzi coś. W tym scenariuszu do odblokowania działania blokującego jest wymagany limit czasu. Typowy scenariusz to ten, który wymaga wykonania zadania w określonym czasie. Limit czasu działania blokującego jest scenariuszem, w którym funkcja wybierz dodaje wiele wartości.

## <a name="wcf-routing-service"></a>Usługa routingu WCF

Usługa routingu jest przeznaczona do ogólnego routera programowego, który umożliwia kontrolowanie sposobu przepływu komunikatów WCF między klientami i usługami. Usługa routingu umożliwia rozdzielenie klientów od usług, co zapewnia znacznie większą swobodę w zakresie konfiguracji, które mogą być obsługiwane, oraz elastyczność, którą należy wykonać, biorąc pod uwagę sposób hostowania usług. W programie .NET 3,5 klienci i usługi były ściśle sprzężone; Klient musiał poznać wszystkie usługi, których potrzebuje, aby komunikować się z nimi i gdzie się znajdują. Ponadto program WCF w .NET Framework 3,5 miał następujące ograniczenia:

- Obsługa błędów była złożona, ponieważ ta logika musiała być trwale zakodowana w kliencie.

- Klienci i usługi musiały zawsze korzystać z tych samych powiązań.

- Usługi były rzadko używane: łatwiejsze jest, aby klient mógł komunikować się z jedną usługą, która implementuje wszystko, zamiast wybierać między wieloma usługami.

Usługa routingu w programie .NET 4 została zaprojektowana tak, aby ułatwić rozwiązywanie tych problemów. Nowa usługa routingu ma następujące funkcje:

1. Routing na podstawie zawartości ( <xref:System.ServiceModel.Dispatcher.MessageFilter> obiekty badają komunikat, aby określić, gdzie powinien być wysyłany).

2. Mostkowanie protokołu (transport & Message)

3. Obsługa błędów (router przechwytuje wyjątki komunikacji i przechodzi w tryb failover do punktów końcowych kopii zapasowej)

4. Aktualizacja aktualizacji dynamicznej (w pamięci) <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> i konfiguracji routingu.

### <a name="getting-started"></a>Getting Started

1. Dokumentacja: [Routing](../wcf/feature-details/routing.md)

2. Przykłady: [usługi routingu &#91;przykłady WCF&#93;](../wcf/samples/routing-services.md)

3. Blog: [reguły routingu!](https://docs.microsoft.com/archive/blogs/RoutingRules/)

### <a name="routing-scenarios"></a>Scenariusze routingu

Usługa routingu jest przydatna w następujących scenariuszach:

- Klienci mogą komunikować się z wieloma usługami bez konieczności bezpośredniego ich rozwiązywania.

- Klienci mogą wykonać dodatkową logikę na żądanie klienta, aby określić, gdzie należy ją skierować

- Rozkład operacji wykonywanych przez klienta w wielu implementacjach usług bez konieczności refaktoryzacji klienta.

- Klienci i usługi mogą mówić różne powiązania z różnymi ustawieniami zabezpieczeń.

- Klienci mogą być włączeni do bardziej niezawodnej obsługi przed awarią lub niedostępności usług.

## <a name="wcf-discovery"></a>Odnajdywanie w programie WCF

Odnajdywanie WCF to technologia platformy, która umożliwia włączenie mechanizmu odnajdywania do infrastruktury aplikacji. Można go użyć, aby umożliwić odnajdywanie usługi i skonfigurować klientów do wyszukiwania usług. Klienci nie muszą już być zakodowani przy użyciu punktu końcowego, co sprawia, że aplikacja jest bardziej niezawodna i odporna na uszkodzenia. Odnajdywanie to idealna platforma do tworzenia funkcji automatycznej konfiguracji w aplikacji.

Produkt jest oparty na standardzie WS-Discovery. Jest ona zaprojektowana tak, aby była interoperacyjna, rozszerzalna i ogólna. Produkt obsługuje dwa tryby działania:

1. Zarządzane: w przypadku, gdy w sieci istnieje jednostka z wiedzą na temat istniejących usług, klienci wysyłają do nich zapytanie bezpośrednio w celu uzyskania informacji. Jest to analogiczne do Active Directory.

2. Ad hoc: gdzie klienci używają komunikatów multiemisji do lokalizowania usług.

Ponadto komunikaty odnajdywania to niezależny od protokołu sieciowego; można ich użyć na górze dowolnego protokołu, który obsługuje wymagania dotyczące trybu. Na przykład komunikaty multiemisji odnajdywania można wysyłać za pośrednictwem kanału UDP lub dowolnej innej sieci obsługującej komunikaty multiemisji. Te punkty projektowe, w połączeniu z elastycznością funkcji, umożliwiają dostosowanie odnajdywania do rozwiązania.

### <a name="getting-started"></a>Getting Started

- Dokumentacja: [Odnajdywanie WCF](../wcf/feature-details/wcf-discovery.md)

- Przykłady: [odnajdywanie (przykłady)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Scenariusze odnajdywania

Deweloper nie chce, aby twarde punkty końcowe kodu, ponieważ jest ono nieznane, gdy usługa będzie dostępna. Zamiast tego deweloper chce wybrać usługę w czasie wykonywania. Między składnikami aplikacji jest wymagana większa oddzielenie, niezawodne i automatycznej konfiguracji.

## <a name="tracking"></a>Śledzenie

Śledzenie przepływu pracy zapewnia wgląd w wykonywanie wystąpienia przepływu pracy. Zdarzenia śledzenia są emitowane z przepływu pracy na poziomie wystąpienia przepływu pracy i podczas wykonywania działań w ramach przepływu pracy. Aby subskrybować śledzenie rekordów, należy dodać uczestnika śledzenia przepływu pracy do hosta przepływu pracy. Rekordy śledzenia są filtrowane przy użyciu profilu śledzenia. .NET Framework udostępnia uczestnika śledzenia funkcji ETW (śledzenie zdarzeń dla systemu Windows), a w pliku Machine. config jest instalowany profil podstawowy.

### <a name="getting-started"></a>Getting Started

1. W programie Visual Studio 2010 Utwórz projekt aplikacji usługi przepływu pracy WCF. <xref:System.ServiceModel.Activities.Receive>Para i <xref:System.ServiceModel.Activities.SendReply> zostanie umieszczona na kanwie, aby rozpocząć.

2. Otwórz plik Web. config i Dodaj zachowanie śledzenia funkcji ETW bez profilu.

    1. Używany jest profil domyślny.

    2. Otwórz Podgląd zdarzeń i Włącz kanał analityczny w następującym węźle: **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji-aplikacje**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Włącz dziennik**.

    3. Uruchom usługę przepływu pracy.

    4. Obserwuj zdarzenia śledzenia przepływu pracy w Podglądzie zdarzeń.

3. Przykłady: [śledzenie](./samples/tracking.md)

4. Dokumentacja dotycząca pojęć: [śledzenie i śledzenie przepływów pracy](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>Magazyn wystąpień przepływu pracy SQL

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>To oparta na SQL Server Implementacja magazynu wystąpień. Magazyn wystąpień przechowuje stan uruchomionego wystąpienia wraz ze wszystkimi danymi, które są niezbędne do załadowania i wznowienia tego wystąpienia. Host usługi instruuje magazyn wystąpień, aby zapisywał stan wystąpienia, jeśli przepływ pracy będzie trwał, i instruuje magazyn wystąpień, aby załadować stan wystąpienia po nadejściu komunikatu dla tego wystąpienia lub wygaśnięcia działania opóźnienia.

### <a name="getting-started"></a>Getting Started

1. W programie Visual Studio 2012 Utwórz przepływ pracy zawierający niejawne lub jawne <xref:System.Activities.Statements.Persist> działanie. Dodaj <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachowanie do hosta usługi przepływu pracy. Można to zrobić w kodzie lub w pliku konfiguracji aplikacji.

2. Przykłady: [trwałość](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. Dokumentacja dotycząca pojęć: [Magazyn wystąpień przepływu pracy SQL](sql-workflow-instance-store.md).
