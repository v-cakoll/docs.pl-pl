---
title: 'Usługa: Wywołania na sekundę'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: c23456f49eb867d5b6f66b4386a83615d95e07da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="service-calls-per-second"></a><span data-ttu-id="1bde8-102">Usługa: Wywołania na sekundę</span><span class="sxs-lookup"><span data-stu-id="1bde8-102">Service: Calls Per Second</span></span>
<span data-ttu-id="1bde8-103">Nazwa licznika: Wywołania na sekundę.</span><span class="sxs-lookup"><span data-stu-id="1bde8-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1bde8-104">Opis</span><span class="sxs-lookup"><span data-stu-id="1bde8-104">Description</span></span>  
 <span data-ttu-id="1bde8-105">Liczba wywołań tej usługi na sekundę.</span><span class="sxs-lookup"><span data-stu-id="1bde8-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="1bde8-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="1bde8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1bde8-107">(N 1 - N 0) / ((D 1 -D 0) / F) gdy licznik (N) reprezentuje liczbę operacji wykonywanych podczas ostatniego interwału próbkowania reprezentuje denominator (D) liczbę znaczników, który upłynął podczas ostatniego interwału próbkowania i F jest częstotliwość to znaczniki osi.</span><span class="sxs-lookup"><span data-stu-id="1bde8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
