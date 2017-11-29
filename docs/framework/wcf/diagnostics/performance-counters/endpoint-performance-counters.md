---
title: "Liczniki wydajności w punkcie końcowym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d34df7c70e0edeef831843d9afcb2db32422ebe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="b16cf-102">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="b16cf-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="b16cf-103">Liczniki wydajności punktu końcowego przechwytywania danych, który pokazuje, jak punkt końcowy jest akceptowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b16cf-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="b16cf-104">Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="b16cf-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="b16cf-105">Wystąpienia są nazywane użycia tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="b16cf-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="b16cf-106">Dane przypomina gromadzone dla poszczególnych działań, ale tylko jest agregowana przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="b16cf-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b16cf-107">Istnieje limit na długość nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="b16cf-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="b16cf-108">Gdy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nazwę wystąpienia licznika przekracza maksymalną długość [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Zamienia część nazwy wystąpienia wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="b16cf-108">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16cf-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b16cf-109">See Also</span></span>  
 [<span data-ttu-id="b16cf-110">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="b16cf-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
