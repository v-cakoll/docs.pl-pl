---
title: 'Instrukcje: Ustalanie wersji odnajdywania żądania sondowania'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 2b7e42714ae1d16a84bcb6f0fc79cf5b376a7a16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595417"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="38382-102">Instrukcje: Ustalanie wersji odnajdywania żądania sondowania</span><span class="sxs-lookup"><span data-stu-id="38382-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="38382-103">Serwer proxy odnajdywania może uwidaczniać wiele punktów końcowych odnajdywania przy użyciu różnych wersji odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="38382-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="38382-104">Po odebraniu żądania sondowania multiemisji UDP na serwerze proxy serwer proxy powinien odpowiedzieć na komunikat o pominięciu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="38382-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="38382-105">W tym celu należy znać wersję odnajdowania żądania.</span><span class="sxs-lookup"><span data-stu-id="38382-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="38382-106">Aby określić wersję odnajdywania żądania sondowania</span><span class="sxs-lookup"><span data-stu-id="38382-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="38382-107">W metodzie, która reaguje na żądanie sondowania (na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ), użyj <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> właściwości statycznej do wyszukania <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="38382-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="38382-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38382-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="38382-109">Implementowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="38382-109">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
