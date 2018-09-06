---
title: Wywołania zakończone niepowodzeniami na sekundę
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ccb5908e9036650e3f21a9496649c8090c2e47b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736325"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="c6f34-102">Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="c6f34-102">Calls Failed Per Second</span></span>
<span data-ttu-id="c6f34-103">Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="c6f34-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="c6f34-104">Opis</span><span class="sxs-lookup"><span data-stu-id="c6f34-104">Description</span></span>  
 <span data-ttu-id="c6f34-105">Liczba wywołań z nieobsługiwanych wyjątków w tę operację za chwilę.</span><span class="sxs-lookup"><span data-stu-id="c6f34-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="c6f34-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="c6f34-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c6f34-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="c6f34-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="c6f34-108">Ten licznik jest zwiększona za każdym, gdy jest nieobsługiwany w tej operacji.</span><span class="sxs-lookup"><span data-stu-id="c6f34-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f34-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6f34-109">See Also</span></span>  
 [<span data-ttu-id="c6f34-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="c6f34-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
