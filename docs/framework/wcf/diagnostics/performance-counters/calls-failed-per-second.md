---
title: "Wywołania zakończone niepowodzeniami na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 504470a7338a22d058f6ae1f99192e9665b4d968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="a1e36-102">Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="a1e36-102">Calls Failed Per Second</span></span>
<span data-ttu-id="a1e36-103">Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę</span><span class="sxs-lookup"><span data-stu-id="a1e36-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="a1e36-104">Opis</span><span class="sxs-lookup"><span data-stu-id="a1e36-104">Description</span></span>  
 <span data-ttu-id="a1e36-105">Liczba wywołań z nieobsługiwanymi wyjątkami w tej operacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="a1e36-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="a1e36-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="a1e36-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a1e36-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="a1e36-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="a1e36-108">Ten licznik jest zwiększany zawsze, gdy jest nieobsługiwany w tej operacji.</span><span class="sxs-lookup"><span data-stu-id="a1e36-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e36-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1e36-109">See Also</span></span>  
 [<span data-ttu-id="a1e36-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="a1e36-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
