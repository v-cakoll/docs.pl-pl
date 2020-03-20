---
title: Klasa DiscoveryClient i DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: c6d87a04a6787725ad7c4546650485af932882b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185181"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="a3658-102">Klasa DiscoveryClient i DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="a3658-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="a3658-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>i <xref:System.ServiceModel.Discovery.DynamicEndpoint> są dwie klasy używane po stronie klienta do wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="a3658-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="a3658-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>udostępnia listę usług, które odpowiadają określonej zestawowi kryteriów i umożliwia nawiązanie połączenia z usługami.</span><span class="sxs-lookup"><span data-stu-id="a3658-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="a3658-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>wykonuje tę samą operację, a ponadto automatycznie łączy się z jedną z znalezionych usług.</span><span class="sxs-lookup"><span data-stu-id="a3658-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="a3658-106">Każdy punkt końcowy można <xref:System.ServiceModel.Discovery.DynamicEndpoint>wprowadzić do , kryteria wyszukiwania można <xref:System.ServiceModel.Discovery.DynamicEndpoint> również dodać w konfiguracji, w związku z tym jest przydatne, gdy trzeba odnajdywania w rozwiązaniu, ale nie chcesz zmodyfikować logiki klienta — wystarczy tylko zmodyfikować punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="a3658-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="a3658-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>z drugiej strony może służyć do uzyskania lepszą kontrolę nad operacją wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="a3658-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="a3658-108">Zastosowania i korzyści każdego z nich są opracowane poniżej.</span><span class="sxs-lookup"><span data-stu-id="a3658-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="a3658-109">Discoveryclient</span><span class="sxs-lookup"><span data-stu-id="a3658-109">DiscoveryClient</span></span>  
 <span data-ttu-id="a3658-110">Definiuje <xref:System.ServiceModel.Discovery.DiscoveryClient> synchroniczne i asynchroniczne Find <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3658-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="a3658-111">Definiuje również synchroniczne i asynchroniczne Resolve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3658-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="a3658-112">Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> lub <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="a3658-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="a3658-113">Obie te metody <xref:System.ServiceModel.Discovery.FindCriteria> przyjmują wystąpienie, które umożliwia określenie nazw typów kontraktów, zakresów, maksymalnej liczby wymaganych wyników i reguł dopasowania zakresu.</span><span class="sxs-lookup"><span data-stu-id="a3658-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="a3658-114">Zdarzenia <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> i mogą być używane <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="a3658-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="a3658-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>jest uruchamiany <xref:System.ServiceModel.Discovery.DiscoveryClient> za każdym razem, gdy otrzymuje odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="a3658-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="a3658-116">Może służyć do wyświetlania paska postępu pokazującego postęp operacji znajdowania.</span><span class="sxs-lookup"><span data-stu-id="a3658-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="a3658-117">Może być również używany do działania na znalezienie odpowiedzi, ponieważ są one odbierane.</span><span class="sxs-lookup"><span data-stu-id="a3658-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="a3658-118">Zdarzenie <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> jest uruchamiane po zakończeniu operacji find.</span><span class="sxs-lookup"><span data-stu-id="a3658-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="a3658-119">Może się tak zdarzyć, ponieważ odebrano maksymalną <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> liczbę odpowiedzi lub jeśli usłyszono tę liczbę.</span><span class="sxs-lookup"><span data-stu-id="a3658-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="a3658-120">Po zakończeniu operacji find wyniki są <xref:System.ServiceModel.Discovery.FindResponse> zwracane w wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="a3658-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="a3658-121">Zawiera <xref:System.ServiceModel.Discovery.FindResponse> kolekcję, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> która zawiera adresy, nazwy typów umowy, rozszerzenia, identyfikatory URI nasłuchiwania i zakresy pasujących usług.</span><span class="sxs-lookup"><span data-stu-id="a3658-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="a3658-122">Następnie można użyć tych informacji, aby połączyć się z jedną z pasujących usług i wywołać ją.</span><span class="sxs-lookup"><span data-stu-id="a3658-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="a3658-123">W poniższym przykładzie pokazano, jak wywołać metodę System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) i użyć zwróconych metadanych do wywołania znalezionej usługi.</span><span class="sxs-lookup"><span data-stu-id="a3658-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="a3658-124">Zaletą użycia <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> jest, że można buforować listę punktów końcowych, które zostały znalezione i używać ich w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="a3658-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="a3658-125">Za pomocą tej pamięci podręcznej można utworzyć niestandardową logikę do obsługi różnych warunków awarii.</span><span class="sxs-lookup"><span data-stu-id="a3658-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="a3658-126">W poniższym przykładzie pokazano, jak wykonać operację znajdowania asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a3658-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="a3658-127">Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> i <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody, aby zlokalizować usługę na podstawie jej adresu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a3658-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="a3658-128">Jest to przydatne, gdy adres punktu końcowego nie jest adresowalny sieci.</span><span class="sxs-lookup"><span data-stu-id="a3658-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="a3658-129">Resolve Metody wziąć wystąpienie, <xref:System.ServiceModel.Discovery.ResolveCriteria> które pozwala określić adres punktu końcowego usługi, które są rozpoznawane, maksymalny czas trwania operacji rozpoznawania i zestaw rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="a3658-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="a3658-130">W poniższym przykładzie <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> pokazano, jak użyć metody, aby rozwiązać usługę.</span><span class="sxs-lookup"><span data-stu-id="a3658-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="a3658-131">Dynamicendpoint</span><span class="sxs-lookup"><span data-stu-id="a3658-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="a3658-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>jest standardowym punktem końcowym (Aby uzyskać więcej informacji, zobacz [standardowe punkty końcowe),](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)który wykonuje odnajdowanie i automatycznie wybiera pasujące usługi.</span><span class="sxs-lookup"><span data-stu-id="a3658-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="a3658-133">Wystarczy utworzyć <xref:System.ServiceModel.Discovery.DynamicEndpoint> przekazywanie w umowie do wyszukiwania i powiązania <xref:System.ServiceModel.Discovery.DynamicEndpoint> do użycia i przekazać wystąpienie do klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="a3658-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="a3658-134">W poniższym przykładzie pokazano, <xref:System.ServiceModel.Discovery.DynamicEndpoint> jak utworzyć i użyć do wywołania usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="a3658-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="a3658-135">Odnajdowanie jest wykonywane za każdym razem, gdy klient jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="a3658-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="a3658-136">Każdy punkt końcowy zdefiniowany w konfiguracji <xref:System.ServiceModel.Discovery.DynamicEndpoint> można `kind ="dynamicEndpoint"` również przekształcić w a, dodając atrybut do elementu konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a3658-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3658-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3658-137">See also</span></span>

- [<span data-ttu-id="a3658-138">Odnajdywanie z zakresami</span><span class="sxs-lookup"><span data-stu-id="a3658-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="a3658-139">Podstawowa (Basic)</span><span class="sxs-lookup"><span data-stu-id="a3658-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
