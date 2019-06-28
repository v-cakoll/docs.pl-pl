---
title: Wywołania zakończone niepowodzeniami na sekundę
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: aa8cd4c2d9f642b525b2b9ccb931c4f2101a5129
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421785"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="9bbda-102">Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="9bbda-102">Calls Failed Per Second</span></span>
<span data-ttu-id="9bbda-103">Nazwa komputera: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="9bbda-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="9bbda-104">Opis</span><span class="sxs-lookup"><span data-stu-id="9bbda-104">Description</span></span>  
 <span data-ttu-id="9bbda-105">Liczba wywołań z nieobsługiwanych wyjątków w tę operację za chwilę.</span><span class="sxs-lookup"><span data-stu-id="9bbda-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="9bbda-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="9bbda-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9bbda-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9bbda-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="9bbda-108">Ten licznik jest zwiększany za każdym razem, gdy zostanie nieobsługiwany wyjątek w tej operacji.</span><span class="sxs-lookup"><span data-stu-id="9bbda-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbda-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bbda-109">See also</span></span>

- [<span data-ttu-id="9bbda-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="9bbda-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
