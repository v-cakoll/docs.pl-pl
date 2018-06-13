---
title: 'Instrukcje: Ustalanie wersji odnajdywania żądania sondowania'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8ac9804b0fe46ca5fbe580d713ec82a2f9bb0128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489784"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Instrukcje: Ustalanie wersji odnajdywania żądania sondowania
Serwer proxy odnajdywania może narazić wiele odnajdywania punktów końcowych przy użyciu odnajdywania w różnych wersjach. Gdy multiemisji UDP żądania sondowania dociera do serwera proxy, który serwer proxy powinien odpowiadać, podając komunikat o pominięciu multiemisji. W tym celu byłyby wiedzieć wersji odnajdywania żądania.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Można ustalić wersji odnajdywania żądania sondowania  
  
1.  W metodzie, która odpowiada na żądania sondowania (na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) Użyj statycznych <xref:System.ServiceModel.OperationContext.Current%2A> właściwości, aby wyszukać <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> jak pokazano w poniższym kodzie.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [Implementowanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [Przykład serwera proxy odnajdywania](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
