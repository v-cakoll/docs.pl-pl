---
title: 'Instrukcje: Używanie filtrów'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 5d3ed4a1d64edee274e60f5bf156b4294902df8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972864"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="8dba4-102">Instrukcje: Używanie filtrów</span><span class="sxs-lookup"><span data-stu-id="8dba4-102">How To: Use Filters</span></span>
<span data-ttu-id="8dba4-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu, który używa wielu filtrów.</span><span class="sxs-lookup"><span data-stu-id="8dba4-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="8dba4-104">W tym przykładzie komunikaty są kierowane do dwie implementacje usługi Kalkulator, regularCalc i roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="8dba4-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="8dba4-105">Zarówno implementacje obsługują te same operacje; Jednak w jednej usłudze zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="8dba4-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="8dba4-106">Aplikacja kliencka musi być w stanie wskazać, czy ma być używany zaokrąglania wersję usługi; Jeśli brak preferencji Usługa bazy danych jest wyrażona wiadomość jest równoważone między obiema usługami.</span><span class="sxs-lookup"><span data-stu-id="8dba4-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="8dba4-107">Operacje udostępniane przez obie te usługi są:</span><span class="sxs-lookup"><span data-stu-id="8dba4-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="8dba4-108">Dodaj</span><span class="sxs-lookup"><span data-stu-id="8dba4-108">Add</span></span>  
  
- <span data-ttu-id="8dba4-109">Odejmowanie</span><span class="sxs-lookup"><span data-stu-id="8dba4-109">Subtract</span></span>  
  
- <span data-ttu-id="8dba4-110">Mnożenie</span><span class="sxs-lookup"><span data-stu-id="8dba4-110">Multiply</span></span>  
  
- <span data-ttu-id="8dba4-111">Dzielenie</span><span class="sxs-lookup"><span data-stu-id="8dba4-111">Divide</span></span>  
  
 <span data-ttu-id="8dba4-112">Ponieważ obie te usługi implementuje te same operacje, nie można użyć filtru akcji, ponieważ z akcją określoną w komunikacie nie jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="8dba4-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="8dba4-113">Zamiast tego należy wykonać dodatkową pracę, aby upewnić się, że komunikaty są kierowane do odpowiednich punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8dba4-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="8dba4-114">Określić unikatowe dane</span><span class="sxs-lookup"><span data-stu-id="8dba4-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="8dba4-115">Ponieważ zarówno implementacji usługi obsługi tych samych operacji i są zasadniczo identyczne inne niż dane, które zwracają, podstawowy dane zawarte w wiadomości wysyłanych z aplikacji klienckich nie jest unikatowy, aby możliwe było określić, jak kierować żądanie.</span><span class="sxs-lookup"><span data-stu-id="8dba4-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="8dba4-116">Ale jeśli aplikacja kliencka dodaje wartości nagłówka do wiadomości, następnie można użyć tej wartości można określić, jak powinny być kierowane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8dba4-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="8dba4-117">Na przykład jeśli aplikacja kliencka potrzebuje komunikat, który ma zostać przetworzony przez zaokrąglania Kalkulator, dodaje niestandardowego nagłówka przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="8dba4-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="8dba4-118">Można teraz umożliwia sprawdzanie komunikatów dla tego pliku nagłówkowego filtr XPath i kierowanie komunikatów w postaci zawierający nagłówek usługą roundCalc.</span><span class="sxs-lookup"><span data-stu-id="8dba4-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="8dba4-119">Ponadto usługa routingu udostępnia dwa punkty końcowe usług wirtualnych, które mogą być używane z Nazwapunktukoncowego, EndpointAddress, lub PrefixEndpointAddress filtrów jednoznacznie kierowanie komunikatów przychodzących do implementacji określonego Kalkulator, oparta na punkcie końcowym do której aplikacja kliencka wysyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="8dba4-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="8dba4-120">Punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="8dba4-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="8dba4-121">Podczas definiowania punktów końcowych używanych przez usługę routingu, najpierw należy określić kształt kanał używany przez klientów i usług.</span><span class="sxs-lookup"><span data-stu-id="8dba4-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="8dba4-122">W tym scenariuszu usług docelowych użyć wzorca "żądanie-odpowiedź", więc <xref:System.ServiceModel.Routing.IRequestReplyRouter> jest używany.</span><span class="sxs-lookup"><span data-stu-id="8dba4-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="8dba4-123">W poniższym przykładzie zdefiniowano punktów końcowych usługi udostępniane przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="8dba4-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="8dba4-124">W przypadku tej konfiguracji usługa routingu udostępnia trzy oddzielne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="8dba4-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="8dba4-125">W zależności od opcji środowiska wykonawczego aplikacja kliencka wysyła komunikaty do jednego z tych adresów.</span><span class="sxs-lookup"><span data-stu-id="8dba4-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="8dba4-126">Komunikaty przychodzące w jednym z punktów końcowych usługi "wirtualne" ("zaokrąglania/Kalkulator" lub "zwykłych/Kalkulator") są przekazywane do odpowiedniej implementacji kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="8dba4-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="8dba4-127">Jeśli aplikacja kliencka nie wysyła żądanie do określonego punktu końcowego, komunikat jest skierowana do endpoint ogólne.</span><span class="sxs-lookup"><span data-stu-id="8dba4-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="8dba4-128">Niezależnie od tego punktu końcowego wybrana aplikacja kliencka może też dołączyć niestandardowy nagłówek, aby wskazać, że komunikat powinien być przekazywany do zaokrąglenia implementacji kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="8dba4-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="8dba4-129">W poniższym przykładzie zdefiniowano punktów końcowych klienta (docelowy), które usługa routingu kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="8dba4-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="8dba4-130">Te punkty końcowe są używane w tabeli filtru do wskazania docelowy punkt końcowy, który jest wysyłany komunikat w przypadku, gdy pasuje do określonego filtru.</span><span class="sxs-lookup"><span data-stu-id="8dba4-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="8dba4-131">Zdefiniuj filtry</span><span class="sxs-lookup"><span data-stu-id="8dba4-131">Define Filters</span></span>  
  
1. <span data-ttu-id="8dba4-132">Aby rozesłać komunikaty oparte na niestandardowy nagłówek "RoundingCalculator", który aplikacja kliencka dodaje do komunikatu, należy zdefiniować filtr, który używa kwerendy XPath Aby sprawdzić obecność tego pliku nagłówkowego.</span><span class="sxs-lookup"><span data-stu-id="8dba4-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="8dba4-133">Ponieważ tego pliku nagłówkowego jest definiowana za pomocą niestandardowej przestrzeni nazw, należy również dodać wpis przestrzeni nazw, który definiuje prefiksem niestandardowej przestrzeni nazw "niestandardowy", który jest używany w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="8dba4-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="8dba4-134">W poniższym przykładzie zdefiniowano niezbędne sekcji routingu, przestrzeń nazw tabeli i filtr XPath.</span><span class="sxs-lookup"><span data-stu-id="8dba4-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="8dba4-135">To **MessageFilter** szuka RoundingCalculator nagłówka wiadomości, która zawiera wartość "zaokrąglania".</span><span class="sxs-lookup"><span data-stu-id="8dba4-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="8dba4-136">Tego pliku nagłówkowego jest ustawionego przez klienta, aby wskazać, czy komunikat powinien być kierowane do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="8dba4-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8dba4-137">Prefiks przestrzeni nazw s12 jest zdefiniowana w przestrzeni nazw tabeli i reprezentuje obszar nazw `http://www.w3.org/2003/05/soap-envelope`.</span><span class="sxs-lookup"><span data-stu-id="8dba4-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="8dba4-138">Należy także zdefiniować filtry, które poszukują komunikatów odebranych w dwóch punktach końcowych wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="8dba4-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="8dba4-139">Pierwszy wirtualnego punkt końcowy jest punktem końcowym "zwykłych/Kalkulator".</span><span class="sxs-lookup"><span data-stu-id="8dba4-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="8dba4-140">Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, czy komunikat powinien być kierowane do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="8dba4-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="8dba4-141">Następująca konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> ustalenie, jeśli wiadomość dotarła za pośrednictwem punktu końcowego o nazwie określonej w danych filtru.</span><span class="sxs-lookup"><span data-stu-id="8dba4-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="8dba4-142">Jeśli komunikat jest odbierany przez punkt końcowy usługi o nazwie "calculatorEndpoint", ten filtr daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="8dba4-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="8dba4-143">Następnie zdefiniuj filtr, który wygląda dla wiadomości wysyłanych na adres roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="8dba4-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="8dba4-144">Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, czy komunikat powinien być kierowane do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="8dba4-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="8dba4-145">Następująca konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> ustalenie, jeśli wiadomość dotarła do endpoint "zaokrąglania/Kalkulator".</span><span class="sxs-lookup"><span data-stu-id="8dba4-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="8dba4-146">Gdy wiadomość zostaje odebrana w adres który rozpoczyna się od `http://localhost/routingservice/router/rounding/` daje w wyniku tego filtru, a następnie **true**.</span><span class="sxs-lookup"><span data-stu-id="8dba4-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="8dba4-147">Ponieważ adres bazowy używany przez tę konfigurację `http://localhost/routingservice/router` i adres określony dla roundingEndpoint jest "zaokrąglania/Kalkulator" pełny adres używany do komunikowania się z tym punktem końcowym `http://localhost/routingservice/router/rounding/calculator`, który pasuje do tego filtru.</span><span class="sxs-lookup"><span data-stu-id="8dba4-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dba4-148">Filtr PrefixEndpointAddress nie może oszacować nazwy hosta podczas wykonywania dopasowanie, ponieważ w jednym hoście mogą się odwoływać przy użyciu różnych nazw hostów, które mogą wszystkie prawidłowe metody odwoływania się do hosta z aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="8dba4-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="8dba4-149">Na przykład wszystkie poniższe może odnosić się do tego samego hosta:</span><span class="sxs-lookup"><span data-stu-id="8dba4-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    > - <span data-ttu-id="8dba4-150">localhost</span><span class="sxs-lookup"><span data-stu-id="8dba4-150">localhost</span></span>  
    > - <span data-ttu-id="8dba4-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="8dba4-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="8dba4-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="8dba4-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="8dba4-153">Ostatni filtr musi obsługiwać routing komunikaty przychodzące w punkcie końcowym ogólnego bez niestandardowego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="8dba4-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="8dba4-154">W tym scenariuszu komunikaty powinny alternatywne między usługami regularCalc i roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="8dba4-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="8dba4-155">Aby obsługiwać routing "działanie okrężne" tych wiadomości, użyj niestandardowy filtr, który umożliwia jedno wystąpienie filtru do dopasowania dla każdego komunikatu przetworzone.</span><span class="sxs-lookup"><span data-stu-id="8dba4-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="8dba4-156">Poniżej definiuje dwa wystąpienia RoundRobinMessageFilter, które są zgrupowane razem do wskazania, że powinien alternatywny między sobą.</span><span class="sxs-lookup"><span data-stu-id="8dba4-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="8dba4-157">W czasie wykonywania filtru tego typu przełącza między wszystkie wystąpienia zdefiniowany filtr tego typu, które są skonfigurowane jako tej samej grupie w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8dba4-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="8dba4-158">Powoduje to, że komunikaty przetwarzane przez ten filtr niestandardowy do alternatywnego między zwracanie `true` dla `RoundRobinFilter1` i `RoundRobinFilter2`.</span><span class="sxs-lookup"><span data-stu-id="8dba4-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="8dba4-159">Definiowanie tabel filtru</span><span class="sxs-lookup"><span data-stu-id="8dba4-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="8dba4-160">Aby skojarzyć z filtrami z punktów końcowych klienta właściwy, trzeba je umieścić w tabeli filtru.</span><span class="sxs-lookup"><span data-stu-id="8dba4-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="8dba4-161">Ten przykładowy scenariusz używa także ustawienia priorytetu filtr, który jest ustawienie opcjonalne, które można określić kolejność, w jakiej są przetwarzane filtrów.</span><span class="sxs-lookup"><span data-stu-id="8dba4-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="8dba4-162">Jeśli żaden priorytet filtru zostanie określony, wszystkie filtry są obliczane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="8dba4-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dba4-163">Podczas określania priorytetu filtr umożliwia pozwala kontrolować kolejność, w której filtry są przetwarzane, jego może niekorzystnie wpłynąć na wydajność usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="8dba4-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="8dba4-164">Jeśli to możliwe, należy utworzyć logikę filtrowania tak, aby korzystanie z priorytetów filtru nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="8dba4-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="8dba4-165">Poniżej definiuje tabelę filtru i dodaje "Obiekt XPathFilter" wcześniej zdefiniowaną w tabeli o priorytecie 2.</span><span class="sxs-lookup"><span data-stu-id="8dba4-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="8dba4-166">Ten wpis określa również, że jeśli `XPathFilter` odpowiada komunikatu, komunikat będą kierowane do `roundingCalcEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="8dba4-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
  
     <span data-ttu-id="8dba4-167">Podczas określania priorytetu filtru, najwyższy priorytet filtry są obliczane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="8dba4-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="8dba4-168">Jeśli co najmniej jeden filtr na poziomie określonym priorytecie są zgodne, zostanie ono ocenione żadnych filtrów na niższych poziomach priorytetu.</span><span class="sxs-lookup"><span data-stu-id="8dba4-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="8dba4-169">W tym scenariuszu 2 ma najwyższy priorytet, które są określone i jest to jedyny wpis filtru na tym poziomie.</span><span class="sxs-lookup"><span data-stu-id="8dba4-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="8dba4-170">Wpisy filtrów zdefiniowano należy sprawdzać, gdy wiadomość zostaje odebrana w określonym punkcie końcowym, sprawdzając nazwę punktu końcowego lub prefiks adresu.</span><span class="sxs-lookup"><span data-stu-id="8dba4-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="8dba4-171">Następujące wpisy Dodaj oba te wpisy filtru do tabeli filtru i skojarzyć je z docelowych punktów końcowych, które wiadomości będą kierowane do.</span><span class="sxs-lookup"><span data-stu-id="8dba4-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="8dba4-172">Te filtry są ustawione na priorytet 1 w celu wskazania, że mogą uruchamiać tylko jeśli poprzednie filtr XPath nie był zgodny komunikat.</span><span class="sxs-lookup"><span data-stu-id="8dba4-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="8dba4-173">Ponieważ te filtry mają priorytet filtru 1, ich będzie być oceniany tylko jeśli filtr na poziomie priorytetu 2 nie jest zgodny komunikat.</span><span class="sxs-lookup"><span data-stu-id="8dba4-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="8dba4-174">Ponadto ponieważ oba filtry mają ten sam poziom priorytetu one zostaną ocenione jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="8dba4-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="8dba4-175">Ponieważ zarówno filtry wykluczają się wzajemnie, jest możliwe tylko jedna lub druga do dopasowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8dba4-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="8dba4-176">Jeśli komunikat nie pasuje do żadnego z poprzednim filtrom, komunikat zostało odebrane za pośrednictwem punktu końcowego Usługa ogólna i zawarte nie informacje nagłówka, która wskazuje, gdzie w celu kierowania go.</span><span class="sxs-lookup"><span data-stu-id="8dba4-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="8dba4-177">Te komunikaty są mają być obsługiwane przez filtr niestandardowy, który równoważy ich między usługami dwóch kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="8dba4-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="8dba4-178">Poniższy przykład pokazuje, jak dodać wpisy filtr do filtru tabeli; Każdy filtr jest skojarzony z jedną z dwóch docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8dba4-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="8dba4-179">Ponieważ te wpisy określić priorytet 0, ich będzie być oceniany tylko jeśli żaden filtr o wyższym priorytecie jest zgodny komunikat.</span><span class="sxs-lookup"><span data-stu-id="8dba4-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="8dba4-180">Ponadto ponieważ oba mają ten sam priorytet, ocenia się je jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="8dba4-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="8dba4-181">Jak wspomniano wcześniej, filtr niestandardowy używany przez te definicje filtrów oblicza tylko jeden lub inne, `true` dla każdego komunikatu odebranego.</span><span class="sxs-lookup"><span data-stu-id="8dba4-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="8dba4-182">Ponieważ tylko dwa filtry są definiowane za pomocą tego samego ustawienia w określonej grupie za pomocą tego filtru, powoduje, że usługa routingu przełącza między wysłaniem regularCalcEndpoint i RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="8dba4-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="8dba4-183">Do analizowania wiadomości te filtry, tabelę filtru najpierw należy skojarzyć z punktami końcowymi usługi, które będą używane do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8dba4-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="8dba4-184">Poniższy przykład pokazuje jak skojarzyć tabeli routingu za pomocą punktów końcowych usługi za pomocą zachowania routingu:</span><span class="sxs-lookup"><span data-stu-id="8dba4-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="8dba4-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dba4-185">Example</span></span>  
 <span data-ttu-id="8dba4-186">Poniżej znajduje się pełna lista pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8dba4-186">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8dba4-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8dba4-187">See also</span></span>

- [<span data-ttu-id="8dba4-188">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="8dba4-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
