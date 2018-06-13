---
title: 'Usługa: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 6af8f79d1fe163967a5c6e8220697aa11bee66c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473830"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="f3d99-102">Usługa: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="f3d99-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="f3d99-103">Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="f3d99-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f3d99-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f3d99-104">Description</span></span>  
 <span data-ttu-id="f3d99-105">Liczba wywołań ma nieobsługiwane wyjątki, które są odbierane przez tę usługę na sekundę.</span><span class="sxs-lookup"><span data-stu-id="f3d99-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="f3d99-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="f3d99-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f3d99-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="f3d99-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="f3d99-108">W kodzie zarządzanym wyjątki są zgłaszane w przypadku wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="f3d99-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="f3d99-109">W kodzie zarządzanym wyjątki są zgłaszane w przypadku wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="f3d99-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="f3d99-110">Ten licznik jest zwiększany za każdym razem, gdy jest nieobsługiwany w tej usłudze.</span><span class="sxs-lookup"><span data-stu-id="f3d99-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d99-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3d99-111">See Also</span></span>  
 [<span data-ttu-id="f3d99-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="f3d99-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
