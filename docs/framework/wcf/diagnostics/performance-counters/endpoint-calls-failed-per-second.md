---
title: 'Punkt końcowy: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: c0273fc90ad5702663862612f52f03c42f410b8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="d2fc2-102">Punkt końcowy: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="d2fc2-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="d2fc2-103">Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="d2fc2-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d2fc2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="d2fc2-104">Description</span></span>  
 <span data-ttu-id="d2fc2-105">Liczba wywołań ma nieobsługiwane wyjątki, które są odbierane przez ten punkt końcowy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="d2fc2-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="d2fc2-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="d2fc2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d2fc2-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d2fc2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="d2fc2-108">Ten licznik jest zwiększany za każdym razem, gdy jest nieobsługiwany w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="d2fc2-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2fc2-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2fc2-109">See Also</span></span>  
 [<span data-ttu-id="d2fc2-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="d2fc2-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
