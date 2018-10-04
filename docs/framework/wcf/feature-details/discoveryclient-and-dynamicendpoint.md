---
title: Klasa DiscoveryClient i DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: ff8cc071b13123a8d04162a2c52a8c3fb486d6db
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579754"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>Klasa DiscoveryClient i DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> i <xref:System.ServiceModel.Discovery.DynamicEndpoint> są dwie klasy używane po stronie klienta do wyszukiwania usług. <xref:System.ServiceModel.Discovery.DiscoveryClient> zawiera listę usług, które odpowiadają określony zestaw kryteriów oraz pozwala na łączenie się z usługami. <xref:System.ServiceModel.Discovery.DynamicEndpoint> wykonuje tę samą operację, a ponadto automatycznie łączy się z jednej z usług, które zostało znalezione. Można uwzględnić w dowolnym punkcie końcowym <xref:System.ServiceModel.Discovery.DynamicEndpoint>, kryteriów wyszukiwania można również dodać w konfiguracji, dlatego <xref:System.ServiceModel.Discovery.DynamicEndpoint> jest przydatne, gdy potrzebujesz odnajdywania w rozwiązaniu, ale nie chcesz zmodyfikować logiki klienta — należy zmodyfikować punktów końcowych. <xref:System.ServiceModel.Discovery.DiscoveryClient> z drugiej strony może być użyte do uzyskania bardziej precyzyjną kontrolę nad operacji wyszukiwania. Zastosowania i zalety każdego z nich są opracowane poniżej.  
  
## <a name="discoveryclient"></a>Klasa DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Definiuje synchroniczne i asynchroniczne metody Znajdź <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia.  Definiuje synchroniczne i asynchroniczne metody rozwiązania i <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> zdarzeń. Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> lub <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody służące do wyszukiwania usług. Obie te metody mają <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienia, która pozwala na określenie nazwy typów kontraktu, zakresy, maksymalna liczba wyników żądane i zakresu z regułami dopasowywania. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia mogą być używane podczas wywoływania <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> jest wywoływane zawsze, gdy <xref:System.ServiceModel.Discovery.DiscoveryClient> otrzyma odpowiedź z usługi. Może służyć do wyświetlania postępu paska pokazujące postęp operacji wyszukiwania. Może również służyć do działania na znajdowanie odpowiedzi są odbierane. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Zdarzenie jest wywoływane po zakończeniu operacji wyszukiwania. Ten problem może wystąpić, ponieważ odebrano maksymalną liczbę odpowiedzi, lub jeśli <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> upłynął. Po zakończeniu operacji Znajdź wyniki są zwracane w <xref:System.ServiceModel.Discovery.FindResponse> wystąpienia. <xref:System.ServiceModel.Discovery.FindResponse> Zawiera zbiór <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> zawierający adresy, nazwy typów kontraktu, rozszerzenia, identyfikatorów URI nasłuchiwania i zakresy zgodnych usług. Te informacje umożliwia następnie nawiązać połączenie i wywołać jedną zgodnych usług. Poniższy przykład pokazuje, jak wywołać metodę System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) i umożliwia wywoływanie usługi znaleziono zwróconych metadanych. Zaletą używania <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> jest, że można buforować listy punktów końcowych Ci się znaleźć i używać ich w późniejszym czasie. Z tą pamięcią podręczną można tworzyć niestandardowe logikę w celu obsługi różnych warunków błędów.  
  
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
  
 Poniższy przykład pokazuje, jak do wykonywania operacji wyszukiwania asynchronicznie.  
  
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
  
 Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> i <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody do zlokalizowania usługi oparte na jej adres punktu końcowego. Jest to przydatne, gdy nie jest adres punktu końcowego sieci mogą być adresowane. Metody Resolve przyjmują wystąpienie <xref:System.ServiceModel.Discovery.ResolveCriteria> umożliwia określanie adresu punktu końcowego usługi użytkownik rozwiązuje, maksymalny czas trwania operacji rozwiązania i zestaw rozszerzeń. Poniższy przykład pokazuje, jak używać <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metodą rozwiązania usługi.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> jest to standardowy punkt końcowy (Aby uzyskać więcej informacji, zobacz [standardowe punkty końcowe](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) który przeprowadza odnajdywanie i automatycznie wybiera zgodnych usług. Po prostu Utwórz <xref:System.ServiceModel.Discovery.DynamicEndpoint> przekazując kontrakt wyszukiwanie i powiązania do użycia i przekazywać <xref:System.ServiceModel.Discovery.DynamicEndpoint> wystąpienie do klienta platformy WCF. Poniższy przykład pokazuje, jak utworzyć i używać <xref:System.ServiceModel.Discovery.DynamicEndpoint> do wywołania kalkulatora. Odnajdywanie odbywa się za każdym razem, gdy klient jest otwarty. Można również zmienić dowolnego punktu końcowego zdefiniowane w konfiguracji <xref:System.ServiceModel.Discovery.DynamicEndpoint> , dodając `kind ="dynamicEndpoint"` atrybutu do elementu konfiguracji punktu końcowego.  
  
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
 [Podstawy](../../../../docs/framework/wcf/samples/basic-sample.md)
