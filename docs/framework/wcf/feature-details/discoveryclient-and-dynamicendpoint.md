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
# <a name="discoveryclient-and-dynamicendpoint"></a>Klasa DiscoveryClient i DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>i <xref:System.ServiceModel.Discovery.DynamicEndpoint> są dwie klasy używane po stronie klienta do wyszukiwania usług. <xref:System.ServiceModel.Discovery.DiscoveryClient>udostępnia listę usług, które odpowiadają określonej zestawowi kryteriów i umożliwia nawiązanie połączenia z usługami. <xref:System.ServiceModel.Discovery.DynamicEndpoint>wykonuje tę samą operację, a ponadto automatycznie łączy się z jedną z znalezionych usług. Każdy punkt końcowy można <xref:System.ServiceModel.Discovery.DynamicEndpoint>wprowadzić do , kryteria wyszukiwania można <xref:System.ServiceModel.Discovery.DynamicEndpoint> również dodać w konfiguracji, w związku z tym jest przydatne, gdy trzeba odnajdywania w rozwiązaniu, ale nie chcesz zmodyfikować logiki klienta — wystarczy tylko zmodyfikować punkty końcowe. <xref:System.ServiceModel.Discovery.DiscoveryClient>z drugiej strony może służyć do uzyskania lepszą kontrolę nad operacją wyszukiwania. Zastosowania i korzyści każdego z nich są opracowane poniżej.  
  
## <a name="discoveryclient"></a>Discoveryclient  
 Definiuje <xref:System.ServiceModel.Discovery.DiscoveryClient> synchroniczne i asynchroniczne Find <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> metody i zdarzenia.  Definiuje również synchroniczne i asynchroniczne Resolve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> metody i zdarzenia. Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> lub <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody wyszukiwania usług. Obie te metody <xref:System.ServiceModel.Discovery.FindCriteria> przyjmują wystąpienie, które umożliwia określenie nazw typów kontraktów, zakresów, maksymalnej liczby wymaganych wyników i reguł dopasowania zakresu. Zdarzenia <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> i mogą być używane <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> podczas wywoływania metody. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>jest uruchamiany <xref:System.ServiceModel.Discovery.DiscoveryClient> za każdym razem, gdy otrzymuje odpowiedź z usługi. Może służyć do wyświetlania paska postępu pokazującego postęp operacji znajdowania. Może być również używany do działania na znalezienie odpowiedzi, ponieważ są one odbierane. Zdarzenie <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> jest uruchamiane po zakończeniu operacji find. Może się tak zdarzyć, ponieważ odebrano maksymalną <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> liczbę odpowiedzi lub jeśli usłyszono tę liczbę. Po zakończeniu operacji find wyniki są <xref:System.ServiceModel.Discovery.FindResponse> zwracane w wystąpieniu. Zawiera <xref:System.ServiceModel.Discovery.FindResponse> kolekcję, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> która zawiera adresy, nazwy typów umowy, rozszerzenia, identyfikatory URI nasłuchiwania i zakresy pasujących usług. Następnie można użyć tych informacji, aby połączyć się z jedną z pasujących usług i wywołać ją. W poniższym przykładzie pokazano, jak wywołać metodę System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) i użyć zwróconych metadanych do wywołania znalezionej usługi. Zaletą użycia <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> jest, że można buforować listę punktów końcowych, które zostały znalezione i używać ich w późniejszym czasie. Za pomocą tej pamięci podręcznej można utworzyć niestandardową logikę do obsługi różnych warunków awarii.  
  
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
  
 W poniższym przykładzie pokazano, jak wykonać operację znajdowania asynchronicznie.  
  
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
  
 Użyj <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> i <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody, aby zlokalizować usługę na podstawie jej adresu punktu końcowego. Jest to przydatne, gdy adres punktu końcowego nie jest adresowalny sieci. Resolve Metody wziąć wystąpienie, <xref:System.ServiceModel.Discovery.ResolveCriteria> które pozwala określić adres punktu końcowego usługi, które są rozpoznawane, maksymalny czas trwania operacji rozpoznawania i zestaw rozszerzeń. W poniższym przykładzie <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> pokazano, jak użyć metody, aby rozwiązać usługę.  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>Dynamicendpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>jest standardowym punktem końcowym (Aby uzyskać więcej informacji, zobacz [standardowe punkty końcowe),](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)który wykonuje odnajdowanie i automatycznie wybiera pasujące usługi. Wystarczy utworzyć <xref:System.ServiceModel.Discovery.DynamicEndpoint> przekazywanie w umowie do wyszukiwania i powiązania <xref:System.ServiceModel.Discovery.DynamicEndpoint> do użycia i przekazać wystąpienie do klienta WCF. W poniższym przykładzie pokazano, <xref:System.ServiceModel.Discovery.DynamicEndpoint> jak utworzyć i użyć do wywołania usługi kalkulatora. Odnajdowanie jest wykonywane za każdym razem, gdy klient jest otwarty. Każdy punkt końcowy zdefiniowany w konfiguracji <xref:System.ServiceModel.Discovery.DynamicEndpoint> można `kind ="dynamicEndpoint"` również przekształcić w a, dodając atrybut do elementu konfiguracji punktu końcowego.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Odnajdywanie z zakresami](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Podstawowa (Basic)](../../../../docs/framework/wcf/samples/basic-sample.md)
