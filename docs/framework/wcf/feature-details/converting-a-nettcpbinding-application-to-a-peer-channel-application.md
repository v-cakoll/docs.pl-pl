---
title: Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: b89afbe59b73288ba357fa55ec5d55c1fb18352b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582789"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
Można utworzyć połączenia między klientami przy użyciu [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] za pomocą powiązania, które opisują parametrów połączenia. Konwertowanie aplikacji .NET Framework, aby używały połączeń peer-to-peer wymaga powiązania, które obsługuje tę technologię, podczas nawiązywania połączeń klientów. Kanał elementu równorzędnego zapewnia powiązanie o nazwie <xref:System.ServiceModel.NetPeerTcpBinding>, którego można używać w podobny sposób jak <xref:System.ServiceModel.NetTcpBinding>. Podstawowe różnice obejmują określanie usługi rozpoznawania nazw oraz definiowanie ustawień zabezpieczeń.  
  
 Jeśli aplikacja używa ustawień zabezpieczeń i domyślny mechanizm rozwiązywania konfliktów, konwertowania normalne aplikacji opartego na kliencie/server do korzystania z kanału równorzędnego pociąga za sobą zmiana nazwy powiązania z "NetTcpBinding" do "NetPeerTcpBinding" w aplikacji plik konfiguracji — nie trzeba zmienić podstawowego kodu aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
