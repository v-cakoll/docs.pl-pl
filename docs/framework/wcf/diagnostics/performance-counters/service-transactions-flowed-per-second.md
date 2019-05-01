---
title: 'Usługa: Przepływ transakcji na sekundę'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: cb41abe74568c3e9641443b81fce3fb6eb6e41bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939415"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="e950c-102">Usługa: Przepływ transakcji na sekundę</span><span class="sxs-lookup"><span data-stu-id="e950c-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="e950c-103">Nazwa komputera: Przepływ transakcji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="e950c-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e950c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e950c-104">Description</span></span>  
 <span data-ttu-id="e950c-105">Liczba transakcji przekazane do operacji w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="e950c-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="e950c-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="e950c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e950c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="e950c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
