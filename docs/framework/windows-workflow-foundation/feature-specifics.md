---
title: Charakterystyka funkcji programu Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 11bde5edea44f09ef1a5658cdf0e20ec1349c84b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182922"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Charakterystyka funkcji programu Windows Workflow Foundation

Program .NET Framework 4 dodaje szereg funkcji do programu Windows Workflow Foundation. W tym dokumencie opisano szereg nowych funkcji i zawiera szczegółowe informacje o scenariuszach, w których mogą być przydatne.

## <a name="messaging-activities"></a>Działania dotyczące komunikatów

Działania obsługi wiadomości<xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply>( <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply>, , , , ) są używane do wysyłania i odbierania wiadomości WCF z przepływu pracy. <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.SendReply> działania są używane do tworzenia operacji usługi Windows Communication Foundation (WCF), która jest narażona za pośrednictwem WSDL podobnie jak standardowe usługi sieci Web WCF. <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.ReceiveReply> są używane do korzystania z usługi <xref:System.ServiceModel.ChannelFactory>internetowej podobnej do WCF; Doświadczenie **Dodaj odwołanie do usługi** istnieje również dla fundacji przepływu pracy, która generuje wstępnie skonfigurowane działania.

### <a name="getting-started-with-messaging-activities"></a>Wprowadzenie do działań związanych z wiadomością

- W programie Visual Studio 2012 utwórz projekt aplikacji usługi przepływu pracy WCF. A <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> i para zostaną umieszczone na płótnie.

- Kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj odwołanie do usługi**. Wskaż istniejącą usługę sieci Web WSDL i kliknij przycisk **OK**. Zbuduj swój projekt, aby pokazać wygenerowane <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply>działania (zaimplementowane przy użyciu i) w przyborniku.

- [Dokumentacja usług przepływu pracy](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Przykładowy scenariusz działań obsługi wiadomości

Usługa `BestPriceFinder` wzywa do wielu usług lotniczych, aby znaleźć najlepszą cenę biletu na daną trasę. Implementowanie tego scenariusza wymagałoby użycia działań wiadomości, aby otrzymać żądanie ceny, pobrać ceny z usług zaplecza i odpowiedzieć na żądanie ceny z najlepszą ceną. Wymagałoby to również korzystania z innych działań out-of-box, aby stworzyć logikę biznesową do obliczania najlepszej ceny.

## <a name="workflowservicehost"></a>Workflowservicehost

Jest <xref:System.ServiceModel.WorkflowServiceHost> to gotowy host przepływu pracy, który obsługuje wiele wystąpień, konfiguracji i wiadomości WCF (chociaż przepływy pracy nie są wymagane do korzystania z obsługi wiadomości w celu hosta). Integruje się również z trwałości, śledzenia i kontroli wystąpienia za pośrednictwem zestawu zachowań usługi. Podobnie jak WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> może być hostowany samodzielnie w konsoli/aplikacji WinForms/WPF lub usłudze Windows lub hostowanej w internecie (jako plik .xamlx) w usługach IIS lub WAS.

### <a name="getting-started-with-workflow-service-host"></a>Wprowadzenie do hosta usługi przepływ pracy

- W programie Visual Studio 2010 utwórz projekt aplikacji usługi przepływu pracy WCF: ten projekt zostanie skonfigurowany do użycia <xref:System.ServiceModel.WorkflowServiceHost> w środowisku hosta sieci web.

- Aby hostować przepływ pracy bez obsługi wiadomości, dodaj niestandardowe, które utworzy wystąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> na podstawie wiadomości.

- Wystąpienia przepływu pracy można kontrolować (np. zawieszone lub zakończone) <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> przez <xref:System.ServiceModel.WorkflowServiceHost> dodanie a <xref:System.ServiceModel.Activities.WorkflowControlClient>do .

- Przykłady do <xref:System.ServiceModel.WorkflowServiceHost> tego można znaleźć w następujących sekcjach:

  - [Wykonanie](./samples/execution.md)

  - Zastosowanie: [Zarządzanie zawieszonymi wystąpieniami](./samples/suspended-instance-management.md)

- [Omówienie usług przepływu pracy hostingu](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>Scenariusz usługi przepływu pracy

Usługa BestPriceFinder wzywa do wielu usług lotniczych, aby znaleźć najlepszą cenę biletu na daną trasę. Implementowanie tego scenariusza wymagałoby hostowania <xref:System.ServiceModel.WorkflowServiceHost>przepływu pracy w . Będzie również korzystać z działań wiadomości, aby otrzymać żądanie ceny, pobrać ceny z usług zaplecza i odpowiedzieć na żądanie ceny z najlepszą ceną.

## <a name="correlation"></a>Korelacja

Korelacja jest jedną z dwóch rzeczy:

- Sposób grupowania wiadomości razem; oznacza to, że związek między komunikatem żądania a jego odpowiedzią.

- Sposób mapowania fragmentu danych do wystąpienia usługi

### <a name="getting-started"></a>Wprowadzenie

- Aby rozpocząć pracę z korelacji, należy utworzyć nowy projekt w programie Visual Studio. Utwórz zmienną <xref:System.ServiceModel.Activities.CorrelationHandle>typu .

- Przykładem korelacji używane do grupowania wiadomości razem jest request-reply korelacji, która grupuje wiadomości razem.

  - W <xref:System.ServiceModel.Activities.Receive> przypadku działania kliknij <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwość <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> i dodaj za pomocą CorrelationHandle utworzone w pierwszym kroku powyżej.

  - Utwórz <xref:System.ServiceModel.Activities.SendReply> działanie, klikając prawym <xref:System.ServiceModel.Activities.Receive> przyciskiem myszy i klikając "Utwórz SendReply". Wklej go do przepływu <xref:System.ServiceModel.Activities.Receive> pracy po zakończeniu działania.

- Przykładem mapowania fragmentu danych do wystąpienia usługi jest korelacja oparta na zawartości, która mapuje fragment danych (na przykład identyfikator zamówienia) do określonego wystąpienia przepływu pracy.

  - W przypadku każdej aktywności `CorrelationInitializers` wiadomości kliknij <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> właściwość <xref:System.ServiceModel.Activities.CorrelationHandle> i dodaj zmienną utworzoną powyżej. Kliknij dwukrotnie żądaną właściwość w wiadomości (np. OrderID) z menu rozwijanego. Ustaw `CorrelatesWith` właściwość <xref:System.ServiceModel.Activities.CorrelationHandle> na zmienną używaną powyżej.

- [Dokumentacja koncepcyjna korelacji](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Scenariusz korelacji

Przepływ pracy przetwarzania zamówień jest używany do obsługi tworzenia nowych zamówień i aktualizowania istniejących zamówień, które są w toku. Implementowanie tego scenariusza wymaga hostowania <xref:System.ServiceModel.WorkflowServiceHost> przepływu pracy i używania działań obsługi wiadomości. Wymagałoby to również korelacji `orderId` w oparciu o zapewnienie, że aktualizacje są dokonywane do prawidłowego przepływu pracy.

## <a name="simplified-configuration"></a>Uproszczona konfiguracja

Schemat konfiguracji WCF jest złożony i zapewnia użytkownikom wiele trudnych do znalezienia funkcji. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]programie skupiliśmy się na pomocy użytkownikom WCF w konfigurowaniu ich usług za pomocą następujących funkcji:

- Usuwanie konieczności jawnego konfiguracji dla usługi. Jeśli nie skonfigurujesz żadnych \<elementów usługi> dla usługi, a usługa nie definiuje programowo dowolnego punktu końcowego, zestaw punktów końcowych zostanie automatycznie dodany do usługi, po jednym na adres podstawowy usługi i na umowę zaimplementowana przez usługę.

- Umożliwia użytkownikowi definiowanie wartości domyślnych dla wcf powiązania i zachowania, które zostaną zastosowane do usług bez jawnych konfiguracji.

- Standardowe punkty końcowe definiują wstępnie skonfigurowane punkty końcowe wielokrotnego użytku, które mają stałe wartości dla jednej lub więcej właściwości punktu końcowego (adres, powiązanie i kontrakt) i umożliwiają definiowanie właściwości niestandardowych.

- Na koniec <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umożliwia centralne zarządzanie konfiguracją klienta WCF, przydatne w scenariuszach, w których konfiguracja jest zaznaczona lub zmieniona po czasie ładowania domeny aplikacji.

### <a name="getting-started"></a>Wprowadzenie

- [Przewodnik dla deweloperów do WCF 4.0](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [Fabryka kanałów konfiguracji](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [Element standardowego punktu końcowego](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [Ulepszenia konfiguracji usługi w programie .NET Framework 4](https://docs.microsoft.com/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [Typowy błąd użytkownika w .NET 4: Mistyping WF/WCF Nazwa konfiguracji usługi](https://docs.microsoft.com/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a>Uproszczone scenariusze konfiguracji

- Doświadczony programista ASMX chce rozpocząć korzystanie z WCF. Jednak WCF wydaje się zbyt skomplikowane! Jakie są wszystkie te informacje, które muszę zapisać w pliku konfiguracyjnym? W programie .NET 4 można nawet zdecydować, że w ogóle nie ma pliku konfiguracyjnego.

- Istniejący zestaw usług WCF są bardzo trudne do skonfigurowania i utrzymania. Plik konfiguracyjny zawiera tysiące wierszy kodu XML, które są niezwykle niebezpieczne w dotyku. Pomoc jest potrzebna, aby zmniejszyć tę ilość kodu do czegoś łatwiejszego w zarządzaniu.

## <a name="data-contract-resolver"></a>Program rozpoznawania kontraktów danych

W .NET 3.5, było kilka ograniczeń w projektowaniu znanych typów:

- Dynamiczne dodawanie znanych typów podczas serializacji lub deserializacji nie było możliwe.

- Serializatory nie mogą poradzić sobie z nieznanymi informacjami xsi:type.

- Nie było możliwe dla użytkowników, aby określić, co xsi:type chcieliby mieć wyświetlane na przewod, aby, na przykład, aby zmniejszyć rozmiar wystąpienia serializacji na przewodze.

[DataContractResolver](../wcf/samples/datacontractresolver.md) rozwiązuje te problemy w .NET 4.5.

### <a name="getting-started"></a>Wprowadzenie

- [Dokumentacja interfejsu API programu Data Contract Resolver](xref:System.Runtime.Serialization.DataContractResolver)

- [Przedstawiamy program do rozwiązywania umów danych](https://docs.microsoft.com/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- Przykłady:

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Scenariusze rozpoznawania nazw kontraktów danych

- Unikanie konieczności deklarowania <xref:System.Runtime.Serialization.KnownTypeAttribute> dziesiątek obiektów w usłudze.

- Zmniejszenie rozmiaru obiektu blob XML.

## <a name="flowchart"></a>Schemat blokowy

Schemat blokowy jest dobrze znanym paradygmatem wizualnie reprezentują problemy domeny. Jest to nowy styl przepływu sterowania wprowadzamy w .NET 4. Podstawową cechą schematu blokowego jest to, że w danym momencie jest wykonywana tylko jedno działanie. Schematy blokowe mogą wyrażać pętle i wyniki alternatywne, ale nie mogą natywnie wyrazić równoczesne wykonanie wielu węzłów.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 utwórz aplikację konsoli przepływu pracy. Dodaj schemat blokowy w projektancie przepływu pracy.

- Funkcja schematu blokowego używa następujących klas:

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- Przykłady:

  - [Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [Proces zatrudniania](./samples/hiring-process.md)

- Dokumentacja projektanta:

  - [Projektanci działań schematu blokowego](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Scenariusze schematu blokowego

Działanie schematu blokowego może służyć do implementowania gry zgadywania. Zgadywanie gra jest bardzo prosta: komputer wybiera losową liczbę i gracz musi odgadnąć, że liczba. Gdy gracz przesyła każde przypuszczenie, komputer pokazuje im podpowiedź (tj. "spróbuj niższej liczby"). Jeśli gracz znajdzie numer w mniej niż 7 próbach, otrzyma specjalne gratulacje z komputera. Ta gra może być realizowana z kombinacją następujących działań proceduralnych:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Działania proceduralne (sekwencja, if, forEach, Switch, Assign, DoWhile, While)

Działania proceduralne zapewniają mechanizm do modelowania sekwencyjnego przepływu sterowania przy użyciu pojęć, które są znane programistom. Te działania umożliwiają tradycyjnie strukturyzowane konstrukcje języka programowania i, w stosownych przypadkach, zapewniają parzystość języka ze wspólnymi językami proceduralnymi, takimi jak C# i Visual Basic.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 utwórz aplikację konsoli przepływu pracy. Dodaj działania proceduralne w projektancie przepływu pracy.

- Przykłady:

  - [Proces zatrudniania](./samples/hiring-process.md)

  - [Proces zakupów firmowych](./samples/corporate-purchase-process.md)

- Dokumentacja projektanta:

  - [Parallel, projektant działań](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach\<T> Projektant działań](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Scenariusze działań proceduralnych

- <xref:System.Activities.Statements.Parallel>: Intranetowy system zarządzania dokumentami ma przepływ pracy zatwierdzania dokumentów. Dokumenty muszą być zatwierdzone przez osoby w kilku działach, zanim będą mogły zostać opublikowane w intranecie. Nie ma ustalonego zamówienia dla zatwierdzeń; mogą one wystąpić w dowolnym momencie, gdy dokument znajduje się w fazie "oczekujące na zatwierdzenie". Gdy użytkownik przesyła dokument do przeglądu, musi zostać zatwierdzony przez swojego bezpośredniego menedżera, administratora intranetu i menedżera komunikacji wewnętrznej.

- <xref:System.Activities.Statements.ParallelForEach%601>: Aplikacja WF zarządza zakupami korporacyjnymi w dużej firmie. Reguły korporacyjne nakazują, że przed zaplanowaniem jakiejkolwiek operacji zakupu wymagane są wyceny trzech różnych dostawców. Pracownik z działu zakupów wybiera trzech dostawców z listy dostawców firmy. Po wybraniu i powiadomieniu tych dostawców firma będzie czekać na ich propozycje ekonomiczne. Propozycje mogą być w dowolnej kolejności. Aby wdrożyć ten scenariusz w <xref:System.Activities.Statements.ParallelForEach%601> WF, używamy, który będzie iterować poprzez naszą kolekcję dostawców i poprosić o ich propozycje ekonomiczne. Po zebraniu wszystkich ofert, najlepsza jest wybierana i wyświetlana.

## <a name="invokemethod"></a>InvokeMethod

Działanie <xref:System.Activities.Statements.InvokeMethod> umożliwia wywoływanie metod publicznych w obiektach lub typach w zakresie. Obsługuje wywoływanie metod instancji i statycznych z parametrami lub bez (w tym tablice parametrów) i metod ogólnych. Umożliwia również wykonywanie metody synchronicznie i asynchronicznie.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 utwórz aplikację konsoli przepływu pracy. Dodaj <xref:System.Activities.Statements.InvokeMethod> działanie w projektancie przepływu pracy i skonfiguruj na nim metody statyczne i metody instancji.

- Dokumentacja projektanta: [InvokeMethod Activity Designer](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>Scenariusze invokeMethod

- Metoda w obiekcie w zakresie musi być wywołana. Na przykład wartość musi zostać dodana do słownika. Add metoda wystąpienia słownika jest wywoływana i klucz i wartość są dostarczane.

- Metoda musi być wywoływana na starszych CLR obiektu. Zamiast tworzenia działania niestandardowego, aby zawinąć wywołanie tej starszej klasy, jeśli <xref:System.Activities.Statements.InvokeMethod> jest w zakresie podczas wykonywania przepływu pracy, można użyć.

## <a name="error-handling-activities"></a>Działania związane z obsługą błędów

Działanie <xref:System.Activities.Statements.TryCatch> zapewnia mechanizm przechwytywania wyjątków, które występują podczas wykonywania zestawu zawartych działań (podobne do Try/Catch konstrukcji w języku C# i Visual Basic). <xref:System.Activities.Statements.TryCatch>zapewnia obsługę wyjątków na poziomie przepływu pracy. Gdy zostanie zgłoszony nieobsługiowany wyjątek, przepływ pracy zostanie przerwany, a blok Finally nie zostanie wykonany. To zachowanie jest zgodne z C#.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 utwórz aplikację konsoli przepływu pracy. Dodaj <xref:System.Activities.Statements.TryCatch> działanie w projektancie przepływu pracy.

- Przykład: [Obsługa błędów w działaniu schematu blokowego przy użyciu funkcji TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Dokumentacja projektanta: [Projektanci działań obsługi błędów](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Scenariusze obsługi błędów

Zestaw działań musi zostać wykonany, a określona logika musi zostać wykonana, gdy wystąpi błąd. Jeśli podczas tej logiki obsługi błędów okaże się, że błąd nie jest możliwe do odzyskania, wyjątek zostanie ponownie rzny, a działanie nadrzędne (lub hosta) zajmie się problemem.

## <a name="pick-activity"></a>Wybierz aktywność

Działanie <xref:System.Activities.Statements.Pick> zapewnia oparte na zdarzeniach modelowanie przepływu sterowania w WF. <xref:System.Activities.Statements.Pick>zawiera wiele gałęzi, w których każda gałąź czeka na wystąpienie określonego zdarzenia przed uruchomieniem. W tej konfiguracji <xref:System.Activities.Statements.Pick> zachowuje się <xref:System.Activities.Statements.Switch%601> podobnie do, do którego działanie wykona tylko jeden z zestawu zdarzeń, które nasłuchuje. Każda gałąź jest sterowana zdarzeniami, a zdarzenie, które występuje, najpierw uruchamia odpowiednią gałąź. Wszystkie inne gałęzie anulują i przestają nasłuchiwać wydarzeń.

### <a name="getting-started"></a>Wprowadzenie

- W programie Visual Studio 2012 utwórz aplikację konsoli przepływu pracy. Dodaj <xref:System.Activities.Statements.Pick> działanie w projektancie przepływu pracy.

- Przykład: [korzystanie z działania pobrania](./samples/using-the-pick-activity.md)

- Dokumentacja projektanta: [Wybierz projektanta działań](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Scenariusz pobrania

Użytkownik musi zostać poproszony o wprowadzenie danych. W normalnych warunkach deweloper użyje wywołania metody, aby <xref:System.Console.ReadLine%2A> monitować o dane wejściowe użytkownika. Problem z tą konfiguracją polega na tym, że program czeka, aż użytkownik coś wprowadzi. W tym scenariuszu limit czasu jest potrzebny do odblokowania działania blokowania. Typowy scenariusz to taki, który wymaga wykonania zadania w określonym czasie. Czas działania blokowania jest scenariusz, w którym Pick dodaje dużo wartości.

## <a name="wcf-routing-service"></a>Usługa routingu WCF

Usługa routingu została zaprojektowana jako ogólny router oprogramowania, który pozwala kontrolować sposób przepływu wiadomości WCF między klientami i usługami. Usługa routingu umożliwia oddzielenie klientów od usług, co daje znacznie większą swobodę pod względem konfiguracji, które można obsługiwać i elastyczności, którą masz, gdy rozważasz sposób hostowania usług. W .NET 3.5 klienci i usługi były ściśle powiązane; klient musiał wiedzieć o wszystkich usługach, z którymi musiał porozmawiać i gdzie się znajdował. Ponadto WCF w .NET Framework 3.5 miał następujące ograniczenia:

- Obsługa błędów była złożona, ponieważ ta logika musiała być zakodowane na czas w kliencie.

- Klienci i usługi zawsze używali tych samych powiązań.

- Usługi rzadko były dobrze brane pod uwagę: łatwiej jest mieć klienta rozmawiać z jedną usługą, która implementuje wszystko, a nie konieczności wyboru między wieloma usługami.

Usługa routingu w .NET 4 ma na celu ułatwienie rozwiązywania tych problemów. Nowa usługa routingu ma następujące funkcje:

1. Routing oparty<xref:System.ServiceModel.Dispatcher.MessageFilter> na zawartości (obiekty sprawdzają wiadomość, aby określić, gdzie ma zostać wysłana).

2. Pomostowanie protokołu (transport & komunikat)

3. Obsługa błędów (router łapie wyjątki komunikacji i działa w trybie fail over do kopii zapasowej punktów końcowych)

4. Dynamiczna <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> aktualizacja (w pamięci) i konfiguracja routingu.

### <a name="getting-started"></a>Wprowadzenie

1. Dokumentacja: [Routing](../wcf/feature-details/routing.md)

2. Przykłady: [usługi routingu &#91;próbkach WCF&#93;](../wcf/samples/routing-services.md)

3. Blog: [Zasady routingu!](https://docs.microsoft.com/archive/blogs/RoutingRules/)

### <a name="routing-scenarios"></a>Scenariusze routingu

Usługa routingu jest przydatna w następujących scenariuszach:

- Klienci mogą rozmawiać z wieloma usługami bez konieczności bezpośredniego zwracania się do nich wszystkich.

- Klienci mogą wykonywać dodatkową logikę na żądanie klienta, aby określić, gdzie go rozsyłać

- Rozkładać operacje, które klient wykonuje w wielu implementacjach usługi bez refaktoryzacji klienta.

- Klienci i usługi mogą mówić różne powiązania z różnymi ustawieniami zabezpieczeń.

- Klienci mogą być bardziej niezawodni przed awarią lub niedostępnością usług.

## <a name="wcf-discovery"></a>Odnajdywanie w programie WCF

WCF Discovery to technologia struktury, która umożliwia włączenie mechanizmu odnajdywania do infrastruktury aplikacji. Można użyć tej funkcji, aby usługa była wykrywalna i skonfigurować klientów do wyszukiwania usług. Klienci nie muszą być już zakodowane na komputerze z punktem końcowym, dzięki czemu aplikacja jest bardziej niezawodna i odporna na uszkodzenia. Odnajdowanie jest doskonałą platformą do tworzenia funkcji automatycznej konfiguracji w aplikacji.

Produkt jest zbudowany na podstawie standardu WS-Discovery. Został zaprojektowany tak, aby był interoperacyjny, rozszerzalny i ogólny. Produkt obsługuje dwa tryby pracy:

1. Zarządzane: w przypadku gdy w sieci znajduje się jednostka posiadająca wiedzę na temat istniejących usług, klienci przeszukuje ją bezpośrednio w celu uzyskania informacji. Jest to analogiczne do usługi Active Directory.

2. Ad hoc: gdzie klienci używają wiadomości multiemisji do lokalizowania usług.

Ponadto komunikaty odnajdywania są niezależną od protokołu sieciowego; można ich używać na górze dowolnego protokołu, który obsługuje wymagania dotyczące trybu. Na przykład wiadomości multiemisji odnajdywania mogą być wysyłane za pośrednictwem kanału UDP lub dowolnej innej sieci obsługującej wiadomości multiemisji. Te punkty konstrukcyjne, w połączeniu z elastycznością funkcji, pozwalają dostosować odkrycie specjalnie do rozwiązania.

### <a name="getting-started"></a>Wprowadzenie

- Dokumentacja: [WCF Discovery](../wcf/feature-details/wcf-discovery.md)

- Przykłady: [odnajdowanie (przykłady)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Scenariusze odnajdowania

Deweloper nie chce mieć twardych punktów końcowych kodu, ponieważ nie wiadomo, kiedy moja usługa będzie dostępna. Zamiast tego deweloper chce wybrać usługę w czasie wykonywania. Potrzebne jest bardziej oddzielenie, niezawodność i automatyczna konfiguracja między składnikami w aplikacji.

## <a name="tracking"></a>Śledzenie

Śledzenie przepływu pracy zapewnia wgląd w wykonanie wystąpienia przepływu pracy. Zdarzenia śledzenia są emitowane z przepływu pracy na poziomie wystąpienia przepływu pracy i podczas wykonywania działań w przepływie pracy. Uczestnik śledzenia przepływu pracy musi zostać dodany do hosta przepływu pracy, aby subskrybować rekordy śledzenia. Rekordy śledzenia są filtrowane przy użyciu profilu śledzenia. Program .NET Framework udostępnia uczestnika śledzenia ETW (Śledzenie zdarzeń dla systemu Windows), a profil podstawowy jest zainstalowany w pliku machine.config.

### <a name="getting-started"></a>Wprowadzenie

1. W programie Visual Studio 2010 utwórz projekt aplikacji usługi przepływu pracy WCF. A <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> i para zostaną umieszczone na płótnie, aby rozpocząć.

2. Otwórz web.config i dodaj zachowanie śledzenia ETW bez profilu.

    1. Używany jest profil domyślny.

    2. Otwórz przeglądarkę zdarzeń i włącz kanał analityczny w następującym węźle: **Podgląd zdarzeń,** **Dzienniki aplikacji i usług,** **Microsoft**, **Windows**, **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy pozycję **Analityczna** i wybierz polecenie **Włącz dziennik**.

    3. Uruchom usługę przepływu pracy.

    4. Obserwuj zdarzenia śledzenia przepływu pracy w podglądzie zdarzeń.

3. Przykłady: [Śledzenie](./samples/tracking.md)

4. Dokumentacja koncepcyjna: [Śledzenie i śledzenie przepływu pracy](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>Magazyn wystąpień przepływu pracy SQL

Jest <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sql server oparte implementacji magazynu wystąpień. Magazyn wystąpień przechowuje stan uruchomionego wystąpienia wraz ze wszystkimi danymi niezbędnymi do załadowania i wznowienia tego wystąpienia. Host usługi nakazuje magazynowi wystąpień, aby zapisać stan wystąpienia, jeśli przepływ pracy będzie się powtarzał, i nakazuje magazynowi wystąpienia załadowanie stanu wystąpienia po odebraniu wiadomości dla tego wystąpienia lub wygaśnięciu działania opóźnienia.

### <a name="getting-started"></a>Wprowadzenie

1. W programie Visual Studio 2012 utwórz przepływ <xref:System.Activities.Statements.Persist> pracy, który zawiera niejawne lub jawne działanie. Dodaj <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachowanie do hosta usługi przepływu pracy. Można to zrobić w kodzie lub w pliku konfiguracji aplikacji.

2. Próbki: [Trwałość](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. Dokumentacja koncepcyjna: [Magazyn wystąpień przepływu pracy SQL](sql-workflow-instance-store.md).
