---
title: 'Usługa: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: e165348a71101b21fa66bd4907c43335b1e476e4
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163985"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="ee247-102">Usługa: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="ee247-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="ee247-103">Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ee247-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ee247-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ee247-104">Description</span></span>  
 <span data-ttu-id="ee247-105">Liczba wywołań, które mają Nieobsłużone wyjątki i są odbierane przez tę usługę w drugim.</span><span class="sxs-lookup"><span data-stu-id="ee247-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="ee247-106">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="ee247-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ee247-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="ee247-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="ee247-108">W kodzie zarządzanym wyjątki są generowane, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="ee247-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="ee247-109">W kodzie zarządzanym wyjątki są generowane, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="ee247-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="ee247-110">Licznik jest zwiększany za każdym razem, gdy w tej usłudze występuje nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ee247-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee247-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee247-111">See also</span></span>

- [<span data-ttu-id="ee247-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="ee247-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
