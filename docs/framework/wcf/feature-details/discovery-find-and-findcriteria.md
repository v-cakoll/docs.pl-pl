---
title: Odnajdywanie — znajdowanie i kryteria znajdowania
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: da4c3c4a1d765e4f91b03f4f8fc1a73c3fea1535
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964837"
---
# <a name="discovery-find-and-findcriteria"></a>Odnajdywanie — znajdowanie i kryteria znajdowania

Operacja odnajdowania odnajdywania jest inicjowana przez klienta w celu odnalezienia co najmniej jednej usługi i jest jednym z głównych działań w ramach odnajdywania. Wykonanie wyszukiwania wysyła komunikat sondy WS-Discovery przez sieć. Usługi zgodne z określonymi kryteriami odpowiadają za pomocą funkcji WS-Discovery ProbeMatch messages. Aby uzyskać więcej informacji na temat komunikatów odnajdywania, zobacz [specyfikację WS-Discovery](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).

## <a name="discoveryclient"></a>Obiekt DiscoveryClient

Klasa <xref:System.ServiceModel.Discovery.DiscoveryClient> zapewnia mechanizm wykonywania operacji znajdowania i ułatwia wykonywanie operacji odnajdywania. Zawiera metodę <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, która wykonuje (blokującą) synchroniczne wyszukiwanie i metodę <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>, która inicjuje nieblokujące asynchroniczne Znajdowanie. Obie metody przyjmują parametr <xref:System.ServiceModel.Discovery.FindCriteria> i zapewniają wyniki użytkownikowi za pomocą obiektu <xref:System.ServiceModel.Discovery.FindResponse>.

## <a name="findcriteria"></a>Kryteria znajdowania

<xref:System.ServiceModel.Discovery.FindCriteria> ma kilka właściwości, które można grupować w kryteria wyszukiwania, które określają usługi, których szukasz, i wyszukiwanie kryteriów zakończenia (jak długo wyszukiwanie powinno trwać). <xref:System.ServiceModel.Discovery.FindCriteria> może zawierać wiele kryteriów wyszukiwania. Domyślnie usługa musi dopasować wszystkie składniki, w przeciwnym razie nie uważa siebie za zgodną usługę. Aby znaleźć usługi, które pasują tylko do niektórych kryteriów, można zaimplementować niestandardowe logiki wyszukiwania w usłudze lub użyć wielu zapytań.

Kryteria wyszukiwania obejmują:

- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> — opcjonalne. Nazwa kontraktu przeszukiwanej usługi i kryteria zwykle używane podczas wyszukiwania usługi. Jeśli określono więcej niż jedną nazwę kontraktu, tylko punkty końcowe usługi pasujące do wszystkich umów odpowiadają. Należy pamiętać, że w programie WCF punkt końcowy może obsługiwać tylko jedną umowę.

- <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> — opcjonalne. Zakresy są bezwzględnymi identyfikatorami URI, które są używane do kategoryzowania poszczególnych punktów końcowych usługi. Może być konieczne użycie tego w scenariuszach, w których wiele punktów końcowych uwidacznia ten sam kontrakt i chcesz wyszukać podzestaw punktów końcowych. Jeśli określono więcej niż jeden zakres, tylko punkty końcowe usługi pasujące do wszystkich zakresów odpowiadają.

- <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> — określa zgodny algorytm, który ma być używany podczas dopasowywania zakresów w komunikacie sondy do punktu końcowego. Istnieją pięć obsługiwanych reguł dopasowania zakresu:

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> to podstawowe porównanie ciągów z uwzględnieniem wielkości liter.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> dopasowania według segmentów rozdzielonych znakiem "/". Wyszukiwanie `http://contoso/building1` jest zgodne z usługą z zakresem `http://contoso/building/floor1`. Należy zauważyć, że nie jest on zgodny z `http://contoso/building100`, ponieważ ostatnie dwa segmenty nie są zgodne.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> dopasowuje zakresy przez segmenty przy użyciu adresu URL LDAP.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> dopasowuje zakresy dokładnie przy użyciu ciągu identyfikatora UUID.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> dopasowuje tylko te usługi, które nie określają zakresu.

  Jeśli nie określono reguły dopasowywania zakresu, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> jest używana.

Kryteria zakończenia obejmują:

1. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> — maksymalny czas oczekiwania na odpowiedzi z usług w sieci. Domyślny czas trwania wynosi 20 sekund.

2. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> — Maksymalna liczba odpowiedzi do odczekania. Jeśli <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> odpowiedzi są odbierane przed upływem <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, kończy się operacja znajdowania.

## <a name="findresponse"></a>FindResponse

<xref:System.ServiceModel.Discovery.FindResponse> ma właściwość kolekcji <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A>, która zawiera odpowiedzi wysyłane przez pasujące usługi w sieci. Jeśli żadna usługa nie odpowiedziała, kolekcja jest pusta. Jeśli co najmniej jedna usługa odpowiedziała, Każda odpowiedź jest przechowywana w obiekcie <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, który zawiera adres, kontrakt i dodatkowe informacje dotyczące usługi.

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

## <a name="see-also"></a>Zobacz także

- [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Używanie kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
- [Odnajdywanie z zakresami](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Podstawy](../../../../docs/framework/wcf/samples/basic-sample.md)
