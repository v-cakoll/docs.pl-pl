---
title: Zakolejkowane komunikaty zanieczyszczone na sekundę
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="d1e3e-102">Zakolejkowane komunikaty zanieczyszczone na sekundę</span><span class="sxs-lookup"><span data-stu-id="d1e3e-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="d1e3e-103">Nazwa licznika: Zakolejkowane komunikaty zanieczyszczone na sekundę.</span><span class="sxs-lookup"><span data-stu-id="d1e3e-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d1e3e-104">Opis</span><span class="sxs-lookup"><span data-stu-id="d1e3e-104">Description</span></span>  
 <span data-ttu-id="d1e3e-105">Liczba komunikatów oznaczonych jako skażone przez transport z kolejką w tej usługi na sekundę.</span><span class="sxs-lookup"><span data-stu-id="d1e3e-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="d1e3e-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="d1e3e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d1e3e-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d1e3e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
