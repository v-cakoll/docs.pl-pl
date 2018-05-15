---
title: 'Usługa: Przekazane transakcje na sekundę'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: 1151117c8537d4a8eaa4de60d14e314b55ce82d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="ba2d2-102">Usługa: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="ba2d2-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="ba2d2-103">Nazwa licznika: Przekazane transakcje na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ba2d2-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ba2d2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ba2d2-104">Description</span></span>  
 <span data-ttu-id="ba2d2-105">Liczba transakcji skierowana do operacji w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ba2d2-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="ba2d2-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="ba2d2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ba2d2-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ba2d2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
