---
title: Wątpliwe operacje transakcyjne na sekundę
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: e165e934f17d599a9bb89f2702bb74d1ba0bf633
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="d8b4a-102">Wątpliwe operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="d8b4a-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="d8b4a-103">Nazwa licznika: Wątpliwe Operacje transakcyjne na sekundę.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d8b4a-104">Opis</span><span class="sxs-lookup"><span data-stu-id="d8b4a-104">Description</span></span>  
 <span data-ttu-id="d8b4a-105">Liczba operacji transakcyjnych z wynikami wątpliwych w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="d8b4a-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d8b4a-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d8b4a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
