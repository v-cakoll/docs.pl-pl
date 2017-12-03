---
title: "Punkt końcowy: Wywołania na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aeeedd05c0da46bc210f6f93e6806e3ea72ca862
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="1bd11-102">Punkt końcowy: Wywołania na sekundę</span><span class="sxs-lookup"><span data-stu-id="1bd11-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="1bd11-103">Nazwa licznika: Wywołania na sekundę.</span><span class="sxs-lookup"><span data-stu-id="1bd11-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1bd11-104">Opis</span><span class="sxs-lookup"><span data-stu-id="1bd11-104">Description</span></span>  
 <span data-ttu-id="1bd11-105">Liczba wywołań tego punktu końcowego na sekundę.</span><span class="sxs-lookup"><span data-stu-id="1bd11-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="1bd11-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="1bd11-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1bd11-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="1bd11-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
