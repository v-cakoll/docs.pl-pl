---
title: Liczniki wydajności w punkcie końcowym
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: de750b3e5ee61b6bfc5b387fb7de84b74171d8d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501964"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="35164-102">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="35164-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="35164-103">Liczniki wydajności w punkcie końcowym przechwytywania danych, która ujawnia się, jak punkt końcowy jest akceptowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="35164-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="35164-104">Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="35164-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="35164-105">Wystąpienia są nazywane użycia tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="35164-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="35164-106">Dane są podobne do zebranych dla poszczególnych działań, ale tylko jest agregowana dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="35164-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="35164-107">Obowiązuje limit długości nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="35164-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="35164-108">Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia z wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="35164-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35164-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35164-109">See also</span></span>
- [<span data-ttu-id="35164-110">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="35164-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
