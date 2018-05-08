---
title: Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 9cc73beeffc9daa9883832b3a6bedd0ff438095c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
Można utworzyć połączenia między klientami przy użyciu [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] za pomocą powiązania, które opisują parametry połączenia. Konwertowanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji do korzystania z połączeń peer-to-peer wymaga powiązania, które obsługuje tę technologię, podczas tworzenia połączenia klienta. Kanał elementu równorzędnego zapewnia powiązanie o nazwie <xref:System.ServiceModel.NetPeerTcpBinding>, którego można użyć w podobny sposób jak <xref:System.ServiceModel.NetTcpBinding>. Podstawowe różnice obejmują określanie usługi rozpoznawania nazw oraz definiowanie ustawień zabezpieczeń.  
  
 Jeśli aplikacja używa ustawień zabezpieczeń i domyślny program rozpoznawania nazw, konwertowanie normalne klienta/serwera aplikacji sieci do używania kanału równorzędnego pociąga za sobą zmiana nazwy powiązania z "NetTcpBinding" do "NetPeerTcpBinding" w aplikacji plik konfiguracji — nie trzeba zmieniać bazy kodu aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
