---
title: Odnajdywanie — znajdowanie i kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: b2f679879bd3a32e770aa934f715dd70b4a2b5f8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856003"
---
# <a name="discovery-find-and-findcriteria"></a>Odnajdywanie — znajdowanie i kryteria znajdowania
Operacja Znajdź odnajdywania jest inicjowane przez klienta, aby dowiedzieć się, co najmniej jednej usługi i jest jednym z głównych działań podczas odnajdywania. Wykonywanie Znajdź wysyła komunikat sondowania usługi WS-Discovery za pośrednictwem sieci. Usługi, które spełniają kryteria określone odpowiedzi przy użyciu protokołu WS Discovery ProbeMatch komunikatów. Aby uzyskać więcej informacji na temat odnajdywania wiadomości zobacz [specyfikacji WS-Discovery](https://go.microsoft.com/fwlink/?LinkID=122347).  
  
## <a name="discoveryclient"></a>Klasa DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Klasa udostępnia mechanizm do wykonywania operacji wyszukiwania i sprawia, że wykonywanie operacji klienta odnajdywania jest łatwe. Zawiera <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody, która wykonuje synchroniczne (blokowanie) Znajdź, a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody, która inicjuje nieblokującej na poziomie znajdowanie asynchroniczne. Obie metody przyjmują <xref:System.ServiceModel.Discovery.FindCriteria> parametru i podaj wyniki za pośrednictwem <xref:System.ServiceModel.Discovery.FindResponse> obiektu.  
  
## <a name="findcriteria"></a>Kryteria znajdowania  
 <xref:System.ServiceModel.Discovery.FindCriteria> ma kilka właściwości, które mogą być grupowane w kryteria wyszukiwania, które określają, jakie usługi, którego szukasz, i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać). Element <xref:System.ServiceModel.Discovery.FindCriteria> może zawierać wiele kryteriów wyszukiwania. Domyślnie usługa ma do dopasowywania wszystkich składników w przeciwnym razie nie uważa się zgodnych usług. Jeśli chcesz znaleźć usługi spełniające tylko niektóre kryteria, można zaimplementować logikę niestandardowego wyszukiwania w usłudze, lub można użyć wielu zapytań.  
  
 Kryteria wyszukiwania, obejmują:  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> — Opcjonalne. Nazwa kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi. Jeżeli określono więcej niż jedną nazwę kontraktu, Odpowiedz tylko punkty końcowe usługi dopasowanie wszystkich umów. Należy pamiętać, że w programie WCF punkt końcowy może obsługiwać tylko jednego kontraktu.  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> — Opcjonalne. Zakresy są bezwzględne identyfikatory URI, które służą do kategoryzowania indywidualnych punktów końcowych usługi. Można skorzystać z tej w scenariuszach, gdzie wiele punktów końcowych udostępnić ten sam kontrakt i chcesz sposobem wyszukiwania dla podzbioru punktów końcowych. Jeżeli określono więcej niż jednego zakresu, Odpowiedz tylko punkty końcowe usługi dopasowanie wszystkich zakresów.  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> -Określa algorytm dopasowania do użycia podczas dopasowywania zakresów w wiadomości sondy z tym punktem końcowym. Istnieje pięć obsługiwanych reguł dopasowania w zakresie:  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> uwzględniana wielkość liter podstawowego ciągu porównania.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> Dopasowuje przez segmenty oddzielone "/". Wyszukiwanie http://contoso/building1 jest zgodny z zakresem usługi http://contoso/building/floor1. Należy zauważyć, że nie jest zgodny http://contoso/building100 ponieważ ostatnie dwa segmenty nie są zgodne.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> Dopasowuje zakresy segmentami przy użyciu adresu URL protokołu LDAP.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> Dopasowuje dokładnie za pomocą ciągu identyfikatora UUID zakresów.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> zastępuje tylko te usługi, które nie określają zakres.  
  
     Jeśli nie określono regułę dopasowania w zakresie, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> jest używany.  
  
 Kryteriów zakończenia obejmują:  
  
1.  <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> — Maksymalny czas oczekiwania na odpowiedzi z usług w sieci. Domyślny czas trwania wynosi 20 sekund.  
  
2.  <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Maksymalna liczba odpowiedzi oczekiwania. Jeśli <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> odpowiedzi są odbierane przed <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> upłynął zakończenia operacji wyszukiwania.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> ma <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> właściwość kolekcji, która zawiera wszystkie odpowiedzi wysyłane przez dopasowanie usług w sieci. Jeśli użytkownik ma usług, Kolekcja jest pusta. Jeśli co najmniej jedna usługa udzielił odpowiedzi, odpowiedź jest przechowywany w <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> obiekt, który zawiera adres, kontrakt i dodatkowe informacje o usłudze.  
  
 Poniższy przykład pokazuje sposób wykonywania operacji wyszukiwania w kodzie.  
  
```  
// Create DiscoveryClient  
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
// Create FindCriteria  
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));  
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));  
findCriteria.Duration = TimeSpan.FromSeconds(10);   
  
// Find ICalculatorService endpoints              
FindResponse findResponse = discoveryClient.Find(findCriteria);  
  
Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Używanie kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Odnajdywanie z zakresami](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Znajdowanie asynchroniczne](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [Podstawy](../../../../docs/framework/wcf/samples/basic-sample.md)
