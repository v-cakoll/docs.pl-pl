---
title: Klasa DiscoveryClient i DynamicEndpoint
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e3ac334d53480ba8b63cc8e8f117dd74315963c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="discoveryclient-and-dynamicendpoint"></a>Klasa DiscoveryClient i DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>i <xref:System.ServiceModel.Discovery.DynamicEndpoint> są dwie klasy używane po stronie klienta do usługi wyszukiwania. <xref:System.ServiceModel.Discovery.DiscoveryClient>zawiera listę usług, które odpowiada określonym ustawieniu kryteriów i służy do łączenia się z usługami. <xref:System.ServiceModel.Discovery.DynamicEndpoint>wykonuje tę samą operację, a ponadto automatycznie łączy się z jednej z usług, które można odnaleźć. Dowolnego punktu końcowego można uwzględnić w <xref:System.ServiceModel.Discovery.DynamicEndpoint>, kryteria wyszukiwania można również dodać w konfiguracji, w związku z tym <xref:System.ServiceModel.Discovery.DynamicEndpoint> jest przydatne, gdy użycie odnajdywania na rozwiązania, ale nie chcesz zmodyfikować logiki klienta — należy zmodyfikować punkty końcowe. <xref:System.ServiceModel.Discovery.DiscoveryClient>z drugiej strony może być użyte do uzyskania bardziej precyzyjną kontrolę nad operacji wyszukiwania. Używa i korzyści zostały opracowane poniżej.  
  
## <a name="discoveryclient"></a>Obiekt DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Definiuje synchroniczne i asynchroniczne metody Find, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia.  Definiuje również synchroniczne i asynchroniczne metod Resolve a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> zdarzeń. Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> lub <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody wyszukiwania usług. Obie te metody mają <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienie, które służy do określenia nazwy typów kontraktu, zakresy, maksymalna liczba wyników żądanie i zakresu reguł dopasowywania. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzeń może być używana przy wywoływaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>jest wywoływane zawsze, gdy <xref:System.ServiceModel.Discovery.DiscoveryClient> odbiera odpowiedź z usługi. Może służyć do wyświetlenia pokazujące postęp operacji wyszukiwania — pasek postępu. Można go również używane do działania w Znajdź odpowiedzi otrzymywanych. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Zdarzenie jest wywoływane po ukończeniu operacji wyszukiwania. Może się tak zdarzyć, ponieważ odebrano maksymalną liczbę odpowiedzi lub jeśli <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> upłynął. Po zakończeniu operacji Znajdź wyniki są zwracane w <xref:System.ServiceModel.Discovery.FindResponse> wystąpienia. <xref:System.ServiceModel.Discovery.FindResponse> Zawiera kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> który zawiera adresy, nazwy typów kontraktu, rozszerzeń, nasłuchiwania URI i zakresy dopasowania usług. Użycie z tych informacji, do łączenia się i wywoływanie jednego pasującego usług. Poniższy przykład przedstawia sposób wywołania metody System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) i użyć metadane zwrócony do wywołania znaleziono usługi. Zaletą używania <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> jest, że można buforować listy punktów końcowych znaleźliśmy i używać ich w późniejszym czasie. Z tej pamięci podręcznej można tworzyć niestandardowej logiki do obsługi różnych awarię.  
  
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
  
 Poniższy przykład pokazuje, jak przeprowadzić asynchronicznie operację wyszukiwania.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]wprowadzania asynchronicznego wywołania znaleźć, zobacz [znajdowanie asynchroniczne](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).  
  
 Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> i <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody, aby zlokalizować usługi oparte na jego adres punktu końcowego. Jest to przydatne, gdy adres punktu końcowego nie jest siecią adresowanego. Metod Resolve zająć wystąpienia <xref:System.ServiceModel.Discovery.ResolveCriteria> umożliwia określenie adresu punktu końcowego usługi użytkownik rozwiązuje, maksymalny czas trwania operacji rozpoznawania i zestaw rozszerzeń. Poniższy przykład przedstawia użycie <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metodą rozwiązania usługi.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>jest to standardowy punkt końcowy ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [standardowych punktów końcowych](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) który wykonuje odnajdowanie i automatycznie wybiera pasującego usługi. Wystarczy utworzyć <xref:System.ServiceModel.Discovery.DynamicEndpoint> przekazując kontraktu do wyszukiwania i powiązanie z użycia i przekazywać <xref:System.ServiceModel.Discovery.DynamicEndpoint> wystąpienie do klienta platformy WCF. Poniższy przykład przedstawia sposób tworzenia i używania <xref:System.ServiceModel.Discovery.DynamicEndpoint> do wywołania tej usługi Kalkulator. Odnajdywanie jest wykonywane za każdym razem, gdy klienta jest otwarty. Można również zmienić żadnych punktów końcowych zdefiniowanych w konfiguracji <xref:System.ServiceModel.Discovery.DynamicEndpoint> przez dodanie `kind ="dynamicEndpoint"` atrybutu elementu konfiguracji punktu końcowego.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Odnajdywanie z zakresami](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Znajdowanie asynchroniczne](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [Podstawy](../../../../docs/framework/wcf/samples/basic-sample.md)
