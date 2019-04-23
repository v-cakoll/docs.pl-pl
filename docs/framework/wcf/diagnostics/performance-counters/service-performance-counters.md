---
title: Liczniki wydajności usługi
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: dc31e05f82f232095f6560c8fdd9bf75c040e2ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210415"
---
# <a name="service-performance-counters"></a><span data-ttu-id="1476e-102">Liczniki wydajności usługi</span><span class="sxs-lookup"><span data-stu-id="1476e-102">Service Performance Counters</span></span>
<span data-ttu-id="1476e-103">Liczniki wydajności usługi zmierzyć zachowanie usługi jako całość i może służyć do diagnozowania wydajności całą usługę.</span><span class="sxs-lookup"><span data-stu-id="1476e-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="1476e-104">Można go znaleźć w `ServiceModelService 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="1476e-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="1476e-105">Wystąpienia są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="1476e-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="1476e-106">Obowiązuje limit długości nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="1476e-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="1476e-107">Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia z wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="1476e-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1476e-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1476e-108">See also</span></span>

- [<span data-ttu-id="1476e-109">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="1476e-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
