---
title: "Liczniki wydajności operacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83460e1c4db17938466051269dbeba3f19e0b40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="2a455-102">Liczniki wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="2a455-102">Operation Performance Counters</span></span>
<span data-ttu-id="2a455-103">Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="2a455-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="2a455-104">Każda operacja wymaga poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="2a455-104">Each operation has an individual instance.</span></span> <span data-ttu-id="2a455-105">Oznacza to jeśli dany kontrakt operacji 10, 10 wystąpień licznika operacji są skojarzone z tej Umowy.</span><span class="sxs-lookup"><span data-stu-id="2a455-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="2a455-106">Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="2a455-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="2a455-107">Ten licznik umożliwia pomiarów sposobu używania połączenia i jak wykonywanie operacji.</span><span class="sxs-lookup"><span data-stu-id="2a455-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2a455-108">Istnieje limit na długość nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="2a455-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="2a455-109">Gdy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nazwę wystąpienia licznika przekracza maksymalną długość [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Zamienia część nazwy wystąpienia wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="2a455-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a455-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a455-110">See Also</span></span>  
 [<span data-ttu-id="2a455-111">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="2a455-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
