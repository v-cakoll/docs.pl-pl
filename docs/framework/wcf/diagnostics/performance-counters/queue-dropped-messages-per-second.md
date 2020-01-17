---
title: Zakolejkowane komunikaty porzucone na sekundę
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 6ec762d7e5dd7daf63b5df76e1ffb48957538538
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164037"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="ca275-102">Zakolejkowane komunikaty porzucone na sekundę</span><span class="sxs-lookup"><span data-stu-id="ca275-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="ca275-103">Nazwa licznika: liczba porzuconych komunikatów w kolejce na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ca275-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ca275-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ca275-104">Description</span></span>  
 <span data-ttu-id="ca275-105">Liczba komunikatów porzuconych przez transport w kolejce w tej usłudze w drugim.</span><span class="sxs-lookup"><span data-stu-id="ca275-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="ca275-106">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="ca275-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ca275-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="ca275-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
