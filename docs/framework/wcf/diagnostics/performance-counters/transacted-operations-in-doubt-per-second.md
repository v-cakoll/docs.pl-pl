---
title: "Wątpliwe operacje transakcyjne na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e911a6112901ee92cb60adb4d2a7b028218d722d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="62c5a-102">Wątpliwe operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="62c5a-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="62c5a-103">Nazwa licznika: Wątpliwe Operacje transakcyjne na sekundę.</span><span class="sxs-lookup"><span data-stu-id="62c5a-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="62c5a-104">Opis</span><span class="sxs-lookup"><span data-stu-id="62c5a-104">Description</span></span>  
 <span data-ttu-id="62c5a-105">Liczba operacji transakcyjnych z wynikami wątpliwych w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="62c5a-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="62c5a-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="62c5a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="62c5a-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="62c5a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
