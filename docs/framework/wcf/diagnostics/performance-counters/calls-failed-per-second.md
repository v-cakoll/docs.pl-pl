---
title: Wywołania zakończone niepowodzeniami na sekundę
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 110ee5c264094f80d5c7c6542c3e388e758e1665
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163166"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="8c805-102">Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="8c805-102">Calls Failed Per Second</span></span>
<span data-ttu-id="8c805-103">Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę</span><span class="sxs-lookup"><span data-stu-id="8c805-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="8c805-104">Opis</span><span class="sxs-lookup"><span data-stu-id="8c805-104">Description</span></span>  
 <span data-ttu-id="8c805-105">Liczba wywołań z nieobsługiwanymi wyjątkami w tej operacji w drugim.</span><span class="sxs-lookup"><span data-stu-id="8c805-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="8c805-106">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="8c805-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8c805-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="8c805-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="8c805-108">Licznik jest zwiększany za każdym razem, gdy w tej operacji występuje nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8c805-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c805-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c805-109">See also</span></span>

- [<span data-ttu-id="8c805-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="8c805-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
