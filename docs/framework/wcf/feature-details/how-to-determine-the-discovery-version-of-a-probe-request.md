---
title: 'Instrukcje: Ustalanie wersji odnajdywania żądania sondowania'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 2b7e42714ae1d16a84bcb6f0fc79cf5b376a7a16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595417"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Instrukcje: Ustalanie wersji odnajdywania żądania sondowania

Serwer proxy odnajdywania może uwidaczniać wiele punktów końcowych odnajdywania przy użyciu różnych wersji odnajdowania. Po odebraniu żądania sondowania multiemisji UDP na serwerze proxy serwer proxy powinien odpowiedzieć na komunikat o pominięciu multiemisji. W tym celu należy znać wersję odnajdowania żądania.

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Aby określić wersję odnajdywania żądania sondowania

W metodzie, która reaguje na żądanie sondowania (na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ), użyj <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> właściwości statycznej do wyszukania <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , jak pokazano w poniższym kodzie.

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [Implementowanie serwera proxy odnajdywania](implementing-a-discovery-proxy.md)
