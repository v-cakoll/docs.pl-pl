---
title: "Przepływ transakcji na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 776b9e9f019aadb5fa96a6b6a7bb4a4a07eb16ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="52b1b-102">Przepływ transakcji na sekundę</span><span class="sxs-lookup"><span data-stu-id="52b1b-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="52b1b-103">Nazwa licznika: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="52b1b-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="52b1b-104">Opis</span><span class="sxs-lookup"><span data-stu-id="52b1b-104">Description</span></span>  
 <span data-ttu-id="52b1b-105">Liczba transakcji skierowana do tej operacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="52b1b-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="52b1b-106">Ten licznik jest zwiększany za każdym razem, który zawiera identyfikator transakcji znajduje się w komunikat, który jest wysyłany do operacji.</span><span class="sxs-lookup"><span data-stu-id="52b1b-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="52b1b-107">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="52b1b-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="52b1b-108">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="52b1b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
