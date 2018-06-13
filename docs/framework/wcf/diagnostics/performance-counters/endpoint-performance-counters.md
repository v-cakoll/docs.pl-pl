---
title: Liczniki wydajności w punkcie końcowym
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 8354cff600f8c16a5ab9b4f6efd3c0b93a46276c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803140"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="357b4-102">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="357b4-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="357b4-103">Liczniki wydajności punktu końcowego przechwytywania danych, który pokazuje, jak punkt końcowy jest akceptowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="357b4-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="357b4-104">Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="357b4-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="357b4-105">Wystąpienia są nazywane użycia tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="357b4-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="357b4-106">Dane przypomina gromadzone dla poszczególnych działań, ale tylko jest agregowana przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="357b4-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="357b4-107">Istnieje limit na długość nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="357b4-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="357b4-108">Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF Zamienia część nazwy wystąpienia wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="357b4-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357b4-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="357b4-109">See Also</span></span>  
 [<span data-ttu-id="357b4-110">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="357b4-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
