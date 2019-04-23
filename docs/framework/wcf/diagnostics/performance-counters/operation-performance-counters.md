---
title: Liczniki wydajności operacji
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: d4f5755129fecb62e6a4da98a2bf642c5e20f9c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077111"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="bdc78-102">Liczniki wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="bdc78-102">Operation Performance Counters</span></span>
<span data-ttu-id="bdc78-103">Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="bdc78-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="bdc78-104">Każda operacja ma poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="bdc78-104">Each operation has an individual instance.</span></span> <span data-ttu-id="bdc78-105">Oznacza to jeśli danego kontraktu operacje 10, 10 wystąpień licznika operacji skojarzonych z tej Umowy.</span><span class="sxs-lookup"><span data-stu-id="bdc78-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="bdc78-106">Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="bdc78-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="bdc78-107">Ten licznik umożliwia pomiar sposobu używania wywołania i jak dobrze działa operacja.</span><span class="sxs-lookup"><span data-stu-id="bdc78-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="bdc78-108">Obowiązuje limit długości nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="bdc78-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="bdc78-109">Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia z wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="bdc78-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc78-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdc78-110">See also</span></span>

- [<span data-ttu-id="bdc78-111">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="bdc78-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
