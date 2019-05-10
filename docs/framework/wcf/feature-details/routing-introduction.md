---
title: Wprowadzenie do routingu
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 41545d0340ae222e427d1e6d428ed1e3f7b4fa76
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912490"
---
# <a name="routing-introduction"></a><span data-ttu-id="934fd-102">Wprowadzenie do routingu</span><span class="sxs-lookup"><span data-stu-id="934fd-102">Routing Introduction</span></span>
<span data-ttu-id="934fd-103">Usługa routingu zawiera ogólny podłączanych SOAP pośrednie umożliwiającym routing wiadomości na podstawie zawartości komunikatu.</span><span class="sxs-lookup"><span data-stu-id="934fd-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="934fd-104">Usługa routingu umożliwia tworzenie złożoną logikę routingu, która pozwala na implementowanie scenariuszy, takich jak usługi agregacji, przechowywanie wersji usługi, routing priorytet i routing multiemisji.</span><span class="sxs-lookup"><span data-stu-id="934fd-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="934fd-105">Usługa routingu znajdują się również dodanymi komentarzami, która pozwala na konfigurowanie wykaz kopii zapasowych punktów końcowych, do którego są wysyłane wiadomości, jeśli wystąpi błąd podczas wysyłania do docelowego podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="934fd-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>  
  
 <span data-ttu-id="934fd-106">W tym temacie jest przeznaczona dla osób, jesteś nowym użytkownikiem usługi Routing i obejmuje konfigurację podstawową i hosting usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="934fd-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="934fd-107">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="934fd-107">Configuration</span></span>  
 <span data-ttu-id="934fd-108">Usługa routingu jest wdrażany jako usługa WCF, która udostępnia jeden lub więcej punktów końcowych usługi, które odbiera komunikaty z aplikacji klienckich i kierowanie komunikatów do co najmniej jeden docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="934fd-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="934fd-109">Usługa zapewnia <xref:System.ServiceModel.Routing.RoutingBehavior>, których są stosowane do punktów końcowych usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="934fd-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="934fd-110">To zachowanie jest używany do konfigurowania różnych aspektów sposób działania usługi.</span><span class="sxs-lookup"><span data-stu-id="934fd-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="934fd-111">W celu ułatwienia konfiguracji, korzystając z pliku konfiguracji, parametry są określone na **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="934fd-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="934fd-112">W scenariuszach opartych na kodzie, te parametry będzie określony jako część <xref:System.ServiceModel.Routing.RoutingConfiguration> obiektu, który może być następnie przekazywany do **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="934fd-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>  
  
 <span data-ttu-id="934fd-113">Podczas uruchamiania, to zachowanie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, które jest używane do wykonywania przetwarzania protokołu SOAP wiadomości do punktów końcowych klienta.</span><span class="sxs-lookup"><span data-stu-id="934fd-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="934fd-114">Dzięki temu usługa routingu do przekazywania wiadomości do punktów końcowych, które wymagają różnych **element MessageVersion** niż wiadomość została odebrana za pośrednictwem punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="934fd-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="934fd-115">**RoutingBehavior** rejestruje także rozszerzenia usługi sieci <xref:System.ServiceModel.Routing.RoutingExtension>, która udostępnia punkt ułatwień dostępu do modyfikowania konfiguracji usługa routingu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="934fd-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>  
  
 <span data-ttu-id="934fd-116">**RoutingConfiguration** klasy zapewnia spójne konfigurowanie i aktualizowanie konfiguracji usługa routingu.</span><span class="sxs-lookup"><span data-stu-id="934fd-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="934fd-117">Zawiera on parametry, które działają jako ustawienia usługi Routing i służy do konfigurowania **RoutingBehavior** po uruchomieniu usługi, lub jest przekazywany do **RoutingExtension** do modyfikowania routingu Konfiguracja w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="934fd-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>  
  
 <span data-ttu-id="934fd-118">Logikę routingu, używany do wykonywania na podstawie zawartości routing komunikatów jest definiowany przez grupowanie wielu <xref:System.ServiceModel.Dispatcher.MessageFilter> obiekty razem do filtrowania tabel (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> obiektów).</span><span class="sxs-lookup"><span data-stu-id="934fd-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="934fd-119">Komunikaty przychodzące są obliczane względem filtry komunikatów znajdujących się w tabeli filtru, a następnie dla każdego **MessageFilter** odpowiadającej wiadomości przesyłane dalej do docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="934fd-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="934fd-120">Filtr tabeli, które mają być używane do przesyłania wiadomości jest określony za pomocą **RoutingBehavior** w konfiguracji lub za pomocą kodu przy użyciu **RoutingConfiguration** obiektu.</span><span class="sxs-lookup"><span data-stu-id="934fd-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>  
  
### <a name="defining-endpoints"></a><span data-ttu-id="934fd-121">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="934fd-121">Defining Endpoints</span></span>  
 <span data-ttu-id="934fd-122">Chociaż może wydawać się, że powinien rozpocząć konfigurację, definiując logikę routingu, który będzie używany, faktycznie powinno być określa kształt punktów końcowych, które będą routingu komunikatów Twoim pierwszym krokiem.</span><span class="sxs-lookup"><span data-stu-id="934fd-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="934fd-123">Usługa routingu używa umowy, które definiują kształt kanały umożliwia odbieranie i wysyłanie wiadomości, a w związku z tym kształt kanał wejściowy musi być zgodna z kanału danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="934fd-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="934fd-124">Na przykład, jeśli routingu do punktów końcowych używających kształtu kanału "żądanie-odpowiedź" następnie musisz podać zgodny kontraktu dla ruchu przychodzącego punktów końcowych, takich jak <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="934fd-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>  
  
 <span data-ttu-id="934fd-125">Oznacza to, że jeśli docelowych punktów końcowych za pomocą kontraktów wielu wzorców komunikacyjnych (na przykład mieszanie operacje jednokierunkową i dwukierunkową), nie można utworzyć punktu końcowego jednej usługi, który może odbierać i kierowanie komunikatów w postaci do wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="934fd-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="934fd-126">Należy określić, które punkty końcowe mają niezgodne kształty i punkty końcowe usługi, które będą używane do odbierania komunikatów w celu przekierowania go do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="934fd-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="934fd-127">Podczas pracy z umowy, które określają wielu wzorców komunikacyjnych (na przykład różne operacje jednokierunkową i dwukierunkową), obejście tego problemu jest użycie kontraktu dwukierunkowego na usługę routingu, takich jak <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span><span class="sxs-lookup"><span data-stu-id="934fd-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="934fd-128">Jednak oznacza to, że powiązanie musi umożliwiać komunikację dupleksową, może nie być możliwe w przypadku wszystkich scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="934fd-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="934fd-129">W scenariuszach, w którym nie jest to możliwe uwzględniając komunikatu do wielu punktów końcowych lub modyfikowania aplikacji może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="934fd-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>  
  
 <span data-ttu-id="934fd-130">Aby uzyskać więcej informacji na temat kontrakty routingu, zobacz [kontrakty routingu](routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="934fd-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>  
  
 <span data-ttu-id="934fd-131">Po zdefiniowaniu punkt końcowy usługi można użyć **RoutingBehavior** do skojarzenia z określonej **RoutingConfiguration** z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="934fd-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="934fd-132">Podczas konfigurowania usługi routingu przy użyciu pliku konfiguracji **RoutingBehavior** służy do określania tabelę filtru, który zawiera logikę routingu, używane do przetwarzania komunikatów odebranych w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="934fd-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="934fd-133">Jeśli konfigurujesz usługę Routing programowo należy określić tabelę filtru, za pomocą **RoutingConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="934fd-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>  
  
 <span data-ttu-id="934fd-134">W poniższym przykładzie zdefiniowano punkty końcowe usługi i klienta, które są używane przez usługę Routing programowo i za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="934fd-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="934fd-135">W tym przykładzie służy do konfigurowania usługi routingu do udostępnienia w jednym punkcie końcowym adresem `http://localhost:8000/routingservice/router`, który jest używany do odbierania komunikatów przesłana.</span><span class="sxs-lookup"><span data-stu-id="934fd-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="934fd-136">Ponieważ komunikaty są kierowane do punktów końcowych typu żądanie odpowiedź, punkt końcowy usługi używa <xref:System.ServiceModel.Routing.IRequestReplyRouter> kontraktu.</span><span class="sxs-lookup"><span data-stu-id="934fd-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="934fd-137">Ta konfiguracja definiuje również punkt końcowy pojedynczego klienta `http://localhost:8000/servicemodelsample/service` że wiadomości są kierowane do.</span><span class="sxs-lookup"><span data-stu-id="934fd-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="934fd-138">Tabela filtru (niewyświetlany) o nazwie "routingTable1" zawiera logikę routingu umożliwia routing komunikatów i jest skojarzony z punktu końcowego usługi za pomocą **RoutingBehavior** (w przypadku pliku konfiguracji) lub  **RoutingConfiguration** (w przypadku konfigurację programistyczną).</span><span class="sxs-lookup"><span data-stu-id="934fd-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>  
  
### <a name="routing-logic"></a><span data-ttu-id="934fd-139">Logikę routingu</span><span class="sxs-lookup"><span data-stu-id="934fd-139">Routing Logic</span></span>  
 <span data-ttu-id="934fd-140">Aby zdefiniować logikę routingu umożliwia routing komunikatów, należy określić danych zawartych w wiadomości przychodzących, które można unikatowo odpowiednio obsługiwane po.</span><span class="sxs-lookup"><span data-stu-id="934fd-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="934fd-141">Na przykład jeśli wszystkie miejsce docelowe punktów końcowych, które są routingu, aby udostępnić te same akcje protokołu SOAP, wartość akcji zawartych w komunikacie nie jest dobry wskaźnik które określonego punktu końcowego komunikat powinien kierowane do.</span><span class="sxs-lookup"><span data-stu-id="934fd-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="934fd-142">Jeśli do jednego określonego punktu końcowego musi jednoznacznie kierowanie komunikatów w postaci, powinien filtrować na danych, który unikatowo identyfikuje docelowy punkt końcowy, który komunikat jest kierowany do.</span><span class="sxs-lookup"><span data-stu-id="934fd-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>  
  
 <span data-ttu-id="934fd-143">Usługa routingu udostępnia wiele **MessageFilter** implementacji, które Zbadaj określone wartości wiadomości, takich jak adres, akcji, nazwy punktu końcowego lub nawet zapytania XPath.</span><span class="sxs-lookup"><span data-stu-id="934fd-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="934fd-144">Jeśli żadna z tych implementacji odpowiada Twoim potrzebom, można utworzyć niestandardowy **MessageFilter** implementacji.</span><span class="sxs-lookup"><span data-stu-id="934fd-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="934fd-145">Aby uzyskać więcej informacji na temat filtry komunikatów oraz porównanie ich z implementacji używane przez usługę Routing zobacz [filtry komunikatów](message-filters.md) i [Wybieranie filtru](choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="934fd-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>  
  
 <span data-ttu-id="934fd-146">Wiele filtrów wiadomości są zorganizowane razem do filtrowania tabel, które skojarzyć każdy **MessageFilter** z punktem końcowym docelowego.</span><span class="sxs-lookup"><span data-stu-id="934fd-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="934fd-147">Opcjonalnie tabelę filtru można również określić listę punktów końcowych kopii zapasowych, które usługa routingu będzie próbował wysłać wiadomości do awarii transmisji.</span><span class="sxs-lookup"><span data-stu-id="934fd-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>  
  
 <span data-ttu-id="934fd-148">Domyślnie wszystkie filtry komunikatu w tabeli filtru są oceniane jednocześnie; Jednak możesz określić <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> , dzięki któremu filtry komunikatów, który ma zostać obliczone w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="934fd-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="934fd-149">Wszystkie wpisy o najwyższym priorytecie są obliczane jako pierwsze, a filtry wiadomości o niższych priorytetach nie są oceniane, jeśli zostanie znalezione dopasowanie na wyższym poziomie priorytetu.</span><span class="sxs-lookup"><span data-stu-id="934fd-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="934fd-150">Aby uzyskać więcej informacji na temat filtrowania tabel zobacz [filtry komunikatów](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="934fd-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>  
  
 <span data-ttu-id="934fd-151">W poniższych przykładach używane <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, która daje w wyniku `true` dla wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="934fd-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="934fd-152">To **MessageFilter** zostanie dodana do tabeli filtru "routingTable1", co umożliwi skojarzenie **MessageFilter** z punktem końcowym klienta o nazwie "CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="934fd-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="934fd-153">**RoutingBehavior** Określa, że ta tabela powinien być używany do przesyłania wiadomości przetworzonych przez punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="934fd-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>  
  
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
>  <span data-ttu-id="934fd-154">Domyślnie usługa routingu oblicza tylko nagłówki komunikatu.</span><span class="sxs-lookup"><span data-stu-id="934fd-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="934fd-155">Aby umożliwić filtry uzyskać dostęp do treści wiadomości, należy ustawić <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="934fd-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>  
  
 <span data-ttu-id="934fd-156">**Multiemisji**</span><span class="sxs-lookup"><span data-stu-id="934fd-156">**Multicast**</span></span>  
  
 <span data-ttu-id="934fd-157">Gdy wiele konfiguracji usługa routingu używana logika wyłączny filtr, które kieruje komunikaty do tylko jednego określonego punktu końcowego, może być konieczne kierowania danego komunikatu do wielu docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="934fd-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="934fd-158">Do obsługi multiemisji komunikatu do wielu miejsc docelowych muszą być spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="934fd-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>  
  
- <span data-ttu-id="934fd-159">Kształtu kanału nie może być "żądanie-odpowiedź" (chociaż może być jedno- lub dupleksowy,), ponieważ tylko jedną odpowiedź może zostać odebrany przez aplikację klienta w odpowiedzi na żądanie.</span><span class="sxs-lookup"><span data-stu-id="934fd-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>  
  
- <span data-ttu-id="934fd-160">Wiele filtrów musi zwracać `true` podczas oceniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="934fd-160">Multiple filters must return `true` when evaluating the message.</span></span>  
  
 <span data-ttu-id="934fd-161">Jeśli te warunki są spełnione, komunikat jest kierowany do wszystkich punktów końcowych wszystkie filtry, które dają `true`.</span><span class="sxs-lookup"><span data-stu-id="934fd-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="934fd-162">W poniższym przykładzie zdefiniowano konfiguracji routingu, powstałego w komunikatach jest kierowany do obu punktów końcowych, jeśli adres punktu końcowego w komunikacie `http://localhost:8000/routingservice/router/rounding`.</span><span class="sxs-lookup"><span data-stu-id="934fd-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>  
  
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
  
### <a name="soap-processing"></a><span data-ttu-id="934fd-163">Przetwarzanie protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="934fd-163">SOAP Processing</span></span>  
 <span data-ttu-id="934fd-164">Aby obsługiwać routing wiadomości między różnych protokołów **RoutingBehavior** domyślnie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do wszystkich klientów punkty końcowe: kierowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="934fd-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="934fd-165">To zachowanie automatycznie tworzy nową **element MessageVersion** przed routing wiadomości do punktu końcowego, a także tworzenie zgodnego **element MessageVersion** dla każdego dokumentu odpowiedzi przed zwróceniem jej do żądania aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="934fd-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>  
  
 <span data-ttu-id="934fd-166">Etapy, Utwórz nową **element MessageVersion** wiadomości wychodzące są następujące:</span><span class="sxs-lookup"><span data-stu-id="934fd-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>  
  
 <span data-ttu-id="934fd-167">**Przetwarzanie żądania**</span><span class="sxs-lookup"><span data-stu-id="934fd-167">**Request processing**</span></span>  
  
- <span data-ttu-id="934fd-168">Pobierz **element MessageVersion** wychodzącego powiązania/kanału.</span><span class="sxs-lookup"><span data-stu-id="934fd-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>  
  
- <span data-ttu-id="934fd-169">Uzyskaj odczytujący treść oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="934fd-169">Get the body reader for the original message.</span></span>  
  
- <span data-ttu-id="934fd-170">Utwórz nową wiadomość z tą samą akcją, treść i nową **element MessageVersion**.</span><span class="sxs-lookup"><span data-stu-id="934fd-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>  
  
- <span data-ttu-id="934fd-171">Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, skopiuj To, z FaultTo i nagłówków RelatesTo nowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="934fd-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
- <span data-ttu-id="934fd-172">Skopiuj wszystkie właściwości wiadomości na nowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="934fd-172">Copy all message properties to the new message.</span></span>  
  
- <span data-ttu-id="934fd-173">Store oryginalnego komunikatu żądania do użycia podczas przetwarzania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="934fd-173">Store the original request message to use when processing the response.</span></span>  
  
- <span data-ttu-id="934fd-174">Zwraca nowy komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="934fd-174">Return the new request message.</span></span>  
  
 <span data-ttu-id="934fd-175">**Przetwarzanie odpowiedzi**</span><span class="sxs-lookup"><span data-stu-id="934fd-175">**Response processing**</span></span>  
  
- <span data-ttu-id="934fd-176">Pobierz **element MessageVersion** oryginalnego komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="934fd-176">Get the **MessageVersion** of the original request message.</span></span>  
  
- <span data-ttu-id="934fd-177">Uzyskaj odczytujący treść komunikatu Odebrano odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="934fd-177">Get the body reader for the received response message.</span></span>  
  
- <span data-ttu-id="934fd-178">Utwórz nowy komunikat odpowiedzi z tą samą akcją odczytujący treść i **element MessageVersion** oryginalnego komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="934fd-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>  
  
- <span data-ttu-id="934fd-179">Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, skopiuj To, z FaultTo i nagłówków RelatesTo nowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="934fd-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
- <span data-ttu-id="934fd-180">Kopiuj właściwości komunikatu do nowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="934fd-180">Copy the message properties to the new message.</span></span>  
  
- <span data-ttu-id="934fd-181">Zwraca nowy komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="934fd-181">Return the new response message.</span></span>  
  
 <span data-ttu-id="934fd-182">Domyślnie **SoapProcessingBehavior** jest automatycznie dodawany do punktów końcowych klienta przez <xref:System.ServiceModel.Routing.RoutingBehavior> podczas uruchamiania usługi; Jednakże, można kontrolować, czy przetwarzanie protokołu SOAP jest dodawany do wszystkich punktów końcowych klienta przy użyciu <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="934fd-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="934fd-183">Można również dodać zachowanie bezpośrednio do określonego punktu końcowego i włączyć lub wyłączyć tego zachowania, na poziomie punktu końcowego, jeśli wymagana jest większą kontrolę nad przetwarzania protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="934fd-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="934fd-184">Jeśli przetwarzanie protokołu SOAP jest wyłączona dla punktu końcowego, który wymaga różnych element MessageVersion niż na pierwotny komunikat żądania, musisz podać niestandardowy mechanizm wszelkie zmiany protokołu SOAP, które są wymagane przed wysłaniem wiadomości do docelowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="934fd-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>  
  
 <span data-ttu-id="934fd-185">W poniższych przykładach **soapProcessingEnabled** właściwość jest używana w celu zapobieżenia **SoapProcessingBehavior** z automatycznie dodawany do wszystkich punktów końcowych klienta.</span><span class="sxs-lookup"><span data-stu-id="934fd-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>  
  
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
  
### <a name="dynamic-configuration"></a><span data-ttu-id="934fd-186">Dynamiczna konfiguracja</span><span class="sxs-lookup"><span data-stu-id="934fd-186">Dynamic Configuration</span></span>  
 <span data-ttu-id="934fd-187">Po dodaniu punktów końcowych klienta dodatkowych, lub należy modyfikować filtry, które są używane do przesyłania wiadomości, konieczne jest posiadanie sposób aktualizowania konfiguracji dynamicznie w czasie wykonywania, aby zapobiec przerywania usługi do obecnie odbieranie komunikatów za pośrednictwem punktów końcowych Usługa routingu.</span><span class="sxs-lookup"><span data-stu-id="934fd-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="934fd-188">Modyfikowanie pliku konfiguracji lub kod aplikacji hosta nie zawsze jest wystarczająca, ponieważ każda z tych metod wymaga aplikacji, co może prowadzić do potencjalnej utraty żadnych wiadomości obecnie w przypadku przesyłania i potencjalnych przestojów podczas odtwarzania Oczekiwanie na ponowne uruchomienie usługi.</span><span class="sxs-lookup"><span data-stu-id="934fd-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>  
  
 <span data-ttu-id="934fd-189">Można modyfikować tylko **RoutingConfiguration** programowo.</span><span class="sxs-lookup"><span data-stu-id="934fd-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="934fd-190">Mimo że możesz wstępnie skonfigurować usługę przy użyciu pliku konfiguracji, można tylko zmodyfikować konfigurację w czasie wykonywania, tworząc nową **RoutingConfigution** i przekazanie do niej jako parametr do <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> — metoda udostępniane przez <xref:System.ServiceModel.Routing.RoutingExtension> usługi rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="934fd-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfigution** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="934fd-191">Obecnie wszystkie wiadomości w dalszym ciągu być kierowane za pomocą poprzedniej konfiguracji, podczas komunikatów odebranych po wywołaniu **ApplyConfiguration** korzystać z nowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="934fd-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="934fd-192">Poniższy przykład przedstawia tworzenie wystąpienia usługi Routing i następnie modyfikowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="934fd-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>  
  
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
>  <span data-ttu-id="934fd-193">Podczas aktualizowania usługi routingu w ten sposób możliwe jest tylko do przekazywania nowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="934fd-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="934fd-194">Nie jest możliwe zmodyfikowanie tylko wybrane elementy w bieżącej konfiguracji, lub Dołącz nowe wpisy do bieżącej konfiguracji; należy utworzyć i przekazać nową konfigurację, która zastępuje istniejącą grupę.</span><span class="sxs-lookup"><span data-stu-id="934fd-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="934fd-195">Wszystkie sesje otwierane przy użyciu poprzedniej konfiguracji nadal przy użyciu poprzedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="934fd-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="934fd-196">Nowa konfiguracja jest używana tylko przez nowych sesji.</span><span class="sxs-lookup"><span data-stu-id="934fd-196">The new configuration is only used by new sessions.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="934fd-197">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="934fd-197">Error Handling</span></span>  
 <span data-ttu-id="934fd-198">Jeśli istnieją <xref:System.ServiceModel.CommunicationException> występuje podczas próby wysłania wiadomości, miejsce do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="934fd-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="934fd-199">Wyjątki te zwykle sygnalizuje Napotkano problem podczas próby skomunikowania się z punktem końcowym zdefiniowanych klienta, takich jak <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, lub <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="934fd-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="934fd-200">Kodu obsługi błędu zostanie też przechwytywać i podjął próbę podczas wysyłania <xref:System.TimeoutException> problem wystąpi, który jest inny wspólnej wyjątek, który nie pochodzi od **communicationexception —**.</span><span class="sxs-lookup"><span data-stu-id="934fd-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>  
  
 <span data-ttu-id="934fd-201">Gdy wystąpi jedno z poprzednich wyjątków, usługa routingu nie powiedzie się za pośrednictwem listę kopii zapasowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="934fd-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="934fd-202">Jeśli wszystkie punkty końcowe kopii zapasowej się nie powieść z błędem łączności lub jeśli punkt końcowy zwraca wyjątek, który wskazuje błąd w ramach usługi docelowej, usługa routingu zwraca błąd do aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="934fd-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="934fd-203">Funkcje obsługi błędów przechwytuje i obsługi wyjątków, które występują podczas próby wysłania wiadomości i podczas próby zamknięcia kanału.</span><span class="sxs-lookup"><span data-stu-id="934fd-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="934fd-204">Kodu obsługi błędu nie jest przeznaczona do wykrycia lub obsługi wyjątków, utworzone przez punkty końcowe aplikacji, z którymi się komunikują; <xref:System.ServiceModel.FaultException> zgłoszony przez usługi pojawia się na usługę Routing jako **FaultMessage** i jest przekazane z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="934fd-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>  
>   
>  <span data-ttu-id="934fd-205">Jeśli wystąpi błąd, gdy usługa routingu próbuje do przekazywania wiadomości, może wystąpić <xref:System.ServiceModel.FaultException> po stronie klienta, a nie <xref:System.ServiceModel.EndpointNotFoundException> zwykle jak w przypadku braku usługa routingu.</span><span class="sxs-lookup"><span data-stu-id="934fd-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="934fd-206">Usługa routingu mogą zatem maskować wyjątki i zapewnia pełną przezroczystość, chyba że badania wyjątków zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="934fd-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="934fd-207">Śledzenie wyjątków</span><span class="sxs-lookup"><span data-stu-id="934fd-207">Tracing Exceptions</span></span>  
 <span data-ttu-id="934fd-208">Podczas wysyłania komunikatu do punktu końcowego na liście nie powiedzie się, usługa routingu śledzi wynikowe dane wyjątku i dołącza szczegóły wyjątku jako właściwość komunikatu o nazwie **wyjątki**.</span><span class="sxs-lookup"><span data-stu-id="934fd-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="934fd-209">Zachowuje dane wyjątku i umożliwia dostęp programowy użytkownika, przy użyciu Inspektora wiadomości.</span><span class="sxs-lookup"><span data-stu-id="934fd-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="934fd-210">Dane wyjątku są przechowywane na komunikat w słowniku, który zmapuje nazwę punktu końcowego do szczegółów wyjątek wystąpił podczas próby wysłania komunikatu do niego.</span><span class="sxs-lookup"><span data-stu-id="934fd-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>  
  
### <a name="backup-endpoints"></a><span data-ttu-id="934fd-211">Punkty końcowe kopii zapasowej</span><span class="sxs-lookup"><span data-stu-id="934fd-211">Backup Endpoints</span></span>  
 <span data-ttu-id="934fd-212">Każdy wpis filtru w tabeli filtru Opcjonalnie możesz określić listę kopii zapasowych punktów końcowych, które są używane w przypadku niepowodzenia przesyłania podczas wysyłania do podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="934fd-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="934fd-213">Jeśli wystąpi taka awaria, usługa routingu próbuje przekazuje komunikat do pierwszej pozycji na liście kopii zapasowych punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="934fd-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="934fd-214">Jeśli ta próba wysłania również napotka błąd transmisji, zostanie podjęta próba następny punkt końcowy na liście kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="934fd-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="934fd-215">Usługa routingu kontynuuje wysyłanie komunikatu do każdego punktu końcowego na liście do momentu wiadomość została odebrana pomyślnie, wszystkie punkty końcowe zwracają błąd transmisji lub niesprawności — jest zwracany przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="934fd-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>  
  
 <span data-ttu-id="934fd-216">Poniższe przykłady skonfigurować usługę routingu, aby użyć listy kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="934fd-216">The following examples configure the Routing Service to use a backup list.</span></span>  
  
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
  
### <a name="supported-error-patterns"></a><span data-ttu-id="934fd-217">Błąd obsługiwane wzorce</span><span class="sxs-lookup"><span data-stu-id="934fd-217">Supported Error Patterns</span></span>  
 <span data-ttu-id="934fd-218">W poniższej tabeli opisano wzorców, które są zgodne z użyciem listy kopii zapasowej punktu końcowego oraz informacje opisujące szczegóły dotyczące obsługi błędów dla określonych wzorców.</span><span class="sxs-lookup"><span data-stu-id="934fd-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>  
  
|<span data-ttu-id="934fd-219">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="934fd-219">Pattern</span></span>|<span data-ttu-id="934fd-220">Sesja</span><span class="sxs-lookup"><span data-stu-id="934fd-220">Session</span></span>|<span data-ttu-id="934fd-221">Transakcja</span><span class="sxs-lookup"><span data-stu-id="934fd-221">Transaction</span></span>|<span data-ttu-id="934fd-222">Kontekstu odbierania</span><span class="sxs-lookup"><span data-stu-id="934fd-222">Receive Context</span></span>|<span data-ttu-id="934fd-223">Lista kopii zapasowych jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="934fd-223">Backup List Supported</span></span>|<span data-ttu-id="934fd-224">Uwagi</span><span class="sxs-lookup"><span data-stu-id="934fd-224">Notes</span></span>|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|<span data-ttu-id="934fd-225">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-225">One-Way</span></span>||||<span data-ttu-id="934fd-226">Tak</span><span class="sxs-lookup"><span data-stu-id="934fd-226">Yes</span></span>|<span data-ttu-id="934fd-227">Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="934fd-228">Jeśli ten komunikat jest multiemisji, tylko wiadomość na kanale zakończonych niepowodzeniem jest przenoszony do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|  
|<span data-ttu-id="934fd-229">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-229">One-Way</span></span>||<span data-ttu-id="934fd-230">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-230">✓</span></span>||<span data-ttu-id="934fd-231">Nie</span><span class="sxs-lookup"><span data-stu-id="934fd-231">No</span></span>|<span data-ttu-id="934fd-232">Jest zgłaszany wyjątek, a transakcja zostanie wycofana.</span><span class="sxs-lookup"><span data-stu-id="934fd-232">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="934fd-233">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-233">One-Way</span></span>|||<span data-ttu-id="934fd-234">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-234">✓</span></span>|<span data-ttu-id="934fd-235">Tak</span><span class="sxs-lookup"><span data-stu-id="934fd-235">Yes</span></span>|<span data-ttu-id="934fd-236">Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="934fd-237">Po pomyślnie odebrany komunikat pełny otrzymywać wszystkich kontekstów.</span><span class="sxs-lookup"><span data-stu-id="934fd-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="934fd-238">Jeśli komunikat nie zostanie pomyślnie odebrany przez dowolnego punktu końcowego, kontekstu odbierania nie jest ukończona.</span><span class="sxs-lookup"><span data-stu-id="934fd-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="934fd-239">Jeśli ten komunikat jest multiemisji kontekstu odbierania jest wypełniane, jeśli wiadomość została odebrana pomyślnie co najmniej jeden punkt końcowy (podstawowych lub zapasowych).</span><span class="sxs-lookup"><span data-stu-id="934fd-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="934fd-240">Jeśli żaden z punktów końcowych, które w żadnym z multiemisji ścieżki pomyślnie wiadomości, kontekstu odbierania nie jest ukończona.</span><span class="sxs-lookup"><span data-stu-id="934fd-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|  
|<span data-ttu-id="934fd-241">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-241">One-Way</span></span>||<span data-ttu-id="934fd-242">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-242">✓</span></span>|<span data-ttu-id="934fd-243">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-243">✓</span></span>|<span data-ttu-id="934fd-244">Tak</span><span class="sxs-lookup"><span data-stu-id="934fd-244">Yes</span></span>|<span data-ttu-id="934fd-245">Przerwij poprzednia transakcja, Utwórz nową transakcję i ponownie wysłać wszystkie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="934fd-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="934fd-246">Komunikaty, które napotkały błąd są przesyłane do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="934fd-247">Po utworzeniu transakcji w którym wszystkie transmisje powiedzie się, wykonaj kontekstów odbierania i zatwierdzania transakcji.</span><span class="sxs-lookup"><span data-stu-id="934fd-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|  
|<span data-ttu-id="934fd-248">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-248">One-Way</span></span>|<span data-ttu-id="934fd-249">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-249">✓</span></span>|||<span data-ttu-id="934fd-250">Tak</span><span class="sxs-lookup"><span data-stu-id="934fd-250">Yes</span></span>|<span data-ttu-id="934fd-251">Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="934fd-252">W przypadku multiemisji tylko wiadomości w sesji, która napotkała błąd lub którego sesja zamknąć sesji nie powiodło się są wysyłane ponownie do tworzenia kopii zapasowej miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="934fd-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|  
|<span data-ttu-id="934fd-253">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-253">One-Way</span></span>|<span data-ttu-id="934fd-254">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-254">✓</span></span>|<span data-ttu-id="934fd-255">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-255">✓</span></span>||<span data-ttu-id="934fd-256">Nie</span><span class="sxs-lookup"><span data-stu-id="934fd-256">No</span></span>|<span data-ttu-id="934fd-257">Jest zgłaszany wyjątek, a transakcja zostanie wycofana.</span><span class="sxs-lookup"><span data-stu-id="934fd-257">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="934fd-258">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-258">One-Way</span></span>|<span data-ttu-id="934fd-259">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-259">✓</span></span>||<span data-ttu-id="934fd-260">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-260">✓</span></span>|<span data-ttu-id="934fd-261">Yes</span><span class="sxs-lookup"><span data-stu-id="934fd-261">Yes</span></span>|<span data-ttu-id="934fd-262">Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="934fd-263">Po wszystkich komunikatów wysyła ukończone bez błędów, sesja wskazuje dalszych komunikatów i usługa routingu pomyślnie zamyka wszystkie kanały wychodzących sesji, wszystkie otrzymywać konteksty są wykonywane i kanałów przychodzących sesji jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="934fd-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|  
|<span data-ttu-id="934fd-264">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-264">One-Way</span></span>|<span data-ttu-id="934fd-265">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-265">✓</span></span>|<span data-ttu-id="934fd-266">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-266">✓</span></span>|<span data-ttu-id="934fd-267">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-267">✓</span></span>|<span data-ttu-id="934fd-268">Tak</span><span class="sxs-lookup"><span data-stu-id="934fd-268">Yes</span></span>|<span data-ttu-id="934fd-269">Przerwanie bieżącej transakcji i Utwórz nową.</span><span class="sxs-lookup"><span data-stu-id="934fd-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="934fd-270">Wyślij ponownie wszystkie poprzednie komunikaty o w sesji.</span><span class="sxs-lookup"><span data-stu-id="934fd-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="934fd-271">Po utworzeniu transakcji, w którym wszystkie komunikaty zostały pomyślnie wysłane i sesji wskazuje, że odbieranie dalszych komunikatów, wszystkie kanały wychodzących sesji są zamknięte, konteksty są wykonywane przy użyciu transakcji, kanał przychodzących sesji jest zamknięte, a transakcja została zatwierdzona.</span><span class="sxs-lookup"><span data-stu-id="934fd-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="934fd-272">Gdy sesje są multiemisji w wiadomości, które miały błąd nie są wysyłane ponownie do tego samego miejsca docelowego jako przed i komunikaty, które napotkał błąd są wysyłane do miejsca docelowe kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|  
|<span data-ttu-id="934fd-273">Dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-273">Two-Way</span></span>||||<span data-ttu-id="934fd-274">Tak</span><span class="sxs-lookup"><span data-stu-id="934fd-274">Yes</span></span>|<span data-ttu-id="934fd-275">Wyślij do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-275">Send to a backup destination.</span></span>  <span data-ttu-id="934fd-276">Po kanał zwraca komunikat odpowiedzi, zwraca odpowiedź do oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="934fd-276">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="934fd-277">Dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-277">Two-Way</span></span>|<span data-ttu-id="934fd-278">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-278">✓</span></span>|||<span data-ttu-id="934fd-279">Tak</span><span class="sxs-lookup"><span data-stu-id="934fd-279">Yes</span></span>|<span data-ttu-id="934fd-280">Wszystkie wiadomości na kanale można wysłać do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="934fd-281">Po kanał zwraca komunikat odpowiedzi, zwraca odpowiedź do oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="934fd-281">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="934fd-282">Dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-282">Two-Way</span></span>||<span data-ttu-id="934fd-283">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-283">✓</span></span>||<span data-ttu-id="934fd-284">Nie</span><span class="sxs-lookup"><span data-stu-id="934fd-284">No</span></span>|<span data-ttu-id="934fd-285">Jest zgłaszany wyjątek, a transakcja zostanie wycofana.</span><span class="sxs-lookup"><span data-stu-id="934fd-285">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="934fd-286">Dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="934fd-286">Two-Way</span></span>|<span data-ttu-id="934fd-287">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-287">✓</span></span>|<span data-ttu-id="934fd-288">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-288">✓</span></span>||<span data-ttu-id="934fd-289">Nie</span><span class="sxs-lookup"><span data-stu-id="934fd-289">No</span></span>|<span data-ttu-id="934fd-290">Jest zgłaszany wyjątek, a transakcja zostanie wycofana.</span><span class="sxs-lookup"><span data-stu-id="934fd-290">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="934fd-291">Dupleks</span><span class="sxs-lookup"><span data-stu-id="934fd-291">Duplex</span></span>||||<span data-ttu-id="934fd-292">Nie</span><span class="sxs-lookup"><span data-stu-id="934fd-292">No</span></span>|<span data-ttu-id="934fd-293">Komunikację dupleksową non sesji nie jest obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="934fd-293">Non-session duplex communication is not currently supported.</span></span>|  
|<span data-ttu-id="934fd-294">Dupleks</span><span class="sxs-lookup"><span data-stu-id="934fd-294">Duplex</span></span>|<span data-ttu-id="934fd-295">✓</span><span class="sxs-lookup"><span data-stu-id="934fd-295">✓</span></span>|||<span data-ttu-id="934fd-296">Tak</span><span class="sxs-lookup"><span data-stu-id="934fd-296">Yes</span></span>|<span data-ttu-id="934fd-297">Wyślij do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="934fd-297">Send to a backup destination.</span></span>|  
  
## <a name="hosting"></a><span data-ttu-id="934fd-298">Hosting</span><span class="sxs-lookup"><span data-stu-id="934fd-298">Hosting</span></span>  
 <span data-ttu-id="934fd-299">Ponieważ usługa routingu jest zaimplementowana jako usługa WCF, musi być albo może być samodzielnie hostowane w aplikacji lub hostowanych przez usługi IIS i WAS.</span><span class="sxs-lookup"><span data-stu-id="934fd-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="934fd-300">Zaleca się, że usługa routingu znajdować IIS, WAS, lub aplikacji usługi Windows można skorzystać z automatycznego uruchamiania i cyklu życia funkcje zarządzania dostępne w tych środowiskach hostingu.</span><span class="sxs-lookup"><span data-stu-id="934fd-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>  
  
 <span data-ttu-id="934fd-301">Poniższy przykład pokazuje usługi routingu w aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="934fd-301">The following example demonstrates hosting the Routing Service in an application.</span></span>  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 <span data-ttu-id="934fd-302">Do obsługi usługi routingu w ramach usług IIS i WAS, możesz utworzyć plik usługi (SVC) lub użyć aktywację w oparciu o konfigurację usługi.</span><span class="sxs-lookup"><span data-stu-id="934fd-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="934fd-303">Korzystając z pliku usługi, należy określić <xref:System.ServiceModel.Routing.RoutingService> za pomocą parametru usługi.</span><span class="sxs-lookup"><span data-stu-id="934fd-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="934fd-304">Poniższy przykład zawiera przykładowy plik usługi, który może służyć do obsługi usługi routingu za pomocą usług IIS i WAS.</span><span class="sxs-lookup"><span data-stu-id="934fd-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a><span data-ttu-id="934fd-305">Usługa routingu i personifikacja</span><span class="sxs-lookup"><span data-stu-id="934fd-305">Routing Service and Impersonation</span></span>  
 <span data-ttu-id="934fd-306">Usługa routingu WCF umożliwia personifikacji zarówno wysyłania i odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="934fd-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="934fd-307">Zastosuj wszystkie zwykle ograniczenia Windows personifikacji.</span><span class="sxs-lookup"><span data-stu-id="934fd-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="934fd-308">Jeśli wymagałby skonfigurować uprawnienia usługi lub konto do użycia personifikacji, podczas pisania własnych usług, będzie konieczne przeprowadzenie tych te same kroki, aby używać personifikacji z usługą routingu.</span><span class="sxs-lookup"><span data-stu-id="934fd-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="934fd-309">Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="934fd-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="934fd-310">Personifikacja z usługą routingu wymaga użycia personifikacji aplikacji ASP.NET w trybie zgodności platformy ASP.NET lub Użyj poświadczeń Windows, które zostały skonfigurowane, aby umożliwić personifikacji.</span><span class="sxs-lookup"><span data-stu-id="934fd-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="934fd-311">Aby uzyskać więcej informacji na temat trybu zgodności programu ASP.NET, zobacz [usługi WCF i platforma ASP.NET](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="934fd-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="934fd-312">Usługa routingu WCF nie obsługuje personifikacji z uwierzytelnianiem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="934fd-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>  
  
 <span data-ttu-id="934fd-313">Aby użyć personifikacji aplikacji ASP.NET z usługą routingu, Włącz tryb zgodności ASP.NET w usłudze Środowisko hostingu.</span><span class="sxs-lookup"><span data-stu-id="934fd-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="934fd-314">Usługa routingu już została oznaczona jako zezwolenie na tryb zgodności ASP.NET i personifikacja zostaną automatycznie włączone.</span><span class="sxs-lookup"><span data-stu-id="934fd-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="934fd-315">Personifikacja jest obsługiwane tylko użytkowania Integracja platformy ASP.NET z usługą routingu.</span><span class="sxs-lookup"><span data-stu-id="934fd-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>  
  
 <span data-ttu-id="934fd-316">Za pomocą Windows poświadczeń personifikacji należy skonfigurować zarówno poświadczenia usługą routingu i usługi.</span><span class="sxs-lookup"><span data-stu-id="934fd-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="934fd-317">Obiekt poświadczeń klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, jest dostępna z <xref:System.ServiceModel.ChannelFactory>) definiuje <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość, która musi być ustawione na Zezwalaj personifikacji.</span><span class="sxs-lookup"><span data-stu-id="934fd-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="934fd-318">Na koniec w usłudze, musisz skonfigurować <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> zachowanie, aby ustawić `ImpersonateCallerForAllOperations` do `true`.</span><span class="sxs-lookup"><span data-stu-id="934fd-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="934fd-319">Usługa routingu używa tej flagi do określania, czy chcesz utworzyć klientów do przekazywania wiadomości z włączona personifikacja.</span><span class="sxs-lookup"><span data-stu-id="934fd-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934fd-320">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="934fd-320">See also</span></span>

- [<span data-ttu-id="934fd-321">Filtry komunikatów</span><span class="sxs-lookup"><span data-stu-id="934fd-321">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="934fd-322">Kontrakty routingu</span><span class="sxs-lookup"><span data-stu-id="934fd-322">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="934fd-323">Wybieranie filtru</span><span class="sxs-lookup"><span data-stu-id="934fd-323">Choosing a Filter</span></span>](choosing-a-filter.md)
