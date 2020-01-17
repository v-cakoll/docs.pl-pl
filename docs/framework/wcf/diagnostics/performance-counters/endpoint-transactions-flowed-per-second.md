---
title: 'Punkt końcowy: Przekazane transakcje na sekundę'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163556"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="5f1c7-102">Punkt końcowy: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="5f1c7-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="5f1c7-103">Nazwa licznika: przepływające na sekundę transakcje.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5f1c7-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5f1c7-104">Description</span></span>  
 <span data-ttu-id="5f1c7-105">Liczba transakcji przepływających do operacji w tym punkcie końcowym w drugim.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="5f1c7-106">Ten licznik jest zwiększany za każdym razem, gdy w komunikacie wysyłanym do punktu końcowego jest obecny identyfikator transakcji.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="5f1c7-107">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5f1c7-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="5f1c7-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
