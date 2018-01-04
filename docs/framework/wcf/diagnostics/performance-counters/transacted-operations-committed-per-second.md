---
title: "Zatwierdzone operacje transakcyjne na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a17d99329248dff4a29f3c68649c67622c45d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="81bbe-102">Zatwierdzone operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="81bbe-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="81bbe-103">Nazwa licznika: Operacje transakcyjne na sekundę.</span><span class="sxs-lookup"><span data-stu-id="81bbe-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="81bbe-104">Opis</span><span class="sxs-lookup"><span data-stu-id="81bbe-104">Description</span></span>  
 <span data-ttu-id="81bbe-105">Liczba operacji transakcyjnych, które zostały zatwierdzone w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="81bbe-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="81bbe-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="81bbe-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="81bbe-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="81bbe-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
