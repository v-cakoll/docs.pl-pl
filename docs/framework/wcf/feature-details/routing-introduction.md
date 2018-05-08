---
title: Wprowadzenie do routingu
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 3ee7ea8271df47354a0897434bf8f203eaf09a51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="routing-introduction"></a>Wprowadzenie do routingu
Usługa routingu zawiera ogólne podłączany SOAP pośredniczące umożliwiającej przesyłania wiadomości, na podstawie zawartości wiadomości. Usługa routingu umożliwia tworzenie złożonej logiki routingu, która umożliwia Implementowanie scenariuszy, takich jak usługi agregacji, przechowywanie wersji usługi routingu priorytet i routing multiemisji. Usługa routingu znajdują się również błąd obsługi, który pozwala zdefiniować listę kopii zapasowych punktów końcowych, do której komunikaty są wysyłane, jeśli wystąpi błąd podczas wysyłania do głównej docelowego punktu końcowego.  
  
 Ten temat jest przeznaczony dla osób jesteś nowym użytkownikiem usługi routingu i obejmuje podstawowej konfiguracji i obsługi usługi routingu.  
  
## <a name="configuration"></a>Konfiguracja  
 Usługa routingu jest implementowany jako ujawniający jeden lub więcej punktów końcowych usługi odbierać komunikaty z aplikacji klienckich, które rozsyłania komunikatów do co najmniej jednego docelowego punktów końcowych usługi WCF. Udostępnia usługę <xref:System.ServiceModel.Routing.RoutingBehavior>, która jest stosowana do punktów końcowych usług udostępnianych przez usługę. To zachowanie jest używany do konfigurowania różnych aspektów sposób działania usługi. W celu ułatwienia konfiguracji przy użyciu pliku konfiguracji, parametry są określone na **RoutingBehavior**. W scenariuszach opartych na kodzie te parametry zostałaby określona jako część <xref:System.ServiceModel.Routing.RoutingConfiguration> obiektu, który można następnie przekazać do **RoutingBehavior**.  
  
 Przy uruchamianiu tego zachowania dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, które jest używane do przetwarzania protokołu SOAP wiadomości do punktów końcowych klienta. Dzięki temu usługa routingu do przesyłania wiadomości do punktów końcowych, które wymagają innego **MessageVersion** niż wiadomość została odebrana za pośrednictwem punktu końcowego. **RoutingBehavior** również rejestruje rozszerzenie usługi <xref:System.ServiceModel.Routing.RoutingExtension>, który udostępnia punkt ułatwień dostępu dla modyfikowania konfiguracji usługi routingu w czasie wykonywania.  
  
 **Konfigurację** klasy zapewnia spójny sposób konfigurowania i aktualizowania konfiguracji usługi routingu.  Zawiera parametrów, które działają jako ustawień usługi Routing i służy do konfigurowania **RoutingBehavior** po uruchomieniu usługi lub są przekazywane do **rozszerzenia RoutingExtension** do modyfikowania routingu Konfiguracja w czasie wykonywania.  
  
 Logiki routingu, używany do wykonywania na podstawie zawartości routing komunikatów jest zdefiniowany przez grupowanie wielu <xref:System.ServiceModel.Dispatcher.MessageFilter> obiektów do filtrowania tabele (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> obiektów). Komunikaty przychodzące są oceniane przed filtry komunikatów zawartych w tabeli filtrów i dla każdego **MessageFilter** odpowiadającego wiadomości przesyłane dalej do docelowego punktu końcowego. Określono tabeli filtrów, które mają być używane do przesyłania wiadomości za pomocą **RoutingBehavior** w konfiguracji lub za pomocą kodu przy użyciu **konfigurację** obiektu.  
  
### <a name="defining-endpoints"></a>Definiowanie punktów końcowych  
 Gdy może wydawać się, że powinien rozpocząć konfigurację, definiując logiki routingu, które będą używane, pierwszym krokiem faktycznie powinno być ustalenie kształt będzie rozesłania wiadomości do punktów końcowych. Usługa routingu używa umów, które definiują kształtu kanały używane w celu odbierania i wysyłania wiadomości, a w związku z tym kształtu kanał wejściowy musi być zgodna z kanał wyjściowy.  Na przykład, jeśli routingu do punktów końcowych używających kształtu kanału "żądanie-odpowiedź" konieczne jest użycie zgodne kontraktu dla ruchu przychodzącego punktów końcowych, takich jak <xref:System.ServiceModel.Routing.IRequestReplyRouter>.  
  
 Oznacza to, że docelowy punktów końcowych za pomocą kontraktów wielu wzorców komunikacji (na przykład równoczesne używanie operacji jednokierunkowych i dwukierunkowych), nie można utworzyć pojedynczą usługę punktu końcowego, który może odbierać i kierowania wiadomości do wszystkich z nich. Należy określić, które punkty końcowe mają niezgodne kształtów i punkty końcowe usługi, które będą używane do odbierania wiadomości będzie kierowany do punktów końcowych docelowego.  
  
> [!NOTE]
>  Podczas pracy z umów, które określają wielu wzorców komunikacji (na przykład różnych operacji jednokierunkowych i dwukierunkowych), obejście tego problemu jest użycie kontraktu dwukierunkowego usługa routingu, takich jak <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. Jednak oznacza to, że powiązanie musi umożliwiać komunikację dupleksową, może nie być możliwe w przypadku wszystkich scenariuszy. W scenariuszach, w którym nie jest to możliwe factoring komunikacji do wielu punktów końcowych lub modyfikowania aplikacji może być konieczne.  
  
 Aby uzyskać więcej informacji na temat kontrakty routingu, zobacz [kontrakty routingu](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Po zdefiniowaniu punktu końcowego usługi można użyć **RoutingBehavior** do skojarzenia z konkretną **konfigurację** z punktem końcowym. Podczas konfigurowania usługi routingu przy użyciu pliku konfiguracji **RoutingBehavior** służy do określania tabeli filtru, która zawiera logikę routingu używane do przetwarzania komunikatów odebranych na tym punkcie końcowym. Jeśli konfigurujesz usługę Routing programowo tabeli filtrów można określić za pomocą **konfigurację**.  
  
 W poniższym przykładzie zdefiniowano punktów końcowych usługi i klienta, które są używane przez usługę Routing programowo i za pomocą pliku konfiguracji.  
  
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
  
 Ten przykład konfiguruje usługi routingu do udostępnienia jeden punkt końcowy o adresie "http://localhost:8000/routingservice/router", który jest używany do odbierania wiadomości przesłana. Ponieważ komunikaty są kierowane do punktów końcowych żądanie odpowiedź, korzysta z punktem końcowym usługi <xref:System.ServiceModel.Routing.IRequestReplyRouter> kontraktu. Ta konfiguracja określa również punkt końcowy jednego klienta "http://localhost:8000/servicemodelsample/service" czy komunikaty są kierowane do. Tabela filtru (tego nie pokazano) o nazwie "routingTable1" zawiera logikę routingu umożliwia rozsyłanie wiadomości i jest skojarzona z punktu końcowego usługi za pomocą **RoutingBehavior** (w przypadku pliku konfiguracji) lub  **Konfigurację** (dla trybu).  
  
### <a name="routing-logic"></a>Logiki routingu  
 Aby zdefiniować routingu logikę używaną do wyznaczania tras wiadomościom, należy określić danych zawartych w wiadomości przychodzących, które można jednoznacznie reagować. Na przykład jeśli wszystkich miejsce docelowe punktów końcowych, które są routingu, aby udostępnić te same akcje SOAP wartość akcję zawarte w wiadomości nie jest dobry wskaźnik określonego punktu końcowego, które wiadomości powinny być kierowane do. Jeśli wiadomości musi jednoznacznie kierować do określonych punktów końcowych, należy filtrować na danych, który unikatowo identyfikuje docelowego punktu końcowego, że wiadomość jest kierowany do.  
  
 Usługa routingu udostępnia wiele **MessageFilter** wdrożenia, sprawdź wartości określone w wiadomości, takie jak adres, akcji, nazwy punktu końcowego lub nawet Kwerenda XPath. Jeśli żadna z tych implementacji nie spełnia Twoje potrzeby możesz utworzyć niestandardowy **MessageFilter** implementacji. Aby uzyskać więcej informacji na temat filtry komunikatów i porównanie implementacje używane przez usługę Routing zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md) i [Wybieranie filtra](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).  
  
 Wiele filtrów wiadomości są zorganizowanych w tabelach filtru skojarzyć każdy **MessageFilter** z docelowym punktem końcowym. Opcjonalnie tabeli filtrów mogą służyć do określania listy punktów końcowych kopii zapasowych, które usługa routingu podejmie próbę wysłania wiadomości do awarii transmisji.  
  
 Domyślnie wszystkie filtry komunikatów w tabeli filtrów są oceniane równocześnie; można jednak określić <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> , która powoduje filtry komunikatów, które ma zostać obliczone w określonej kolejności. Wszystkie pozycje o najwyższym priorytecie są oceniane najpierw, a filtry komunikatów niższe priorytetów nie są oceniane, gdy dopasowanie znajduje się na wyższym poziomie priorytetu. Aby uzyskać więcej informacji o tabelach filtru, zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 W poniższych przykładach użyto <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, która daje w wyniku `true` dla wszystkich wiadomości. To **MessageFilter** zostanie dodany do tabeli filtru "routingTable1", co umożliwia skojarzenie **MessageFilter** z punktem końcowym klienta o nazwie "CalculatorService". **RoutingBehavior** następnie określa, że ta tabela ma być używany do przesyłania wiadomości przetworzonych przez punkt końcowy usługi.  
  
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
>  Domyślnie usługa routingu oblicza tylko nagłówki komunikatu. Aby umożliwić filtry, aby uzyskać dostęp do treści komunikatu, należy ustawić <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> do `false`.  
  
 **Multiemisji**  
  
 Gdy wielu konfiguracji usługa routingu, użyj logiki wyłączny filtr, który kieruje komunikaty do tylko jednej określonego punktu końcowego, konieczne może być kierować danej wiadomości do wielu punktów końcowych docelowego. Do obsługi multiemisji wiadomości do wielu miejsc docelowych muszą być spełnione następujące warunki:  
  
-   Kształtu kanału nie może być "żądanie-odpowiedź" (mimo że może być jednokierunkowe lub dupleksowy,), ponieważ tylko jedną odpowiedź może zostać odebrany przez aplikację klienta w odpowiedzi na żądanie.  
  
-   Wiele filtrów musi zwracać `true` podczas oceniania wiadomości.  
  
 Jeśli te warunki są spełnione, wiadomość jest kierowany do wszystkich punktów końcowych wszystkie filtry, których ocena ma `true`. W poniższym przykładzie zdefiniowano konfiguracji routingu, która powoduje występowanie rozsyłane do obu punktów końcowych, jeśli adres punktu końcowego w komunikacie http://localhost:8000/routingservice/router/rounding.  
  
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
  
### <a name="soap-processing"></a>Przetwarzania protokołu SOAP  
 Aby obsługiwać routing wiadomości między niepodobnych protokołów **RoutingBehavior** domyślnie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do wszystkich punktów końcowych klienta, które komunikaty są kierowane do. To zachowanie automatycznie tworzy nowy **MessageVersion** przed routing wiadomości do punktu końcowego, a także tworzenie zgodnego **MessageVersion** dla każdego dokumentu odpowiedzi przed przywróceniem go do żądania aplikacji klienckiej.  
  
 Etapy, aby utworzyć nową **MessageVersion** dla komunikatu wychodzącego są następujące:  
  
 **Przetwarzanie żądania**  
  
-   Pobierz **MessageVersion** wychodzącego powiązania/kanału.  
  
-   Pobierz odczytujący treść oryginalnej wiadomości.  
  
-   Utwórz nową wiadomość z tą samą akcją, odczytujący treść i nowy **MessageVersion**.  
  
-   Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, skopiować do, z FaultTo i nagłówków RelatesTo do nowej wiadomości.  
  
-   Skopiuj wszystkie właściwości komunikatu do nowego komunikatu.  
  
-   Przechowywanie na pierwotny komunikat żądania do użycia podczas przetwarzania odpowiedzi.  
  
-   Zwraca nowy komunikat żądania.  
  
 **Przetwarzanie odpowiedzi**  
  
-   Pobierz **MessageVersion** oryginalnego komunikatu żądania.  
  
-   Pobierz odczytujący treść wiadomości odebranej odpowiedzi.  
  
-   Utwórz nowy komunikat odpowiedzi z tą samą akcją odczytujący treść i **MessageVersion** oryginalnego komunikatu żądania.  
  
-   Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, skopiować do, z FaultTo i nagłówków RelatesTo do nowej wiadomości.  
  
-   Skopiuj właściwości wiadomości na nowy komunikat.  
  
-   Zwraca nowy komunikat odpowiedzi.  
  
 Domyślnie **SoapProcessingBehavior** jest automatycznie dodawany do punktów końcowych klienta przez <xref:System.ServiceModel.Routing.RoutingBehavior> podczas uruchamiania usługi; jednak można kontrolować, czy przetwarzania protokołu SOAP jest dodawane do wszystkich punktów końcowych klienta przy użyciu <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> właściwości. Można również dodać zachowanie bezpośrednio do określonego punktu końcowego i włączyć lub wyłączyć to zachowanie na poziomie punktu końcowego, jeśli wymagana jest większą kontrolę przetwarzania protokołu SOAP.  
  
> [!NOTE]
>  W przypadku przetwarzania protokołu SOAP jest wyłączone dla punktu końcowego, który wymaga innego MessageVersion niż oryginalny komunikat żądania, należy podać niestandardowy mechanizm wszelkie modyfikacje protokołu SOAP, które są wymagane przed wysłaniem wiadomości docelowy punkt końcowy.  
  
 W poniższych przykładach **soapProcessingEnabled** właściwość jest używana w celu zapobieżenia **SoapProcessingBehavior** z automatycznie dodawane do wszystkich punktów końcowych klienta.  
  
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
  
### <a name="dynamic-configuration"></a>Konfiguracji dynamicznej  
 Podczas dodawania punktów końcowych klienta dodatkowych, lub konieczne zmodyfikowanie filtry, które są używane do przesyłania wiadomości, musi mieć sposób, aby zaktualizować konfigurację dynamicznie w czasie wykonywania, aby zapobiec przerywania usługi do punktów końcowych, które obecnie odbieranie komunikatów za pośrednictwem Usługa routingu. Modyfikowanie pliku konfiguracji lub kod aplikacji hosta nie zawsze jest wystarczające, ponieważ każda z tych metod wymaga aplikacji, co może spowodować ryzyka utraty żadnych wiadomości w przesyłania oraz możliwości wystąpienia przestoju podczas odtwarzania Oczekiwanie na ponowne uruchomienie usługi.  
  
 Można modyfikować tylko **konfigurację** programowo. Mimo że początkowo możesz skonfigurować usługę przy użyciu pliku konfiguracji, można modyfikować tylko konfiguracji w czasie wykonywania tworząc nową **RoutingConfigution** i przekazaniem go jako parametr <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> — metoda udostępniany przez <xref:System.ServiceModel.Routing.RoutingExtension> obsługi rozszerzenia. Obecnie wszystkie wiadomości w dalszym ciągu przesłane za pomocą poprzedniej konfiguracji podczas komunikatów odebranych po wywołaniu **ApplyConfiguration** korzystać z nowej konfiguracji. W poniższym przykładzie pokazano tworzenie wystąpienia usługi Routing i następnie modyfikowania konfiguracji.  
  
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
>  Podczas aktualizacji usługi routingu w ten sposób jest tylko możliwych do przekazania nowej konfiguracji. Nie można modyfikować tylko elementy bieżącej konfiguracji lub dołączenie nowych wpisów do bieżącej konfiguracji. należy utworzyć i przekazać nowej konfiguracji, który zastąpi istniejącą.  
  
> [!NOTE]
>  Wszystkie sesje otwartego przy użyciu poprzedniej konfiguracji nadal przy użyciu poprzedniej konfiguracji. Nowa konfiguracja jest używana tylko w nowej sesji.  
  
## <a name="error-handling"></a>Obsługa błędów  
 Jeśli istnieją <xref:System.ServiceModel.CommunicationException> napotkano podczas próby wysłania wiadomości, miejsce do obsługi błędów. Tych wyjątków zwykle oznaczają, że wystąpił problem podczas próby komunikacji z punktem końcowym zdefiniowanych klienta, takich jak <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, lub <xref:System.ServiceModel.CommunicationObjectFaultedException>. Obsługa kod błędu zostanie również catch i podejmować próbę, gdy wysyłanie <xref:System.TimeoutException> występuje, który jest inny wspólnej wyjątek, który nie pochodzi od **communicationexception —**.  
  
 Występuje w jednym z powyższych wyjątków, usługa routingu nie powiedzie się za pośrednictwem do listy punktów końcowych kopii zapasowej. Jeśli wszystkie punkty końcowe kopii zapasowej zakończyć się niepowodzeniem z błędem łączności, lub jeśli punkt końcowy zwraca wyjątek, który wskazuje błąd w ramach usługi docelowej, usługa routingu zwraca błąd do aplikacji klienckiej.  
  
> [!NOTE]
>  Funkcja obsługi błędów przechwytuje i obsługi wyjątków występujących podczas próby wysłania wiadomości i próba zamknięcia kanału. Kod obsługi błędów nie jest przeznaczona do wykrycia lub obsługi wyjątków utworzone przez punkty końcowe aplikacji, który komunikuje się z; <xref:System.ServiceModel.FaultException> zgłaszanych przez usługi pojawia się usługa routingu jako **FaultMessage** i jest umieszczane do klienta.  
>   
>  Jeśli wystąpi błąd usługi routingu próba przekazywania wiadomości, mogą wystąpić <xref:System.ServiceModel.FaultException> po stronie klienta, a nie <xref:System.ServiceModel.EndpointNotFoundException> zwykle jak w przypadku braku usługi routingu. Usługa routingu może w związku z tym maskować wyjątki i zapewnia pełną przezroczystość chyba, że należy zbadać wyjątków zagnieżdżonych.  
  
### <a name="tracing-exceptions"></a>Śledzenie wyjątków  
 Podczas wysyłania komunikatu do punktu końcowego na liście nie powiedzie się, usługa routingu śledzi wynikowe dane wyjątku i dołącza szczegóły wyjątku jako właściwość komunikatu o nazwie **wyjątki**. To zachowuje dane wyjątku i zezwala na dostęp programistyczny użytkownika, za pomocą Inspektora wiadomości.  Dane wyjątku jest przechowywany na jeden komunikat w słownik, który mapuje nazwę punktu końcowego szczegóły wyjątku podczas próby wysłania wiadomości do niej.  
  
### <a name="backup-endpoints"></a>Punkty końcowe kopii zapasowej  
 Każdego wpisu w tabeli filtrów można opcjonalnie określić listę punktów końcowych kopii zapasowej, które są używane w przypadku niepowodzenia przesyłania przy wysyłaniu do podstawowego punktu końcowego. Jeśli wystąpi błąd takie, usługa routingu podejmuje próbę przesłania wiadomości do pierwszej pozycji na liście zapasowego punktu końcowego. Jeśli ta próba wysłania również napotka błąd transmisji, zostanie podjęta próba następnego punktu końcowego na liście kopii zapasowej. Usługa routingu nadal wysyłanie komunikatu do każdego punktu końcowego na liście do momentu wiadomość została odebrana pomyślnie, wszystkie punkty końcowe zwraca błąd transmisji lub niesprawności — jest zwracana przez punkt końcowy.  
  
 W poniższych przykładach konfigurowane usługa routingu, aby użyć listy kopii zapasowych.  
  
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
  
### <a name="supported-error-patterns"></a>Błąd obsługiwane wzorce  
 W poniższej tabeli opisano wzorców, które są zgodne z użyciem list zapasowego punktu końcowego, oraz informacje opisujące szczegóły obsługę błędów dla określonych wzorców.  
  
|Wzorzec|Sesja|Transakcja|Kontekstu odbierania|Obsługiwane listy kopii zapasowych|Uwagi|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Komunikacja jednokierunkowa||||Tak|Próbuje ponownie wysłać wiadomość na zapasowego punktu końcowego. Jeśli ten komunikat jest multiemisji, tylko wiadomość kanałem nie powiodło się zostaje przeniesiona do miejsca docelowego kopii zapasowej.|  
|Komunikacja jednokierunkowa||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||Nie|Wyjątek i transakcja zostanie wycofana.|  
|Komunikacja jednokierunkowa|||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|Tak|Próbuje ponownie wysłać wiadomość na zapasowego punktu końcowego. Po pomyślnie odebrany komunikat pełny odbierać wszystkie konteksty. Jeśli komunikat nie zostanie pomyślnie odebrany przez dowolnego punktu końcowego, kontekstu odbierania nie jest ukończona.<br /><br /> Jeśli ten komunikat jest zostanie multiemisji kontekstu odbierania jest możliwe tylko, jeśli wiadomość została odebrana pomyślnie co najmniej jeden punkt końcowy (podstawowych lub zapasowych). Jeśli żaden z punktów końcowych w żadnej ze ścieżek multiemisji odbiorą komunikatu kontekstu odbierania nie jest ukończona.|  
|Komunikacja jednokierunkowa||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|Tak|Przerwać poprzedniej transakcji, utworzyć nową transakcję i Wyślij ponownie wszystkie komunikaty. Komunikaty, które napotkały błąd, są przesyłane do docelowego kopii zapasowych.<br /><br /> Po utworzeniu transakcji, w których wszystkie transmisje powiedzie się, wypełnij kontekstu odbierania i zatwierdzić transakcji.|  
|Komunikacja jednokierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|||Tak|Próbuje ponownie wysłać wiadomość na zapasowego punktu końcowego. W scenariuszu multiemisji tylko wiadomości w sesji, która napotkała błąd lub którego sesja zamknąć sesji nie powiodło się są wysłane ponownie miejsca docelowe kopii zapasowej.|  
|Komunikacja jednokierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||Nie|Wyjątek i transakcja zostanie wycofana.|  
|Komunikacja jednokierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|Tak|Próbuje ponownie wysłać wiadomość na zapasowego punktu końcowego. Po wszystkich komunikatów wysyła ukończone bez błędów, sesja wskazuje dalszych komunikatów i usługa routingu zamyka pomyślnie wszystkich kanałów wychodzących sesji, odbierać wszystkie konteksty zostały zakończone i nastąpi zamknięcie kanału sesji przychodzących.|  
|Komunikacja jednokierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|Tak|Przerwanie bieżącej transakcji i Utwórz nową. Wyślij ponownie wszystkie poprzednie wiadomości w sesji. Po transakcji został utworzony, w którym wszystkie wiadomości zostały pomyślnie wysłane i sesji wskazuje uzyskują dalszych komunikatów, kanałów wychodzących sesji są zamknięte, wszystkie konteksty są wykonywane przy użyciu transakcji, jest kanału sesji przychodzących zamknięte, a transakcja została przekazana.<br /><br /> Jeśli zostanie sesji multiemisji w wiadomości, które ma błąd nie są ponownie wysyłane do tego samego miejsca docelowego jako przed i komunikaty, które napotkały błąd są wysyłane do miejsca docelowe kopii zapasowej.|  
|Dwukierunkowe||||Tak|Wyślij do miejsce docelowe kopii zapasowej.  Po kanał zwraca komunikat odpowiedzi, zwraca odpowiedź do klienta oryginalnym.|  
|Dwukierunkowe|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|||Tak|Wszystkie wiadomości w kanale wysłać do miejsca docelowego kopii zapasowej.  Po kanał zwraca komunikat odpowiedzi, zwraca odpowiedź do klienta oryginalnym.|  
|Dwukierunkowe||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||Nie|Wyjątek i transakcja zostanie wycofana.|  
|Dwukierunkowe|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||Nie|Wyjątek i transakcja zostanie wycofana.|  
|Dupleks||||Nie|Komunikację dupleksową non sesji nie jest obecnie obsługiwane.|  
|Dupleks|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|||Tak|Wyślij do miejsce docelowe kopii zapasowej.|  
  
## <a name="hosting"></a>Hosting  
 Ponieważ usługa routingu jest zaimplementowany jako usługa WCF, musi być hosta samodzielnego w aplikacji lub hostowanych przez usługi IIS lub WAS. Zaleca się, że usługa routingu być obsługiwana przez usługi IIS, WAS albo usługa systemu Windows można skorzystać z automatycznego uruchamiania i dostępne w tych środowiskach hostingu funkcje zarządzania cyklem życia.  
  
 W poniższym przykładzie pokazano, usługi routingu w aplikacji hosta.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 Do obsługi usługi routingu w usługach IIS lub WAS, możesz utworzyć plik usługi (SVC) lub użyć aktywacja oparta na konfiguracji usługi. Korzystając z pliku usługi, należy określić <xref:System.ServiceModel.Routing.RoutingService> za pomocą parametru usługi. Poniższy przykład zawiera przykładowy plik usługi, który może służyć do obsługi usługi routingu z usług IIS lub WAS.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Usługa routingu i personifikacja  
 Usługa routingu WCF można o personifikacji dla wysyłania i odbierania wiadomości. Zastosuj wszystkie zwykłe ograniczenia Windows personifikacji. Jeśli potrzebne były do konfigurowania konta usługi lub uprawnień do podczas zapisywania własnej usługi należy używać personifikacji, będzie konieczne przeprowadzenie tych te same czynności należy używać personifikacji z usługą routingu. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Personifikacja z usługą routingu wymaga użycia personifikacji aplikacji ASP.NET w trybie zgodności ASP.NET lub Użyj poświadczeń systemu Windows, które zostały skonfigurowane do zezwala na personifikację. Aby uzyskać więcej informacji na temat tryb zgodności ASP.NET, zobacz [usługi WCF i platformy ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
> [!WARNING]
>  Usługa routingu WCF nie obsługuje personifikacji z uwierzytelnianiem podstawowym.  
  
 Aby użyć personifikacji aplikacji ASP.NET z usługą routingu, Włącz tryb zgodności ASP.NET na usługę hostingu. Usługa routingu już została oznaczona jako zezwalające na tryb zgodności ASP.NET i personifikacji zostaną automatycznie włączone. Personifikacja jest obsługiwane są tylko symbole ASP.NET integracji z usługą routingu.  
  
 Do użycia z usługą routingu personifikacji poświadczeń systemu Windows, musisz skonfigurować poświadczenia i usługi. Obiekt poświadczeń klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, dostępne <xref:System.ServiceModel.ChannelFactory>) definiuje <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość, która musi być ustawiona na zezwala na personifikację. Ponadto usługi należy skonfigurować <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> zachowanie można ustawić `ImpersonateCallerForAllOperations` do `true`. Usługa routingu używa tej flagi zdecydować, czy należy utworzyć klientów do przesyłania dalej wiadomości z włączona personifikacja.  
  
## <a name="see-also"></a>Zobacz też  
 [Filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Kontrakty routingu](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Wybieranie filtru](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)
