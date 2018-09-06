---
title: 'Usługa: Przekazane transakcje na sekundę'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: cb41abe74568c3e9641443b81fce3fb6eb6e41bf
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874943"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="ded73-102">Usługa: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="ded73-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="ded73-103">Nazwa licznika: Przekazane transakcje na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ded73-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ded73-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ded73-104">Description</span></span>  
 <span data-ttu-id="ded73-105">Liczba transakcji przekazane do operacji w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ded73-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="ded73-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="ded73-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ded73-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ded73-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
