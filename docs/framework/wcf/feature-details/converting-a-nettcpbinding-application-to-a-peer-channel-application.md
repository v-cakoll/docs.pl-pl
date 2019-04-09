---
title: Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 2daeb28ee984e6df576fc3da0aacc9d5f7497c96
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077501"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
Można utworzyć połączenia między klientami przy użyciu [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] za pomocą powiązania, które opisują parametrów połączenia. Konwertowanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji do korzystania z połączeń peer-to-peer wymaga powiązania, które obsługuje tę technologię, podczas nawiązywania połączenia klienta. Kanał elementu równorzędnego zapewnia powiązanie o nazwie <xref:System.ServiceModel.NetPeerTcpBinding>, którego można używać w podobny sposób jak <xref:System.ServiceModel.NetTcpBinding>. Podstawowe różnice obejmują określanie usługi rozpoznawania nazw oraz definiowanie ustawień zabezpieczeń.  
  
 Jeśli aplikacja używa ustawień zabezpieczeń i domyślny mechanizm rozwiązywania konfliktów, konwertowania normalne aplikacji opartego na kliencie/server do korzystania z kanału równorzędnego pociąga za sobą zmiana nazwy powiązania z "NetTcpBinding" do "NetPeerTcpBinding" w aplikacji plik konfiguracji — nie trzeba zmienić podstawowego kodu aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [Wiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
