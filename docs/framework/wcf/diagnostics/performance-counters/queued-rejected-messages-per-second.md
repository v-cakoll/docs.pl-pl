---
title: Zakolejkowane komunikaty odrzucone na sekundę
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 096e2188b13d0fd5a9be35e5e6473107a58c5566
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507283"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="ad68b-102">Zakolejkowane komunikaty odrzucone na sekundę</span><span class="sxs-lookup"><span data-stu-id="ad68b-102">Queued Rejected Messages Per Second</span></span>
<span data-ttu-id="ad68b-103">Nazwa licznika: Zakolejkowane komunikaty odrzucone na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ad68b-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ad68b-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ad68b-104">Description</span></span>  
 <span data-ttu-id="ad68b-105">Liczba wiadomości, które zostały odrzucone przez umieszczonych w kolejce transportu na tę usługę na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ad68b-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="ad68b-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="ad68b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ad68b-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ad68b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
