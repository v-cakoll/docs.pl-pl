---
title: 'Usługa: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 9cd649788e1304c68caa1bbf4b5fd27e6fc9d508
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861819"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="79130-102">Usługa: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="79130-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="79130-103">Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="79130-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="79130-104">Opis</span><span class="sxs-lookup"><span data-stu-id="79130-104">Description</span></span>  
 <span data-ttu-id="79130-105">Liczba wywołań, ma nieobsługiwane wyjątki, które są odbierane przez tę usługę na sekundę.</span><span class="sxs-lookup"><span data-stu-id="79130-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="79130-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="79130-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="79130-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="79130-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="79130-108">W zarządzanym kodzie są zgłaszane wyjątki, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="79130-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="79130-109">W zarządzanym kodzie są zgłaszane wyjątki, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="79130-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="79130-110">Ten licznik jest zwiększany za każdym razem, gdy zostanie nieobsługiwany wyjątek w tej usłudze.</span><span class="sxs-lookup"><span data-stu-id="79130-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79130-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79130-111">See Also</span></span>  
 [<span data-ttu-id="79130-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="79130-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
