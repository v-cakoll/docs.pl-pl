---
title: 'Instrukcje: Ustalanie wersji odnajdywania żądania sondowania'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 6bd112be311eb9397ad89801be5358d67c7499fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332277"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Instrukcje: Ustalanie wersji odnajdywania żądania sondowania
Serwera proxy odnajdywania może narazić wiele odnajdywania punktów końcowych przy użyciu odnajdywania w różnych wersjach. Gdy multiemisji UDP żądania sondowania dociera do serwera proxy, należy odpowiedzieć przy użyciu komunikatów multiemisji pomijanie dla serwera proxy. Aby to zrobić, to będzie trzeba znać wersji odnajdywania żądania.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Można określić wersji odnajdywania żądania sondowania  
  
1. W metodzie, która odpowiada na żądania sondowania (na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) używa się statycznej <xref:System.ServiceModel.OperationContext.Current%2A> właściwości, aby wyszukać <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> jak pokazano w poniższym kodzie.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [Implementowanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
