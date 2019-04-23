---
title: Wywołania zakończone niepowodzeniami na sekundę
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ff9320b0990a0543bbb1da553d040ff5a4b4fed9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178623"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="f594e-102">Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="f594e-102">Calls Failed Per Second</span></span>
<span data-ttu-id="f594e-103">Nazwa komputera: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="f594e-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="f594e-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f594e-104">Description</span></span>  
 <span data-ttu-id="f594e-105">Liczba wywołań z nieobsługiwanych wyjątków w tę operację za chwilę.</span><span class="sxs-lookup"><span data-stu-id="f594e-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="f594e-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="f594e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f594e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="f594e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="f594e-108">Ten licznik jest zwiększona za każdym, gdy jest nieobsługiwany w tej operacji.</span><span class="sxs-lookup"><span data-stu-id="f594e-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f594e-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f594e-109">See also</span></span>

- [<span data-ttu-id="f594e-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="f594e-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
