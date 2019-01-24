---
title: 'Punkt końcowy: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 03fbdd83246fa811424f445823f705a3bef5697a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608040"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="5b4d1-102">Punkt końcowy: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="5b4d1-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="5b4d1-103">Nazwa komputera: Wywołania zakończone niepowodzeniami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5b4d1-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5b4d1-104">Description</span></span>  
 <span data-ttu-id="5b4d1-105">Liczba wywołań, ma nieobsługiwane wyjątki, które są odbierane przez ten punkt końcowy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="5b4d1-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5b4d1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5b4d1-108">Ten licznik jest zwiększany za każdym razem, gdy zostanie nieobsługiwany wyjątek w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b4d1-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b4d1-109">See also</span></span>
- [<span data-ttu-id="5b4d1-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="5b4d1-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
