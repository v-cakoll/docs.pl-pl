---
title: Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 2daeb28ee984e6df576fc3da0aacc9d5f7497c96
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857299"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="065a0-102">Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="065a0-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="065a0-103">Można utworzyć połączenia między klientami przy użyciu [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] za pomocą powiązania, które opisują parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="065a0-103">You can create connections between clients using the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="065a0-104">Konwertowanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji do korzystania z połączeń peer-to-peer wymaga powiązania, które obsługuje tę technologię, podczas nawiązywania połączenia klienta.</span><span class="sxs-lookup"><span data-stu-id="065a0-104">Converting a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="065a0-105">Kanał elementu równorzędnego zapewnia powiązanie o nazwie <xref:System.ServiceModel.NetPeerTcpBinding>, którego można używać w podobny sposób jak <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="065a0-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="065a0-106">Podstawowe różnice obejmują określanie usługi rozpoznawania nazw oraz definiowanie ustawień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="065a0-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="065a0-107">Jeśli aplikacja używa ustawień zabezpieczeń i domyślny mechanizm rozwiązywania konfliktów, konwertowania normalne aplikacji opartego na kliencie/server do korzystania z kanału równorzędnego pociąga za sobą zmiana nazwy powiązania z "NetTcpBinding" do "NetPeerTcpBinding" w aplikacji plik konfiguracji — nie trzeba zmienić podstawowego kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="065a0-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065a0-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="065a0-108">See also</span></span>

- [<span data-ttu-id="065a0-109">Tworzenie aplikacji kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="065a0-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [<span data-ttu-id="065a0-110">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="065a0-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
