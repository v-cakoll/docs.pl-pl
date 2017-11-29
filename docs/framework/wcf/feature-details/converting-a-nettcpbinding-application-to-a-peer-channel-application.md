---
title: "Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 532171dfeba965ae30dc92f31448cf38964fc695
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
Można utworzyć połączenia między klientami przy użyciu [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] za pomocą powiązania, które opisują parametry połączenia. Konwertowanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji do korzystania z połączeń peer-to-peer wymaga powiązania, które obsługuje tę technologię, podczas tworzenia połączenia klienta. Kanał elementu równorzędnego zapewnia powiązanie o nazwie <xref:System.ServiceModel.NetPeerTcpBinding>, którego można użyć w podobny sposób jak <xref:System.ServiceModel.NetTcpBinding>. Podstawowe różnice obejmują określanie usługi rozpoznawania nazw oraz definiowanie ustawień zabezpieczeń.  
  
 Jeśli aplikacja używa ustawień zabezpieczeń i domyślny program rozpoznawania nazw, konwertowanie normalne klienta/serwera aplikacji sieci do używania kanału równorzędnego pociąga za sobą zmiana nazwy powiązania z "NetTcpBinding" do "NetPeerTcpBinding" w aplikacji plik konfiguracji — nie trzeba zmieniać bazy kodu aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
