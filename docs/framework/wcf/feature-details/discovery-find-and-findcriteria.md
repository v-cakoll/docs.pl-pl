---
title: Odnajdywanie — znajdowanie i kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: 1d6a0e3fcca45c3fe57aab84b0f2b6b86fabb404
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599181"
---
# <a name="discovery-find-and-findcriteria"></a>Odnajdywanie — znajdowanie i kryteria znajdowania

Operacja odnajdowania odnajdywania jest inicjowana przez klienta w celu odnalezienia co najmniej jednej usługi i jest jednym z głównych działań w ramach odnajdywania. Wykonanie wyszukiwania wysyła komunikat sondy WS-Discovery przez sieć. Usługi zgodne z określonymi kryteriami odpowiadają za pomocą funkcji WS-Discovery ProbeMatch messages. Aby uzyskać więcej informacji na temat komunikatów odnajdywania, zobacz [specyfikację WS-Discovery](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).

## <a name="discoveryclient"></a>Obiekt DiscoveryClient

<xref:System.ServiceModel.Discovery.DiscoveryClient>Klasa udostępnia mechanizm wykonywania operacji znajdowania i ułatwia wykonywanie operacji w ramach klienta odnajdowania. Zawiera ona <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodę, która wykonuje (blokującą) synchroniczne wyszukiwanie i <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metodę, która inicjuje nieblokujące asynchroniczne Znajdowanie. Obie metody przyjmują <xref:System.ServiceModel.Discovery.FindCriteria> parametr i dostarczają wyniki do użytkownika za pomocą <xref:System.ServiceModel.Discovery.FindResponse> obiektu.

## <a name="findcriteria"></a>Kryteria znajdowania

<xref:System.ServiceModel.Discovery.FindCriteria>ma kilka właściwości, które można grupować w kryteria wyszukiwania, które określają usługi, których szukasz, i wyszukiwanie kryteriów zakończenia (jak długo wyszukiwanie powinno trwać). <xref:System.ServiceModel.Discovery.FindCriteria>Może zawierać wiele kryteriów wyszukiwania. Domyślnie usługa musi dopasować wszystkie składniki, w przeciwnym razie nie uważa siebie za zgodną usługę. Aby znaleźć usługi, które pasują tylko do niektórych kryteriów, można zaimplementować niestandardowe logiki wyszukiwania w usłudze lub użyć wielu zapytań.

Kryteria wyszukiwania obejmują:

- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>Obowiązkowe. Nazwa kontraktu przeszukiwanej usługi i kryteria zwykle używane podczas wyszukiwania usługi. Jeśli określono więcej niż jedną nazwę kontraktu, tylko punkty końcowe usługi pasujące do wszystkich umów odpowiadają. Należy pamiętać, że w programie WCF punkt końcowy może obsługiwać tylko jedną umowę.

- <xref:System.ServiceModel.Discovery.Configuration.ScopeElement>Obowiązkowe. Zakresy są bezwzględnymi identyfikatorami URI, które są używane do kategoryzowania poszczególnych punktów końcowych usługi. Może być konieczne użycie tego w scenariuszach, w których wiele punktów końcowych uwidacznia ten sam kontrakt i chcesz wyszukać podzestaw punktów końcowych. Jeśli określono więcej niż jeden zakres, tylko punkty końcowe usługi pasujące do wszystkich zakresów odpowiadają.

- <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A>-Określa zgodny algorytm, który ma być używany podczas dopasowywania zakresów w komunikacie sondy do punktu końcowego. Istnieją pięć obsługiwanych reguł dopasowania zakresu:

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>wykonuje podstawowe porównanie ciągów z uwzględnieniem wielkości liter.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType>dopasowuje się do segmentów rozdzielonych znakiem "/". Wyszukiwanie pasuje do `http://contoso/building1` usługi z zakresem `http://contoso/building/floor1` . Należy zauważyć, że nie jest to zgodne, `http://contoso/building100` ponieważ ostatnie dwa segmenty nie są zgodne.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>dopasowuje zakresy przez segmenty przy użyciu adresu URL LDAP.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>dopasowuje zakresy dokładnie przy użyciu ciągu identyfikatora UUID.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType>Dopasowuje tylko te usługi, które nie określają zakresu.

  Jeśli nie określono reguły dopasowania zakresu, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> jest używana.

Kryteria zakończenia obejmują:

1. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>— Maksymalny czas oczekiwania na odpowiedzi z usług w sieci. Domyślny czas trwania wynosi 20 sekund.

2. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>— Maksymalna liczba odpowiedzi, które należy oczekiwać. Jeśli <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> odpowiedzi są odbierane przed <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> upływem, kończy się operacja znajdowania.

## <a name="findresponse"></a>FindResponse

<xref:System.ServiceModel.Discovery.FindResponse>zawiera <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> Właściwość kolekcji, która zawiera wszystkie odpowiedzi wysyłane przez pasujące usługi w sieci. Jeśli żadna usługa nie odpowiedziała, kolekcja jest pusta. Jeśli co najmniej jedna usługa odpowiedziała, Każda odpowiedź jest przechowywana w <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> obiekcie, który zawiera adres, kontrakt i kilka dodatkowych informacji o usłudze.

Poniższy przykład pokazuje, jak wykonać operację znajdowania w kodzie.

```csharp
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

- [Omówienie odnajdywania WCF](wcf-discovery-overview.md)
- [Używanie kanału klienta odnajdywania](using-the-discovery-client-channel.md)
- [Odnajdywanie z zakresami](../samples/discovery-with-scopes-sample.md)
- [Podstawowe](../samples/basic-sample.md)
