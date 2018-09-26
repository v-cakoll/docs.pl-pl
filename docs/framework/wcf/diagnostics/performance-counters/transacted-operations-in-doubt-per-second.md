---
title: Wątpliwe operacje transakcyjne na sekundę
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169908"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="59925-102">Wątpliwe operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="59925-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="59925-103">Nazwa licznika: Wątpliwe Operacje transakcyjne na sekundę.</span><span class="sxs-lookup"><span data-stu-id="59925-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="59925-104">Opis</span><span class="sxs-lookup"><span data-stu-id="59925-104">Description</span></span>  
 <span data-ttu-id="59925-105">Liczba operacji transakcyjnych według w stanie wątpliwości wyniku w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="59925-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="59925-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="59925-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="59925-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="59925-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
