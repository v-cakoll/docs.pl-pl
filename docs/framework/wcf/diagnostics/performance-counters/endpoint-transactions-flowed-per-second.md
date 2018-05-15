---
title: 'Punkt końcowy: Przekazane transakcje na sekundę'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: ff3d76025bbae0759dba005adbd62609701c5a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="0e81c-102">Punkt końcowy: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="0e81c-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="0e81c-103">Nazwa licznika: Przekazane transakcje na sekundę.</span><span class="sxs-lookup"><span data-stu-id="0e81c-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0e81c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0e81c-104">Description</span></span>  
 <span data-ttu-id="0e81c-105">Liczba transakcji skierowana do operacji w tym punkcie końcowym na sekundę.</span><span class="sxs-lookup"><span data-stu-id="0e81c-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="0e81c-106">Ten licznik jest zwiększany za każdym razem jest obecny w komunikatu wysłanego do punktu końcowego zawiera identyfikator transakcji.</span><span class="sxs-lookup"><span data-stu-id="0e81c-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="0e81c-107">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="0e81c-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0e81c-108">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="0e81c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
