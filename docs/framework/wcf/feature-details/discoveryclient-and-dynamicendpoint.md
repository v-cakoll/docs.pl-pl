---
title: Klasa DiscoveryClient i DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 6e7b1cf13309ba6fc1da424649c667efe255278e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709991"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="20bc3-102">Klasa DiscoveryClient i DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="20bc3-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="20bc3-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> i <xref:System.ServiceModel.Discovery.DynamicEndpoint> są dwie klasy używane po stronie klienta do wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="20bc3-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="20bc3-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> zawiera listę usług, które odpowiadają określony zestaw kryteriów oraz pozwala na łączenie się z usługami.</span><span class="sxs-lookup"><span data-stu-id="20bc3-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="20bc3-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> wykonuje tę samą operację, a ponadto automatycznie łączy się z jednej z usług, które zostało znalezione.</span><span class="sxs-lookup"><span data-stu-id="20bc3-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="20bc3-106">Można uwzględnić w dowolnym punkcie końcowym <xref:System.ServiceModel.Discovery.DynamicEndpoint>, kryteriów wyszukiwania można również dodać w konfiguracji, dlatego <xref:System.ServiceModel.Discovery.DynamicEndpoint> jest przydatne, gdy potrzebujesz odnajdywania w rozwiązaniu, ale nie chcesz zmodyfikować logiki klienta — należy zmodyfikować punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="20bc3-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="20bc3-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> z drugiej strony może być użyte do uzyskania bardziej precyzyjną kontrolę nad operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="20bc3-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="20bc3-108">Zastosowania i zalety każdego z nich są opracowane poniżej.</span><span class="sxs-lookup"><span data-stu-id="20bc3-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="20bc3-109">Klasa DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="20bc3-109">DiscoveryClient</span></span>  
 <span data-ttu-id="20bc3-110"><xref:System.ServiceModel.Discovery.DiscoveryClient> Definiuje synchroniczne i asynchroniczne metody Znajdź <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="20bc3-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="20bc3-111">Definiuje synchroniczne i asynchroniczne metody rozwiązania i <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="20bc3-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="20bc3-112">Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> lub <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody służące do wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="20bc3-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="20bc3-113">Obie te metody mają <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienia, która pozwala na określenie nazwy typów kontraktu, zakresy, maksymalna liczba wyników żądane i zakresu z regułami dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="20bc3-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="20bc3-114"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia mogą być używane podczas wywoływania <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="20bc3-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="20bc3-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> jest wywoływane zawsze, gdy <xref:System.ServiceModel.Discovery.DiscoveryClient> otrzyma odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="20bc3-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="20bc3-116">Może służyć do wyświetlania postępu paska pokazujące postęp operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="20bc3-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="20bc3-117">Może również służyć do działania na znajdowanie odpowiedzi są odbierane.</span><span class="sxs-lookup"><span data-stu-id="20bc3-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="20bc3-118"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Zdarzenie jest wywoływane po zakończeniu operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="20bc3-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="20bc3-119">Ten problem może wystąpić, ponieważ odebrano maksymalną liczbę odpowiedzi, lub jeśli <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> upłynął.</span><span class="sxs-lookup"><span data-stu-id="20bc3-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="20bc3-120">Po zakończeniu operacji Znajdź wyniki są zwracane w <xref:System.ServiceModel.Discovery.FindResponse> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="20bc3-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="20bc3-121"><xref:System.ServiceModel.Discovery.FindResponse> Zawiera zbiór <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> zawierający adresy, nazwy typów kontraktu, rozszerzenia, identyfikatorów URI nasłuchiwania i zakresy zgodnych usług.</span><span class="sxs-lookup"><span data-stu-id="20bc3-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="20bc3-122">Te informacje umożliwia następnie nawiązać połączenie i wywołać jedną zgodnych usług.</span><span class="sxs-lookup"><span data-stu-id="20bc3-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="20bc3-123">Poniższy przykład pokazuje, jak wywołać metodę System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) i umożliwia wywoływanie usługi znaleziono zwróconych metadanych.</span><span class="sxs-lookup"><span data-stu-id="20bc3-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="20bc3-124">Zaletą używania <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> jest, że można buforować listy punktów końcowych Ci się znaleźć i używać ich w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="20bc3-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="20bc3-125">Z tą pamięcią podręczną można tworzyć niestandardowe logikę w celu obsługi różnych warunków błędów.</span><span class="sxs-lookup"><span data-stu-id="20bc3-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="20bc3-126">Poniższy przykład pokazuje, jak do wykonywania operacji wyszukiwania asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="20bc3-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```  
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 <span data-ttu-id="20bc3-127">Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> i <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody do zlokalizowania usługi oparte na jej adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="20bc3-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="20bc3-128">Jest to przydatne, gdy nie jest adres punktu końcowego sieci mogą być adresowane.</span><span class="sxs-lookup"><span data-stu-id="20bc3-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="20bc3-129">Metody Resolve przyjmują wystąpienie <xref:System.ServiceModel.Discovery.ResolveCriteria> umożliwia określanie adresu punktu końcowego usługi użytkownik rozwiązuje, maksymalny czas trwania operacji rozwiązania i zestaw rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="20bc3-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="20bc3-130">Poniższy przykład pokazuje, jak używać <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metodą rozwiązania usługi.</span><span class="sxs-lookup"><span data-stu-id="20bc3-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="20bc3-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="20bc3-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="20bc3-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> jest to standardowy punkt końcowy (Aby uzyskać więcej informacji, zobacz [standardowe punkty końcowe](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) który przeprowadza odnajdywanie i automatycznie wybiera zgodnych usług.</span><span class="sxs-lookup"><span data-stu-id="20bc3-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="20bc3-133">Po prostu Utwórz <xref:System.ServiceModel.Discovery.DynamicEndpoint> przekazując kontrakt wyszukiwanie i powiązania do użycia i przekazywać <xref:System.ServiceModel.Discovery.DynamicEndpoint> wystąpienie do klienta platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="20bc3-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="20bc3-134">Poniższy przykład pokazuje, jak utworzyć i używać <xref:System.ServiceModel.Discovery.DynamicEndpoint> do wywołania kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="20bc3-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="20bc3-135">Odnajdywanie odbywa się za każdym razem, gdy klient jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="20bc3-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="20bc3-136">Można również zmienić dowolnego punktu końcowego zdefiniowane w konfiguracji <xref:System.ServiceModel.Discovery.DynamicEndpoint> , dodając `kind ="dynamicEndpoint"` atrybutu do elementu konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="20bc3-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="20bc3-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20bc3-137">See also</span></span>
- [<span data-ttu-id="20bc3-138">Odnajdywanie z zakresami</span><span class="sxs-lookup"><span data-stu-id="20bc3-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="20bc3-139">Podstawy</span><span class="sxs-lookup"><span data-stu-id="20bc3-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
