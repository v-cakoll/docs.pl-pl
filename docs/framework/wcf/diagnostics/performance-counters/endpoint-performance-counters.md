---
title: Liczniki wydajności w punkcie końcowym
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 1b0f7462fea8843bcb0a0938a8034f405f30a6fb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320515"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="7664c-102">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="7664c-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="7664c-103">Liczniki wydajności punktów końcowych przechwytują dane, które ujawniają, w jaki sposób punkt końcowy akceptuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="7664c-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="7664c-104">Można je znaleźć w obiekcie wydajności `ServiceModelEndpoint 4.0.0.0` podczas wyświetlania z monitorem wydajności.</span><span class="sxs-lookup"><span data-stu-id="7664c-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="7664c-105">Wystąpienia są nazwane przy użyciu tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="7664c-105">The instances are named using this pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 <span data-ttu-id="7664c-106">Dane są podobne do tych zebranych dla poszczególnych operacji, ale są agregowane w całym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7664c-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7664c-107">Istnieje limit długości nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="7664c-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="7664c-108">Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="7664c-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7664c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7664c-109">See also</span></span>

- [<span data-ttu-id="7664c-110">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="7664c-110">Performance Counters</span></span>](index.md)
