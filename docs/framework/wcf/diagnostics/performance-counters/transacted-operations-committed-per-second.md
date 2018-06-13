---
title: Zatwierdzone operacje transakcyjne na sekundę
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 3bec51a7be63c54a240b85032ecac09b87173393
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474275"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="32853-102">Zatwierdzone operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="32853-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="32853-103">Nazwa licznika: Operacje transakcyjne na sekundę.</span><span class="sxs-lookup"><span data-stu-id="32853-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="32853-104">Opis</span><span class="sxs-lookup"><span data-stu-id="32853-104">Description</span></span>  
 <span data-ttu-id="32853-105">Liczba operacji transakcyjnych, które zostały zatwierdzone w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="32853-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="32853-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="32853-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="32853-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="32853-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
