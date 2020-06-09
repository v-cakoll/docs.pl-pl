---
title: Klasa DiscoveryClient i DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 6144a3fb528e64fd55fa125b6254d415ec3e8b26
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599168"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="27888-102">Klasa DiscoveryClient i DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="27888-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="27888-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>i <xref:System.ServiceModel.Discovery.DynamicEndpoint> są dwie klasy używane po stronie klienta do wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="27888-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="27888-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>zapewnia listę usług, które pasują do określonego zestawu kryteriów i umożliwiają łączenie się z usługami.</span><span class="sxs-lookup"><span data-stu-id="27888-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="27888-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>wykonuje tę samą operację, a ponadto automatycznie nawiązuje połączenie z jedną z znalezionych usług.</span><span class="sxs-lookup"><span data-stu-id="27888-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="27888-106">Każdy punkt końcowy może zostać dodany do <xref:System.ServiceModel.Discovery.DynamicEndpoint> , kryteria wyszukiwania można również dodać w konfiguracji, co <xref:System.ServiceModel.Discovery.DynamicEndpoint> jest przydatne, gdy potrzebujesz odnajdywania w rozwiązaniu, ale nie chcesz modyfikować logiki klienta — wystarczy tylko zmodyfikować punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="27888-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="27888-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>z drugiej strony można użyć, aby uzyskać dokładniejszą kontrolę nad operacją wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="27888-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="27888-108">Poniższe korzyści są opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="27888-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="27888-109">Obiekt DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="27888-109">DiscoveryClient</span></span>  
 <span data-ttu-id="27888-110"><xref:System.ServiceModel.Discovery.DiscoveryClient>Definiuje metody szukania synchronicznego i asynchronicznego <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> oraz <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="27888-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="27888-111">Definiuje również synchroniczną i asynchroniczną metodę rozpoznawania oraz <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="27888-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="27888-112">Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metod lub, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> Aby wyszukać usługi.</span><span class="sxs-lookup"><span data-stu-id="27888-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="27888-113">Obie te metody przyjmują <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienie, które pozwala określić nazwy typu kontraktu, zakresy, liczbę żądanych wyników i reguły dopasowywania zakresu.</span><span class="sxs-lookup"><span data-stu-id="27888-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="27888-114"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted>Zdarzenia i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> mogą być używane podczas wywoływania <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="27888-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="27888-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>jest uruchamiany za każdym razem, gdy <xref:System.ServiceModel.Discovery.DiscoveryClient> odbierze odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="27888-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="27888-116">Może służyć do wyświetlania paska postępu pokazującego postęp operacji znajdowania.</span><span class="sxs-lookup"><span data-stu-id="27888-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="27888-117">Może również służyć do działania podczas wyszukiwania odpowiedzi po ich odebraniu.</span><span class="sxs-lookup"><span data-stu-id="27888-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="27888-118"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted>Zdarzenie jest wywoływane po zakończeniu operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="27888-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="27888-119">Może się tak zdarzyć, ponieważ odebrano maksymalną liczbę odpowiedzi lub jeśli <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> upłynął.</span><span class="sxs-lookup"><span data-stu-id="27888-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="27888-120">Po zakończeniu operacji Find wyniki są zwracane w <xref:System.ServiceModel.Discovery.FindResponse> wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="27888-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="27888-121"><xref:System.ServiceModel.Discovery.FindResponse>Zawiera kolekcję zawierającą <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> adresy, nazwy typów kontraktów, rozszerzenia, identyfikatory URI nasłuchiwania i zakresy pasujących usług.</span><span class="sxs-lookup"><span data-stu-id="27888-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="27888-122">Możesz następnie użyć tych informacji, aby nawiązać połączenie z jedną z zgodnych usług i wywołać ją.</span><span class="sxs-lookup"><span data-stu-id="27888-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="27888-123">Poniższy przykład pokazuje, jak wywołać metodę System. ServiceModel. Discovery. obiekt DiscoveryClient. Find (System. ServiceModel. Discovery. kryteria znajdowania) i użyć zwróconych metadanych do wywołania znalezionej usługi.</span><span class="sxs-lookup"><span data-stu-id="27888-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="27888-124">Korzyścią z używania <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> jest to, że można buforować listę znalezionych punktów końcowych i używać ich w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="27888-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="27888-125">Za pomocą tej pamięci podręcznej można utworzyć logikę niestandardową w celu obsługi różnych warunków awarii.</span><span class="sxs-lookup"><span data-stu-id="27888-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="27888-126">Poniższy przykład pokazuje, jak wykonać operację znajdowania asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="27888-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 <span data-ttu-id="27888-127">Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metod i, <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> Aby zlokalizować usługę na podstawie adresu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="27888-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="27888-128">Jest to przydatne, gdy adres punktu końcowego nie jest adresami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="27888-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="27888-129">Metody rozwiązywania to wystąpienie, z <xref:System.ServiceModel.Discovery.ResolveCriteria> którego można określić adres punktu końcowego rozwiązywanej usługi, maksymalny czas trwania operacji rozpoznawania oraz zestaw rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="27888-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="27888-130">Poniższy przykład pokazuje, jak używać <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metody do rozwiązywania usługi.</span><span class="sxs-lookup"><span data-stu-id="27888-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="27888-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="27888-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="27888-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>jest standardowym punktem końcowym (Aby uzyskać więcej informacji, zobacz [standardowe punkty końcowe](standard-endpoints.md)), które wykonuje odnajdywanie i automatycznie wybiera zgodną usługę.</span><span class="sxs-lookup"><span data-stu-id="27888-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="27888-133">Po prostu Utwórz <xref:System.ServiceModel.Discovery.DynamicEndpoint> przekazywanie kontraktu w celu wyszukania i powiązania, aby użyć i przekazać <xref:System.ServiceModel.Discovery.DynamicEndpoint> wystąpienie do klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="27888-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="27888-134">Poniższy przykład pokazuje, jak utworzyć i użyć wywołania, <xref:System.ServiceModel.Discovery.DynamicEndpoint> Aby wywołać usługę Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="27888-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="27888-135">Odnajdywanie jest wykonywane za każdym razem, gdy klient zostanie otwarty.</span><span class="sxs-lookup"><span data-stu-id="27888-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="27888-136">Każdy punkt końcowy zdefiniowany w konfiguracji może również zostać włączony <xref:System.ServiceModel.Discovery.DynamicEndpoint> przez dodanie `kind ="dynamicEndpoint"` atrybutu do elementu konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="27888-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27888-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27888-137">See also</span></span>

- [<span data-ttu-id="27888-138">Odnajdywanie z zakresami</span><span class="sxs-lookup"><span data-stu-id="27888-138">Discovery with Scopes</span></span>](../samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="27888-139">Podstawowe</span><span class="sxs-lookup"><span data-stu-id="27888-139">Basic</span></span>](../samples/basic-sample.md)
