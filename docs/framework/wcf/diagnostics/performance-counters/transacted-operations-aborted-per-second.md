---
title: "Przerwane operacje transakcyjne na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 96ef8181b95d8614ae6cbfeaa468b0138d1129d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="5fefe-102">Przerwane operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="5fefe-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="5fefe-103">Nazwa licznika: Nietransakcyjnego operacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="5fefe-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5fefe-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5fefe-104">Description</span></span>  
 <span data-ttu-id="5fefe-105">Liczba operacji transakcyjnych, które zostały przerwane w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="5fefe-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="5fefe-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="5fefe-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5fefe-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="5fefe-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
