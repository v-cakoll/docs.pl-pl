---
title: Liczniki wydajności w punkcie końcowym
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 72512a15d5b378b1ccb65995441f8f67e251febb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856100"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="58585-102">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="58585-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="58585-103">Liczniki wydajności punktów końcowych przechwytują dane, które ujawniają, w jaki sposób punkt końcowy akceptuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="58585-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="58585-104">Można je znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekcie wydajności podczas wyświetlania z monitorem wydajności.</span><span class="sxs-lookup"><span data-stu-id="58585-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="58585-105">Wystąpienia są nazwane przy użyciu tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="58585-105">The instances are named using this pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 <span data-ttu-id="58585-106">Dane są podobne do tych zebranych dla poszczególnych operacji, ale są agregowane w całym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="58585-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="58585-107">Istnieje limit długości nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="58585-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="58585-108">Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="58585-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58585-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58585-109">See also</span></span>

- [<span data-ttu-id="58585-110">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="58585-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
