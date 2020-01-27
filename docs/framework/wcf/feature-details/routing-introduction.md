---
title: Wprowadzenie do routingu
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 8ce98aab2ed14401fa7c2cbf43eb92a633fa96b0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746469"
---
# <a name="routing-introduction"></a>Wprowadzenie do routingu

Usługa routingu oferuje ogólny, podłączany pośrednik protokołu SOAP, który umożliwia kierowanie komunikatów na podstawie treści wiadomości. Za pomocą usługi routingu można utworzyć złożoną logikę routingu, która umożliwia implementowanie scenariuszy, takich jak agregacja usług, przechowywanie wersji usług, routing priorytetów i Routing multiemisji. Usługa routingu oferuje również obsługę błędów, która pozwala na skonfigurowanie list punktów końcowych kopii zapasowych, do których komunikaty są wysyłane w przypadku wystąpienia błędu podczas wysyłania do podstawowego docelowego punktu końcowego.

Ten temat jest przeznaczony dla nowych usługi routingu i obejmuje podstawową konfigurację i hosting usługi routingu.

## <a name="configuration"></a>Konfiguracja

Usługa routingu jest zaimplementowana jako usługa WCF, która udostępnia jeden lub więcej punktów końcowych usługi, które odbierają komunikaty z aplikacji klienckich i kierują komunikaty do co najmniej jednego docelowego punktu końcowego. Usługa udostępnia <xref:System.ServiceModel.Routing.RoutingBehavior>, która jest stosowana do punktów końcowych usługi udostępnianych przez usługę. To zachowanie służy do konfigurowania różnych aspektów działania usługi. Aby ułatwić konfigurację podczas korzystania z pliku konfiguracji, parametry są określone w **RoutingBehavior**. W scenariuszach opartych na kodzie te parametry byłyby określone jako część obiektu <xref:System.ServiceModel.Routing.RoutingConfiguration>, który następnie można przesłać do **RoutingBehavior**.

Podczas uruchamiania to zachowanie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, który jest używany do przetwarzania komunikatów przez protokół SOAP, do punktów końcowych klienta. Dzięki temu usługa routingu może przesyłać wiadomości do punktów końcowych, które wymagają innego elementu **MessageVersion** niż punkt końcowy, w którym wiadomość została odebrana. **RoutingBehavior** rejestruje także rozszerzenie usługi, <xref:System.ServiceModel.Routing.RoutingExtension>, która zapewnia punkt dostępności do modyfikowania konfiguracji usługi routingu w czasie wykonywania.

Klasa **zastosowano** zapewnia spójny sposób konfigurowania i aktualizowania konfiguracji usługi routingu.  Zawiera parametry, które działają jako ustawienia usługi routingu i służy do konfigurowania **RoutingBehavior** podczas uruchamiania usługi lub są przesyłane do **RoutingExtension** w celu zmodyfikowania konfiguracji routingu w czasie wykonywania.

Logika routingu używana do przeprowadzania routingu komunikatów opartych na zawartości jest definiowana przez Grupowanie wielu <xref:System.ServiceModel.Dispatcher.MessageFilter> obiektów w tabele filtrów (obiekty<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>). Komunikaty przychodzące są oceniane względem filtrów komunikatów zawartych w tabeli filtrów i dla każdego **MessageFilter** , który odpowiada komunikatowi, przekazywany do docelowego punktu końcowego. Tabela filtrów, która powinna być używana do routowania komunikatów, jest określana za pomocą **RoutingBehavior** w konfiguracji lub za pośrednictwem kodu przy użyciu obiektu **zastosowano** .

### <a name="defining-endpoints"></a>Definiowanie punktów końcowych

Chociaż może się wydawać, że należy rozpocząć konfigurację przez zdefiniowanie logiki routingu, która będzie używana, pierwszym krokiem powinno być określenie kształtu punktów końcowych, do których będą wysyłane wiadomości. Usługa routingu korzysta z kontraktów, które definiują kształt kanałów używanych do odbierania i wysyłania komunikatów, a w związku z tym kształt kanału wejściowego musi pasować do tego kanału wyjściowego.  Na przykład w przypadku kierowania do punktów końcowych, które używają kształtu kanału żądanie-odpowiedź, należy użyć zgodnego kontraktu dla przychodzących punktów końcowych, takich jak <xref:System.ServiceModel.Routing.IRequestReplyRouter>.

Oznacza to, że jeśli docelowe punkty końcowe używają kontraktów z wieloma wzorcami komunikacji (takich jak mieszanie operacji jednokierunkowych i dwukierunkowych), nie można utworzyć pojedynczego punktu końcowego usługi, który może odbierać i kierować wiadomości do wszystkich z nich. Należy określić, które punkty końcowe mają zgodne kształty i zdefiniować co najmniej jeden punkt końcowy usługi, który będzie używany do odbierania komunikatów do kierowania do docelowego punktu końcowego.

> [!NOTE]
> Podczas pracy z kontraktami, które określają wiele wzorców komunikacji (takich jak mieszanie jednokierunkowych i dwukierunkowych operacji), obejście polega na użyciu kontraktu dupleksowego w usłudze routingu, takiego jak <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. Oznacza to jednak, że powiązanie musi mieć możliwość komunikacji dwukierunkowej, co może nie być możliwe w przypadku wszystkich scenariuszy. W scenariuszach, w których nie jest to możliwe, może być konieczne nawiązanie komunikacji z wieloma punktami końcowymi lub zmodyfikowanie aplikacji.

Aby uzyskać więcej informacji na temat kontraktów routingu, zobacz [Kontrakty routingu](routing-contracts.md).

Po zdefiniowaniu punktu końcowego usługi można użyć **RoutingBehavior** do skojarzenia określonego **zastosowano** z punktem końcowym. Podczas konfigurowania usługi routingu przy użyciu pliku konfiguracji **RoutingBehavior** jest używany do określania tabeli filtrów zawierającej logikę routingu służącą do przetwarzania komunikatów odebranych w tym punkcie końcowym. Jeśli konfigurujesz usługę routingu programowo, możesz określić tabelę filtrów za pomocą **zastosowano**.

W poniższym przykładzie zdefiniowano punkty końcowe usługi i klienta, które są używane przez usługę routingu programowo i przy użyciu pliku konfiguracji.

```xml
<services>
  <!--ROUTING SERVICE -->
  <service behaviorConfiguration="routingData"
            name="System.ServiceModel.Routing.RoutingService">
    <host>
      <baseAddresses>
        <add baseAddress="http://localhost:8000/routingservice/router"/>
      </baseAddresses>
    </host>
    <!-- Define the service endpoints that are receive messages -->
    <endpoint address=""
              binding="wsHttpBinding"
              name="reqReplyEndpoint"
              contract="System.ServiceModel.Routing.IRequestReplyRouter" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<client>
<!-- Define the client endpoint(s) to route messages to -->
  <endpoint name="CalculatorService"
            address="http://localhost:8000/servicemodelsamples/service"
            binding="wsHttpBinding" contract="*" />
</client>
```

```csharp
//set up some communication defaults
string clientAddress = "http://localhost:8000/servicemodelsamples/service";
string routerAddress = "http://localhost:8000/routingservice/router";
Binding routerBinding = new WSHttpBinding();
Binding clientBinding = new WSHttpBinding();
//add the endpoint the router uses to receive messages
serviceHost.AddServiceEndpoint(
     typeof(IRequestReplyRouter),
     routerBinding,
     routerAddress);
//create the client endpoint the router routes messages to
ContractDescription contract = ContractDescription.GetContract(
     typeof(IRequestReplyRouter));
ServiceEndpoint client = new ServiceEndpoint(
     contract,
     clientBinding,
     new EndpointAddress(clientAddress));
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
….
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
//attach the behavior to the service host
serviceHost.Description.Behaviors.Add(
     new RoutingBehavior(rc));
```

Ten przykład umożliwia skonfigurowanie usługi routingu w celu uwidocznienia pojedynczego punktu końcowego z adresem `http://localhost:8000/routingservice/router`, który jest używany do odbierania komunikatów do rozesłania. Ponieważ komunikaty są kierowane do punktów końcowych żądania-odpowiedź, punkt końcowy usługi używa kontraktu <xref:System.ServiceModel.Routing.IRequestReplyRouter>. Ta konfiguracja definiuje także jeden punkt końcowy klienta `http://localhost:8000/servicemodelsample/service`, do którego są kierowane komunikaty. Tabela filtrów (niepokazywana) o nazwie "routingTable1" zawiera logikę routingu służącą do przesyłania komunikatów i jest skojarzona z punktem końcowym usługi przy użyciu **RoutingBehavior** (dla pliku konfiguracji) lub **zastosowano** (do konfiguracji programowej).

### <a name="routing-logic"></a>Logika routingu

Aby zdefiniować logikę routingu służącą do przesyłania komunikatów, należy określić, jakie dane zawarte w wiadomościach przychodzących mogą być w sposób unikatowy. Na przykład, jeśli wszystkie docelowe punkty końcowe, które mają być współużytkowane przez Ciebie te same akcje protokołu SOAP, wartość akcji zawartej w komunikacie nie jest dobrym wskaźnikiem, do którego określony punkt końcowy powinien być kierowany. Jeśli musisz jednoznacznie skierować komunikaty do jednego określonego punktu końcowego, należy odfiltrować dane, które jednoznacznie identyfikują docelowy punkt końcowy, do którego wiadomość jest kierowana.

Usługa routingu udostępnia kilka implementacji **MessageFilter** , które sprawdzają określone wartości w wiadomości, takie jak adres, Akcja, nazwa punktu końcowego, a nawet zapytanie XPath. Jeśli żadna z tych implementacji nie spełnia Twoich potrzeb, możesz utworzyć niestandardową implementację **MessageFilter** . Aby uzyskać więcej informacji na temat filtrów komunikatów i porównania implementacji używanych przez usługę routingu, zobacz [filtry komunikatów](message-filters.md) i [Wybieranie filtru](choosing-a-filter.md).

Wiele filtrów komunikatów jest zorganizowanych w tabelach filtru, które kojarzą poszczególne **MessageFilter** z docelowym punktem końcowym. Opcjonalnie można również użyć tabeli filtrów, aby określić listę punktów końcowych kopii zapasowych, które usługa routingu podejmie próbę wysłania komunikatu w przypadku niepowodzenia transmisji.

Domyślnie wszystkie filtry komunikatów w tabeli filtrów są oceniane jednocześnie; można jednak określić <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>, która powoduje, że filtry komunikatów mają być oceniane w określonej kolejności. Wszystkie wpisy o najwyższym priorytecie są oceniane jako pierwsze, a filtry komunikatów o niższych priorytetach nie są oceniane, jeśli dopasowanie zostanie znalezione na wyższym poziomie priorytetu. Aby uzyskać więcej informacji na temat tabel filtrów, zobacz [filtry komunikatów](message-filters.md).

W poniższych przykładach użyto <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, które oblicza `true` dla wszystkich komunikatów. Ten **MessageFilter** jest dodawany do tabeli filtrów "routingTable1", która kojarzy **MessageFilter** z punktem końcowym klienta o nazwie "CalculatorService". **RoutingBehavior** następnie określa, że ta tabela powinna być używana do przesyłania komunikatów przetwarzanych przez punkt końcowy usługi.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
//create the endpoint list that contains the endpoints to route to
//in this case we have only one
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();
endpointList.Add(client);
//add a MatchAll filter to the Router's filter table
//map it to the endpoint list defined earlier
//when a message matches this filter, it is sent to the endpoint contained in the list
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
```

> [!NOTE]
> Domyślnie usługa routingu szacuje tylko nagłówki wiadomości. Aby zezwolić filtrom na dostęp do treści wiadomości, należy ustawić <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> na `false`.

**Multicast**

Chociaż wiele konfiguracji usługi routingu korzysta z logiki filtru wyłącznego, która kieruje komunikaty tylko do jednego określonego punktu końcowego, może być konieczne kierowanie danego komunikatu do wielu docelowych punktów końcowych. Aby dokonać multiemisji komunikatu do wielu miejsc docelowych, muszą być spełnione następujące warunki:

- Kształt kanału nie może być odpowiedzią na żądanie (choć może być jednokierunkowa lub dwustronna), ponieważ aplikacja kliencka może odebrać tylko jedną odpowiedź w odpowiedzi na żądanie.

- Podczas oceny komunikatu wiele filtrów musi zwrócić `true`.

Jeśli te warunki są spełnione, komunikat jest kierowany do wszystkich punktów końcowych wszystkich filtrów, które mają być `true`. Poniższy przykład definiuje konfigurację routingu, która powoduje, że komunikaty są przesyłane do obu punktów końcowych, jeśli adres punktu końcowego w komunikacie jest `http://localhost:8000/routingservice/router/rounding`.

```xml
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
    <filter name="RoundingFilter1" filterType="EndpointAddress"
            filterData="http://localhost:8000/routingservice/router/rounding" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(
    "http://localhost:8000/routingservice/router/rounding")),
    roundingCalcEndpointList);
```

### <a name="soap-processing"></a>Przetwarzanie SOAP

W celu obsługi routingu komunikatów między niepodobnymi protokołami **RoutingBehavior** domyślnie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do wszystkich punktów końcowych klienta, do których są kierowane komunikaty. To zachowanie powoduje automatyczne utworzenie nowego elementu **MessageVersion** przed przekazaniem komunikatu do punktu końcowego, a także utworzenie zgodnego elementu **MessageVersion** dla dowolnego dokumentu odpowiedzi przed zwróceniem go do żądającej aplikacji klienckiej.

Kroki wykonywane w celu utworzenia nowego elementu **MessageVersion** dla wiadomości wychodzącej są następujące:

**Przetwarzanie żądania**

- Pobierz element **MessageVersion** powiązania/kanału wychodzącego.

- Pobierz czytnik treści dla oryginalnej wiadomości.

- Utwórz nową wiadomość z tą samą akcją, czytelnikem treści i nową wartość **MessageVersion**.

- Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **Addressing. None**, skopiuj nagłówki do, from, FaultTo i RelatesTo do nowej wiadomości.

- Skopiuj wszystkie właściwości wiadomości do nowej wiadomości.

- Zapisz oryginalny komunikat żądania, który ma być używany podczas przetwarzania odpowiedzi.

- Zwróć nowy komunikat żądania.

**Przetwarzanie odpowiedzi**

- Pobierz element **MessageVersion** oryginalnego komunikatu żądania.

- Pobierz czytnik treści dla odebranego komunikatu odpowiedzi.

- Utwórz nowy komunikat odpowiedzi z tą samą akcją, czytelnikem treści i elementem **MessageVersion** oryginalnego komunikatu żądania.

- Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **Addressing. None**, skopiuj nagłówki do, from, FaultTo i RelatesTo do nowej wiadomości.

- Skopiuj właściwości wiadomości do nowej wiadomości.

- Zwróć nowy komunikat odpowiedzi.

Domyślnie **SoapProcessingBehavior** jest automatycznie dodawany do punktów końcowych klienta przez <xref:System.ServiceModel.Routing.RoutingBehavior> podczas uruchamiania usługi; można jednak kontrolować, czy przetwarzanie protokołu SOAP jest dodawane do wszystkich punktów końcowych klienta przy użyciu właściwości <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A>. Możesz również dodać zachowanie bezpośrednio do określonego punktu końcowego i włączać lub wyłączać to zachowanie na poziomie punktu końcowego, jeśli jest wymagany bardziej szczegółowy formant przetwarzania protokołu SOAP.

> [!NOTE]
> Jeśli przetwarzanie protokołu SOAP jest wyłączone dla punktu końcowego, który wymaga innego elementu MessageVersion niż oryginalny komunikat żądania, należy podać niestandardowy mechanizm wykonywania wszelkich modyfikacji protokołu SOAP, które są wymagane przed wysłaniem komunikatu do docelowy punkt końcowy.

W poniższych przykładach Właściwość **soapProcessingEnabled** służy do zapobiegania automatycznemu dodawaniu **SoapProcessingBehavior** do wszystkich punktów końcowych klienta.

```xml
<behaviors>
  <!--default routing service behavior definition-->
  <serviceBehaviors>
    <behavior name="routingConfiguration">
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

```csharp
//create the default RoutingConfiguration
RoutingConfiguration rc = new RoutingConfiguration();
rc.SoapProcessingEnabled = false;
```

### <a name="dynamic-configuration"></a>Konfiguracja dynamiczna

Po dodaniu kolejnych punktów końcowych klienta lub konieczności zmodyfikowania filtrów używanych do przesyłania komunikatów należy mieć możliwość dynamicznego aktualizowania konfiguracji w czasie wykonywania, aby zapobiec przerywaniu usługi do punktów końcowych, w których obecnie są wysyłane komunikaty Usługa routingu. Modyfikowanie pliku konfiguracji lub kodu aplikacji hosta nie zawsze jest wystarczające, ponieważ każda metoda wymaga odzyskania aplikacji, co może prowadzić do potencjalnej utraty wszelkich komunikatów, które są obecnie przesyłane i potencjalną przyczyną przestoju oczekiwanie na ponowne uruchomienie usługi.

**Zastosowano** można modyfikować tylko programowo. Podczas początkowego konfigurowania usługi za pomocą pliku konfiguracji można zmodyfikować konfigurację w czasie wykonywania przez skonstruowanie nowego **zastosowano** i przekazanie go jako parametru do metody <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> udostępnionej przez rozszerzenie usługi <xref:System.ServiceModel.Routing.RoutingExtension>. Wszystkie komunikaty w trakcie przesyłania są nadal kierowane przy użyciu poprzedniej konfiguracji, a komunikaty odebrane po wywołaniu **ApplyConfiguration** używają nowej konfiguracji. Poniższy przykład ilustruje tworzenie wystąpienia usługi routingu, a następnie modyfikowanie konfiguracji.

```csharp
RoutingConfiguration routingConfig = new RoutingConfiguration();
routingConfig.RouteOnHeadersOnly = true;
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
RoutingBehavior routing = new RoutingBehavior(routingConfig);
routerHost.Description.Behaviors.Add(routing);
routerHost.Open();
// Construct a new RoutingConfiguration
RoutingConfiguration rc2 = new RoutingConfiguration();
ServiceEndpoint clientEndpoint = new ServiceEndpoint();
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();
// Add filters to the FilterTable in the new configuration
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint });
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint2 });
rc2.RouteOnHeadersOnly = false;
// Apply the new configuration to the Routing Service hosted in
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);
```

> [!NOTE]
> Podczas aktualizowania usługi routingu w ten sposób można tylko przekazać nową konfigurację. Nie można modyfikować tylko wybranych elementów bieżącej konfiguracji lub dołączać nowych wpisów do bieżącej konfiguracji; należy utworzyć i przekazać nową konfigurację, która zastąpi istniejącą.

> [!NOTE]
> Wszystkie sesje otwarte przy użyciu poprzedniej konfiguracji nadal używają poprzedniej konfiguracji. Nowa konfiguracja jest używana tylko przez nowe sesje.

## <a name="error-handling"></a>Obsługa błędów

Jeśli podczas próby wysłania komunikatu wystąpił <xref:System.ServiceModel.CommunicationException>, zostanie przeprowadzona obsługa błędów. Te wyjątki zwykle wskazują, że wystąpił problem podczas próby komunikacji ze zdefiniowanym punktem końcowym klienta, takim jak <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>lub <xref:System.ServiceModel.CommunicationObjectFaultedException>. Obsługa błędów — kod również będzie przechwytywać i próbować ponowić próbę wysłania, gdy wystąpi <xref:System.TimeoutException>, który jest innym wspólnym wyjątkiem, który nie pochodzi od **CommunicationException**.

Po wystąpieniu jednego z powyższych wyjątków usługa routingu zostaje przełączona w tryb failover do listy punktów końcowych kopii zapasowych. Jeśli wszystkie punkty końcowe kopii zapasowej zakończą się niepowodzeniem z błędem komunikacji lub jeśli punkt końcowy zwróci wyjątek wskazujący awarię w ramach usługi docelowej, usługa routingu zwróci błąd do aplikacji klienckiej.

> [!NOTE]
> Funkcja obsługi błędów przechwytuje i obsługuje wyjątki występujące podczas próby wysłania komunikatu i próby zamknięcia kanału. Kod obsługi błędu nie jest przeznaczony do wykrywania lub obsługi wyjątków utworzonych przez punkty końcowe aplikacji, z którymi się komunikują. <xref:System.ServiceModel.FaultException> zgłoszone przez usługę pojawia się w usłudze routingu jako **FaultMessage** i jest przepływa z powrotem do klienta.
>
> Jeśli wystąpi błąd, gdy usługa routingu próbuje przekazać komunikat, może zostać wyświetlony <xref:System.ServiceModel.FaultException> po stronie klienta, a nie <xref:System.ServiceModel.EndpointNotFoundException>, zwykle w przypadku braku usługi routingu. Usługa routingu może w ten sposób maskować wyjątki i nie zapewniać pełnej przejrzystości, chyba że zostanie sprawdzona zagnieżdżonych wyjątków.

### <a name="tracing-exceptions"></a>Śledzenie wyjątków

Gdy wysyłanie komunikatu do punktu końcowego na liście kończy się niepowodzeniem, usługa routingu śledzi otrzymane dane wyjątku i dołącza szczegóły wyjątku jako właściwość komunikatu o nazwie **Exceptions**. Pozwala to zachować dane wyjątku i umożliwia użytkownikom dostęp programistyczny za pomocą Inspektora komunikatów.  Dane wyjątku są przechowywane na komunikat w słowniku, który mapuje nazwę punktu końcowego na szczegóły wyjątku napotkane podczas próby wysłania do niego komunikatu.

### <a name="backup-endpoints"></a>Punkty końcowe kopii zapasowej

Każdy wpis filtru w tabeli filtrów może opcjonalnie określić listę punktów końcowych kopii zapasowych, które są używane w przypadku niepowodzenia transmisji podczas wysyłania do podstawowego punktu końcowego. Jeśli wystąpi awaria, usługa routingu próbuje przesłać komunikat do pierwszego wpisu na liście punktów końcowych kopii zapasowych. Jeśli próba wysłania spowoduje również awarię transmisji, zostanie podjęta próba następnego punktu końcowego z listy kopii zapasowych. Usługa routingu kontynuuje wysyłanie komunikatów do każdego punktu końcowego na liście do momentu pomyślnego odebrania komunikatu. wszystkie punkty końcowe zwracają błąd transmisji lub w punkcie końcowym jest zwracany błąd niebędący przekazaniem.

Poniższe przykłady umożliwiają skonfigurowanie usługi routingu do korzystania z listy kopii zapasowych.

```xml
<routing>
  <filters>
    <!-- Create a MatchAll filter that catches all messages -->
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <!-- Set up the Routing Service's Message Filter Table -->
    <filterTable name="filterTable1">
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
        <!-- Listed in the backupEndpointList -->
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
    </filterTable>
  </filterTables>
  <!-- Create the backup endpoint list -->
  <backupLists>
    <!-- Add an endpoint list that contains the backup destinations -->
    <backupList name="backupEndpointList">
      <add endpointName="realDestination" />
      <add endpointName="backupDestination" />
    </backupList>
  </backupLists>
</routing>
```

```csharp
//create the endpoint list that contains the service endpoints we want to route to
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();
//add the endpoints in the order that the Routing Service should contact them
//first add the endpoint that we know is down
//clearly, normally you wouldn't know that this endpoint was down by default
backupList.Add(fakeDestination);
//then add the real Destination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationException when sending
//to the previous endpoint in the list.
backupList.Add(realDestination);
//add the backupDestination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationsException when sending
//to the previous endpoints in the list
backupList.Add(backupDestination);
//create the default RoutingConfiguration option
RoutingConfiguration rc = new RoutingConfiguration();
//add a MatchAll filter to the Routing Configuration's filter table
//map it to the list of endpoints defined above
//when a message matches this filter, it is sent to the endpoints in the list in order
//if an endpoint is down or does not respond (which the first endpoint won't
//since the client does not exist), the Routing Service automatically moves the message
//to the next endpoint in the list and try again.
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);
```

### <a name="supported-error-patterns"></a>Obsługiwane wzorce błędów

W poniższej tabeli opisano wzorce zgodne z użyciem list punktów końcowych kopii zapasowych oraz uwagi opisujące szczegóły obsługi błędów dla określonych wzorców.

|Wzorzec|Sesja|Transakcja|Odbieranie kontekstu|Lista kopii zapasowych jest obsługiwana|Uwagi|
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|
|Komunikacja jednokierunkowa||||Tak|Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej. Jeśli ten komunikat jest multiemisją, tylko komunikat w kanale zakończonym niepowodzeniem jest przenoszony do jego miejsca docelowego kopii zapasowej.|
|Komunikacja jednokierunkowa||✔️||Nie|Wyjątek jest zgłaszany, a transakcja jest wycofywana.|
|Komunikacja jednokierunkowa|||✔️|Tak|Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej. Po pomyślnym odebraniu komunikatu Ukończ wszystkie konteksty odbierania. Jeśli komunikat nie został pomyślnie odebrany przez żaden punkt końcowy, nie należy kończyć kontekstu odbierania.<br /><br /> Gdy ten komunikat jest multiemisją, kontekst odbierania jest wykonywany tylko wtedy, gdy komunikat zostanie pomyślnie odebrany przez co najmniej jeden punkt końcowy (podstawowy lub zapasowy). Jeśli żaden z punktów końcowych we wszystkich ścieżkach multiemisji nie otrzyma komunikatu, nie wypełniaj kontekstu odbierania.|
|Komunikacja jednokierunkowa||✔️|✔️|Tak|Przerwij poprzednią transakcję, Utwórz nową transakcję i ponownie Wyślij wszystkie komunikaty. Komunikaty, które napotkały błąd, są przesyłane do miejsca docelowego kopii zapasowej.<br /><br /> Po utworzeniu transakcji, w której wszystkie operacje kończą się powodzeniem, Wypełnij konteksty odbierania i zatwierdź transakcję.|
|Komunikacja jednokierunkowa|✔️|||Tak|Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej. W scenariuszu multiemisji tylko komunikaty w sesji, które napotkały błąd lub w sesji, której zamknięcie nie powiodło się, są ponownie wysyłane do miejsc docelowych kopii zapasowych.|
|Komunikacja jednokierunkowa|✔️|✔️||Nie|Wyjątek jest zgłaszany, a transakcja jest wycofywana.|
|Komunikacja jednokierunkowa|✔️||✔️|Tak|Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej. Gdy wszystkie komunikaty zostaną zakończone bez błędu, sesja wskazuje, że nie ma więcej komunikatów, a usługa routingu pomyślnie zamknie wszystkie wychodzące kanały sesji, wszystkie konteksty odbioru są wykonywane i zamknięto kanał sesji przychodzącej.|
|Komunikacja jednokierunkowa|✔️|✔️|✔️|Tak|Przerwij bieżącą transakcję i Utwórz nową. Wyślij ponownie wszystkie poprzednie wiadomości w sesji. Po utworzeniu transakcji, w której wszystkie komunikaty zostały pomyślnie wysłane, a sesja wskazuje, że nie ma więcej komunikatów, wszystkie kanały sesji wychodzącej są zamknięte, a wszystkie, konteksty odbierania zostały zakończone z transakcją, kanał sesji przychodzącej to zamknięte, a transakcja jest zatwierdzona.<br /><br /> Gdy sesje są multiemisją, komunikaty, które nie miały błędu, są ponownie wysyłane do tego samego miejsca docelowego, co wcześniej, a komunikaty, które napotkały błąd, są wysyłane do miejsc docelowych kopii zapasowych.|
|Dwukierunkowa||||Tak|Wyślij do miejsca docelowego kopii zapasowej.  Gdy kanał zwróci komunikat odpowiedzi, zwróć odpowiedź do oryginalnego klienta.|
|Dwukierunkowa|✔️|||Tak|Wyślij wszystkie komunikaty z kanału do miejsca docelowego kopii zapasowej.  Gdy kanał zwróci komunikat odpowiedzi, zwróć odpowiedź do oryginalnego klienta.|
|Dwukierunkowa||✔️||Nie|Wyjątek jest zgłaszany, a transakcja jest wycofywana.|
|Dwukierunkowa|✔️|✔️||Nie|Wyjątek jest zgłaszany, a transakcja jest wycofywana.|
|Dupleks||||Nie|Komunikacja niezgodna z dupleksem nie jest obecnie obsługiwana.|
|Dupleks|✔️|||Tak|Wyślij do miejsca docelowego kopii zapasowej.|

## <a name="hosting"></a>Hosting

Ponieważ usługa routingu jest zaimplementowana jako usługa WCF, musi być samodzielnie hostowana w aplikacji lub hostowana przez usługi IIS lub była. Zaleca się, aby usługa routingu była hostowana w usługach IIS, WAS lub w aplikacji usługi systemu Windows, aby korzystać z funkcji automatycznego uruchamiania i zarządzania cyklem życia dostępnych w tych środowiskach hostingu.

Poniższy przykład ilustruje hosting usługi routingu w aplikacji.

```csharp
using (ServiceHost serviceHost =
                new ServiceHost(typeof(RoutingService)))
```

Aby hostować usługę routingu w ramach usług IIS lub WAS, należy utworzyć plik usługi (. svc) lub użyć aktywacji usługi opartej na konfiguracji. W przypadku korzystania z pliku usługi należy określić <xref:System.ServiceModel.Routing.RoutingService> przy użyciu parametru usługi. Poniższy przykład zawiera przykładowy plik usługi, który może służyć do hostowania usługi routingu w usługach IIS lub WAS.

```aspx-csharp
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,
     PublicKeyToken=31bf3856ad364e35" %>
```

## <a name="routing-service-and-impersonation"></a>Usługa routingu i personifikacja

Usługa routingu WCF może być używana z personifikacją zarówno w przypadku wysyłania, jak i otrzymywania wiadomości. Wszystkie typowe ograniczenia dotyczące personifikacji systemu Windows mają zastosowanie. Jeśli konieczne jest skonfigurowanie uprawnień usługi lub konta do korzystania z personifikacji podczas pisania własnej usługi, należy wykonać te same kroki, aby użyć personifikacji w usłudze routingu. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](delegation-and-impersonation-with-wcf.md).

Personifikacja w usłudze routingu wymaga użycia personifikacji ASP.NET w trybie zgodności ASP.NET lub użycia poświadczeń systemu Windows, które zostały skonfigurowane w celu zezwolenia na personifikację. Aby uzyskać więcej informacji na temat trybu zgodności ASP.NET, zobacz [usługi WCF i ASP.NET](wcf-services-and-aspnet.md).

> [!WARNING]
> Usługa routingu WCF nie obsługuje personifikacji z uwierzytelnianiem podstawowym.

Aby użyć personifikacji ASP.NET w usłudze routingu, Włącz tryb zgodności ASP.NET w środowisku hostingu usługi. Usługa routingu została już oznaczona jako zezwalająca na tryb zgodności ASP.NET, a personifikacja zostanie automatycznie włączona. Personifikacja jest jedynym obsługiwanym wykorzystaniem integracji ASP.NET z usługą routingu.

Aby użyć personifikacji poświadczeń systemu Windows przy użyciu usługi routingu, należy skonfigurować zarówno poświadczenia, jak i usługę. Obiekt poświadczeń klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, do którego można uzyskać dostęp z <xref:System.ServiceModel.ChannelFactory>) definiuje Właściwość <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>, która musi być ustawiona, aby zezwalać na personifikację. Na koniec usługi należy skonfigurować zachowanie <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>, aby ustawić `ImpersonateCallerForAllOperations` `true`. Usługa routingu używa tej flagi, aby zdecydować, czy należy utworzyć klientów do przekazywania komunikatów z włączoną personifikacją.

## <a name="see-also"></a>Zobacz także

- [Filtry komunikatów](message-filters.md)
- [Kontrakty routingu](routing-contracts.md)
- [Wybieranie filtru](choosing-a-filter.md)
