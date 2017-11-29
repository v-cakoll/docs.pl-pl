---
title: "Instrukcje: Ustalanie wersji odnajdywania żądania sondowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ff5d45997456c12d0292176771ad3c332f6c043
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Wdrażanie serwera Proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [Przykład serwera Proxy odnajdywania](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
