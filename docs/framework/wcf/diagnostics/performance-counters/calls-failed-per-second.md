---
title: Wywołania zakończone niepowodzeniami na sekundę
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 19f09b2a2132cab56da5dec49bdc8d5f5e4c8b8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474457"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="98061-102">Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="98061-102">Calls Failed Per Second</span></span>
<span data-ttu-id="98061-103">Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="98061-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="98061-104">Opis</span><span class="sxs-lookup"><span data-stu-id="98061-104">Description</span></span>  
 <span data-ttu-id="98061-105">Liczba wywołań z nieobsługiwanymi wyjątkami w tej operacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="98061-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="98061-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="98061-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="98061-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="98061-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="98061-108">Ten licznik jest zwiększany zawsze, gdy jest nieobsługiwany w tej operacji.</span><span class="sxs-lookup"><span data-stu-id="98061-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98061-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98061-109">See Also</span></span>  
 [<span data-ttu-id="98061-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="98061-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
