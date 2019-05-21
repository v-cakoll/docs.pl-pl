---
title: Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 362945959a781fac360c42475148fee1e47a1183
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960131"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="16177-102">Konwertowanie aplikacji NetTcpBinding na aplikację kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="16177-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="16177-103">Można utworzyć połączenia między klientami za pomocą WinFX przy użyciu powiązania, które opisują parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="16177-103">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="16177-104">Konwertowanie aplikacji .NET Framework, aby używały połączeń peer-to-peer wymaga powiązania, które obsługuje tę technologię, podczas nawiązywania połączeń klientów.</span><span class="sxs-lookup"><span data-stu-id="16177-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="16177-105">Kanał elementu równorzędnego zapewnia powiązanie o nazwie <xref:System.ServiceModel.NetPeerTcpBinding>, którego można używać w podobny sposób jak <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="16177-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="16177-106">Podstawowe różnice obejmują określanie usługi rozpoznawania nazw oraz definiowanie ustawień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="16177-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="16177-107">Jeśli aplikacja używa ustawień zabezpieczeń i domyślny mechanizm rozwiązywania konfliktów, konwertowania normalne aplikacji opartego na kliencie/server do korzystania z kanału równorzędnego pociąga za sobą zmiana nazwy powiązania z "NetTcpBinding" do "NetPeerTcpBinding" w aplikacji plik konfiguracji — nie trzeba zmienić podstawowego kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16177-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16177-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16177-108">See also</span></span>

- [<span data-ttu-id="16177-109">Tworzenie aplikacji kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="16177-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [<span data-ttu-id="16177-110">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="16177-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
