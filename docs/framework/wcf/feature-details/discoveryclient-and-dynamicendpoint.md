---
title: Klasa DiscoveryClient i DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: d9bf5bf0032a299589292e51ad9bc273c56ced3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="b4283-102">Klasa DiscoveryClient i DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="b4283-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="b4283-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> i <xref:System.ServiceModel.Discovery.DynamicEndpoint> są dwie klasy używane po stronie klienta do usługi wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="b4283-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="b4283-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> zawiera listę usług, które odpowiada określonym ustawieniu kryteriów i służy do łączenia się z usługami.</span><span class="sxs-lookup"><span data-stu-id="b4283-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="b4283-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> wykonuje tę samą operację, a ponadto automatycznie łączy się z jednej z usług, które można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="b4283-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="b4283-106">Dowolnego punktu końcowego można uwzględnić w <xref:System.ServiceModel.Discovery.DynamicEndpoint>, kryteria wyszukiwania można również dodać w konfiguracji, w związku z tym <xref:System.ServiceModel.Discovery.DynamicEndpoint> jest przydatne, gdy użycie odnajdywania na rozwiązania, ale nie chcesz zmodyfikować logiki klienta — należy zmodyfikować punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="b4283-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="b4283-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> z drugiej strony może być użyte do uzyskania bardziej precyzyjną kontrolę nad operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="b4283-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="b4283-108">Używa i korzyści zostały opracowane poniżej.</span><span class="sxs-lookup"><span data-stu-id="b4283-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="b4283-109">Obiekt DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="b4283-109">DiscoveryClient</span></span>  
 <span data-ttu-id="b4283-110"><xref:System.ServiceModel.Discovery.DiscoveryClient> Definiuje synchroniczne i asynchroniczne metody Find, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b4283-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="b4283-111">Definiuje również synchroniczne i asynchroniczne metod Resolve a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b4283-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="b4283-112">Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> lub <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="b4283-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="b4283-113">Obie te metody mają <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienie, które służy do określenia nazwy typów kontraktu, zakresy, maksymalna liczba wyników żądanie i zakresu reguł dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="b4283-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="b4283-114"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzeń może być używana przy wywoływaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4283-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="b4283-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> jest wywoływane zawsze, gdy <xref:System.ServiceModel.Discovery.DiscoveryClient> odbiera odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="b4283-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="b4283-116">Może służyć do wyświetlenia pokazujące postęp operacji wyszukiwania — pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="b4283-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="b4283-117">Można go również używane do działania w Znajdź odpowiedzi otrzymywanych.</span><span class="sxs-lookup"><span data-stu-id="b4283-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="b4283-118"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Zdarzenie jest wywoływane po ukończeniu operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="b4283-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="b4283-119">Może się tak zdarzyć, ponieważ odebrano maksymalną liczbę odpowiedzi lub jeśli <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> upłynął.</span><span class="sxs-lookup"><span data-stu-id="b4283-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="b4283-120">Po zakończeniu operacji Znajdź wyniki są zwracane w <xref:System.ServiceModel.Discovery.FindResponse> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b4283-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="b4283-121"><xref:System.ServiceModel.Discovery.FindResponse> Zawiera kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> który zawiera adresy, nazwy typów kontraktu, rozszerzeń, nasłuchiwania URI i zakresy dopasowania usług.</span><span class="sxs-lookup"><span data-stu-id="b4283-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="b4283-122">Użycie z tych informacji, do łączenia się i wywoływanie jednego pasującego usług.</span><span class="sxs-lookup"><span data-stu-id="b4283-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="b4283-123">Poniższy przykład przedstawia sposób wywołania metody System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) i użyć metadane zwrócony do wywołania znaleziono usługi.</span><span class="sxs-lookup"><span data-stu-id="b4283-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="b4283-124">Zaletą używania <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> jest, że można buforować listy punktów końcowych znaleźliśmy i używać ich w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="b4283-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="b4283-125">Z tej pamięci podręcznej można tworzyć niestandardowej logiki do obsługi różnych awarię.</span><span class="sxs-lookup"><span data-stu-id="b4283-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="b4283-126">Poniższy przykład pokazuje, jak przeprowadzić asynchronicznie operację wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="b4283-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 <span data-ttu-id="b4283-127">Aby uzyskać więcej informacji o wprowadzaniu asynchroniczne znaleźć wywołania, zobacz [znajdowanie asynchroniczne](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b4283-127">For more information about making asynchronous find calls, see [Asynchronous Find](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span></span>  
  
 <span data-ttu-id="b4283-128">Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> i <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody, aby zlokalizować usługi oparte na jego adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b4283-128">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="b4283-129">Jest to przydatne, gdy adres punktu końcowego nie jest siecią adresowanego.</span><span class="sxs-lookup"><span data-stu-id="b4283-129">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="b4283-130">Metod Resolve zająć wystąpienia <xref:System.ServiceModel.Discovery.ResolveCriteria> umożliwia określenie adresu punktu końcowego usługi użytkownik rozwiązuje, maksymalny czas trwania operacji rozpoznawania i zestaw rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="b4283-130">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="b4283-131">Poniższy przykład przedstawia użycie <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metodą rozwiązania usługi.</span><span class="sxs-lookup"><span data-stu-id="b4283-131">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="b4283-132">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="b4283-132">DynamicEndpoint</span></span>  
 <span data-ttu-id="b4283-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> jest to standardowy punkt końcowy (Aby uzyskać więcej informacji, zobacz [standardowych punktów końcowych](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) który wykonuje odnajdowanie i automatycznie wybiera pasującego usługi.</span><span class="sxs-lookup"><span data-stu-id="b4283-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="b4283-134">Wystarczy utworzyć <xref:System.ServiceModel.Discovery.DynamicEndpoint> przekazując kontraktu do wyszukiwania i powiązanie z użycia i przekazywać <xref:System.ServiceModel.Discovery.DynamicEndpoint> wystąpienie do klienta platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="b4283-134">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="b4283-135">Poniższy przykład przedstawia sposób tworzenia i używania <xref:System.ServiceModel.Discovery.DynamicEndpoint> do wywołania tej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="b4283-135">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="b4283-136">Odnajdywanie jest wykonywane za każdym razem, gdy klienta jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b4283-136">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="b4283-137">Można również zmienić żadnych punktów końcowych zdefiniowanych w konfiguracji <xref:System.ServiceModel.Discovery.DynamicEndpoint> przez dodanie `kind ="dynamicEndpoint"` atrybutu elementu konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b4283-137">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4283-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4283-138">See Also</span></span>  
 [<span data-ttu-id="b4283-139">Odnajdywanie z zakresami</span><span class="sxs-lookup"><span data-stu-id="b4283-139">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [<span data-ttu-id="b4283-140">Znajdowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="b4283-140">Asynchronous Find</span></span>](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [<span data-ttu-id="b4283-141">Podstawy</span><span class="sxs-lookup"><span data-stu-id="b4283-141">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
