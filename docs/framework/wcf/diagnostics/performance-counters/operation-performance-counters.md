---
title: Liczniki wydajności operacji
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 59c75dacb2a01f1b85d67d5cc1651dbc55b6aa8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320175"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="ef176-102">Liczniki wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="ef176-102">Operation Performance Counters</span></span>
<span data-ttu-id="ef176-103">Liczniki wydajności operacji są dostępne pod obiektem wydajności `ServiceModelOperation 4.0.0.0` podczas wyświetlania z monitorem wydajności (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="ef176-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="ef176-104">Każda operacja ma pojedyncze wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="ef176-104">Each operation has an individual instance.</span></span> <span data-ttu-id="ef176-105">Oznacza to, że jeśli dany kontrakt zawiera 10 operacji, do tego kontraktu są skojarzone 10 wystąpień liczników operacji.</span><span class="sxs-lookup"><span data-stu-id="ef176-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="ef176-106">Wystąpienia obiektów są nazwane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="ef176-106">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="ef176-107">Ten licznik umożliwia pomiar sposobu użycia wywołania oraz sposobu wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="ef176-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="ef176-108">Istnieje limit długości nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="ef176-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="ef176-109">Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="ef176-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef176-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef176-110">See also</span></span>

- [<span data-ttu-id="ef176-111">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="ef176-111">Performance Counters</span></span>](index.md)
