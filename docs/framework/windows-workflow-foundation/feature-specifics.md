---
title: Charakterystyka funkcji programu Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 0c312eed1a5ba064771e7cc4c260b43d97b16315
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141870"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Charakterystyka funkcji programu Windows Workflow Foundation

.NET Framework 4 dodaje wiele funkcji do Windows Workflow Foundation. W tym dokumencie opisano szereg nowych funkcji i przedstawiono szczegółowe informacje na temat scenariuszy, w których mogą być przydatne.

## <a name="messaging-activities"></a>Działania dotyczące komunikatów

Działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>) są używane do wysyłania i odbierania komunikatów WCF z przepływu pracy. działania <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> są używane do tworzenia operacji usługi Windows Communication Foundation (WCF), która jest udostępniana za pośrednictwem WSDL, podobnie jak w przypadku standardowych usług sieci Web WCF. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> są używane do korzystania z usługi sieci Web podobnej do <xref:System.ServiceModel.ChannelFactory>WCF; środowisko pracy **Dodaj odwołanie do usługi** również istnieje dla programu Workflow Foundation generującego wstępnie skonfigurowane działania.

### <a name="getting-started-with-messaging-activities"></a>Wprowadzenie z działaniami związanymi z obsługą komunikatów

- W programie Visual Studio 2012 Utwórz projekt aplikacji usługi przepływu pracy WCF. Para <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> zostanie umieszczona na kanwie.

- Kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj odwołanie do usługi**. Wskaż istniejący WSDL usługi sieci Web i kliknij przycisk **OK**. Skompiluj projekt, aby wyświetlić wygenerowane działania (zaimplementowane przy użyciu <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply>) w przyborniku.

- [Dokumentacja usług przepływu pracy](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Przykładowy scenariusz działań związanych z przesyłaniem komunikatów

Usługa `BestPriceFinder` wywołuje wiele usług lotniczych, aby znaleźć najlepszą cenę biletów dla określonej trasy. Wdrożenie tego scenariusza wymagało użycia komunikatów o działaniach w celu uzyskania żądania ceny, pobrania cen z usług zaplecza i odpowiedzi na żądanie ceny przy użyciu najlepszej ceny. Wymaga to również użycia innych działań poza biurem do tworzenia logiki biznesowej do obliczania najlepszej ceny.

## <a name="workflowservicehost"></a>Obiektu

<xref:System.ServiceModel.WorkflowServiceHost> jest hostem przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i komunikatów WCF (chociaż przepływy pracy nie są wymagane do obsługi komunikatów, aby były hostowane). Integruje się ona również z zachowaniem trwałości, śledzenia i kontroli wystąpienia za pomocą zestawu zachowań usługi. Podobnie jak w przypadku <xref:System.ServiceModel.ServiceHost>WCF, <xref:System.ServiceModel.WorkflowServiceHost> może być samodzielnie hostowane w konsoli/WinForms/aplikacji WPF lub usłudze systemu Windows albo w sieci Web (jako plik. xamlx) w usługach IIS lub WAS.

### <a name="getting-started-with-workflow-service-host"></a>Wprowadzenie z hostem usługi przepływu pracy

- W programie Visual Studio 2010 Utwórz projekt aplikacji usługi przepływu pracy WCF: ten projekt zostanie skonfigurowany tak, aby używał <xref:System.ServiceModel.WorkflowServiceHost> w środowisku hosta sieci Web.

- W celu hostowania przepływu pracy bez obsługi komunikatów należy dodać niestandardowy <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, który utworzy wystąpienie na podstawie komunikatu.

- Wystąpienia przepływu pracy mogą być kontrolowane (np. zawieszone lub zakończone) poprzez dodanie <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> do <xref:System.ServiceModel.WorkflowServiceHost> a następnie użycie <xref:System.ServiceModel.Activities.WorkflowControlClient>.

- Przykłady dla <xref:System.ServiceModel.WorkflowServiceHost> można znaleźć w następujących sekcjach:

  - [Wykonanie](./samples/execution.md)

  - Aplikacja: [Zarządzanie wystąpieniami zawieszonymi](./samples/suspended-instance-management.md)

- [Hostowanie usług przepływu pracy — Omówienie](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>Scenariusz obiektu WorkflowServiceHost

Usługa BestPriceFinder odwołuje się do wielu usług lotniczych, aby znaleźć najlepszą cenę biletów dla określonej trasy. Wdrożenie tego scenariusza wymaga hostowania przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost>. Będzie ona również używać działań komunikatów do otrzymywania żądania ceny, pobierania cen z usług zaplecza i odpowiadania na żądanie ceny przy użyciu najlepszej ceny.

## <a name="correlation"></a>Korelacja

Korelacja jest jedną z dwóch rzeczy:

- Sposób grupowania komunikatów ze sobą; to jest relacja między komunikatem żądania a jego odpowiedzią.

- Sposób mapowania danych na wystąpienie usługi

### <a name="getting-started"></a>Wprowadzenie

- Aby rozpocząć pracę z korelacją, Utwórz nowy projekt w programie Visual Studio. Utwórz zmienną typu <xref:System.ServiceModel.Activities.CorrelationHandle>.

- Przykładem korelacji używanym do grupowania komunikatów jest korelacja typu żądanie-odpowiedź, która powoduje grupowanie komunikatów.

  - Na <xref:System.ServiceModel.Activities.Receive> działania kliknij właściwość <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> i Dodaj <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> przy użyciu obiekt CorrelationHandle utworzonych w pierwszym kroku powyżej.

  - Utwórz działanie <xref:System.ServiceModel.Activities.SendReply>, klikając prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> i klikając polecenie "Utwórz działanie SendReply". Wklej je do przepływu pracy po działaniu <xref:System.ServiceModel.Activities.Receive>.

- Przykładem mapowania danych do wystąpienia usługi jest korelacja oparta na zawartości, która mapuje dane (na przykład identyfikator zamówienia) do określonego wystąpienia przepływu pracy.

  - Na wszystkich działaniach związanych z obsługą wiadomości kliknij właściwość `CorrelationInitializers` i Dodaj <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> przy użyciu utworzonej powyżej zmiennej <xref:System.ServiceModel.Activities.CorrelationHandle>. Kliknij dwukrotnie odpowiednią właściwość wiadomości (np. IDZamówienia) z menu rozwijanego. Ustaw właściwość `CorrelatesWith` na zmienną <xref:System.ServiceModel.Activities.CorrelationHandle> użytą powyżej.

- [Dokumentacja koncepcyjna korelacji](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Scenariusz korelacji

Przepływ pracy przetwarzania zamówień jest używany do obsługi nowego zamówienia i aktualizowania istniejących zamówień, które są w toku. Wdrożenie tego scenariusza wymaga hostowania przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> i korzystania z działań związanych z obsługą komunikatów. Wymaga również korelacji na podstawie `orderId`, aby upewnić się, że aktualizacje są wykonywane w prawidłowym przepływie pracy.

## <a name="simplified-configuration"></a>Uproszczona konfiguracja

Schemat konfiguracji programu WCF jest skomplikowany i oferuje użytkownikom wiele trudnych do znalezienia funkcji. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]koncentrujemy się na ułatwianiu użytkownikom usługi WCF konfigurowania usług przy użyciu następujących funkcji:

- Usuwanie potrzeby jawnej konfiguracji dla poszczególnych usług. Jeśli nie skonfigurujesz żadnych elementów usługi \<> dla usługi, a usługa nie będzie definiować programistycznie żadnych punktów końcowych, zestaw punktów końcowych zostanie automatycznie dodany do usługi, jeden na adres podstawowy usługi i dla kontraktu zaimplementowanego przez usługę.

- Umożliwia użytkownikowi Definiowanie wartości domyślnych dla powiązań i zachowań programu WCF, które będą stosowane do usług bez wyraźnej konfiguracji.

- Standardowe punkty końcowe definiują wstępnie skonfigurowane punkty końcowe wielokrotnego użytku, które mają ustalone wartości dla co najmniej jednej właściwości punktu końcowego (adresu, powiązania i kontraktu) i umożliwiają definiowanie właściwości niestandardowych.

- Na koniec <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umożliwia centralne zarządzanie konfiguracją klienta programu WCF, przydatną w scenariuszach, w których konfiguracja jest wybierana lub zmieniana po upływie czasu ładowania domeny aplikacji.

### <a name="getting-started"></a>Wprowadzenie

- [Przewodnik dewelopera dotyczący programu WCF 4,0](https://go.microsoft.com/fwlink/?LinkId=204940)

- [Fabryka kanałów konfiguracji](https://go.microsoft.com/fwlink/?LinkId=204941)

- [Standardowy element punktu końcowego](https://go.microsoft.com/fwlink/?LinkId=204942)

- [Ulepszenia konfiguracji usługi w .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=204943)

- [Typowy błąd użytkownika w programie .NET 4: wpisywanie nazwy konfiguracji WF/WCF usługi](https://go.microsoft.com/fwlink/?LinkId=204944)

### <a name="simplified-configuration-scenarios"></a>Uproszczone scenariusze konfiguracji

- Doświadczony programista może rozpocząć korzystanie z programu WCF. Jednak program WCF wygląda zbyt skomplikowany. Jakie są wszystkie informacje potrzebne do zapisu w pliku konfiguracji? W programie .NET 4 można nawet zdecydować, aby nie mieć pliku konfiguracji.

- Konfigurowanie i konserwowanie istniejącego zestawu usług WCF jest bardzo trudne. Plik konfiguracji zawiera tysiące wierszy kodu XML, które są niezwykle niebezpieczne do dotknięcia. Pomoc jest wymagana w celu zmniejszenia ilości kodu do łatwiejszego zarządzania.

## <a name="data-contract-resolver"></a>Program rozpoznawania kontraktu danych

W programie .NET 3,5 istniały pewne ograniczenia dotyczące projektowania znanych typów:

- Dynamiczne dodawanie znanych typów podczas serializacji lub deserializacji nie było możliwe.

- Serializatory nie mogą zajmować się nieznanymi informacjami typu xsi: Type.

- Użytkownicy mogą określić, jakie dane xsi: Type mają być wyświetlane w sieci, na przykład, aby rozmiar wystąpienia serializacji w sieci był mniejszy.

[Obiektu DataContractResolver](../wcf/samples/datacontractresolver.md) rozwiązuje te problemy w programie .NET 4,5.

### <a name="getting-started"></a>Wprowadzenie

- [Dokumentacja interfejsu API programu rozpoznawania kontraktów danych](https://go.microsoft.com/fwlink/?LinkId=204946)

- [Wprowadzenie do programu rozpoznawania kontraktu danych](https://go.microsoft.com/fwlink/?LinkId=204947)

- Badan

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Scenariusze dotyczące programu rozpoznawania kontraktów danych

- Unikanie konieczności deklarowania dziesiątek <xref:System.Runtime.Serialization.KnownTypeAttribute> obiektów w usłudze.

- Zmniejszenie rozmiaru obiektu BLOB XML.

## <a name="flowchart"></a>Schemat blokowy

Schemat blokowy jest dobrze znanym modelem, aby wizualnie reprezentować problemy z domeną. Jest to nowy styl przepływu sterowania wprowadzany w programie .NET 4. Podstawowa charakterystyka schematu blokowego polega na tym, że w danym momencie wykonywane jest tylko jedno działanie. Schematy blokowe mogą wyznaczać pętle i alternatywne wyniki, ale nie mogą natywnie wyrażać jednoczesnego wykonywania wielu węzłów.

### <a name="getting-started"></a>Wprowadzenie

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

Działanie Flowchart może służyć do implementowania gry do odgadnięcia. Gra do odgadnięcia jest bardzo prosta: komputer wybiera liczbę losową i gracz musi odgadnąć ten numer. Gdy gracz przesyła każde odgadnięcie, komputer wyświetla wskazówkę (np. "Wypróbuj mniejszą liczbę"). Jeśli gracz znajdzie liczbę w krótszym niż 7 próbach, otrzyma specjalny Congratulation z komputera. Tę grę można zaimplementować przy użyciu kombinacji następujących działań proceduralnych:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Działania proceduralne (sekwencja, if, ForEach, Switch, Assign, DoWhile, while)

Działania proceduralne zapewniają mechanizm modelowania sekwencyjnego przepływu sterowania przy użyciu koncepcji, które są znane dla programistów. Działania te umożliwiają tradycyjną strukturę programowania strukturalnego i, w razie potrzeby, zapewniają parzystość języka za pomocą wspólnych C#języków proceduralnych, takich jak/VB.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodaj działania proceduralne w Projektancie przepływu pracy.

- Badan

  - [Proces zatrudniania](./samples/hiring-process.md)

  - [Proces zakupów firmowych](./samples/corporate-purchase-process.md)

- Dokumentacja projektanta:

  - [Parallel, projektant działań](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach\<T >, Projektant działań](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Scenariusze działań proceduralnych

- <xref:System.Activities.Statements.Parallel>: system zarządzania dokumentami w intranecie ma przepływ pracy zatwierdzania dokumentów. Dokumenty muszą zostać zatwierdzone przez osoby w kilku działach, zanim będą mogły zostać opublikowane w intranecie. Nie ma ustalonej kolejności dla zatwierdzeń; mogą one występować w dowolnym momencie, gdy dokument jest w fazie "Oczekiwanie na zatwierdzenie". Gdy użytkownik przesyła dokument do przeglądu, musi zostać zatwierdzony przez jego Menedżera bezpośredniego, administratora intranetu i wewnętrznego menedżera komunikacji.

- <xref:System.Activities.Statements.ParallelForEach%601>: aplikacja WF zarządza kupowaniem firmy w ramach dużej firmy. Reguły firmowe określają, że przed zaplanowaniem jakiejkolwiek operacji zakupu wymagane jest przeprowadzenie oceny dla trzech różnych dostawców. Pracownik działu zakupów wybiera trzech dostawców z listy dostawców firmy. Po wybraniu i powiadomieniu tych dostawców firma będzie czekać na swoje propozycje gospodarcze. Propozycje mogą występować w dowolnej kolejności. Aby zaimplementować ten scenariusz w programie WF, użyjemy <xref:System.Activities.Statements.ParallelForEach%601>, który będzie się powtarzać w ramach naszej kolekcji dostawców i poprosił o ich propozycje gospodarcze. Po zebraniu wszystkich ofert zostanie wybrana i wyświetlona Najlepsza.

## <a name="invokemethod"></a>InvokeMethod

Działanie <xref:System.Activities.Statements.InvokeMethod> umożliwia wywoływanie metod publicznych w obiektach lub typach w zakresie. Obsługuje ona wywoływanie wystąpień i metod statycznych z parametrami lub bez parametrów (w tym tablicami parametrów) i metodami ogólnymi. Umożliwia również wykonywanie synchronicznie i asynchronicznie metody.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodawanie działania <xref:System.Activities.Statements.InvokeMethod> w Projektancie przepływu pracy i Konfigurowanie na nim metod statycznych i wystąpień.

- Dokumentacja projektanta: [Projektant działań InvokeMethod](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>Scenariusze Metody InvokeMethod

- Należy wywołać metodę w obiekcie w zakresie. Na przykład należy dodać wartość do słownika. Wywoływana jest metoda Add wystąpienia słownika, a podano klucz i wartość.

- Metoda musi zostać wywołana dla starszego obiektu CLR. Zamiast tworzyć działanie niestandardowe, aby otoczyć wywołanie tej starszej klasy, jeśli jest w zakresie podczas wykonywania przepływu pracy, można użyć <xref:System.Activities.Statements.InvokeMethod>.

## <a name="error-handling-activities"></a>Działania obsługi błędów

Działanie <xref:System.Activities.Statements.TryCatch> zapewnia mechanizm przechwytywania wyjątków, które występują podczas wykonywania zestawu zawartych działań (podobnie jak konstrukcja try/catch w C#/VB). <xref:System.Activities.Statements.TryCatch> zapewnia obsługę wyjątków na poziomie przepływu pracy. Gdy zostanie zgłoszony nieobsługiwany wyjątek, przepływ pracy zostanie przerwany i blok finally nie zostanie wykonany. To zachowanie jest zgodne z C#programem.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodawanie działania <xref:System.Activities.Statements.TryCatch> w Projektancie przepływu pracy.

- Przykład: [Obsługa błędów w działaniu Flowchart przy użyciu TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Dokumentacja projektanta: Tworzenie [obsługi błędów projektantów działań](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Scenariusze obsługi błędów

Należy wykonać zestaw działań i należy wykonać konkretną logikę w przypadku wystąpienia błędu. Jeśli podczas tej logiki obsługi błędów okaże się, że błąd nie jest możliwy do odzyskania, wyjątek zostanie ponownie wygenerowany, a działanie nadrzędne (lub hosta) będzie rozwiązywać problem.

## <a name="pick-activity"></a>Wybierz działanie

Działanie <xref:System.Activities.Statements.Pick> zapewnia modelowanie przepływu sterowania opartego na zdarzeniach w WF. <xref:System.Activities.Statements.Pick> zawiera wiele gałęzi, w których poszczególne gałęzie czekają na wystąpienie określonego zdarzenia przed uruchomieniem. W tej konfiguracji <xref:System.Activities.Statements.Pick> zachowuje się podobnie do <xref:System.Activities.Statements.Switch%601>, do którego działanie wykona tylko jeden z zestawów zdarzeń, które nasłuchuje. Każda gałąź jest sterowana zdarzeniami, a zdarzenie, które występuje, uruchamia najpierw odpowiadającą gałąź. Wszystkie inne gałęzie anulują i przerywają nasłuchiwanie zdarzeń.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 Utwórz aplikację konsolową przepływu pracy. Dodawanie działania <xref:System.Activities.Statements.Pick> w Projektancie przepływu pracy.

- Przykład: [Korzystanie z działania pobrania](./samples/using-the-pick-activity.md)

- Dokumentacja projektanta: [Wybierz projektanta działań](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Wybierz scenariusz

Użytkownik musi zostać poproszony o podanie danych wejściowych. W normalnych warunkach deweloper użyje wywołania metody, takiego jak <xref:System.Console.ReadLine%2A>, aby wyświetlić monit o wprowadzenie danych przez użytkownika. Problem z tą konfiguracją polega na tym, że program czeka, aż użytkownik wprowadzi coś. W tym scenariuszu do odblokowania działania blokującego jest wymagany limit czasu. Typowy scenariusz to ten, który wymaga wykonania zadania w określonym czasie. Limit czasu działania blokującego jest scenariuszem, w którym funkcja wybierz dodaje wiele wartości.

## <a name="wcf-routing-service"></a>Usługa routingu WCF

Usługa routingu jest przeznaczona do ogólnego routera programowego, który umożliwia kontrolowanie sposobu przepływu komunikatów WCF między klientami i usługami. Usługa routingu umożliwia rozdzielenie klientów od usług, co zapewnia znacznie większą swobodę w zakresie konfiguracji, które mogą być obsługiwane, oraz elastyczność, którą należy wykonać, biorąc pod uwagę sposób hostowania usług. W programie .NET 3,5 klienci i usługi były ściśle sprzężone; Klient musiał poznać wszystkie usługi, których potrzebuje, aby komunikować się z nimi i gdzie się znajdują. Ponadto program WCF w .NET Framework 3,5 miał następujące ograniczenia:

- Obsługa błędów była złożona, ponieważ ta logika musiała być trwale zakodowana w kliencie.

- Klienci i usługi musiały zawsze korzystać z tych samych powiązań.

- Usługi były rzadko używane: łatwiejsze jest, aby klient mógł komunikować się z jedną usługą, która implementuje wszystko, zamiast wybierać między wieloma usługami.

Usługa routingu w programie .NET 4 została zaprojektowana tak, aby ułatwić rozwiązywanie tych problemów. Nowa usługa routingu ma następujące funkcje:

1. Routing oparty na zawartości (<xref:System.ServiceModel.Dispatcher.MessageFilter> obiekty badają komunikat, aby określić, gdzie należy wysłać).

2. Mostkowanie protokołu (Transport & Message)

3. Obsługa błędów (router przechwytuje wyjątki komunikacji i przechodzi w tryb failover do punktów końcowych kopii zapasowej)

4. Aktualizacja dynamicznego (w pamięci) <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> i konfiguracji routingu.

### <a name="getting-started"></a>Wprowadzenie

1. Dokumentacja: [Routing](../wcf/feature-details/routing.md)

2. Przykłady: [usługi &#91;routingu — przykłady&#93; WCF](../wcf/samples/routing-services.md)

3. Blog: [reguły routingu!](https://go.microsoft.com/fwlink/?LinkId=204956)

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

### <a name="getting-started"></a>Wprowadzenie

- Dokumentacja: [Odnajdywanie WCF](../wcf/feature-details/wcf-discovery.md)

- Przykłady: [odnajdywanie (przykłady)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Scenariusze odnajdywania

Deweloper nie chce, aby twarde punkty końcowe kodu, ponieważ jest ono nieznane, gdy usługa będzie dostępna. Zamiast tego deweloper chce wybrać usługę w czasie wykonywania. Między składnikami aplikacji jest wymagana większa oddzielenie, niezawodne i automatycznej konfiguracji.

## <a name="tracking"></a>Śledzenie

Śledzenie przepływu pracy zapewnia wgląd w wykonywanie wystąpienia przepływu pracy. Zdarzenia śledzenia są emitowane z przepływu pracy na poziomie wystąpienia przepływu pracy i podczas wykonywania działań w ramach przepływu pracy. Aby subskrybować śledzenie rekordów, należy dodać uczestnika śledzenia przepływu pracy do hosta przepływu pracy. Rekordy śledzenia są filtrowane przy użyciu profilu śledzenia. .NET Framework udostępnia uczestnika śledzenia funkcji ETW (śledzenie zdarzeń dla systemu Windows), a w pliku Machine. config jest instalowany profil podstawowy.

### <a name="getting-started"></a>Wprowadzenie

1. W programie Visual Studio 2010 Utwórz projekt aplikacji usługi przepływu pracy WCF. Para <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> zostanie umieszczona na kanwie, aby rozpocząć.

2. Otwórz plik Web. config i Dodaj zachowanie śledzenia funkcji ETW bez profilu.

    1. Używany jest profil domyślny.

    2. Otwórz Podgląd zdarzeń i Włącz kanał analityczny w następującym węźle: **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji-aplikacje**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Włącz dziennik**.

    3. Uruchom usługę przepływu pracy.

    4. Obserwuj zdarzenia śledzenia przepływu pracy w Podglądzie zdarzeń.

3. Przykłady: [śledzenie](./samples/tracking.md)

4. Dokumentacja dotycząca pojęć: [śledzenie i śledzenie przepływów pracy](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>Magazyn wystąpień przepływu pracy SQL

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> to oparta na SQL Server Implementacja magazynu wystąpień. Magazyn wystąpień przechowuje stan uruchomionego wystąpienia wraz ze wszystkimi danymi, które są niezbędne do załadowania i wznowienia tego wystąpienia. Host usługi instruuje magazyn wystąpień, aby zapisywał stan wystąpienia, jeśli przepływ pracy będzie trwał, i instruuje magazyn wystąpień, aby załadować stan wystąpienia po nadejściu komunikatu dla tego wystąpienia lub wygaśnięcia działania opóźnienia.

### <a name="getting-started"></a>Wprowadzenie

1. W programie Visual Studio 2012 Utwórz przepływ pracy zawierający niejawną lub niejawną aktywność <xref:System.Activities.Statements.Persist>. Dodaj zachowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> do hosta usługi przepływu pracy. Można to zrobić w kodzie lub w pliku konfiguracji aplikacji.

2. Przykłady: [trwałość](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. Dokumentacja dotycząca pojęć: [Magazyn wystąpień przepływu pracy SQL](sql-workflow-instance-store.md).
