---
title: Wprowadzenie do routingu
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: eaf09c0d724521c3c69fde0e90ecd7cd5aadb253
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988665"
---
# <a name="routing-introduction"></a><span data-ttu-id="33278-102">Wprowadzenie do routingu</span><span class="sxs-lookup"><span data-stu-id="33278-102">Routing Introduction</span></span>
<span data-ttu-id="33278-103">Usługa routingu oferuje ogólny, podłączany pośrednik protokołu SOAP, który umożliwia kierowanie komunikatów na podstawie treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="33278-104">Za pomocą usługi routingu można utworzyć złożoną logikę routingu, która umożliwia implementowanie scenariuszy, takich jak agregacja usług, przechowywanie wersji usług, routing priorytetów i Routing multiemisji.</span><span class="sxs-lookup"><span data-stu-id="33278-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="33278-105">Usługa routingu oferuje również obsługę błędów, która pozwala na skonfigurowanie list punktów końcowych kopii zapasowych, do których komunikaty są wysyłane w przypadku wystąpienia błędu podczas wysyłania do podstawowego docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="33278-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>  
  
 <span data-ttu-id="33278-106">Ten temat jest przeznaczony dla nowych usługi routingu i obejmuje podstawową konfigurację i hosting usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="33278-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="33278-107">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="33278-107">Configuration</span></span>  
 <span data-ttu-id="33278-108">Usługa routingu jest zaimplementowana jako usługa WCF, która udostępnia jeden lub więcej punktów końcowych usługi, które odbierają komunikaty z aplikacji klienckich i kierują komunikaty do co najmniej jednego docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="33278-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="33278-109">Usługa udostępnia <xref:System.ServiceModel.Routing.RoutingBehavior>, która jest stosowana do punktów końcowych usługi udostępnianych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="33278-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="33278-110">To zachowanie służy do konfigurowania różnych aspektów działania usługi.</span><span class="sxs-lookup"><span data-stu-id="33278-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="33278-111">Aby ułatwić konfigurację podczas korzystania z pliku konfiguracji, parametry są określone w **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="33278-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="33278-112">W scenariuszach opartych na kodzie te parametry byłyby określone jako część <xref:System.ServiceModel.Routing.RoutingConfiguration> obiektu, który można następnie przesłać do **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="33278-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>  
  
 <span data-ttu-id="33278-113">Po uruchomieniu to zachowanie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, który jest używany do przeprowadzenia przetwarzania komunikatów przez protokół SOAP, do punktów końcowych klienta.</span><span class="sxs-lookup"><span data-stu-id="33278-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="33278-114">Dzięki temu usługa routingu może przesyłać wiadomości do punktów końcowych, które wymagają innego elementu **MessageVersion** niż punkt końcowy, w którym wiadomość została odebrana.</span><span class="sxs-lookup"><span data-stu-id="33278-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="33278-115">**RoutingBehavior** rejestruje także rozszerzenie usługi, <xref:System.ServiceModel.Routing.RoutingExtension>która zapewnia punkt dostępności do modyfikowania konfiguracji usługi routingu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="33278-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>  
  
 <span data-ttu-id="33278-116">Klasa **zastosowano** zapewnia spójny sposób konfigurowania i aktualizowania konfiguracji usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="33278-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="33278-117">Zawiera parametry, które działają jako ustawienia usługi routingu i służy do konfigurowania **RoutingBehavior** podczas uruchamiania usługi lub są przesyłane do **RoutingExtension** w celu zmodyfikowania konfiguracji routingu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="33278-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>  
  
 <span data-ttu-id="33278-118">Logika routingu używana do przeprowadzania routingu komunikatów opartych na zawartości jest definiowana przez grupowanie <xref:System.ServiceModel.Dispatcher.MessageFilter> wielu obiektów w tabele filtrów (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> obiekty).</span><span class="sxs-lookup"><span data-stu-id="33278-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="33278-119">Komunikaty przychodzące są oceniane względem filtrów komunikatów zawartych w tabeli filtrów i dla każdego **MessageFilter** , który odpowiada komunikatowi, przekazywany do docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="33278-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="33278-120">Tabela filtrów, która powinna być używana do routowania komunikatów, jest określana za pomocą **RoutingBehavior** w konfiguracji lub za pośrednictwem kodu przy użyciu obiektu **zastosowano** .</span><span class="sxs-lookup"><span data-stu-id="33278-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>  
  
### <a name="defining-endpoints"></a><span data-ttu-id="33278-121">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="33278-121">Defining Endpoints</span></span>  
 <span data-ttu-id="33278-122">Chociaż może się wydawać, że należy rozpocząć konfigurację przez zdefiniowanie logiki routingu, która będzie używana, pierwszym krokiem powinno być określenie kształtu punktów końcowych, do których będą wysyłane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="33278-123">Usługa routingu korzysta z kontraktów, które definiują kształt kanałów używanych do odbierania i wysyłania komunikatów, a w związku z tym kształt kanału wejściowego musi pasować do tego kanału wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="33278-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="33278-124">Na przykład w przypadku kierowania do punktów końcowych, które używają kształtu kanału żądanie-odpowiedź, należy użyć zgodnego kontraktu dla przychodzących punktów końcowych, takich jak <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="33278-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>  
  
 <span data-ttu-id="33278-125">Oznacza to, że jeśli docelowe punkty końcowe używają kontraktów z wieloma wzorcami komunikacji (takich jak mieszanie operacji jednokierunkowych i dwukierunkowych), nie można utworzyć pojedynczego punktu końcowego usługi, który może odbierać i kierować wiadomości do wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="33278-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="33278-126">Należy określić, które punkty końcowe mają zgodne kształty i zdefiniować co najmniej jeden punkt końcowy usługi, który będzie używany do odbierania komunikatów do kierowania do docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="33278-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33278-127">Podczas pracy z kontraktami, które określają wiele wzorców komunikacji (takich jak mieszanie jednokierunkowych i dwukierunkowych operacji), obejście polega na użyciu kontraktu dupleksowego w usłudze routingu, takiego jak <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span><span class="sxs-lookup"><span data-stu-id="33278-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="33278-128">Oznacza to jednak, że powiązanie musi mieć możliwość komunikacji dwukierunkowej, co może nie być możliwe w przypadku wszystkich scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="33278-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="33278-129">W scenariuszach, w których nie jest to możliwe, może być konieczne nawiązanie komunikacji z wieloma punktami końcowymi lub zmodyfikowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="33278-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>  
  
 <span data-ttu-id="33278-130">Aby uzyskać więcej informacji na temat kontraktów routingu, zobacz [Kontrakty routingu](routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="33278-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>  
  
 <span data-ttu-id="33278-131">Po zdefiniowaniu punktu końcowego usługi można użyć **RoutingBehavior** do skojarzenia określonego **zastosowano** z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="33278-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="33278-132">Podczas konfigurowania usługi routingu przy użyciu pliku konfiguracji **RoutingBehavior** jest używany do określania tabeli filtrów zawierającej logikę routingu służącą do przetwarzania komunikatów odebranych w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="33278-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="33278-133">Jeśli konfigurujesz usługę routingu programowo, możesz określić tabelę filtrów za pomocą **zastosowano**.</span><span class="sxs-lookup"><span data-stu-id="33278-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>  
  
 <span data-ttu-id="33278-134">W poniższym przykładzie zdefiniowano punkty końcowe usługi i klienta, które są używane przez usługę routingu programowo i przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="33278-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="33278-135">Ten przykład umożliwia skonfigurowanie usługi routingu w celu uwidocznienia pojedynczego punktu końcowego przy użyciu `http://localhost:8000/routingservice/router`adresu, który jest używany do odbierania komunikatów do rozesłania.</span><span class="sxs-lookup"><span data-stu-id="33278-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="33278-136">Ponieważ komunikaty są kierowane do punktów końcowych żądania-odpowiedź, punkt końcowy usługi używa <xref:System.ServiceModel.Routing.IRequestReplyRouter> kontraktu.</span><span class="sxs-lookup"><span data-stu-id="33278-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="33278-137">Ta konfiguracja definiuje także jeden punkt końcowy `http://localhost:8000/servicemodelsample/service` klienta, do którego są kierowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="33278-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="33278-138">Tabela filtrów (niepokazywana) o nazwie "routingTable1" zawiera logikę routingu służącą do przesyłania komunikatów i jest skojarzona z punktem końcowym usługi przy użyciu **RoutingBehavior** (dla pliku konfiguracji) lub **zastosowano** (dla Konfiguracja programowa).</span><span class="sxs-lookup"><span data-stu-id="33278-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>  
  
### <a name="routing-logic"></a><span data-ttu-id="33278-139">Logika routingu</span><span class="sxs-lookup"><span data-stu-id="33278-139">Routing Logic</span></span>  
 <span data-ttu-id="33278-140">Aby zdefiniować logikę routingu służącą do przesyłania komunikatów, należy określić, jakie dane zawarte w wiadomościach przychodzących mogą być w sposób unikatowy.</span><span class="sxs-lookup"><span data-stu-id="33278-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="33278-141">Na przykład, jeśli wszystkie docelowe punkty końcowe, które mają być współużytkowane przez Ciebie te same akcje protokołu SOAP, wartość akcji zawartej w komunikacie nie jest dobrym wskaźnikiem, do którego określony punkt końcowy powinien być kierowany.</span><span class="sxs-lookup"><span data-stu-id="33278-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="33278-142">Jeśli musisz jednoznacznie skierować komunikaty do jednego określonego punktu końcowego, należy odfiltrować dane, które jednoznacznie identyfikują docelowy punkt końcowy, do którego wiadomość jest kierowana.</span><span class="sxs-lookup"><span data-stu-id="33278-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>  
  
 <span data-ttu-id="33278-143">Usługa routingu udostępnia kilka implementacji **MessageFilter** , które sprawdzają określone wartości w wiadomości, takie jak adres, Akcja, nazwa punktu końcowego, a nawet zapytanie XPath.</span><span class="sxs-lookup"><span data-stu-id="33278-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="33278-144">Jeśli żadna z tych implementacji nie spełnia Twoich potrzeb, możesz utworzyć niestandardową implementację **MessageFilter** .</span><span class="sxs-lookup"><span data-stu-id="33278-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="33278-145">Aby uzyskać więcej informacji na temat filtrów komunikatów i porównania implementacji używanych przez usługę routingu, zobacz [filtry komunikatów](message-filters.md) i [Wybieranie filtru](choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="33278-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>  
  
 <span data-ttu-id="33278-146">Wiele filtrów komunikatów jest zorganizowanych w tabelach filtru, które kojarzą poszczególne **MessageFilter** z docelowym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="33278-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="33278-147">Opcjonalnie można również użyć tabeli filtrów, aby określić listę punktów końcowych kopii zapasowych, które usługa routingu podejmie próbę wysłania komunikatu w przypadku niepowodzenia transmisji.</span><span class="sxs-lookup"><span data-stu-id="33278-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>  
  
 <span data-ttu-id="33278-148">Domyślnie wszystkie filtry komunikatów w tabeli filtrów są oceniane jednocześnie; można jednak określić <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> , że filtry komunikatów mają być oceniane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="33278-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="33278-149">Wszystkie wpisy o najwyższym priorytecie są oceniane jako pierwsze, a filtry komunikatów o niższych priorytetach nie są oceniane, jeśli dopasowanie zostanie znalezione na wyższym poziomie priorytetu.</span><span class="sxs-lookup"><span data-stu-id="33278-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="33278-150">Aby uzyskać więcej informacji na temat tabel filtrów, zobacz [filtry komunikatów](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="33278-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>  
  
 <span data-ttu-id="33278-151">W poniższych przykładach użyto <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> `true` elementu, który jest przeznaczony dla wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="33278-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="33278-152">Ten **MessageFilter** jest dodawany do tabeli filtrów "routingTable1", która kojarzy **MessageFilter** z punktem końcowym klienta o nazwie "CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="33278-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="33278-153">**RoutingBehavior** następnie określa, że ta tabela powinna być używana do przesyłania komunikatów przetwarzanych przez punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="33278-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>  
  
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
> <span data-ttu-id="33278-154">Domyślnie usługa routingu szacuje tylko nagłówki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="33278-155">Aby zezwolić filtrom na dostęp do treści wiadomości, należy ustawić <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> na. `false`</span><span class="sxs-lookup"><span data-stu-id="33278-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>  
  
 <span data-ttu-id="33278-156">**Multicast**</span><span class="sxs-lookup"><span data-stu-id="33278-156">**Multicast**</span></span>  
  
 <span data-ttu-id="33278-157">Chociaż wiele konfiguracji usługi routingu korzysta z logiki filtru wyłącznego, która kieruje komunikaty tylko do jednego określonego punktu końcowego, może być konieczne kierowanie danego komunikatu do wielu docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="33278-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="33278-158">Aby dokonać multiemisji komunikatu do wielu miejsc docelowych, muszą być spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="33278-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>  
  
- <span data-ttu-id="33278-159">Kształt kanału nie może być odpowiedzią na żądanie (choć może być jednokierunkowa lub dwustronna), ponieważ aplikacja kliencka może odebrać tylko jedną odpowiedź w odpowiedzi na żądanie.</span><span class="sxs-lookup"><span data-stu-id="33278-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>  
  
- <span data-ttu-id="33278-160">Podczas oceny komunikatu należy `true` zwrócić wiele filtrów.</span><span class="sxs-lookup"><span data-stu-id="33278-160">Multiple filters must return `true` when evaluating the message.</span></span>  
  
 <span data-ttu-id="33278-161">Jeśli te warunki są spełnione, komunikat jest kierowany do wszystkich punktów końcowych wszystkich filtrów, które podlegają `true`ocenie.</span><span class="sxs-lookup"><span data-stu-id="33278-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="33278-162">Poniższy przykład definiuje konfigurację routingu, która powoduje, że komunikaty są przesyłane do obu punktów końcowych, jeśli adres punktu końcowego w `http://localhost:8000/routingservice/router/rounding`komunikacie jest.</span><span class="sxs-lookup"><span data-stu-id="33278-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>  
  
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
  
### <a name="soap-processing"></a><span data-ttu-id="33278-163">Przetwarzanie SOAP</span><span class="sxs-lookup"><span data-stu-id="33278-163">SOAP Processing</span></span>  
 <span data-ttu-id="33278-164">W celu obsługi routingu komunikatów między niepodobnymi protokołami **RoutingBehavior** domyślnie dodaje <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do wszystkich punktów końcowych klienta, do których są kierowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="33278-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="33278-165">To zachowanie powoduje automatyczne utworzenie nowego elementu **MessageVersion** przed przekazaniem komunikatu do punktu końcowego, a także utworzenie zgodnego elementu **MessageVersion** dla dowolnego dokumentu odpowiedzi przed zwróceniem go do żądającej aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="33278-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>  
  
 <span data-ttu-id="33278-166">Kroki wykonywane w celu utworzenia nowego elementu **MessageVersion** dla wiadomości wychodzącej są następujące:</span><span class="sxs-lookup"><span data-stu-id="33278-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>  
  
 <span data-ttu-id="33278-167">**Przetwarzanie żądania**</span><span class="sxs-lookup"><span data-stu-id="33278-167">**Request processing**</span></span>  
  
- <span data-ttu-id="33278-168">Pobierz element **MessageVersion** powiązania/kanału wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="33278-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>  
  
- <span data-ttu-id="33278-169">Pobierz czytnik treści dla oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-169">Get the body reader for the original message.</span></span>  
  
- <span data-ttu-id="33278-170">Utwórz nową wiadomość z tą samą akcją, czytelnikem treści i nową wartość **MessageVersion**.</span><span class="sxs-lookup"><span data-stu-id="33278-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>  
  
- <span data-ttu-id="33278-171">Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing. None**, skopiuj nagłówki do, from, FaultTo i RelatesTo do nowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
- <span data-ttu-id="33278-172">Skopiuj wszystkie właściwości wiadomości do nowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-172">Copy all message properties to the new message.</span></span>  
  
- <span data-ttu-id="33278-173">Zapisz oryginalny komunikat żądania, który ma być używany podczas przetwarzania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="33278-173">Store the original request message to use when processing the response.</span></span>  
  
- <span data-ttu-id="33278-174">Zwróć nowy komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="33278-174">Return the new request message.</span></span>  
  
 <span data-ttu-id="33278-175">**Przetwarzanie odpowiedzi**</span><span class="sxs-lookup"><span data-stu-id="33278-175">**Response processing**</span></span>  
  
- <span data-ttu-id="33278-176">Pobierz element **MessageVersion** oryginalnego komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="33278-176">Get the **MessageVersion** of the original request message.</span></span>  
  
- <span data-ttu-id="33278-177">Pobierz czytnik treści dla odebranego komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="33278-177">Get the body reader for the received response message.</span></span>  
  
- <span data-ttu-id="33278-178">Utwórz nowy komunikat odpowiedzi z tą samą akcją, czytelnikem treści i elementem **MessageVersion** oryginalnego komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="33278-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>  
  
- <span data-ttu-id="33278-179">Jeśli <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing. None**, skopiuj nagłówki do, from, FaultTo i RelatesTo do nowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
- <span data-ttu-id="33278-180">Skopiuj właściwości wiadomości do nowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-180">Copy the message properties to the new message.</span></span>  
  
- <span data-ttu-id="33278-181">Zwróć nowy komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="33278-181">Return the new response message.</span></span>  
  
 <span data-ttu-id="33278-182">Domyślnie **SoapProcessingBehavior** jest automatycznie dodawany do punktów końcowych klienta przez <xref:System.ServiceModel.Routing.RoutingBehavior> uruchomienie usługi, jednak można kontrolować, czy przetwarzanie protokołu SOAP jest dodawane do wszystkich <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> punktów końcowych klienta przy użyciu właściwości .</span><span class="sxs-lookup"><span data-stu-id="33278-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="33278-183">Możesz również dodać zachowanie bezpośrednio do określonego punktu końcowego i włączać lub wyłączać to zachowanie na poziomie punktu końcowego, jeśli jest wymagany bardziej szczegółowy formant przetwarzania protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="33278-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33278-184">Jeśli przetwarzanie protokołu SOAP jest wyłączone dla punktu końcowego, który wymaga innego elementu MessageVersion niż oryginalny komunikat żądania, należy podać niestandardowy mechanizm wykonywania wszelkich modyfikacji protokołu SOAP, które są wymagane przed wysłaniem komunikatu do docelowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="33278-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>  
  
 <span data-ttu-id="33278-185">W poniższych przykładach Właściwość **soapProcessingEnabled** służy do zapobiegania automatycznemu dodawaniu **SoapProcessingBehavior** do wszystkich punktów końcowych klienta.</span><span class="sxs-lookup"><span data-stu-id="33278-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>  
  
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
  
### <a name="dynamic-configuration"></a><span data-ttu-id="33278-186">Konfiguracja dynamiczna</span><span class="sxs-lookup"><span data-stu-id="33278-186">Dynamic Configuration</span></span>  
 <span data-ttu-id="33278-187">Po dodaniu kolejnych punktów końcowych klienta lub konieczności zmodyfikowania filtrów używanych do przesyłania komunikatów należy mieć możliwość dynamicznego aktualizowania konfiguracji w czasie wykonywania, aby zapobiec przerywaniu usługi do punktów końcowych, w których obecnie są wysyłane komunikaty Usługa routingu.</span><span class="sxs-lookup"><span data-stu-id="33278-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="33278-188">Modyfikowanie pliku konfiguracji lub kodu aplikacji hosta nie zawsze jest wystarczające, ponieważ każda metoda wymaga odzyskania aplikacji, co może prowadzić do potencjalnej utraty wszelkich komunikatów, które są obecnie przesyłane i potencjalną przyczyną przestoju oczekiwanie na ponowne uruchomienie usługi.</span><span class="sxs-lookup"><span data-stu-id="33278-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>  
  
 <span data-ttu-id="33278-189">**Zastosowano** można modyfikować tylko programowo.</span><span class="sxs-lookup"><span data-stu-id="33278-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="33278-190">Podczas początkowego konfigurowania usługi za pomocą pliku konfiguracji można zmienić tylko konfigurację w czasie wykonywania, tworząc nową **zastosowano** i przekazując ją jako parametr do <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> metody uwidocznionej przez <xref:System.ServiceModel.Routing.RoutingExtension>rozszerzenie usługi.</span><span class="sxs-lookup"><span data-stu-id="33278-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfiguration** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="33278-191">Wszystkie komunikaty w trakcie przesyłania są nadal kierowane przy użyciu poprzedniej konfiguracji, a komunikaty odebrane po wywołaniu **ApplyConfiguration** używają nowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="33278-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="33278-192">Poniższy przykład ilustruje tworzenie wystąpienia usługi routingu, a następnie modyfikowanie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="33278-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>  
  
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
> <span data-ttu-id="33278-193">Podczas aktualizowania usługi routingu w ten sposób można tylko przekazać nową konfigurację.</span><span class="sxs-lookup"><span data-stu-id="33278-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="33278-194">Nie można modyfikować tylko wybranych elementów bieżącej konfiguracji lub dołączać nowych wpisów do bieżącej konfiguracji; należy utworzyć i przekazać nową konfigurację, która zastąpi istniejącą.</span><span class="sxs-lookup"><span data-stu-id="33278-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33278-195">Wszystkie sesje otwarte przy użyciu poprzedniej konfiguracji nadal używają poprzedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="33278-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="33278-196">Nowa konfiguracja jest używana tylko przez nowe sesje.</span><span class="sxs-lookup"><span data-stu-id="33278-196">The new configuration is only used by new sessions.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="33278-197">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="33278-197">Error Handling</span></span>  
 <span data-ttu-id="33278-198">Jeśli wystąpił błąd podczas próby wysłania komunikatu, zostanieprzeprowadzonaobsługabłędów.<xref:System.ServiceModel.CommunicationException></span><span class="sxs-lookup"><span data-stu-id="33278-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="33278-199">Te wyjątki zwykle wskazują, że wystąpił problem podczas próby komunikowania się ze zdefiniowanym punktem końcowym klienta, <xref:System.ServiceModel.EndpointNotFoundException>na przykład, <xref:System.ServiceModel.ServerTooBusyException>lub <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="33278-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="33278-200">Obsługa błędów — kod również będzie przechwytywać i próbować ponowić próbę wysłania <xref:System.TimeoutException> , który jest innym typowym wyjątkiem, który nie pochodzi od **CommunicationException**.</span><span class="sxs-lookup"><span data-stu-id="33278-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>  
  
 <span data-ttu-id="33278-201">Po wystąpieniu jednego z powyższych wyjątków usługa routingu zostaje przełączona w tryb failover do listy punktów końcowych kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="33278-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="33278-202">Jeśli wszystkie punkty końcowe kopii zapasowej zakończą się niepowodzeniem z błędem komunikacji lub jeśli punkt końcowy zwróci wyjątek wskazujący awarię w ramach usługi docelowej, usługa routingu zwróci błąd do aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="33278-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33278-203">Funkcja obsługi błędów przechwytuje i obsługuje wyjątki występujące podczas próby wysłania komunikatu i próby zamknięcia kanału.</span><span class="sxs-lookup"><span data-stu-id="33278-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="33278-204">Kod obsługi błędu nie jest przeznaczony do wykrywania lub obsługi wyjątków utworzonych przez punkty końcowe aplikacji, z którymi się komunikują. zgłoszone przez usługę pojawia się w usłudze routingu jako FaultMessage i jest przepływa z powrotem do klienta. <xref:System.ServiceModel.FaultException></span><span class="sxs-lookup"><span data-stu-id="33278-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>  
>   
>  <span data-ttu-id="33278-205">Jeśli wystąpi błąd, gdy usługa routingu próbuje przekazać komunikat, może się pojawić <xref:System.ServiceModel.FaultException> po stronie klienta, a nie <xref:System.ServiceModel.EndpointNotFoundException> w przypadku braku usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="33278-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="33278-206">Usługa routingu może w ten sposób maskować wyjątki i nie zapewniać pełnej przejrzystości, chyba że zostanie sprawdzona zagnieżdżonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="33278-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="33278-207">Śledzenie wyjątków</span><span class="sxs-lookup"><span data-stu-id="33278-207">Tracing Exceptions</span></span>  
 <span data-ttu-id="33278-208">Gdy wysyłanie komunikatu do punktu końcowego na liście kończy się niepowodzeniem, usługa routingu śledzi otrzymane dane wyjątku i dołącza szczegóły wyjątku jako właściwość komunikatu o nazwie Exceptions.</span><span class="sxs-lookup"><span data-stu-id="33278-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="33278-209">Pozwala to zachować dane wyjątku i umożliwia użytkownikom dostęp programistyczny za pomocą Inspektora komunikatów.</span><span class="sxs-lookup"><span data-stu-id="33278-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="33278-210">Dane wyjątku są przechowywane na komunikat w słowniku, który mapuje nazwę punktu końcowego na szczegóły wyjątku napotkane podczas próby wysłania do niego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="33278-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>  
  
### <a name="backup-endpoints"></a><span data-ttu-id="33278-211">Punkty końcowe kopii zapasowej</span><span class="sxs-lookup"><span data-stu-id="33278-211">Backup Endpoints</span></span>  
 <span data-ttu-id="33278-212">Każdy wpis filtru w tabeli filtrów może opcjonalnie określić listę punktów końcowych kopii zapasowych, które są używane w przypadku niepowodzenia transmisji podczas wysyłania do podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="33278-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="33278-213">Jeśli wystąpi awaria, usługa routingu próbuje przesłać komunikat do pierwszego wpisu na liście punktów końcowych kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="33278-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="33278-214">Jeśli próba wysłania spowoduje również awarię transmisji, zostanie podjęta próba następnego punktu końcowego z listy kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="33278-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="33278-215">Usługa routingu kontynuuje wysyłanie komunikatów do każdego punktu końcowego na liście do momentu pomyślnego odebrania komunikatu. wszystkie punkty końcowe zwracają błąd transmisji lub w punkcie końcowym jest zwracany błąd niebędący przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="33278-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>  
  
 <span data-ttu-id="33278-216">Poniższe przykłady umożliwiają skonfigurowanie usługi routingu do korzystania z listy kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="33278-216">The following examples configure the Routing Service to use a backup list.</span></span>  
  
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
  
### <a name="supported-error-patterns"></a><span data-ttu-id="33278-217">Obsługiwane wzorce błędów</span><span class="sxs-lookup"><span data-stu-id="33278-217">Supported Error Patterns</span></span>  
 <span data-ttu-id="33278-218">W poniższej tabeli opisano wzorce zgodne z użyciem list punktów końcowych kopii zapasowych oraz uwagi opisujące szczegóły obsługi błędów dla określonych wzorców.</span><span class="sxs-lookup"><span data-stu-id="33278-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>  
  
|<span data-ttu-id="33278-219">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="33278-219">Pattern</span></span>|<span data-ttu-id="33278-220">Sesja</span><span class="sxs-lookup"><span data-stu-id="33278-220">Session</span></span>|<span data-ttu-id="33278-221">Transakcja</span><span class="sxs-lookup"><span data-stu-id="33278-221">Transaction</span></span>|<span data-ttu-id="33278-222">Odbieranie kontekstu</span><span class="sxs-lookup"><span data-stu-id="33278-222">Receive Context</span></span>|<span data-ttu-id="33278-223">Lista kopii zapasowych jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="33278-223">Backup List Supported</span></span>|<span data-ttu-id="33278-224">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33278-224">Notes</span></span>|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|<span data-ttu-id="33278-225">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-225">One-Way</span></span>||||<span data-ttu-id="33278-226">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-226">Yes</span></span>|<span data-ttu-id="33278-227">Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="33278-228">Jeśli ten komunikat jest multiemisją, tylko komunikat w kanale zakończonym niepowodzeniem jest przenoszony do jego miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|  
|<span data-ttu-id="33278-229">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-229">One-Way</span></span>||<span data-ttu-id="33278-230">✓</span><span class="sxs-lookup"><span data-stu-id="33278-230">✓</span></span>||<span data-ttu-id="33278-231">Nie</span><span class="sxs-lookup"><span data-stu-id="33278-231">No</span></span>|<span data-ttu-id="33278-232">Wyjątek jest zgłaszany, a transakcja jest wycofywana.</span><span class="sxs-lookup"><span data-stu-id="33278-232">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="33278-233">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-233">One-Way</span></span>|||<span data-ttu-id="33278-234">✓</span><span class="sxs-lookup"><span data-stu-id="33278-234">✓</span></span>|<span data-ttu-id="33278-235">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-235">Yes</span></span>|<span data-ttu-id="33278-236">Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="33278-237">Po pomyślnym odebraniu komunikatu Ukończ wszystkie konteksty odbierania.</span><span class="sxs-lookup"><span data-stu-id="33278-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="33278-238">Jeśli komunikat nie został pomyślnie odebrany przez żaden punkt końcowy, nie należy kończyć kontekstu odbierania.</span><span class="sxs-lookup"><span data-stu-id="33278-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="33278-239">Gdy ten komunikat jest multiemisją, kontekst odbierania jest wykonywany tylko wtedy, gdy komunikat zostanie pomyślnie odebrany przez co najmniej jeden punkt końcowy (podstawowy lub zapasowy).</span><span class="sxs-lookup"><span data-stu-id="33278-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="33278-240">Jeśli żaden z punktów końcowych we wszystkich ścieżkach multiemisji nie otrzyma komunikatu, nie wypełniaj kontekstu odbierania.</span><span class="sxs-lookup"><span data-stu-id="33278-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|  
|<span data-ttu-id="33278-241">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-241">One-Way</span></span>||<span data-ttu-id="33278-242">✓</span><span class="sxs-lookup"><span data-stu-id="33278-242">✓</span></span>|<span data-ttu-id="33278-243">✓</span><span class="sxs-lookup"><span data-stu-id="33278-243">✓</span></span>|<span data-ttu-id="33278-244">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-244">Yes</span></span>|<span data-ttu-id="33278-245">Przerwij poprzednią transakcję, Utwórz nową transakcję i ponownie Wyślij wszystkie komunikaty.</span><span class="sxs-lookup"><span data-stu-id="33278-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="33278-246">Komunikaty, które napotkały błąd, są przesyłane do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="33278-247">Po utworzeniu transakcji, w której wszystkie operacje kończą się powodzeniem, Wypełnij konteksty odbierania i zatwierdź transakcję.</span><span class="sxs-lookup"><span data-stu-id="33278-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|  
|<span data-ttu-id="33278-248">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-248">One-Way</span></span>|<span data-ttu-id="33278-249">✓</span><span class="sxs-lookup"><span data-stu-id="33278-249">✓</span></span>|||<span data-ttu-id="33278-250">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-250">Yes</span></span>|<span data-ttu-id="33278-251">Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="33278-252">W scenariuszu multiemisji tylko komunikaty w sesji, które napotkały błąd lub w sesji, której zamknięcie nie powiodło się, są ponownie wysyłane do miejsc docelowych kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="33278-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|  
|<span data-ttu-id="33278-253">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-253">One-Way</span></span>|<span data-ttu-id="33278-254">✓</span><span class="sxs-lookup"><span data-stu-id="33278-254">✓</span></span>|<span data-ttu-id="33278-255">✓</span><span class="sxs-lookup"><span data-stu-id="33278-255">✓</span></span>||<span data-ttu-id="33278-256">Nie</span><span class="sxs-lookup"><span data-stu-id="33278-256">No</span></span>|<span data-ttu-id="33278-257">Wyjątek jest zgłaszany, a transakcja jest wycofywana.</span><span class="sxs-lookup"><span data-stu-id="33278-257">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="33278-258">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-258">One-Way</span></span>|<span data-ttu-id="33278-259">✓</span><span class="sxs-lookup"><span data-stu-id="33278-259">✓</span></span>||<span data-ttu-id="33278-260">✓</span><span class="sxs-lookup"><span data-stu-id="33278-260">✓</span></span>|<span data-ttu-id="33278-261">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-261">Yes</span></span>|<span data-ttu-id="33278-262">Próbuje ponownie wysłać wiadomość w punkcie końcowym kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="33278-263">Gdy wszystkie komunikaty zostaną zakończone bez błędu, sesja wskazuje, że nie ma więcej komunikatów, a usługa routingu pomyślnie zamknie wszystkie wychodzące kanały sesji, wszystkie konteksty odbioru są wykonywane i zamknięto kanał sesji przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="33278-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|  
|<span data-ttu-id="33278-264">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-264">One-Way</span></span>|<span data-ttu-id="33278-265">✓</span><span class="sxs-lookup"><span data-stu-id="33278-265">✓</span></span>|<span data-ttu-id="33278-266">✓</span><span class="sxs-lookup"><span data-stu-id="33278-266">✓</span></span>|<span data-ttu-id="33278-267">✓</span><span class="sxs-lookup"><span data-stu-id="33278-267">✓</span></span>|<span data-ttu-id="33278-268">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-268">Yes</span></span>|<span data-ttu-id="33278-269">Przerwij bieżącą transakcję i Utwórz nową.</span><span class="sxs-lookup"><span data-stu-id="33278-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="33278-270">Wyślij ponownie wszystkie poprzednie wiadomości w sesji.</span><span class="sxs-lookup"><span data-stu-id="33278-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="33278-271">Po utworzeniu transakcji, w której wszystkie komunikaty zostały pomyślnie wysłane, a sesja wskazuje, że nie ma więcej komunikatów, wszystkie kanały sesji wychodzącej są zamknięte, a wszystkie, konteksty odbierania zostały zakończone z transakcją, kanał sesji przychodzącej to zamknięte, a transakcja jest zatwierdzona.</span><span class="sxs-lookup"><span data-stu-id="33278-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="33278-272">Gdy sesje są multiemisją, komunikaty, które nie miały błędu, są ponownie wysyłane do tego samego miejsca docelowego, co wcześniej, a komunikaty, które napotkały błąd, są wysyłane do miejsc docelowych kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="33278-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|  
|<span data-ttu-id="33278-273">Dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-273">Two-Way</span></span>||||<span data-ttu-id="33278-274">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-274">Yes</span></span>|<span data-ttu-id="33278-275">Wyślij do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-275">Send to a backup destination.</span></span>  <span data-ttu-id="33278-276">Gdy kanał zwróci komunikat odpowiedzi, zwróć odpowiedź do oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="33278-276">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="33278-277">Dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-277">Two-Way</span></span>|<span data-ttu-id="33278-278">✓</span><span class="sxs-lookup"><span data-stu-id="33278-278">✓</span></span>|||<span data-ttu-id="33278-279">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-279">Yes</span></span>|<span data-ttu-id="33278-280">Wyślij wszystkie komunikaty z kanału do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="33278-281">Gdy kanał zwróci komunikat odpowiedzi, zwróć odpowiedź do oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="33278-281">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="33278-282">Dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-282">Two-Way</span></span>||<span data-ttu-id="33278-283">✓</span><span class="sxs-lookup"><span data-stu-id="33278-283">✓</span></span>||<span data-ttu-id="33278-284">Nie</span><span class="sxs-lookup"><span data-stu-id="33278-284">No</span></span>|<span data-ttu-id="33278-285">Wyjątek jest zgłaszany, a transakcja jest wycofywana.</span><span class="sxs-lookup"><span data-stu-id="33278-285">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="33278-286">Dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="33278-286">Two-Way</span></span>|<span data-ttu-id="33278-287">✓</span><span class="sxs-lookup"><span data-stu-id="33278-287">✓</span></span>|<span data-ttu-id="33278-288">✓</span><span class="sxs-lookup"><span data-stu-id="33278-288">✓</span></span>||<span data-ttu-id="33278-289">Nie</span><span class="sxs-lookup"><span data-stu-id="33278-289">No</span></span>|<span data-ttu-id="33278-290">Wyjątek jest zgłaszany, a transakcja jest wycofywana.</span><span class="sxs-lookup"><span data-stu-id="33278-290">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="33278-291">Dupleks</span><span class="sxs-lookup"><span data-stu-id="33278-291">Duplex</span></span>||||<span data-ttu-id="33278-292">Nie</span><span class="sxs-lookup"><span data-stu-id="33278-292">No</span></span>|<span data-ttu-id="33278-293">Komunikacja niezgodna z dupleksem nie jest obecnie obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="33278-293">Non-session duplex communication is not currently supported.</span></span>|  
|<span data-ttu-id="33278-294">Dupleks</span><span class="sxs-lookup"><span data-stu-id="33278-294">Duplex</span></span>|<span data-ttu-id="33278-295">✓</span><span class="sxs-lookup"><span data-stu-id="33278-295">✓</span></span>|||<span data-ttu-id="33278-296">Tak</span><span class="sxs-lookup"><span data-stu-id="33278-296">Yes</span></span>|<span data-ttu-id="33278-297">Wyślij do miejsca docelowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="33278-297">Send to a backup destination.</span></span>|  
  
## <a name="hosting"></a><span data-ttu-id="33278-298">Hosting</span><span class="sxs-lookup"><span data-stu-id="33278-298">Hosting</span></span>  
 <span data-ttu-id="33278-299">Ponieważ usługa routingu jest zaimplementowana jako usługa WCF, musi być samodzielnie hostowana w aplikacji lub hostowana przez usługi IIS lub była.</span><span class="sxs-lookup"><span data-stu-id="33278-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="33278-300">Zaleca się, aby usługa routingu była hostowana w usługach IIS, WAS lub w aplikacji usługi systemu Windows, aby korzystać z funkcji automatycznego uruchamiania i zarządzania cyklem życia dostępnych w tych środowiskach hostingu.</span><span class="sxs-lookup"><span data-stu-id="33278-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>  
  
 <span data-ttu-id="33278-301">Poniższy przykład ilustruje hosting usługi routingu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="33278-301">The following example demonstrates hosting the Routing Service in an application.</span></span>  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 <span data-ttu-id="33278-302">Aby hostować usługę routingu w ramach usług IIS lub WAS, należy utworzyć plik usługi (. svc) lub użyć aktywacji usługi opartej na konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="33278-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="33278-303">W <xref:System.ServiceModel.Routing.RoutingService> przypadku korzystania z pliku usługi należy określić parametr using usługi.</span><span class="sxs-lookup"><span data-stu-id="33278-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="33278-304">Poniższy przykład zawiera przykładowy plik usługi, który może służyć do hostowania usługi routingu w usługach IIS lub WAS.</span><span class="sxs-lookup"><span data-stu-id="33278-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a><span data-ttu-id="33278-305">Usługa routingu i personifikacja</span><span class="sxs-lookup"><span data-stu-id="33278-305">Routing Service and Impersonation</span></span>  
 <span data-ttu-id="33278-306">Usługa routingu WCF może być używana z personifikacją zarówno w przypadku wysyłania, jak i otrzymywania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="33278-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="33278-307">Wszystkie typowe ograniczenia dotyczące personifikacji systemu Windows mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="33278-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="33278-308">Jeśli konieczne jest skonfigurowanie uprawnień usługi lub konta do korzystania z personifikacji podczas pisania własnej usługi, należy wykonać te same kroki, aby użyć personifikacji w usłudze routingu.</span><span class="sxs-lookup"><span data-stu-id="33278-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="33278-309">Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="33278-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="33278-310">Personifikacja w usłudze routingu wymaga użycia personifikacji ASP.NET w trybie zgodności ASP.NET lub użycia poświadczeń systemu Windows, które zostały skonfigurowane w celu zezwolenia na personifikację.</span><span class="sxs-lookup"><span data-stu-id="33278-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="33278-311">Aby uzyskać więcej informacji na temat trybu zgodności ASP.NET, zobacz [usługi WCF i ASP.NET](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="33278-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="33278-312">Usługa routingu WCF nie obsługuje personifikacji z uwierzytelnianiem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="33278-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>  
  
 <span data-ttu-id="33278-313">Aby użyć personifikacji ASP.NET w usłudze routingu, Włącz tryb zgodności ASP.NET w środowisku hostingu usługi.</span><span class="sxs-lookup"><span data-stu-id="33278-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="33278-314">Usługa routingu została już oznaczona jako zezwalająca na tryb zgodności ASP.NET, a personifikacja zostanie automatycznie włączona.</span><span class="sxs-lookup"><span data-stu-id="33278-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="33278-315">Personifikacja jest jedynym obsługiwanym wykorzystaniem integracji ASP.NET z usługą routingu.</span><span class="sxs-lookup"><span data-stu-id="33278-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>  
  
 <span data-ttu-id="33278-316">Aby użyć personifikacji poświadczeń systemu Windows przy użyciu usługi routingu, należy skonfigurować zarówno poświadczenia, jak i usługę.</span><span class="sxs-lookup"><span data-stu-id="33278-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="33278-317">Obiekt poświadczeń klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, do którego można uzyskać dostęp <xref:System.ServiceModel.ChannelFactory>z) definiuje <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość, która musi być ustawiona, aby zezwalać na personifikację.</span><span class="sxs-lookup"><span data-stu-id="33278-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="33278-318">Na koniec należy skonfigurować <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> zachowanie `true`ustawione na wartość `ImpersonateCallerForAllOperations` .</span><span class="sxs-lookup"><span data-stu-id="33278-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="33278-319">Usługa routingu używa tej flagi, aby zdecydować, czy należy utworzyć klientów do przekazywania komunikatów z włączoną personifikacją.</span><span class="sxs-lookup"><span data-stu-id="33278-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33278-320">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33278-320">See also</span></span>

- [<span data-ttu-id="33278-321">Filtry komunikatów</span><span class="sxs-lookup"><span data-stu-id="33278-321">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="33278-322">Kontrakty routingu</span><span class="sxs-lookup"><span data-stu-id="33278-322">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="33278-323">Wybieranie filtru</span><span class="sxs-lookup"><span data-stu-id="33278-323">Choosing a Filter</span></span>](choosing-a-filter.md)
