---
title: 'Punkt końcowy: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 52419f45adde768d19d6b46642d52ad0a1844197
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100031"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="50168-102">Punkt końcowy: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="50168-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="50168-103">Nazwa komputera: Wywołania zakończone niepowodzeniami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="50168-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="50168-104">Opis</span><span class="sxs-lookup"><span data-stu-id="50168-104">Description</span></span>  
 <span data-ttu-id="50168-105">Liczba wywołań, ma nieobsługiwane wyjątki, które są odbierane przez ten punkt końcowy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="50168-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="50168-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="50168-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="50168-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="50168-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="50168-108">Ten licznik jest zwiększany za każdym razem, gdy zostanie nieobsługiwany wyjątek w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="50168-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50168-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50168-109">See also</span></span>

- [<span data-ttu-id="50168-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="50168-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
