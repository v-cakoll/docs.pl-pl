---
title: Przechowywanie wersji odnajdywania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5a15f740e9db4eb58ec4e410db9ef5e014fe0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-versioning"></a>Przechowywanie wersji odnajdywania
Ten temat zawiera krótki przegląd wdrożenia niektóre nowe funkcje odnajdywania. Również zawiera omówienie dotyczące wybierz wersję odnajdywania do użycia.  
  
## <a name="discovery-versioning"></a>Przechowywanie wersji odnajdywania  
 Funkcja odnajdowania obsługuje trzy wersje protokołu WS_Discovery. Odnajdywanie interfejsów API umożliwiają wybierz, która wersja protokołu, którego chcesz użyć. Tym dokumencie krótko opisano ustawienia związane z kontroli wersji.  
  
 Następujące klasy odnajdywania teraz mają <xref:System.ServiceModel.Discovery.DiscoveryVersion> właściwości i podejmij <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument w swoich konstruktorach:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion.WSDiscoveryApril2005  
 Zapewnianie <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> jako konstruktora parametru zapewnia wdrożenia przy użyciu wersji April2005 protokołu WS-Discovery. Ta wersja odpowiada opublikowana wersja specyfikacji protokołu WS-Discovery. Współdziałanie z starszych aplikacji przy użyciu wersji April2005 WS-Discovery należy używać tej wersji.  
  
### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion.WSDiscovery11  
 Domyślną wersję odnajdywania używanych przez interfejsy API <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>. Jest to bieżąca wersja protokołu WS-Discovery standardowych.  
  
## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion.WSDiscoveryCD1  
 Zapewnianie <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> jak wdrożenia, użyj parametru konstruktora Komitetu projekt 1 wersja protokołu WS-Discovery. Współdziałanie z dysku CD 1 wersją protokołu WS-Discovery implementacje powinny używać tej wersji protokołu.  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>Obsługa wielu punktów końcowych odnajdywania protokołu UDP dla wersji odnajdywania inny na hoście z jednej usługi  
 Warto udostępnić wiele punktów końcowych odnajdywania protokołu UDP dla wersji odnajdywania inny na hoście z jednej usługi. W tym celu należy określić unikatowy adres dla każdego punktu końcowego odnajdywania protokołu UDP. W przykładzie poniżej pokazano, jak to zrobić.  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
