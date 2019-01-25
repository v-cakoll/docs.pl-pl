---
title: 'Instrukcje: Ustalanie wersji odnajdywania żądania sondowania'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 356ddd76bdee0698fa446d830791f702af5742b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595126"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="a5bea-102">Instrukcje: Ustalanie wersji odnajdywania żądania sondowania</span><span class="sxs-lookup"><span data-stu-id="a5bea-102">How to:Determine the Discovery Version of a Probe Request</span></span>
<span data-ttu-id="a5bea-103">Serwera proxy odnajdywania może narazić wiele odnajdywania punktów końcowych przy użyciu odnajdywania w różnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="a5bea-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="a5bea-104">Gdy multiemisji UDP żądania sondowania dociera do serwera proxy, należy odpowiedzieć przy użyciu komunikatów multiemisji pomijanie dla serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a5bea-104">When a UDP multicast Probe request arrives at the proxy the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="a5bea-105">Aby to zrobić, to będzie trzeba znać wersji odnajdywania żądania.</span><span class="sxs-lookup"><span data-stu-id="a5bea-105">In order to do this it would have to know the discovery version of the request.</span></span>  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="a5bea-106">Można określić wersji odnajdywania żądania sondowania</span><span class="sxs-lookup"><span data-stu-id="a5bea-106">To Determine the Discovery Version of a Probe Request</span></span>  
  
1.  <span data-ttu-id="a5bea-107">W metodzie, która odpowiada na żądania sondowania (na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) używa się statycznej <xref:System.ServiceModel.OperationContext.Current%2A> właściwości, aby wyszukać <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a5bea-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) use the static <xref:System.ServiceModel.OperationContext.Current%2A> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> as shown in the following code.</span></span>  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a5bea-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5bea-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="a5bea-109">Implementowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="a5bea-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
