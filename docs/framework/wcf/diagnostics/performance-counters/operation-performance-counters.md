---
title: Liczniki wydajności operacji
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 46b7d5ff071ebf1e3f790a9b56906d9908028ae9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804420"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="94d73-102">Liczniki wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="94d73-102">Operation Performance Counters</span></span>
<span data-ttu-id="94d73-103">Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="94d73-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="94d73-104">Każda operacja wymaga poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="94d73-104">Each operation has an individual instance.</span></span> <span data-ttu-id="94d73-105">Oznacza to jeśli dany kontrakt operacji 10, 10 wystąpień licznika operacji są skojarzone z tej Umowy.</span><span class="sxs-lookup"><span data-stu-id="94d73-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="94d73-106">Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="94d73-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="94d73-107">Ten licznik umożliwia pomiarów sposobu używania połączenia i jak wykonywanie operacji.</span><span class="sxs-lookup"><span data-stu-id="94d73-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="94d73-108">Istnieje limit na długość nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="94d73-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="94d73-109">Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF Zamienia część nazwy wystąpienia wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="94d73-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d73-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94d73-110">See Also</span></span>  
 [<span data-ttu-id="94d73-111">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="94d73-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
