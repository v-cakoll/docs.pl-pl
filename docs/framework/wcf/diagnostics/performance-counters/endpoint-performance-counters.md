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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 157f0cc5d860841940b0850ca3895f82a12d47ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="e383f-102">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="e383f-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="e383f-103">Liczniki wydajności punktu końcowego przechwytywania danych, który pokazuje, jak punkt końcowy jest akceptowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e383f-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="e383f-104">Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="e383f-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="e383f-105">Wystąpienia są nazywane użycia tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="e383f-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="e383f-106">Dane przypomina gromadzone dla poszczególnych działań, ale tylko jest agregowana przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="e383f-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e383f-107">Istnieje limit na długość nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="e383f-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="e383f-108">Gdy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nazwę wystąpienia licznika przekracza maksymalną długość [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Zamienia część nazwy wystąpienia wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="e383f-108">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e383f-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e383f-109">See Also</span></span>  
 [<span data-ttu-id="e383f-110">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="e383f-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
