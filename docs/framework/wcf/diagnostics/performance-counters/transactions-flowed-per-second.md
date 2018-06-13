---
title: Przepływ transakcji na sekundę
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: a71095b9fdd16d7e220be8a0aeb0a746bb50527e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472921"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="e2d15-102">Przepływ transakcji na sekundę</span><span class="sxs-lookup"><span data-stu-id="e2d15-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="e2d15-103">Nazwa licznika: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="e2d15-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2d15-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e2d15-104">Description</span></span>  
 <span data-ttu-id="e2d15-105">Liczba transakcji skierowana do tej operacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="e2d15-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="e2d15-106">Ten licznik jest zwiększany za każdym razem, który zawiera identyfikator transakcji znajduje się w komunikat, który jest wysyłany do operacji.</span><span class="sxs-lookup"><span data-stu-id="e2d15-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="e2d15-107">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="e2d15-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e2d15-108">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e2d15-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
