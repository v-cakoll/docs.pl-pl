---
title: 'Instrukcje: Ustalanie wersji odnajdywania żądania sondowania'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8fbc3936278a5c6f403f48b59390c69c64378004
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425268"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Instrukcje: Ustalanie wersji odnajdywania żądania sondowania

Serwera proxy odnajdywania może narazić wiele odnajdywania punktów końcowych przy użyciu odnajdywania w różnych wersjach. Gdy multiemisji UDP żądania sondowania dociera do serwera proxy, serwer proxy powinien odpowiedzieć za pomocą komunikatów multiemisji pomijania. Aby to zrobić, jego musi znać wersji odnajdywania żądania.

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Można określić wersji odnajdywania żądania sondowania

W metodzie, która odpowiada na żądania sondowania (na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) używa się statycznej <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> właściwości, aby wyszukać <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, jak pokazano w poniższym kodzie.

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [Implementowanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
