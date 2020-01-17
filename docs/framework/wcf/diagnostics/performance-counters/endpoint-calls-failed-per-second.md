---
title: 'Punkt końcowy: wywołania zakończone niepowodzeniem na sekundę'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 25e504221097505e622a3ba60f0c7e85ec455f36
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163621"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="35a3c-102">Punkt końcowy: wywołania zakończone niepowodzeniem na sekundę</span><span class="sxs-lookup"><span data-stu-id="35a3c-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="35a3c-103">Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę.</span><span class="sxs-lookup"><span data-stu-id="35a3c-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="35a3c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="35a3c-104">Description</span></span>  
 <span data-ttu-id="35a3c-105">Liczba wywołań, które mają Nieobsłużone wyjątki i są odbierane przez ten punkt końcowy w drugim.</span><span class="sxs-lookup"><span data-stu-id="35a3c-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="35a3c-106">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="35a3c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="35a3c-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="35a3c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="35a3c-108">Licznik jest zwiększany za każdym razem, gdy w tym punkcie końcowym występuje nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="35a3c-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a3c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35a3c-109">See also</span></span>

- [<span data-ttu-id="35a3c-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="35a3c-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
