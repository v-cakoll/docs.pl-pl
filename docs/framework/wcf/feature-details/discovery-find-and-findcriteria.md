---
title: Odnajdywanie — znajdowanie i kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: 70739647ac5904159b71121e86aa98e92981d4ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495323"
---
# <a name="discovery-find-and-findcriteria"></a>Odnajdywanie — znajdowanie i kryteria znajdowania
Operacja find odnajdywania jest inicjowane przez klienta, aby dowiedzieć się, co najmniej jednej usługi i jest jednym z głównych działań podczas odnajdywania. Wykonywanie Znajdź wysyła komunikat sondowania usługi WS-Discovery za pośrednictwem sieci. Usługi, które spełniają kryteria określone odpowiedzi z wiadomości WS-Discovery ProbeMatch. Aby uzyskać więcej informacji na temat wiadomości odnajdywania, zobacz [specyfikacji WS-Discovery](http://go.microsoft.com/fwlink/?LinkID=122347).  
  
## <a name="discoveryclient"></a>Obiekt DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Klasa udostępnia mechanizm do wykonania operacji wyszukiwania i umożliwia wykonywanie operacji klienta odnajdywania łatwe. Zawiera on <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodę, która wykonuje (blokowanie) find synchroniczne, a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metodę, która inicjuje nieblokujące znajdowanie asynchroniczne. Obie metody przyjmują <xref:System.ServiceModel.Discovery.FindCriteria> parametru i podaj wyniki za pośrednictwem <xref:System.ServiceModel.Discovery.FindResponse> obiektu.  
  
## <a name="findcriteria"></a>Kryteria znajdowania  
 <xref:System.ServiceModel.Discovery.FindCriteria> ma kilka właściwości, które można grupować w kryteria wyszukiwania, które określają, jakie usługi, którego szukasz, oraz zapoznać się z kryteriów zakończenia (jak długo wyszukiwanie powinno trwać). A <xref:System.ServiceModel.Discovery.FindCriteria> może zawierać wiele kryteriów wyszukiwania. Domyślnie usługa musi odpowiadać wszystkich składników w przeciwnym razie go nie uważa się pasującego usługi. Jeśli chcesz znaleźć usługi spełniające tylko niektóre kryteria, można zaimplementować Znajdź niestandardowej logiki w usłudze lub można użyć wielu zapytań.  
  
 Kryteria wyszukiwania, obejmują:  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> -Opcjonalne. Nazwa kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi. Jeśli określono więcej niż jedną nazwę kontraktu, Odpowiedz, tylko punktów końcowych usługi dopasowania wszystkich umów. Należy pamiętać, że w programie WCF punktu końcowego może obsługiwać tylko jeden kontrakt.  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> -Opcjonalne. Zakresy są bezwzględne klasyfikowania punktów końcowych usługi poszczególnych identyfikatorów URI. Możesz użyć tej funkcji w scenariuszach, w której wiele punktów końcowych narazić ten sam kontrakt, i chcesz sposobem wyszukiwania dla podzbioru punktów końcowych. Jeśli określono więcej niż jednego zakresu, Odpowiedz, tylko punktów końcowych usługi dopasowania wszystkich zakresów.  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> — Określa algorytm dopasowania do użycia podczas dopasowywania zakresów w wiadomości sondy z tym punktem końcowym. Istnieją pięć obsługiwane reguły dopasowywania w zakresie:  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> rozróżniana wielkość liter podstawowego ciągu porównania.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> dopasowań przez segmenty oddzielone "/". Wyszukiwanie http://contoso/building1 zgodny z zakresem usługi http://contoso/building/floor1. Należy pamiętać, że nie odpowiada http://contoso/building100 ponieważ ostatnie dwa segmenty nie są zgodne.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> Dopasowuje zakresy segmentami przy użyciu adresu URL protokołu LDAP.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> Dopasowuje zakresy dokładnie przy użyciu ciągu identyfikatora UUID.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> jest zgodna tylko tych usług, które nie określają zakres.  
  
     Jeśli nie zostanie określona reguła dopasowywania zakresu, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> jest używany.  
  
 Kończenie działania obejmują:  
  
1.  <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> -Maksymalny czas oczekiwania na odpowiedzi z usług w sieci. Czas domyślny to 20 sekund.  
  
2.  <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> -Maksymalną liczbę odpowiedzi oczekiwania. Jeśli <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> odpowiedzi są odbierane przed <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> upłynął zakończenia operacji wyszukiwania.  
  
## <a name="findresponse"></a>Obiektu FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> ma <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> właściwości kolekcji, która zawiera wszystkie odpowiedzi wysyłane przez dopasowanie usług w sieci. Jeśli usługi nie odpowiedział, Kolekcja jest pusta. Jeśli co najmniej jedną usługę odpowiedzi, odpowiedź jest przechowywany w <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> obiekt, który zawiera adres, kontrakt i dodatkowe informacje o usłudze.  
  
 Poniższy przykład przedstawia sposób wykonywania operacji wyszukiwania w kodzie.  
  
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
