---
title: "Punkt końcowy: Przekazane transakcje na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc0764c689db15a256ad8384c10010c33b6a99f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="2a1ed-102">Punkt końcowy: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="2a1ed-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="2a1ed-103">Nazwa licznika: Przekazane transakcje na sekundę.</span><span class="sxs-lookup"><span data-stu-id="2a1ed-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2a1ed-104">Opis</span><span class="sxs-lookup"><span data-stu-id="2a1ed-104">Description</span></span>  
 <span data-ttu-id="2a1ed-105">Liczba transakcji skierowana do operacji w tym punkcie końcowym na sekundę.</span><span class="sxs-lookup"><span data-stu-id="2a1ed-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="2a1ed-106">Ten licznik jest zwiększany za każdym razem jest obecny w komunikatu wysłanego do punktu końcowego zawiera identyfikator transakcji.</span><span class="sxs-lookup"><span data-stu-id="2a1ed-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="2a1ed-107">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="2a1ed-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2a1ed-108">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="2a1ed-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
