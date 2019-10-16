---
title: Wywołania zakończone niepowodzeniami na sekundę
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321122"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="26c74-102">Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="26c74-102">Calls Failed Per Second</span></span>
<span data-ttu-id="26c74-103">Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę</span><span class="sxs-lookup"><span data-stu-id="26c74-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="26c74-104">Opis</span><span class="sxs-lookup"><span data-stu-id="26c74-104">Description</span></span>  
 <span data-ttu-id="26c74-105">Liczba wywołań z nieobsługiwanymi wyjątkami w tej operacji w drugim.</span><span class="sxs-lookup"><span data-stu-id="26c74-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="26c74-106">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="26c74-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="26c74-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="26c74-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="26c74-108">Licznik jest zwiększany za każdym razem, gdy w tej operacji występuje nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="26c74-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c74-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26c74-109">See also</span></span>

- [<span data-ttu-id="26c74-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="26c74-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
