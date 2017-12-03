---
title: "Punkt końcowy: Wywołania zakończone niepowodzeniami na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b41a1fba1c1630532524bb4d6bc759ec21e2865
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="5b2b7-102">Punkt końcowy: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="5b2b7-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="5b2b7-103">Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="5b2b7-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5b2b7-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5b2b7-104">Description</span></span>  
 <span data-ttu-id="5b2b7-105">Liczba wywołań ma nieobsługiwane wyjątki, które są odbierane przez ten punkt końcowy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="5b2b7-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="5b2b7-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="5b2b7-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5b2b7-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="5b2b7-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5b2b7-108">Ten licznik jest zwiększany za każdym razem, gdy jest nieobsługiwany w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="5b2b7-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2b7-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b2b7-109">See Also</span></span>  
 [<span data-ttu-id="5b2b7-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="5b2b7-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
