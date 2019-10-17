---
title: 'Usługa: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5431144a4618b146a10dfaa3bbdaae34c519319e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315785"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="e5a69-102">Usługa: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="e5a69-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="e5a69-103">Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę.</span><span class="sxs-lookup"><span data-stu-id="e5a69-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e5a69-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e5a69-104">Description</span></span>  
 <span data-ttu-id="e5a69-105">Liczba wywołań, które mają Nieobsłużone wyjątki i są odbierane przez tę usługę w drugim.</span><span class="sxs-lookup"><span data-stu-id="e5a69-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="e5a69-106">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="e5a69-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e5a69-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="e5a69-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="e5a69-108">W kodzie zarządzanym wyjątki są generowane, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="e5a69-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="e5a69-109">W kodzie zarządzanym wyjątki są generowane, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="e5a69-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="e5a69-110">Licznik jest zwiększany za każdym razem, gdy w tej usłudze występuje nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e5a69-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a69-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5a69-111">See also</span></span>

- [<span data-ttu-id="e5a69-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="e5a69-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
