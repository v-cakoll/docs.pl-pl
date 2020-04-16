---
title: 'Instrukcje: używanie filtrów'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 34ea961b0ef5db51efcae0b86f2c06171d6d756c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464101"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="3c8a2-102">Instrukcje: używanie filtrów</span><span class="sxs-lookup"><span data-stu-id="3c8a2-102">How To: Use Filters</span></span>
<span data-ttu-id="3c8a2-103">W tym temacie opisano podstawowe kroki wymagane do utworzenia konfiguracji routingu, która używa wielu filtrów.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="3c8a2-104">W tym przykładzie wiadomości są kierowane do dwóch implementacji usługi kalkulatora, regularCalc i roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="3c8a2-105">Obie implementacje obsługują te same operacje; jednak jedna usługa zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="3c8a2-106">Aplikacja kliencka musi być w stanie wskazać, czy ma być używana wersja zaokrąglania usługi; jeśli nie preferencje usługi jest wyrażona, a następnie komunikat jest równoważenie obciążenia między dwiema usługami.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="3c8a2-107">Operacje udostępniane przez obie usługi są następujące:</span><span class="sxs-lookup"><span data-stu-id="3c8a2-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="3c8a2-108">Dodaj</span><span class="sxs-lookup"><span data-stu-id="3c8a2-108">Add</span></span>  
  
- <span data-ttu-id="3c8a2-109">Odejmowanie</span><span class="sxs-lookup"><span data-stu-id="3c8a2-109">Subtract</span></span>  
  
- <span data-ttu-id="3c8a2-110">Mnożenie</span><span class="sxs-lookup"><span data-stu-id="3c8a2-110">Multiply</span></span>  
  
- <span data-ttu-id="3c8a2-111">Dzielenie</span><span class="sxs-lookup"><span data-stu-id="3c8a2-111">Divide</span></span>  
  
 <span data-ttu-id="3c8a2-112">Ponieważ obie usługi implementują te same operacje, nie można użyć filtru Akcja, ponieważ akcja określona w komunikacie nie będzie unikatowa.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="3c8a2-113">Zamiast tego należy wykonać dodatkową pracę, aby upewnić się, że wiadomości są kierowane do odpowiednich punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="3c8a2-114">Określanie unikatowych danych</span><span class="sxs-lookup"><span data-stu-id="3c8a2-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="3c8a2-115">Ponieważ obie implementacje usługi obsługują te same operacje i są zasadniczo identyczne inne niż dane, które zwracają, dane podstawowe zawarte w komunikatach wysyłanych z aplikacji klienckich nie jest wystarczająco unikatowy, aby umożliwić określenie sposobu kierowania żądania.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="3c8a2-116">Ale jeśli aplikacja kliencka dodaje unikatową wartość nagłówka do wiadomości, można użyć tej wartości, aby określić, jak wiadomość powinna być kierowana.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="3c8a2-117">W tym przykładzie, jeśli aplikacja kliencka wymaga, aby komunikat został przetworzony przez kalkulator zaokrąglania, dodaje niestandardowy nagłówek przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="3c8a2-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="3c8a2-118">Teraz można użyć filtru XPath do sprawdzania wiadomości dla tego nagłówka i wysyłać komunikaty zawierające nagłówek do usługi roundCalc.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="3c8a2-119">Ponadto usługa routingu udostępnia dwa punkty końcowe usługi wirtualnej, które mogą być używane z EndpointName, EndpointAddress lub PrefixEndpointAddress filtrów jednoznacznie trasy przychodzące wiadomości do implementacji określonego kalkulatora na podstawie punktu końcowego, do którego aplikacja kliencka przesyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="3c8a2-120">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="3c8a2-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="3c8a2-121">Podczas definiowania punktów końcowych używanych przez usługę routingu, należy najpierw określić kształt kanału używanego przez klientów i usług.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="3c8a2-122">W tym scenariuszu usługi docelowe używają wzorca <xref:System.ServiceModel.Routing.IRequestReplyRouter> żądanie odpowiedź, więc jest używany.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="3c8a2-123">Poniższy przykład definiuje punkty końcowe usługi udostępniane przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="3c8a2-124">W tej konfiguracji usługa routingu udostępnia trzy oddzielne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="3c8a2-125">W zależności od wyborów w czasie wykonywania aplikacja kliencka wysyła komunikaty do jednego z tych adresów.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="3c8a2-126">Wiadomości docierające do jednego z "wirtualnych" punktów końcowych usługi ("zaokrąglanie/kalkulator" lub "zwykły/kalkulator") są przekazywane do odpowiedniej implementacji kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="3c8a2-127">Jeśli aplikacja kliencka nie wysyła żądania do określonego punktu końcowego, komunikat jest adresowany do ogólnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="3c8a2-128">Niezależnie od wybranego punktu końcowego aplikacja kliencka może również dołączyć niestandardowy nagłówek, aby wskazać, że wiadomość powinna być przekazycona do implementacji kalkulatora zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="3c8a2-129">Poniższy przykład definiuje klienta (miejsce docelowe) punkty końcowe, do których usługa routingu kieruje wiadomości do.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="3c8a2-130">Te punkty końcowe są używane w tabeli filtrów, aby wskazać docelowy punkt końcowy, do którego jest wysyłana wiadomość, gdy pasuje do określonego filtru.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="3c8a2-131">Definiowanie filtrów</span><span class="sxs-lookup"><span data-stu-id="3c8a2-131">Define Filters</span></span>  
  
1. <span data-ttu-id="3c8a2-132">Aby rozsyłać wiadomości na podstawie niestandardowego nagłówka "Zaokrąglanie obliczania", który aplikacja kliencka dodaje do wiadomości, zdefiniuj filtr, który używa kwerendy XPath do sprawdzenia obecności tego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="3c8a2-133">Ponieważ ten nagłówek jest zdefiniowany przy użyciu niestandardowego obszaru nazw, należy również dodać wpis obszaru nazw, który definiuje niestandardowy prefiks obszaru nazw "niestandardowy", który jest używany w kwerendzie XPath.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="3c8a2-134">Poniższy przykład definiuje niezbędną sekcję routingu, tabelę obszaru nazw i filtr XPath.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="3c8a2-135">Ten **messagefilter** szuka zaokrąglaniawejszy nagłówek w wiadomości, która zawiera wartość "zaokrąglania".</span><span class="sxs-lookup"><span data-stu-id="3c8a2-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="3c8a2-136">Ten nagłówek jest ustawiany przez klienta, aby wskazać, że wiadomość powinna być kierowana do usługi zaokrąglaniaCalc.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3c8a2-137">Prefiks obszaru nazw s12 jest zdefiniowany domyślnie w tabeli obszaru nazw i reprezentuje obszar nazw `http://www.w3.org/2003/05/soap-envelope`.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="3c8a2-138">Należy również zdefiniować filtry, które szukają wiadomości odebranych w dwóch wirtualnych punktach końcowych.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="3c8a2-139">Pierwszym wirtualnym punktem końcowym jest punkt końcowy "zwykły/kalkulator".</span><span class="sxs-lookup"><span data-stu-id="3c8a2-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="3c8a2-140">Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że wiadomość powinna być kierowana do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="3c8a2-141">Poniższa konfiguracja definiuje filtr, <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> który używa do określenia, czy wiadomość dotarła przez punkt końcowy o nazwie określonej w filterData.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="3c8a2-142">Jeśli komunikat zostanie odebrany przez punkt końcowy usługi o nazwie "calculatorEndpoint", ten filtr ocenia wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="3c8a2-143">Następnie zdefiniuj filtr, który wyszukuje wiadomości wysłane na adres zaokrągleniaEndpoint.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="3c8a2-144">Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że wiadomość powinna być kierowana do usługi zaokrąglaniaCalc.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="3c8a2-145">Poniższa konfiguracja definiuje filtr, <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> który używa do określenia, czy wiadomość dotarła do punktu końcowego "zaokrąglania/kalkulatora".</span><span class="sxs-lookup"><span data-stu-id="3c8a2-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="3c8a2-146">Jeśli wiadomość zostanie odebrana pod `http://localhost/routingservice/router/rounding/` adresem, który zaczyna się od tego, filtr ten jest oceniany jako **true**.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="3c8a2-147">Ponieważ adres podstawowy używany przez `http://localhost/routingservice/router` tę konfigurację jest i adres określony dla zaokrągleniaEndpoint jest "zaokrąglanie/kalkulator", pełny adres używany do komunikowania się z tym punktem końcowym jest `http://localhost/routingservice/router/rounding/calculator`, który pasuje do tego filtru.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3c8a2-148">Filtr PrefixEndpointAddress nie ocenia nazwy hosta podczas wykonywania dopasowania, ponieważ można odwoływać się do pojedynczego hosta przy użyciu różnych nazw hostów, które mogą być prawidłowymi sposobami odwoływania się do hosta z aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="3c8a2-149">Na przykład wszystkie następujące mogą odwoływać się do tego samego hosta:</span><span class="sxs-lookup"><span data-stu-id="3c8a2-149">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="3c8a2-150">localhost</span><span class="sxs-lookup"><span data-stu-id="3c8a2-150">localhost</span></span>  
    > - <span data-ttu-id="3c8a2-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="3c8a2-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="3c8a2-152">Sieć ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="3c8a2-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="3c8a2-153">Filtr końcowy musi obsługiwać routingu wiadomości, które docierają do ogólnego punktu końcowego bez nagłówka niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="3c8a2-154">W tym scenariuszu komunikaty powinny naprzemiennie między regularCalc i roundingSedy.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="3c8a2-155">Aby obsługiwać routing "okrężny" tych wiadomości, użyj filtru niestandardowego, który umożliwia dopasowywanie jednego wystąpienia filtru dla każdej przetworzonej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="3c8a2-156">Poniżej definiuje dwa wystąpienia RoundRobinMessageFilter, które są zgrupowane razem, aby wskazać, że powinny one naprzemiennie między sobą.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="3c8a2-157">W czasie wykonywania ten typ filtru przełącza się między wszystkimi zdefiniowanymi wystąpieniami filtru tego typu, które są skonfigurowane jako ta sama grupa w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="3c8a2-158">Powoduje to, że wiadomości przetwarzane przez ten `true` `RoundRobinFilter1` filtr `RoundRobinFilter2`niestandardowy zmieniają się między zwracaniem dla i .</span><span class="sxs-lookup"><span data-stu-id="3c8a2-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="3c8a2-159">Definiowanie tabel filtrów</span><span class="sxs-lookup"><span data-stu-id="3c8a2-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="3c8a2-160">Aby skojarzyć filtry z określonymi punktami końcowymi klienta, należy umieścić je w tabeli filtrów.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="3c8a2-161">W tym przykładzie scenariusza użyto również ustawień priorytetu filtru, które jest ustawieniem opcjonalnym, które umożliwia wskazanie kolejności przetwarzania filtrów.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="3c8a2-162">Jeśli nie określono priorytetu filtru, wszystkie filtry są oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3c8a2-163">Podczas określania priorytetu filtru pozwala kontrolować kolejność, w jakiej filtry są przetwarzane, może to niekorzystnie wpłynąć na wydajność usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="3c8a2-164">Jeśli to możliwe, skonstruuj logikę filtru, aby użycie priorytetów filtru nie było wymagane.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="3c8a2-165">Poniżej definiuje tabelę filtrów i dodaje "XPathFilter" zdefiniowane wcześniej do tabeli o priorytecie 2.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="3c8a2-166">Ten wpis określa również, `XPathFilter` że jeśli wiadomość jest zgodna z `roundingCalcEndpoint`komunikatem, zostanie przekierowana do pliku .</span><span class="sxs-lookup"><span data-stu-id="3c8a2-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
  
     <span data-ttu-id="3c8a2-167">Podczas określania priorytetu filtru filtry o najwyższym priorytecie są oceniane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="3c8a2-168">Jeśli jeden lub więcej filtrów na określonym poziomie priorytetu pasuje, nie filtry na niższych poziomach priorytetu będą oceniane.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="3c8a2-169">W tym scenariuszu 2 jest najwyższy priorytet określony i jest to tylko wpis filtru na tym poziomie.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="3c8a2-170">Wpisy filtru zostały zdefiniowane, aby sprawdzić, czy wiadomość jest odbierana w określonym punkcie końcowym, sprawdzając nazwę punktu końcowego lub prefiks adresu.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="3c8a2-171">Następujące wpisy dodać oba te wpisy filtru do tabeli filtru i skojarzyć je z docelowymi punktami końcowymi, do których zostanie skierowana wiadomość.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="3c8a2-172">Filtry te są ustawione na priorytet 1, aby wskazać, że powinny działać tylko wtedy, gdy poprzedni filtr XPath nie pasuje do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="3c8a2-173">Ponieważ te filtry mają priorytet filtru 1, będą one oceniane tylko wtedy, gdy filtr na poziomie priorytetu 2 nie pasuje do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="3c8a2-174">Ponadto, ponieważ oba filtry mają ten sam poziom priorytetu będą oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="3c8a2-175">Ponieważ oba filtry wzajemnie się wykluczają, jest możliwe tylko jeden lub drugi, aby dopasować wiadomość.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="3c8a2-176">Jeśli wiadomość nie pasuje do żadnego z poprzednich filtrów, wiadomość została odebrana za pośrednictwem punktu końcowego usługi ogólnej i nie zawierała żadnych informacji nagłówka wskazujących, gdzie ją rozsyłać.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="3c8a2-177">Te komunikaty mają być obsługiwane przez filtr niestandardowy, który równoważy je między dwiema usługami kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="3c8a2-178">W poniższym przykładzie pokazano, jak dodać wpisy filtru do tabeli filtrów; każdy filtr jest skojarzony z jednym z dwóch docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="3c8a2-179">Ponieważ te wpisy określają priorytet 0, będą one oceniane tylko wtedy, gdy żaden filtr o wyższym priorytecie nie pasuje do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="3c8a2-180">Ponadto, ponieważ oba są tego samego priorytetu, są one oceniane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="3c8a2-181">Jak wspomniano wcześniej, filtr niestandardowy używany przez te definicje filtrów `true` ocenia tylko jeden lub drugi, jak dla każdej odebranej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="3c8a2-182">Ponieważ tylko dwa filtry są zdefiniowane przy użyciu tego filtru, z tym samym ustawieniem określonej grupy, efekt jest, że usługa routingu przełącza się między wysyłaniem do regularCalcEndpoint i RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="3c8a2-183">Aby ocenić komunikaty względem filtrów, tabela filtrów musi być najpierw skojarzona z punktami końcowymi usługi, które będą używane do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="3c8a2-184">W poniższym przykładzie pokazano, jak skojarzyć tabelę routingu z punktami końcowymi usługi przy użyciu zachowania routingu:</span><span class="sxs-lookup"><span data-stu-id="3c8a2-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3c8a2-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c8a2-185">Example</span></span>  
 <span data-ttu-id="3c8a2-186">Poniżej znajduje się pełna lista pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="3c8a2-186">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c8a2-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c8a2-187">See also</span></span>

- [<span data-ttu-id="3c8a2-188">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="3c8a2-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
