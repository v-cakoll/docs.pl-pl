---
title: Wprowadzenie do routingu
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 3ee7ea8271df47354a0897434bf8f203eaf09a51
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "33496867"
---
# <a name="routing-introduction"></a>Wprowadzenie do routingu
Usługa routingu zawiera ogólny podłączanych SOAP pośrednie umożliwiającym routing wiadomości na podstawie zawartości komunikatu. Usługa routingu umożliwia tworzenie złożoną logikę routingu, która pozwala na implementowanie scenariuszy, takich jak usługi agregacji, przechowywanie wersji usługi, routing priorytet i routing multiemisji. Usługa routingu znajdują się również dodanymi komentarzami, która pozwala na konfigurowanie wykaz kopii zapasowych punktów końcowych, do którego są wysyłane wiadomości, jeśli wystąpi błąd podczas wysyłania do docelowego podstawowego punktu końcowego.  
  
 W tym temacie jest przeznaczona dla osób, jesteś nowym użytkownikiem usługi Routing i obejmuje konfigurację podstawową i hosting usługi routingu.  
  
## <a name="configuration"></a>Konfiguracja  
 Usługa routingu jest wdrażany jako usługa WCF, która udostępnia jeden lub więcej punktów końcowych usługi, które odbiera komunikaty z aplikacji klienckich i kierowanie komunikatów do co najmniej jeden docelowych punktów końcowych. Usługa zapewnia <xref:System.ServiceModel.Routing.RoutingBehavior>, których są stosowane do punktów końcowych usługi udostępniane przez usługę. To zachowanie jest używany do konfigurowania różnych aspektów sposób działania usługi. W celu ułatwienia konfiguracji, korzystając z pliku konfiguracji, parametry są określone na **RoutingBehavior**. W scenariuszach opartych na kodzie, te parametry będzie określony jako część <xref:System.ServiceModel.Routing.RoutingConfiguration> obiektu, który może być następnie przekazywany do **RoutingBehavior**.  
  
 Podczas uruchamiania, to zachowanie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, które jest używane do wykonywania przetwarzania protokołu SOAP wiadomości do punktów końcowych klienta. Dzięki temu usługa routingu do przekazywania wiadomości do punktów końcowych, które wymagają różnych **element MessageVersion** niż wiadomość została odebrana za pośrednictwem punktu końcowego. **RoutingBehavior** rejestruje także rozszerzenia usługi sieci <xref:System.ServiceModel.Routing.RoutingExtension>, która udostępnia punkt ułatwień dostępu do modyfikowania konfiguracji usługa routingu w czasie wykonywania.  
  
 **RoutingConfiguration** klasy zapewnia spójne konfigurowanie i aktualizowanie konfiguracji usługa routingu.  Zawiera on parametry, które działają jako ustawienia usługi Routing i służy do konfigurowania **RoutingBehavior** po uruchomieniu usługi, lub jest przekazywany do **RoutingExtension** do modyfikowania routingu Konfiguracja w czasie wykonywania.  
  
 Logikę routingu, używany do wykonywania na podstawie zawartości routing komunikatów jest definiowany przez grupowanie wielu <xref:System.ServiceModel.Dispatcher.MessageFilter> obiekty razem do filtrowania tabel (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> obiektów). Komunikaty przychodzące są obliczane względem filtry komunikatów znajdujących się w tabeli filtru, a następnie dla każdego **MessageFilter** odpowiadającej wiadomości przesyłane dalej do docelowego punktu końcowego. Filtr tabeli, które mają być używane do przesyłania wiadomości jest określony za pomocą **RoutingBehavior** w konfiguracji lub za pomocą kodu przy użyciu **RoutingConfiguration** obiektu.  
  
### <a name="defining-endpoints"></a>Definiowanie punktów końcowych  
 Chociaż może wydawać się, że powinien rozpocząć konfigurację, definiując logikę routingu, który będzie używany, faktycznie powinno być określa kształt punktów końcowych, które będą routingu komunikatów Twoim pierwszym krokiem. Usługa routingu używa umowy, które definiują kształt kanały umożliwia odbieranie i wysyłanie wiadomości, a w związku z tym kształt kanał wejściowy musi być zgodna z kanału danych wyjściowych.  Na przykład, jeśli routingu do punktów końcowych używających kształtu kanału "żądanie-odpowiedź" następnie musisz podać zgodny kontraktu dla ruchu przychodzącego punktów końcowych, takich jak <xref:System.ServiceModel.Routing.IRequestReplyRouter>.  
  
 Oznacza to, że jeśli docelowych punktów końcowych za pomocą kontraktów wielu wzorców komunikacyjnych (na przykład mieszanie operacje jednokierunkową i dwukierunkową), nie można utworzyć punktu końcowego jednej usługi, który może odbierać i kierowanie komunikatów w postaci do wszystkich z nich. Należy określić, które punkty końcowe mają niezgodne kształty i punkty końcowe usługi, które będą używane do odbierania komunikatów w celu przekierowania go do docelowych punktów końcowych.  
  
> [!NOTE]
>  Podczas pracy z umowy, które określają wielu wzorców komunikacyjnych (na przykład różne operacje jednokierunkową i dwukierunkową), obejście tego problemu jest użycie kontraktu dwukierunkowego na usługę routingu, takich jak <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. Jednak oznacza to, że powiązanie musi umożliwiać komunikację dupleksową, może nie być możliwe w przypadku wszystkich scenariuszy. W scenariuszach, w którym nie jest to możliwe uwzględniając komunikatu do wielu punktów końcowych lub modyfikowania aplikacji może być konieczne.  
  
 Aby uzyskać więcej informacji na temat kontrakty routingu, zobacz [kontrakty routingu](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Po zdefiniowaniu punkt końcowy usługi można użyć **RoutingBehavior** do skojarzenia z określonej **RoutingConfiguration** z punktem końcowym. Podczas konfigurowania usługi routingu przy użyciu pliku konfiguracji **RoutingBehavior** służy do określania tabelę filtru, który zawiera logikę routingu, używane do przetwarzania komunikatów odebranych w tym punkcie końcowym. Jeśli konfigurujesz usługę Routing programowo należy określić tabelę filtru, za pomocą **RoutingConfiguration**.  
  
 W poniższym przykładzie zdefiniowano punkty końcowe usługi i klienta, które są używane przez usługę Routing programowo i za pomocą pliku konfiguracji.  
  
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
  
 W tym przykładzie służy do konfigurowania usługi routingu do udostępnienia w jednym punkcie końcowym adresem "http://localhost:8000/routingservice/router", który jest używany do odbierania komunikatów przesłana. Ponieważ komunikaty są kierowane do punktów końcowych typu żądanie odpowiedź, punkt końcowy usługi używa <xref:System.ServiceModel.Routing.IRequestReplyRouter> kontraktu. Ta konfiguracja definiuje również punkt końcowy pojedynczego klienta "http://localhost:8000/servicemodelsample/service" czy komunikaty są kierowane do. Tabela filtru (niewyświetlany) o nazwie "routingTable1" zawiera logikę routingu umożliwia routing komunikatów i jest skojarzony z punktu końcowego usługi za pomocą **RoutingBehavior** (w przypadku pliku konfiguracji) lub  **RoutingConfiguration** (w przypadku konfigurację programistyczną).  
  
### <a name="routing-logic"></a>Logikę routingu  
 Aby zdefiniować logikę routingu umożliwia routing komunikatów, należy określić danych zawartych w wiadomości przychodzących, które można unikatowo odpowiednio obsługiwane po. Na przykład jeśli wszystkie miejsce docelowe punktów końcowych, które są routingu, aby udostępnić te same akcje protokołu SOAP, wartość akcji zawartych w komunikacie nie jest dobry wskaźnik które określonego punktu końcowego komunikat powinien kierowane do. Jeśli do jednego określonego punktu końcowego musi jednoznacznie kierowanie komunikatów w postaci, powinien filtrować na danych, który unikatowo identyfikuje docelowy punkt końcowy, który komunikat jest kierowany do.  
  
 Usługa routingu udostępnia wiele **MessageFilter** implementacji, które Zbadaj określone wartości wiadomości, takich jak adres, akcji, nazwy punktu końcowego lub nawet zapytania XPath. Jeśli żadna z tych implementacji odpowiada Twoim potrzebom, można utworzyć niestandardowy **MessageFilter** implementacji. Aby uzyskać więcej informacji na temat filtry komunikatów oraz porównanie ich z implementacji używane przez usługę Routing zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md) i [Wybieranie filtru](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).  
  
 Wiele filtrów wiadomości są zorganizowane razem do filtrowania tabel, które skojarzyć każdy **MessageFilter** z punktem końcowym docelowego. Opcjonalnie tabelę filtru można również określić listę punktów końcowych kopii zapasowych, które usługa routingu będzie próbował wysłać wiadomości do awarii transmisji.  
  
 Domyślnie wszystkie filtry komunikatu w tabeli filtru są oceniane jednocześnie; Jednak możesz określić <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> , dzięki któremu filtry komunikatów, który ma zostać obliczone w określonej kolejności. Wszystkie wpisy o najwyższym priorytecie są obliczane jako pierwsze, a filtry wiadomości o niższych priorytetach nie są oceniane, jeśli zostanie znalezione dopasowanie na wyższym poziomie priorytetu. Aby uzyskać więcej informacji na temat filtrowania tabel zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 W poniższych przykładach używane <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, która daje w wyniku `true` dla wszystkich wiadomości. To **MessageFilter** zostanie dodana do tabeli filtru "routingTable1", co umożliwi skojarzenie **MessageFilter** z punktem końcowym klienta o nazwie "CalculatorService". **RoutingBehavior** Określa, że ta tabela powinien być używany do przesyłania wiadomości przetworzonych przez punkt końcowy usługi.  
  
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
>  Domyślnie usługa routingu oblicza tylko nagłówki komunikatu. Aby umożliwić filtry uzyskać dostęp do treści wiadomości, należy ustawić <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> do `false`.  
  
 **Multiemisji**  
  
 Gdy wiele konfiguracji usługa routingu używana logika wyłączny filtr, które kieruje komunikaty do tylko jednego określonego punktu końcowego, może być konieczne kierowania danego komunikatu do wielu docelowych punktów końcowych. Do obsługi multiemisji komunikatu do wielu miejsc docelowych muszą być spełnione następujące warunki:  
  
-   Kształtu kanału nie może być "żądanie-odpowiedź" (chociaż może być jedno- lub dupleksowy,), ponieważ tylko jedną odpowiedź może zostać odebrany przez aplikację klienta w odpowiedzi na żądanie.  
  
-   Wiele filtrów musi zwracać `true` podczas oceniania wiadomości.  
  
 Jeśli te warunki są spełnione, komunikat jest kierowany do wszystkich punktów końcowych wszystkie filtry, które dają `true`. W poniższym przykładzie zdefiniowano konfiguracji routingu, powstałego w komunikatach jest kierowany do obu punktów końcowych, jeśli adres punktu końcowego w komunikacie http://localhost:8000/routingservice/router/rounding.  
  
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
  
### <a name="soap-processing"></a>Przetwarzanie protokołu SOAP  
 Aby obsługiwać routing wiadomości między różnych protokołów **RoutingBehavior** domyślnie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do wszystkich klientów punkty końcowe: kierowane do wiadomości. To zachowanie automatycznie tworzy nową **element MessageVersion** przed routing wiadomości do punktu końcowego, a także tworzenie zgodnego **element MessageVersion** dla każdego dokumentu odpowiedzi przed zwróceniem jej do żądania aplikacji klienckiej.  
  
 Etapy, Utwórz nową **element MessageVersion** wiadomości wychodzące są następujące:  
  
 **Przetwarzanie żądania**  
  
-   Pobierz **element MessageVersion** wychodzącego powiązania/kanału.  
  
-   Uzyskaj odczytujący treść oryginalnej wiadomości.  
  
-   Utwórz nową wiadomość z tą samą akcją, treść i nową **element MessageVersion**.  
  
-   Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, skopiuj To, z FaultTo i nagłówków RelatesTo nowy komunikat.  
  
-   Skopiuj wszystkie właściwości wiadomości na nowy komunikat.  
  
-   Store oryginalnego komunikatu żądania do użycia podczas przetwarzania odpowiedzi.  
  
-   Zwraca nowy komunikat żądania.  
  
 **Przetwarzanie odpowiedzi**  
  
-   Pobierz **element MessageVersion** oryginalnego komunikatu żądania.  
  
-   Uzyskaj odczytujący treść komunikatu Odebrano odpowiedź.  
  
-   Utwórz nowy komunikat odpowiedzi z tą samą akcją odczytujący treść i **element MessageVersion** oryginalnego komunikatu żądania.  
  
-   Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, skopiuj To, z FaultTo i nagłówków RelatesTo nowy komunikat.  
  
-   Kopiuj właściwości komunikatu do nowej wiadomości.  
  
-   Zwraca nowy komunikat odpowiedzi.  
  
 Domyślnie **SoapProcessingBehavior** jest automatycznie dodawany do punktów końcowych klienta przez <xref:System.ServiceModel.Routing.RoutingBehavior> podczas uruchamiania usługi; Jednakże, można kontrolować, czy przetwarzanie protokołu SOAP jest dodawany do wszystkich punktów końcowych klienta przy użyciu <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> właściwości. Można również dodać zachowanie bezpośrednio do określonego punktu końcowego i włączyć lub wyłączyć tego zachowania, na poziomie punktu końcowego, jeśli wymagana jest większą kontrolę nad przetwarzania protokołu SOAP.  
  
> [!NOTE]
>  Jeśli przetwarzanie protokołu SOAP jest wyłączona dla punktu końcowego, który wymaga różnych element MessageVersion niż na pierwotny komunikat żądania, musisz podać niestandardowy mechanizm wszelkie zmiany protokołu SOAP, które są wymagane przed wysłaniem wiadomości do docelowy punkt końcowy.  
  
 W poniższych przykładach **soapProcessingEnabled** właściwość jest używana w celu zapobieżenia **SoapProcessingBehavior** z automatycznie dodawany do wszystkich punktów końcowych klienta.  
  
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
  
### <a name="dynamic-configuration"></a>Dynamiczna konfiguracja  
 Po dodaniu punktów końcowych klienta dodatkowych, lub należy modyfikować filtry, które są używane do przesyłania wiadomości, konieczne jest posiadanie sposób aktualizowania konfiguracji dynamicznie w czasie wykonywania, aby zapobiec przerywania usługi do obecnie odbieranie komunikatów za pośrednictwem punktów końcowych Usługa routingu. Modyfikowanie pliku konfiguracji lub kod aplikacji hosta nie zawsze jest wystarczająca, ponieważ każda z tych metod wymaga aplikacji, co może prowadzić do potencjalnej utraty żadnych wiadomości obecnie w przypadku przesyłania i potencjalnych przestojów podczas odtwarzania Oczekiwanie na ponowne uruchomienie usługi.  
  
 Można modyfikować tylko **RoutingConfiguration** programowo. Mimo że możesz wstępnie skonfigurować usługę przy użyciu pliku konfiguracji, można tylko zmodyfikować konfigurację w czasie wykonywania, tworząc nową **RoutingConfigution** i przekazanie do niej jako parametr do <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> — metoda udostępniane przez <xref:System.ServiceModel.Routing.RoutingExtension> usługi rozszerzenia. Obecnie wszystkie wiadomości w dalszym ciągu być kierowane za pomocą poprzedniej konfiguracji, podczas komunikatów odebranych po wywołaniu **ApplyConfiguration** korzystać z nowej konfiguracji. Poniższy przykład przedstawia tworzenie wystąpienia usługi Routing i następnie modyfikowania konfiguracji.  
  
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
>  Podczas aktualizowania usługi routingu w ten sposób możliwe jest tylko do przekazywania nowej konfiguracji. Nie jest możliwe zmodyfikowanie tylko wybrane elementy w bieżącej konfiguracji, lub Dołącz nowe wpisy do bieżącej konfiguracji; należy utworzyć i przekazać nową konfigurację, która zastępuje istniejącą grupę.  
  
> [!NOTE]
>  Wszystkie sesje otwierane przy użyciu poprzedniej konfiguracji nadal przy użyciu poprzedniej konfiguracji. Nowa konfiguracja jest używana tylko przez nowych sesji.  
  
## <a name="error-handling"></a>Obsługa błędów  
 Jeśli istnieją <xref:System.ServiceModel.CommunicationException> występuje podczas próby wysłania wiadomości, miejsce do obsługi błędów. Wyjątki te zwykle sygnalizuje Napotkano problem podczas próby skomunikowania się z punktem końcowym zdefiniowanych klienta, takich jak <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, lub <xref:System.ServiceModel.CommunicationObjectFaultedException>. Kodu obsługi błędu zostanie też przechwytywać i podjął próbę podczas wysyłania <xref:System.TimeoutException> problem wystąpi, który jest inny wspólnej wyjątek, który nie pochodzi od **communicationexception —**.  
  
 Gdy wystąpi jedno z poprzednich wyjątków, usługa routingu nie powiedzie się za pośrednictwem listę kopii zapasowych punktów końcowych. Jeśli wszystkie punkty końcowe kopii zapasowej się nie powieść z błędem łączności lub jeśli punkt końcowy zwraca wyjątek, który wskazuje błąd w ramach usługi docelowej, usługa routingu zwraca błąd do aplikacji klienckiej.  
  
> [!NOTE]
>  Funkcje obsługi błędów przechwytuje i obsługi wyjątków, które występują podczas próby wysłania wiadomości i podczas próby zamknięcia kanału. Kodu obsługi błędu nie jest przeznaczona do wykrycia lub obsługi wyjątków, utworzone przez punkty końcowe aplikacji, z którymi się komunikują; <xref:System.ServiceModel.FaultException> zgłoszony przez usługi pojawia się na usługę Routing jako **FaultMessage** i jest przekazane z powrotem do klienta.  
>   
>  Jeśli wystąpi błąd, gdy usługa routingu próbuje do przekazywania wiadomości, może wystąpić <xref:System.ServiceModel.FaultException> po stronie klienta, a nie <xref:System.ServiceModel.EndpointNotFoundException> zwykle jak w przypadku braku usługa routingu. Usługa routingu mogą zatem maskować wyjątki i zapewnia pełną przezroczystość, chyba że badania wyjątków zagnieżdżonych.  
  
### <a name="tracing-exceptions"></a>Śledzenie wyjątków  
 Podczas wysyłania komunikatu do punktu końcowego na liście nie powiedzie się, usługa routingu śledzi wynikowe dane wyjątku i dołącza szczegóły wyjątku jako właściwość komunikatu o nazwie **wyjątki**. Zachowuje dane wyjątku i umożliwia dostęp programowy użytkownika, przy użyciu Inspektora wiadomości.  Dane wyjątku są przechowywane na komunikat w słowniku, który zmapuje nazwę punktu końcowego do szczegółów wyjątek wystąpił podczas próby wysłania komunikatu do niego.  
  
### <a name="backup-endpoints"></a>Punkty końcowe kopii zapasowej  
 Każdy wpis filtru w tabeli filtru Opcjonalnie możesz określić listę kopii zapasowych punktów końcowych, które są używane w przypadku niepowodzenia przesyłania podczas wysyłania do podstawowego punktu końcowego. Jeśli wystąpi taka awaria, usługa routingu próbuje przekazuje komunikat do pierwszej pozycji na liście kopii zapasowych punktu końcowego. Jeśli ta próba wysłania również napotka błąd transmisji, zostanie podjęta próba następny punkt końcowy na liście kopii zapasowych. Usługa routingu kontynuuje wysyłanie komunikatu do każdego punktu końcowego na liście do momentu wiadomość została odebrana pomyślnie, wszystkie punkty końcowe zwracają błąd transmisji lub niesprawności — jest zwracany przez punkt końcowy.  
  
 Poniższe przykłady skonfigurować usługę routingu, aby użyć listy kopii zapasowych.  
  
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
 W poniższej tabeli opisano wzorców, które są zgodne z użyciem listy kopii zapasowej punktu końcowego oraz informacje opisujące szczegóły dotyczące obsługi błędów dla określonych wzorców.  
  
|Wzorzec|Sesja|Transakcja|Kontekstu odbierania|Lista kopii zapasowych jest obsługiwana|Uwagi|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Komunikacja jednokierunkowa||||Tak|Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej. Jeśli ten komunikat jest multiemisji, tylko wiadomość na kanale zakończonych niepowodzeniem jest przenoszony do miejsca docelowego kopii zapasowej.|  
|Komunikacja jednokierunkowa||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||Nie|Jest zgłaszany wyjątek, a transakcja zostanie wycofana.|  
|Komunikacja jednokierunkowa|||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|Tak|Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej. Po pomyślnie odebrany komunikat pełny otrzymywać wszystkich kontekstów. Jeśli komunikat nie zostanie pomyślnie odebrany przez dowolnego punktu końcowego, kontekstu odbierania nie jest ukończona.<br /><br /> Jeśli ten komunikat jest multiemisji kontekstu odbierania jest wypełniane, jeśli wiadomość została odebrana pomyślnie co najmniej jeden punkt końcowy (podstawowych lub zapasowych). Jeśli żaden z punktów końcowych, które w żadnym z multiemisji ścieżki pomyślnie wiadomości, kontekstu odbierania nie jest ukończona.|  
|Komunikacja jednokierunkowa||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|Tak|Przerwij poprzednia transakcja, Utwórz nową transakcję i ponownie wysłać wszystkie wiadomości. Komunikaty, które napotkały błąd są przesyłane do miejsca docelowego kopii zapasowej.<br /><br /> Po utworzeniu transakcji w którym wszystkie transmisje powiedzie się, wykonaj kontekstów odbierania i zatwierdzania transakcji.|  
|Komunikacja jednokierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|||Tak|Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej. W przypadku multiemisji tylko wiadomości w sesji, która napotkała błąd lub którego sesja zamknąć sesji nie powiodło się są wysyłane ponownie do tworzenia kopii zapasowej miejsc docelowych.|  
|Komunikacja jednokierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||Nie|Jest zgłaszany wyjątek, a transakcja zostanie wycofana.|  
|Komunikacja jednokierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|Tak|Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej. Po wszystkich komunikatów wysyła ukończone bez błędów, sesja wskazuje dalszych komunikatów i usługa routingu pomyślnie zamyka wszystkie kanały wychodzących sesji, wszystkie otrzymywać konteksty są wykonywane i kanałów przychodzących sesji jest zamknięty.|  
|Komunikacja jednokierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|Tak|Przerwanie bieżącej transakcji i Utwórz nową. Wyślij ponownie wszystkie poprzednie komunikaty o w sesji. Po utworzeniu transakcji, w którym wszystkie komunikaty zostały pomyślnie wysłane i sesji wskazuje, że odbieranie dalszych komunikatów, wszystkie kanały wychodzących sesji są zamknięte, konteksty są wykonywane przy użyciu transakcji, kanał przychodzących sesji jest zamknięte, a transakcja została zatwierdzona.<br /><br /> Gdy sesje są multiemisji w wiadomości, które miały błąd nie są wysyłane ponownie do tego samego miejsca docelowego jako przed i komunikaty, które napotkał błąd są wysyłane do miejsca docelowe kopii zapasowej.|  
|Dwukierunkowa||||Tak|Wyślij do miejsca docelowego kopii zapasowej.  Po kanał zwraca komunikat odpowiedzi, zwraca odpowiedź do oryginalnego klienta.|  
|Dwukierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|||Tak|Wszystkie wiadomości na kanale można wysłać do miejsca docelowego kopii zapasowej.  Po kanał zwraca komunikat odpowiedzi, zwraca odpowiedź do oryginalnego klienta.|  
|Dwukierunkowa||![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||Nie|Jest zgłaszany wyjątek, a transakcja zostanie wycofana.|  
|Dwukierunkowa|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")||Nie|Jest zgłaszany wyjątek, a transakcja zostanie wycofana.|  
|Dupleks||||Nie|Komunikację dupleksową non sesji nie jest obecnie obsługiwane.|  
|Dupleks|![Znacznik wyboru](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "znacznik wyboru")|||Tak|Wyślij do miejsca docelowego kopii zapasowej.|  
  
## <a name="hosting"></a>Hosting  
 Ponieważ usługa routingu jest zaimplementowana jako usługa WCF, musi być albo może być samodzielnie hostowane w aplikacji lub hostowanych przez usługi IIS i WAS. Zaleca się, że usługa routingu znajdować IIS, WAS, lub aplikacji usługi Windows można skorzystać z automatycznego uruchamiania i cyklu życia funkcje zarządzania dostępne w tych środowiskach hostingu.  
  
 Poniższy przykład pokazuje usługi routingu w aplikacji hosta.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 Do obsługi usługi routingu w ramach usług IIS i WAS, możesz utworzyć plik usługi (SVC) lub użyć aktywację w oparciu o konfigurację usługi. Korzystając z pliku usługi, należy określić <xref:System.ServiceModel.Routing.RoutingService> za pomocą parametru usługi. Poniższy przykład zawiera przykładowy plik usługi, który może służyć do obsługi usługi routingu za pomocą usług IIS i WAS.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Usługa routingu i personifikacja  
 Usługa routingu WCF umożliwia personifikacji zarówno wysyłania i odbierania komunikatów. Zastosuj wszystkie zwykle ograniczenia Windows personifikacji. Jeśli wymagałby skonfigurować uprawnienia usługi lub konto do użycia personifikacji, podczas pisania własnych usług, będzie konieczne przeprowadzenie tych te same kroki, aby używać personifikacji z usługą routingu. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Personifikacja z usługą routingu wymaga użycia personifikacji aplikacji ASP.NET w trybie zgodności platformy ASP.NET lub Użyj poświadczeń Windows, które zostały skonfigurowane, aby umożliwić personifikacji. Aby uzyskać więcej informacji na temat trybu zgodności programu ASP.NET, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
> [!WARNING]
>  Usługa routingu WCF nie obsługuje personifikacji z uwierzytelnianiem podstawowym.  
  
 Aby użyć personifikacji aplikacji ASP.NET z usługą routingu, Włącz tryb zgodności ASP.NET w usłudze Środowisko hostingu. Usługa routingu już została oznaczona jako zezwolenie na tryb zgodności ASP.NET i personifikacja zostaną automatycznie włączone. Personifikacja jest obsługiwane tylko użytkowania Integracja platformy ASP.NET z usługą routingu.  
  
 Za pomocą Windows poświadczeń personifikacji należy skonfigurować zarówno poświadczenia usługą routingu i usługi. Obiekt poświadczeń klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, jest dostępna z <xref:System.ServiceModel.ChannelFactory>) definiuje <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość, która musi być ustawione na Zezwalaj personifikacji. Na koniec w usłudze, musisz skonfigurować <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> zachowanie, aby ustawić `ImpersonateCallerForAllOperations` do `true`. Usługa routingu używa tej flagi do określania, czy chcesz utworzyć klientów do przekazywania wiadomości z włączona personifikacja.  
  
## <a name="see-also"></a>Zobacz też  
 [Filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Kontrakty routingu](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Wybieranie filtru](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)
