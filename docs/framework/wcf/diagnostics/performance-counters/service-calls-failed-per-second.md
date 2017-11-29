---
title: "Usługa: Wywołania zakończone niepowodzeniami na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2072a686d5d424f90ac2f32cf5fc11564b07542c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="209ee-102">Usługa: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="209ee-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="209ee-103">Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="209ee-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="209ee-104">Opis</span><span class="sxs-lookup"><span data-stu-id="209ee-104">Description</span></span>  
 <span data-ttu-id="209ee-105">Liczba wywołań ma nieobsługiwane wyjątki, które są odbierane przez tę usługę na sekundę.</span><span class="sxs-lookup"><span data-stu-id="209ee-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="209ee-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="209ee-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="209ee-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="209ee-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="209ee-108">W kodzie zarządzanym wyjątki są zgłaszane w przypadku wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="209ee-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="209ee-109">W kodzie zarządzanym wyjątki są zgłaszane w przypadku wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="209ee-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="209ee-110">Ten licznik jest zwiększany za każdym razem, gdy jest nieobsługiwany w tej usłudze.</span><span class="sxs-lookup"><span data-stu-id="209ee-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="209ee-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="209ee-111">See Also</span></span>  
 [<span data-ttu-id="209ee-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="209ee-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
