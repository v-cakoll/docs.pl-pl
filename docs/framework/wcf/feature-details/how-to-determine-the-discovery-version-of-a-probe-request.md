---
title: 'Instrukcje: Ustalanie wersji odnajdywania żądania sondowania'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8fbc3936278a5c6f403f48b59390c69c64378004
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425268"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="f17ee-102">Instrukcje: Ustalanie wersji odnajdywania żądania sondowania</span><span class="sxs-lookup"><span data-stu-id="f17ee-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="f17ee-103">Serwera proxy odnajdywania może narazić wiele odnajdywania punktów końcowych przy użyciu odnajdywania w różnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="f17ee-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="f17ee-104">Gdy multiemisji UDP żądania sondowania dociera do serwera proxy, serwer proxy powinien odpowiedzieć za pomocą komunikatów multiemisji pomijania.</span><span class="sxs-lookup"><span data-stu-id="f17ee-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="f17ee-105">Aby to zrobić, jego musi znać wersji odnajdywania żądania.</span><span class="sxs-lookup"><span data-stu-id="f17ee-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="f17ee-106">Można określić wersji odnajdywania żądania sondowania</span><span class="sxs-lookup"><span data-stu-id="f17ee-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="f17ee-107">W metodzie, która odpowiada na żądania sondowania (na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) używa się statycznej <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> właściwości, aby wyszukać <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f17ee-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="f17ee-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f17ee-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="f17ee-109">Implementowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="f17ee-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
