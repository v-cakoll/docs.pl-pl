---
title: "Wystąpienia na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 18423684e6f816ae2d2e2829664b1be71939335d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="instances-per-second"></a><span data-ttu-id="9a29c-102">Wystąpienia na sekundę</span><span class="sxs-lookup"><span data-stu-id="9a29c-102">Instances Per Second</span></span>
<span data-ttu-id="9a29c-103">Nazwa licznika: Utworzone wystąpienia na sekundę.</span><span class="sxs-lookup"><span data-stu-id="9a29c-103">Counter Name: Instances Created Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9a29c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="9a29c-104">Description</span></span>  
 <span data-ttu-id="9a29c-105">Całkowita liczba wystąpień usługi utworzone na sekundę.</span><span class="sxs-lookup"><span data-stu-id="9a29c-105">Total number of service instances created in a second.</span></span>  
  
 <span data-ttu-id="9a29c-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="9a29c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9a29c-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="9a29c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
