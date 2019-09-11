---
title: Liczniki wydajności usługi
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 4ce0efbeb0a1d6f2409bb976102b8ec8821d5cdc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848998"
---
# <a name="service-performance-counters"></a><span data-ttu-id="38871-102">Liczniki wydajności usługi</span><span class="sxs-lookup"><span data-stu-id="38871-102">Service Performance Counters</span></span>
<span data-ttu-id="38871-103">Liczniki wydajności usługi mierzą zachowanie usługi jako całość i mogą służyć do diagnozowania wydajności całej usługi.</span><span class="sxs-lookup"><span data-stu-id="38871-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="38871-104">Można je znaleźć w `ServiceModelService 4.0.0.0` obiekcie wydajności podczas wyświetlania z monitorem wydajności (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="38871-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="38871-105">Wystąpienia są nazwane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="38871-105">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="38871-106">Istnieje limit długości nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="38871-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="38871-107">Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="38871-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38871-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38871-108">See also</span></span>

- [<span data-ttu-id="38871-109">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="38871-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
