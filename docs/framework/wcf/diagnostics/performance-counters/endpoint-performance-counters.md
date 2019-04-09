---
title: Liczniki wydajności w punkcie końcowym
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: f07e318e39a68e689ec484b09fa743623cfb51d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158395"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="fa669-102">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="fa669-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="fa669-103">Liczniki wydajności w punkcie końcowym przechwytywania danych, która ujawnia się, jak punkt końcowy jest akceptowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fa669-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="fa669-104">Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="fa669-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="fa669-105">Wystąpienia są nazywane użycia tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="fa669-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="fa669-106">Dane są podobne do zebranych dla poszczególnych działań, ale tylko jest agregowana dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fa669-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fa669-107">Obowiązuje limit długości nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="fa669-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="fa669-108">Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia z wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="fa669-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa669-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa669-109">See also</span></span>

- [<span data-ttu-id="fa669-110">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="fa669-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
