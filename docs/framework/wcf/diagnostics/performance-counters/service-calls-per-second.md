---
title: 'Usługa: Wywołania na sekundę'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499890"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="08d97-102">Usługa: Wywołania na sekundę</span><span class="sxs-lookup"><span data-stu-id="08d97-102">Service: Calls Per Second</span></span>
<span data-ttu-id="08d97-103">Nazwa licznika: Wywołania na sekundę.</span><span class="sxs-lookup"><span data-stu-id="08d97-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="08d97-104">Opis</span><span class="sxs-lookup"><span data-stu-id="08d97-104">Description</span></span>  
 <span data-ttu-id="08d97-105">Liczba wywołań tej usługi na sekundę.</span><span class="sxs-lookup"><span data-stu-id="08d97-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="08d97-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="08d97-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="08d97-107">(N 1 - N 0) / ((D 1 -D 0) / F) gdzie licznika (N) reprezentuje liczbę operacji wykonywanych podczas ostatniego interwału próbkowania reprezentuje mianownik (D), liczbę znaczników, który upłynął podczas ostatniego interwału próbkowania, a F to częstotliwość to znaczniki osi.</span><span class="sxs-lookup"><span data-stu-id="08d97-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
