---
title: 'Usługa: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: d87d5f06d0c9a3849ec80a3d1c7badefde7cf372
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167495"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="891c5-102">Usługa: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="891c5-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="891c5-103">Nazwa komputera: Wywołania zakończone niepowodzeniami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="891c5-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="891c5-104">Opis</span><span class="sxs-lookup"><span data-stu-id="891c5-104">Description</span></span>  
 <span data-ttu-id="891c5-105">Liczba wywołań, ma nieobsługiwane wyjątki, które są odbierane przez tę usługę na sekundę.</span><span class="sxs-lookup"><span data-stu-id="891c5-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="891c5-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="891c5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="891c5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="891c5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="891c5-108">W zarządzanym kodzie są zgłaszane wyjątki, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="891c5-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="891c5-109">W zarządzanym kodzie są zgłaszane wyjątki, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="891c5-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="891c5-110">Ten licznik jest zwiększany za każdym razem, gdy zostanie nieobsługiwany wyjątek w tej usłudze.</span><span class="sxs-lookup"><span data-stu-id="891c5-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="891c5-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="891c5-111">See also</span></span>

- [<span data-ttu-id="891c5-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="891c5-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
