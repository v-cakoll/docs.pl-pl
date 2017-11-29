---
title: "Usługa: Przekazane transakcje na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9172075294de8431216540b06aec542753c94621
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="30df1-102">Usługa: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="30df1-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="30df1-103">Nazwa licznika: Przekazane transakcje na sekundę.</span><span class="sxs-lookup"><span data-stu-id="30df1-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="30df1-104">Opis</span><span class="sxs-lookup"><span data-stu-id="30df1-104">Description</span></span>  
 <span data-ttu-id="30df1-105">Liczba transakcji skierowana do operacji w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="30df1-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="30df1-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="30df1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="30df1-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="30df1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
