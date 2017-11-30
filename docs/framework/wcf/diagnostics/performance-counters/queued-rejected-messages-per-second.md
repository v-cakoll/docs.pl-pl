---
title: "Zakolejkowane komunikaty odrzucone na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a773d30cc9cb33a9bd3a1e1fb5562026bcfb7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="7a9c6-102">Zakolejkowane komunikaty odrzucone na sekundę</span><span class="sxs-lookup"><span data-stu-id="7a9c6-102">Queued Rejected Messages Per Second</span></span>
<span data-ttu-id="7a9c6-103">Nazwa licznika: Zakolejkowane komunikaty odrzucone na sekundę.</span><span class="sxs-lookup"><span data-stu-id="7a9c6-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7a9c6-104">Opis</span><span class="sxs-lookup"><span data-stu-id="7a9c6-104">Description</span></span>  
 <span data-ttu-id="7a9c6-105">Liczba komunikatów, które zostały odrzucone przez transport z kolejką w tej usługi na sekundę.</span><span class="sxs-lookup"><span data-stu-id="7a9c6-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="7a9c6-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="7a9c6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7a9c6-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="7a9c6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
