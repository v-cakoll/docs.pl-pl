---
title: 'Instrukcje: używanie filtrów'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 434171138e75a0f4c336cd80cc2beb574b10001e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598895"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="3d8de-102">Instrukcje: używanie filtrów</span><span class="sxs-lookup"><span data-stu-id="3d8de-102">How To: Use Filters</span></span>
<span data-ttu-id="3d8de-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu korzystającej z wielu filtrów.</span><span class="sxs-lookup"><span data-stu-id="3d8de-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="3d8de-104">W tym przykładzie komunikaty są kierowane do dwóch implementacji usługi kalkulatora, regularCalc i roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="3d8de-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="3d8de-105">Obie implementacje obsługują te same operacje; Jednak jedna usługa zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="3d8de-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="3d8de-106">Aplikacja kliencka musi być w stanie wskazać, czy ma być używana zaokrąglana wersja usługi. Jeśli preferencja usługi nie jest określona, komunikat jest równoważony między obiema usługami.</span><span class="sxs-lookup"><span data-stu-id="3d8de-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="3d8de-107">Operacje udostępniane przez obie usługi są następujące:</span><span class="sxs-lookup"><span data-stu-id="3d8de-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="3d8de-108">Dodaj</span><span class="sxs-lookup"><span data-stu-id="3d8de-108">Add</span></span>  
  
- <span data-ttu-id="3d8de-109">Odejmowanie</span><span class="sxs-lookup"><span data-stu-id="3d8de-109">Subtract</span></span>  
  
- <span data-ttu-id="3d8de-110">Mnożenie</span><span class="sxs-lookup"><span data-stu-id="3d8de-110">Multiply</span></span>  
  
- <span data-ttu-id="3d8de-111">Dzielenie</span><span class="sxs-lookup"><span data-stu-id="3d8de-111">Divide</span></span>  
  
 <span data-ttu-id="3d8de-112">Ponieważ obie usługi implementują te same operacje, nie można użyć filtru akcji, ponieważ akcja określona w komunikacie nie będzie unikatowa.</span><span class="sxs-lookup"><span data-stu-id="3d8de-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="3d8de-113">Zamiast tego należy wykonać dodatkowe czynności, aby upewnić się, że komunikaty są kierowane do odpowiednich punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="3d8de-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="3d8de-114">Określanie unikatowych danych</span><span class="sxs-lookup"><span data-stu-id="3d8de-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="3d8de-115">Ponieważ oba implementacje usług obsługują te same operacje i są zasadniczo identyczne jak dane, które zwracają, dane podstawowe zawarte w komunikatach wysyłanych z aplikacji klienckich nie są wystarczająco unikatowe, aby umożliwić określenie sposobu kierowania żądania.</span><span class="sxs-lookup"><span data-stu-id="3d8de-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="3d8de-116">Jeśli jednak aplikacja kliencka dodaje do wiadomości unikatową wartość nagłówka, można użyć tej wartości, aby określić sposób, w jaki komunikat powinien być kierowany.</span><span class="sxs-lookup"><span data-stu-id="3d8de-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="3d8de-117">W tym przykładzie, jeśli aplikacja kliencka wymaga przetworzenia komunikatu przez kalkulator zaokrąglenia, dodaje niestandardowy nagłówek przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="3d8de-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="3d8de-118">Można teraz użyć filtru XPath do sprawdzenia komunikatów dla tego nagłówka i trasy komunikatów zawierających nagłówek do usługi roundCalc.</span><span class="sxs-lookup"><span data-stu-id="3d8de-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="3d8de-119">Dodatkowo usługa routingu udostępnia dwa punkty końcowe usługi wirtualnej, które mogą być używane z filtrami EndpointName, EndpointAddress lub PrefixEndpointAddress w celu jednoznacznego kierowania komunikatów przychodzących do określonej implementacji kalkulatora na podstawie punktu końcowego, do którego aplikacja kliencka przesyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="3d8de-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="3d8de-120">Definiuj punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="3d8de-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="3d8de-121">Podczas definiowania punktów końcowych używanych przez usługę routingu należy najpierw określić kształt kanału używanego przez klientów i usługi.</span><span class="sxs-lookup"><span data-stu-id="3d8de-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="3d8de-122">W tym scenariuszu zarówno usługi docelowe używają wzorca żądania-odpowiedzi, więc <xref:System.ServiceModel.Routing.IRequestReplyRouter> jest używany.</span><span class="sxs-lookup"><span data-stu-id="3d8de-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="3d8de-123">W poniższym przykładzie zdefiniowano punkty końcowe usługi udostępniane przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="3d8de-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="3d8de-124">W przypadku tej konfiguracji usługa routingu ujawnia trzy oddzielne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="3d8de-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="3d8de-125">W zależności od opcji w czasie wykonywania aplikacja kliencka wysyła komunikaty do jednego z tych adresów.</span><span class="sxs-lookup"><span data-stu-id="3d8de-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="3d8de-126">Komunikaty docierające do jednego z "wirtualnych" punktów końcowych usługi ("zaokrąglenie/Kalkulator" lub "regularne/Kalkulator") są przekazywane do odpowiedniej implementacji kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="3d8de-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="3d8de-127">Jeśli aplikacja kliencka nie wyśle żądania do określonego punktu końcowego, komunikat zostanie rozkierowany do ogólnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3d8de-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="3d8de-128">Niezależnie od wybranego punktu końcowego aplikacja kliencka może również dołączyć nagłówek niestandardowy, aby wskazać, że wiadomość powinna być przekazywana do implementacji kalkulatora zaokrąglenia.</span><span class="sxs-lookup"><span data-stu-id="3d8de-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="3d8de-129">W poniższym przykładzie zdefiniowano punkty końcowe klienta (miejsce docelowe), do których usługa routingu kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="3d8de-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="3d8de-130">Te punkty końcowe są używane w tabeli filtrów, aby wskazać docelowy punkt końcowy, do którego komunikat jest wysyłany, gdy jest zgodny z określonym filtrem.</span><span class="sxs-lookup"><span data-stu-id="3d8de-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="3d8de-131">Definiuj filtry</span><span class="sxs-lookup"><span data-stu-id="3d8de-131">Define Filters</span></span>  
  
1. <span data-ttu-id="3d8de-132">Aby przesłać komunikaty na podstawie niestandardowego nagłówka "RoundingCalculator", który aplikacja kliencka dodaje do wiadomości, zdefiniuj filtr, który używa zapytania XPath do sprawdzenia obecności tego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="3d8de-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="3d8de-133">Ponieważ ten nagłówek jest definiowany przy użyciu niestandardowej przestrzeni nazw, należy również dodać wpis przestrzeni nazw, który definiuje niestandardowy prefiks przestrzeni nazw "Custom", który jest używany w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="3d8de-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="3d8de-134">W poniższym przykładzie zdefiniowano niezbędną sekcję routingu, tabelę przestrzeni nazw oraz filtr XPath.</span><span class="sxs-lookup"><span data-stu-id="3d8de-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="3d8de-135">Ta **MessageFilter** szuka nagłówka RoundingCalculator w komunikacie zawierającym wartość "rounding".</span><span class="sxs-lookup"><span data-stu-id="3d8de-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="3d8de-136">Ten nagłówek jest ustawiany przez klienta w celu wskazania, że komunikat powinien być kierowany do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="3d8de-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3d8de-137">Prefiks przestrzeni nazw S12 jest definiowany domyślnie w tabeli przestrzeni nazw i reprezentuje przestrzeń nazw `http://www.w3.org/2003/05/soap-envelope` .</span><span class="sxs-lookup"><span data-stu-id="3d8de-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="3d8de-138">Należy również zdefiniować filtry, które szukają komunikatów odebranych w dwóch wirtualnych punktach końcowych.</span><span class="sxs-lookup"><span data-stu-id="3d8de-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="3d8de-139">Pierwszy wirtualny punkt końcowy to punkt końcowy "Regular/Kalkulator".</span><span class="sxs-lookup"><span data-stu-id="3d8de-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="3d8de-140">Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że komunikat powinien być kierowany do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="3d8de-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="3d8de-141">Poniższa konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> do określenia, czy komunikat dotarł do punktu końcowego o nazwie określonej w danych filtru.</span><span class="sxs-lookup"><span data-stu-id="3d8de-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="3d8de-142">Jeśli komunikat jest odbierany przez punkt końcowy usługi o nazwie "calculatorEndpoint", ten filtr szacuje wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="3d8de-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="3d8de-143">Następnie zdefiniuj filtr, który szuka komunikatów wysyłanych na adres roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="3d8de-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="3d8de-144">Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że komunikat powinien być kierowany do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="3d8de-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="3d8de-145">Poniższa konfiguracja definiuje filtr, który używa w <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> celu ustalenia, czy wiadomość dotarła do punktu końcowego "zaokrąglenie/kalkulatora".</span><span class="sxs-lookup"><span data-stu-id="3d8de-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="3d8de-146">Jeśli otrzymasz komunikat o adresie zaczynającym się od, `http://localhost/routingservice/router/rounding/` ten filtr zwróci **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="3d8de-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="3d8de-147">Ponieważ adres podstawowy używany przez tę konfigurację jest `http://localhost/routingservice/router` i adresem określonym dla roundingEndpoint jest "zaokrąglenie/Kalkulator", pełny adres używany do komunikacji z tym punktem końcowym jest zgodny z `http://localhost/routingservice/router/rounding/calculator` tym filtrem.</span><span class="sxs-lookup"><span data-stu-id="3d8de-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3d8de-148">Filtr PrefixEndpointAddress nie oblicza nazwy hosta podczas dopasowywania, ponieważ pojedynczy host może być określony przy użyciu różnych nazw hostów, które mogą być prawidłowymi sposobami odwoływania się do hosta z aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="3d8de-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="3d8de-149">Na przykład wszystkie następujące elementy mogą odnosić się do tego samego hosta:</span><span class="sxs-lookup"><span data-stu-id="3d8de-149">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="3d8de-150">localhost</span><span class="sxs-lookup"><span data-stu-id="3d8de-150">localhost</span></span>  
    > - <span data-ttu-id="3d8de-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="3d8de-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="3d8de-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="3d8de-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="3d8de-153">Filtr końcowy musi obsługiwać Routing komunikatów, które docierają do ogólnego punktu końcowego bez niestandardowego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="3d8de-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="3d8de-154">W tym scenariuszu komunikaty powinny być zastępowane przez usługi regularCalc i roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="3d8de-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="3d8de-155">Aby zapewnić obsługę routingu "Round Robin" tych komunikatów, należy użyć filtru niestandardowego, który umożliwia dopasowanie jednego wystąpienia filtru dla każdego przetworzonego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="3d8de-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="3d8de-156">Poniżej zdefiniowano dwa wystąpienia RoundRobinMessageFilter, które są pogrupowane w celu wskazania, że powinny one być różne od siebie.</span><span class="sxs-lookup"><span data-stu-id="3d8de-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="3d8de-157">W czasie wykonywania ten filtr typu alternatywy między wszystkimi zdefiniowanymi wystąpieniami filtru tego typu, które są skonfigurowane jako ta sama Grupa w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3d8de-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="3d8de-158">Powoduje to, że komunikaty przetwarzane przez ten filtr niestandardowy do alternatywy między zwracanymi `true` `RoundRobinFilter1` a i `RoundRobinFilter2` .</span><span class="sxs-lookup"><span data-stu-id="3d8de-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="3d8de-159">Definiowanie tabel filtrów</span><span class="sxs-lookup"><span data-stu-id="3d8de-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="3d8de-160">Aby skojarzyć filtry z określonymi punktami końcowymi klienta, należy umieścić je w tabeli filtrów.</span><span class="sxs-lookup"><span data-stu-id="3d8de-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="3d8de-161">W tym przykładowym scenariuszu są używane również ustawienia priorytetu filtru, które jest ustawieniem opcjonalnym umożliwiającym wskazanie kolejności przetwarzania filtrów.</span><span class="sxs-lookup"><span data-stu-id="3d8de-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="3d8de-162">Jeśli nie określono priorytetu filtru, wszystkie filtry są oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3d8de-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3d8de-163">Chociaż określenie priorytetu filtru pozwala kontrolować kolejność przetwarzania filtrów, może niekorzystnie wpłynąć na wydajność usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="3d8de-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="3d8de-164">Jeśli to możliwe, Utwórz logikę filtru, aby użycie priorytetów filtru nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="3d8de-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="3d8de-165">Poniższy schemat definiuje tabelę filtrów i dodaje element "obiekt XPathFilter" zdefiniowany wcześniej do tabeli o priorytecie 2.</span><span class="sxs-lookup"><span data-stu-id="3d8de-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="3d8de-166">Ten wpis określa również, że jeśli `XPathFilter` dopasowuje komunikat, komunikat zostanie rozesłany do `roundingCalcEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="3d8de-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
          </filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="3d8de-167">Podczas określania priorytetu filtru najpierw są oceniane filtry o najwyższym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="3d8de-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="3d8de-168">Jeśli co najmniej jeden filtr o określonym poziomie priorytetu jest zgodny, nie będą oceniane żadne filtry o niższych poziomach.</span><span class="sxs-lookup"><span data-stu-id="3d8de-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="3d8de-169">W tym scenariuszu wartość 2 to najwyższy określony priorytet i jest to jedyna pozycja filtru na tym poziomie.</span><span class="sxs-lookup"><span data-stu-id="3d8de-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="3d8de-170">Zdefiniowano wpisy filtru, aby sprawdzić, czy wiadomość została odebrana w określonym punkcie końcowym przez sprawdzenie nazwy punktu końcowego lub prefiksu adresu.</span><span class="sxs-lookup"><span data-stu-id="3d8de-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="3d8de-171">Poniższe wpisy umożliwiają dodanie obu tych wpisów filtru do tabeli filtrów i skojarzenie ich z docelowym miejscem końcowym, do którego zostanie rozesłany komunikat.</span><span class="sxs-lookup"><span data-stu-id="3d8de-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="3d8de-172">Te filtry mają ustawiony priorytet 1, aby wskazać, że powinny być uruchamiane tylko wtedy, gdy poprzedni filtr XPath nie jest zgodny z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="3d8de-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="3d8de-173">Ponieważ te filtry mają priorytet filtru 1, będą oceniane tylko wtedy, gdy filtr na poziomie priorytetu 2 nie jest zgodny z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="3d8de-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="3d8de-174">Ponadto, ponieważ oba filtry mają taki sam poziom priorytetu, będą oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3d8de-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="3d8de-175">Ponieważ oba filtry wykluczają się wzajemnie, możliwe jest tylko jedno lub drugie, aby dopasować komunikat.</span><span class="sxs-lookup"><span data-stu-id="3d8de-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="3d8de-176">Jeśli komunikat nie jest zgodny z żadnym z poprzednich filtrów, komunikat został odebrany za pomocą punktu końcowego usługi ogólnej i nie zawierał informacji nagłówka wskazujących, gdzie należy je przekierować.</span><span class="sxs-lookup"><span data-stu-id="3d8de-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="3d8de-177">Te komunikaty mają być obsługiwane przez filtr niestandardowy, który równoważy obciążenie między obiema usługami kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="3d8de-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="3d8de-178">Poniższy przykład ilustruje sposób dodawania wpisów filtru do tabeli filtrów; Każdy filtr jest skojarzony z jednym z dwóch docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="3d8de-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="3d8de-179">Ponieważ te wpisy określają priorytet 0, będą oceniane tylko wtedy, gdy żaden filtr o wyższym priorytecie nie jest zgodny z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="3d8de-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="3d8de-180">Ponadto, ponieważ oba mają ten sam priorytet, są one oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3d8de-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="3d8de-181">Jak wspomniano wcześniej, filtr niestandardowy używany przez te definicje filtru oblicza tylko jedną lub drugą wartość `true` dla każdego odebranego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="3d8de-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="3d8de-182">Ponieważ tylko dwa filtry są zdefiniowane przy użyciu tego filtru, z tym samym ustawieniem określonej grupy, efektem jest to, że usługa routingu jest alternatywna dla wysyłania do regularCalcEndpoint i RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="3d8de-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="3d8de-183">Aby można było oszacować komunikaty względem filtrów, tabela filtrów musi być najpierw skojarzona z punktami końcowymi usługi, które będą używane do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d8de-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="3d8de-184">W poniższym przykładzie pokazano, jak skojarzyć tabelę routingu z punktami końcowymi usługi przy użyciu zachowania routingu:</span><span class="sxs-lookup"><span data-stu-id="3d8de-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3d8de-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d8de-185">Example</span></span>  
 <span data-ttu-id="3d8de-186">Poniżej znajduje się kompletna lista plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="3d8de-186">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d8de-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d8de-187">See also</span></span>

- [<span data-ttu-id="3d8de-188">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="3d8de-188">Routing Services</span></span>](../samples/routing-services.md)
