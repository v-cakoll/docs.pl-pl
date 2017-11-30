---
title: "Porady: Używanie filtrów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 20e9fd7bd962adb20d2c4bc394012603c7e0f2ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-filters"></a><span data-ttu-id="73378-102">Porady: Używanie filtrów</span><span class="sxs-lookup"><span data-stu-id="73378-102">How To: Use Filters</span></span>
<span data-ttu-id="73378-103">W tym temacie przedstawiono podstawowe czynności wymagane do utworzenia konfiguracji routingu, która używa wielu filtrów.</span><span class="sxs-lookup"><span data-stu-id="73378-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="73378-104">W tym przykładzie wiadomości są kierowane do dwóch implementacji usługi Kalkulator, regularCalc i roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="73378-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="73378-105">Zarówno implementacje obsługują te same operacje; Jednak jedna usługa zaokrągla wszystkich obliczeń do najbliższej liczby całkowitej wartości przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="73378-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="73378-106">Aplikacja kliencka musi mieć możliwość wskazuje, czy należy użyć wersji zaokrąglania usługi; Jeśli wyrażono ma preferencji usługi wiadomość jest równoważone między dwie usługi.</span><span class="sxs-lookup"><span data-stu-id="73378-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="73378-107">Operacje udostępnianych przez obie te usługi są:</span><span class="sxs-lookup"><span data-stu-id="73378-107">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="73378-108">Dodaj</span><span class="sxs-lookup"><span data-stu-id="73378-108">Add</span></span>  
  
-   <span data-ttu-id="73378-109">Odejmowanie</span><span class="sxs-lookup"><span data-stu-id="73378-109">Subtract</span></span>  
  
-   <span data-ttu-id="73378-110">Mnożenia</span><span class="sxs-lookup"><span data-stu-id="73378-110">Multiply</span></span>  
  
-   <span data-ttu-id="73378-111">Podziel</span><span class="sxs-lookup"><span data-stu-id="73378-111">Divide</span></span>  
  
 <span data-ttu-id="73378-112">Ponieważ obie te usługi zaimplementować te same operacje, można użyć filtru akcji, ponieważ z akcją określoną w komunikacie nie jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="73378-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="73378-113">Zamiast tego należy wykonać dodatkowe czynności, aby upewnić się, że komunikaty są kierowane do odpowiednich punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="73378-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="73378-114">Określić unikatowe dane</span><span class="sxs-lookup"><span data-stu-id="73378-114">Determine Unique Data</span></span>  
  
1.  <span data-ttu-id="73378-115">Ponieważ obu implementacji usługi obsługi tych samych operacji i są zasadniczo identyczne inne niż dane, które zwracają, podstawowe dane zawarte w wiadomości wysyłane przez aplikacje klienckie nie jest unikatowa, co pozwala określić sposób kierowania żądanie.</span><span class="sxs-lookup"><span data-stu-id="73378-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="73378-116">Ale jeśli aplikacja kliencka dodaje wartości nagłówka do wiadomości, następnie można użyć tej wartości można określić, jak powinny być kierowane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73378-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="73378-117">Na przykład jeśli aplikacja kliencka musi komunikat, który ma zostać przetworzone przez zaokrąglania Kalkulator on dodaje niestandardowy nagłówek przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="73378-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="73378-118">Można teraz filtr XPath umożliwia inspekcję komunikatów dla tego nagłówka i kierowania wiadomości zawierające nagłówka z usługą roundCalc.</span><span class="sxs-lookup"><span data-stu-id="73378-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2.  <span data-ttu-id="73378-119">Ponadto usługa routingu udostępnia dwa punkty końcowe usług wirtualnych, które mogą być używane z EndpointName, EndpointAddress, lub PrefixEndpointAddress filtrów jednoznacznie kierowania wiadomości przychodzących implementacji określonego Kalkulator oparte na punkt końcowy do którego aplikacja kliencka przesyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="73378-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="73378-120">Punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="73378-120">Define Endpoints</span></span>  
  
1.  <span data-ttu-id="73378-121">Podczas definiowania punktów końcowych używanych przez usługi routingu, należy najpierw określić kształtu kanału używany przez klientów i usług.</span><span class="sxs-lookup"><span data-stu-id="73378-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="73378-122">W tym scenariuszu usług docelowych Użyj wzorca "żądanie-odpowiedź", więc <xref:System.ServiceModel.Routing.IRequestReplyRouter> jest używany.</span><span class="sxs-lookup"><span data-stu-id="73378-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="73378-123">W poniższym przykładzie zdefiniowano punktów końcowych usługi udostępniane przez usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="73378-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="73378-124">W tej konfiguracji usługa routingu udostępnia trzy oddzielne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="73378-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="73378-125">W zależności od opcji czasu wykonywania aplikacji klient wysyła komunikaty do jednego z tych adresów.</span><span class="sxs-lookup"><span data-stu-id="73378-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="73378-126">Komunikaty przychodzące w jednym z punktów końcowych usługi "wirtualne" ("zaokrąglania/Kalkulator" lub "regular/Kalkulator") są przekazywane do odpowiedniej implementacji Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="73378-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="73378-127">Jeśli aplikacja kliencka nie wysyłać żądania do danego punktu końcowego, wiadomość jest skierowana do ogólne punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="73378-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="73378-128">Niezależnie od wybranego punktu końcowego aplikacji klienckiej mogą też dołączyć niestandardowy nagłówek, aby wskazać, że wiadomość jest przekazywany do zaokrąglania implementacji Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="73378-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2.  <span data-ttu-id="73378-129">W poniższym przykładzie zdefiniowano punktów końcowych klienta (docelowy), które usługa routingu kieruje komunikaty do.</span><span class="sxs-lookup"><span data-stu-id="73378-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="73378-130">Te punkty końcowe są używane w tabeli filtrów wskazująca docelowego punktu końcowego, który komunikat jest wysyłany do, gdy są one zgodne określonego filtru.</span><span class="sxs-lookup"><span data-stu-id="73378-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="73378-131">Zdefiniuj filtry</span><span class="sxs-lookup"><span data-stu-id="73378-131">Define Filters</span></span>  
  
1.  <span data-ttu-id="73378-132">Aby rozesłać komunikaty oparte na niestandardowy nagłówek "RoundingCalculator", który aplikacja kliencka dodaje do wiadomości, zdefiniuj filtr, który używa zapytanie XPath do sprawdzenia obecności tego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="73378-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="73378-133">Ponieważ ten nagłówek jest definiowana za pomocą niestandardowej przestrzeni nazw, należy również dodać wpis przestrzeni nazw, który definiuje prefiksem niestandardowej przestrzeni nazw "custom", który jest używany w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="73378-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="73378-134">W poniższym przykładzie zdefiniowano niezbędne sekcji routingu, przestrzeni nazw tabeli i filtr XPath.</span><span class="sxs-lookup"><span data-stu-id="73378-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="73378-135">To **MessageFilter** szuka RoundingCalculator nagłówka wiadomości, która zawiera wartość "zaokrąglania".</span><span class="sxs-lookup"><span data-stu-id="73378-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="73378-136">Ten nagłówek jest ustawionego przez klienta, aby wskazać, że komunikat powinny być kierowane do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="73378-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73378-137">Prefiks przestrzeni nazw s12 jest zdefiniowany w tabeli nazw domyślnie i reprezentuje przestrzeni nazw "http://www.w3.org/2003/05/soap-envelope".</span><span class="sxs-lookup"><span data-stu-id="73378-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace "http://www.w3.org/2003/05/soap-envelope".</span></span>  
  
2.  <span data-ttu-id="73378-138">Należy również zdefiniować filtry mające poszukaj komunikatów odebranych na dwa punkty końcowe wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="73378-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="73378-139">Pierwszy wirtualnego punkt końcowy jest punktem końcowym "regular/kalkulatora".</span><span class="sxs-lookup"><span data-stu-id="73378-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="73378-140">Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że komunikat powinny być kierowane do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="73378-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="73378-141">Następująca konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> ustalenie, czy odebrania wiadomości za pośrednictwem punktu końcowego o podanej nazwie w danych filtru.</span><span class="sxs-lookup"><span data-stu-id="73378-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="73378-142">Jeśli wiadomość zostanie odebrana przez punkt końcowy usługi o nazwie "calculatorEndpoint", filtr daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="73378-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3.  <span data-ttu-id="73378-143">Następnie określ filtr, który wygląda komunikaty wysyłane na adres roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="73378-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="73378-144">Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że komunikat powinny być kierowane do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="73378-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="73378-145">Następująca konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> ustalenie, czy wiadomość dotarła do punktu końcowego "zaokrąglania/kalkulatora".</span><span class="sxs-lookup"><span data-stu-id="73378-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="73378-146">Jeśli wiadomość zostanie odebrana na adres, który rozpoczyna się od "http://localhost/routingservice/router/rounding/", a następnie daje w wyniku tego filtru **true**.</span><span class="sxs-lookup"><span data-stu-id="73378-146">If a message is received at an address that begins with "http://localhost/routingservice/router/rounding/" then this filter evaluates to **true**.</span></span> <span data-ttu-id="73378-147">Adres podstawowy używany przez tę konfigurację jest "http://localhost/routingservice/router" i "zaokrąglania/Kalkulator" jest określony dla roundingEndpoint adres, pełny adres używany do komunikacji z tym punktem końcowym jest "http://localhost/ obiektu routingservice/routera/zaokrąglania/Kalkulator", który spełni warunki tego filtru.</span><span class="sxs-lookup"><span data-stu-id="73378-147">Because the base address used by this configuration is "http://localhost/routingservice/router" and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is "http://localhost/routingservice/router/rounding/calculator", which matches this filter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73378-148">Filtr PrefixEndpointAddress nie może oszacować nazwy hosta podczas wykonywania dopasowania, ponieważ w jednym hoście można odwoływać się przy użyciu różnych nazw hostów, które może wszystkie mieć prawidłowe metody odwoływania się do hosta z aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="73378-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="73378-149">Na przykład następujące czynności mogą odwoływać się do tego samego hosta:</span><span class="sxs-lookup"><span data-stu-id="73378-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    >  -   <span data-ttu-id="73378-150">localhost</span><span class="sxs-lookup"><span data-stu-id="73378-150">localhost</span></span>  
    > -   <span data-ttu-id="73378-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="73378-151">127.0.0.1</span></span>  
    > -   <span data-ttu-id="73378-152">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="73378-152">www.contoso.com</span></span>  
    > -   <span data-ttu-id="73378-153">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="73378-153">ContosoWeb01</span></span>  
  
4.  <span data-ttu-id="73378-154">Ostatni filtr musi obsługiwać routing komunikaty przychodzące w punkcie końcowym w ogólne bez nagłówek niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="73378-154">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="73378-155">W tym scenariuszu wiadomości powinna alternatywny między usługami regularCalc i roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="73378-155">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="73378-156">Aby obsługiwać routing "działanie okrężne" tych wiadomości, należy używać niestandardowego filtru umożliwiający jedno wystąpienie filtru do dopasowania dla każdego komunikatu przetworzone.</span><span class="sxs-lookup"><span data-stu-id="73378-156">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="73378-157">Poniższy schemat określa dwa wystąpienia RoundRobinMessageFilter, które są zgrupowane aby wskazać, że należy alternatywny między sobą.</span><span class="sxs-lookup"><span data-stu-id="73378-157">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="73378-158">W czasie wykonywania ten typ filtru przełącza między wszystkich wystąpień zdefiniowany filtr tego typu, które są skonfigurowane jako tej samej grupie w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="73378-158">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="73378-159">Powoduje to, że komunikaty przetwarzane przez ten niestandardowy filtr, aby przełącza między zwracanie `true` RoundRobinFilter1 i RoundRobinFilter2.</span><span class="sxs-lookup"><span data-stu-id="73378-159">This causes messages processed by this custom filter to alternate between returning `true` for RoundRobinFilter1 and RoundRobinFilter2.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="73378-160">Zdefiniuj filtr tabel</span><span class="sxs-lookup"><span data-stu-id="73378-160">Define Filter Tables</span></span>  
  
1.  <span data-ttu-id="73378-161">Aby skojarzyć filtrów z punktami końcowymi określonego klienta, należy umieścić je w tabeli filtrów.</span><span class="sxs-lookup"><span data-stu-id="73378-161">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="73378-162">Ten przykładowy scenariusz używa również filtru ustawienia priorytetu, która jest ustawienie opcjonalne, które można określić kolejność, w jakiej są przetwarzane filtrów.</span><span class="sxs-lookup"><span data-stu-id="73378-162">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="73378-163">Jeśli jest określony żaden priorytet filtru, wszystkie filtry, które są oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="73378-163">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73378-164">Podczas określania priorytet filtru umożliwia można kontrolować kolejność, w których filtry są przetwarzane go może niekorzystnie wpłynąć na wydajność usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="73378-164">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="73378-165">Jeśli to możliwe, należy utworzyć filtr logiki tak, aby korzystanie z priorytetów filtru nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="73378-165">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="73378-166">Następujące definiuje tabeli filtrów i dodaje "Obiekt XPathFilter" zdefiniowanego wcześniej do tabeli o priorytecie 2.</span><span class="sxs-lookup"><span data-stu-id="73378-166">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="73378-167">Ten wpis określa, że jeśli obiekt "XPathFilter" pasuje do komunikatu, komunikat będą kierowane do "roundingCalcEndpoint"</span><span class="sxs-lookup"><span data-stu-id="73378-167">This entry also specifies that if the "XPathFilter" matches the message, the message will be routed to the "roundingCalcEndpoint"</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="73378-168">Podczas określania priorytet filtru, najpierw są oceniane filtry najwyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="73378-168">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="73378-169">Jeśli co najmniej jeden filtr na poziomie określonym priorytecie są zgodne, zostanie obliczone żadnych filtrów na niższych poziomach priorytet.</span><span class="sxs-lookup"><span data-stu-id="73378-169">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="73378-170">W tym scenariuszu 2 jest najwyższy priorytet określone i to tylko wpisu filtru na tym poziomie.</span><span class="sxs-lookup"><span data-stu-id="73378-170">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2.  <span data-ttu-id="73378-171">Wpisy filtrów zostały zdefiniowane Aby sprawdzić, czy wiadomość zostanie odebrana w określonym punkcie końcowym, sprawdzając nazwę punktu końcowego lub prefiks adresu.</span><span class="sxs-lookup"><span data-stu-id="73378-171">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="73378-172">Następujące pozycje Dodaj oba te wpisy filtru do tabeli filtrów i skojarzyć je z punktów końcowych docelowego, które wiadomości będą kierowane do.</span><span class="sxs-lookup"><span data-stu-id="73378-172">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="73378-173">Te filtry są ustawione na o priorytecie 1, aby wskazać, że ich powinien uruchamiać tylko jeśli poprzedni filtr XPath nie jest zgodny komunikat.</span><span class="sxs-lookup"><span data-stu-id="73378-173">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="73378-174">Ponieważ te filtry mają priorytet filtru 1, ich tylko ocenia się filtru na poziomie priorytetu 2 jest niezgodna z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="73378-174">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="73378-175">Ponadto ponieważ oba filtry mają ten sam poziom priorytetu one będą oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="73378-175">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="73378-176">Ponieważ obu filtrów wzajemnie się wykluczają, jest możliwe tylko jednego lub drugiego odpowiadające wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73378-176">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3.  <span data-ttu-id="73378-177">Jeśli wiadomość nie pasuje do żadnego z poprzednich filtrów, wiadomość została odebrana za pośrednictwem punktu końcowego usługi ogólnej i zawarte żadne informacje nagłówka, która wskazuje, gdzie go rozesłać.</span><span class="sxs-lookup"><span data-stu-id="73378-177">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="73378-178">Komunikaty te są mają być obsługiwane przez filtr niestandardowy, obciążenia, która równoważy ich między usługami dwóch Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="73378-178">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="73378-179">W poniższym przykładzie pokazano, jak dodać filtr wpisów do tabeli filtru; Każdy filtr jest skojarzony z jednym z docelowym dwa punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="73378-179">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="73378-180">Ponieważ te wpisy Określ priorytet 0, one tylko ocenia się Jeśli żaden filtr o wyższym priorytecie zgodny komunikat.</span><span class="sxs-lookup"><span data-stu-id="73378-180">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="73378-181">Ponadto ponieważ zarówno z takim samym priorytecie, są one oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="73378-181">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="73378-182">Jak wspomniano wcześniej, filtr niestandardowy używany przez te definicje filtrów ocenia tylko jedną lub inne, `true` dla każdego komunikatu Odebrano.</span><span class="sxs-lookup"><span data-stu-id="73378-182">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="73378-183">Ponieważ tylko dwa filtry są zdefiniowane przy użyciu tego filtru, to samo ustawienie określonej grupy, powoduje, że usługa routingu przełącza między wysłaniem regularCalcEndpoint i RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="73378-183">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4.  <span data-ttu-id="73378-184">Aby ocenić komunikaty te filtry, tabeli filtrów najpierw musi być skojarzony z punktów końcowych usługi, które będą używane do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73378-184">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="73378-185">W poniższym przykładzie pokazano, jak skojarzyć tabeli routingu z punktów końcowych usługi przy użyciu routingu zachowanie:</span><span class="sxs-lookup"><span data-stu-id="73378-185">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="73378-186">Przykład</span><span class="sxs-lookup"><span data-stu-id="73378-186">Example</span></span>  
 <span data-ttu-id="73378-187">Poniżej znajduje się pełna lista pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73378-187">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="73378-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73378-188">See Also</span></span>  
 [<span data-ttu-id="73378-189">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="73378-189">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
