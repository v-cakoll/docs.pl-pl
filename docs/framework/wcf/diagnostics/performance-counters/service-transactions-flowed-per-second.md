---
title: 'Usługa: przepływające transakcje na sekundę'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: e8fbc314321a46fd3539998bd3dd22770086ca37
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164011"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="d60ce-102">Usługa: przepływające transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="d60ce-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="d60ce-103">Nazwa licznika: przepływające na sekundę transakcje.</span><span class="sxs-lookup"><span data-stu-id="d60ce-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d60ce-104">Opis</span><span class="sxs-lookup"><span data-stu-id="d60ce-104">Description</span></span>  
 <span data-ttu-id="d60ce-105">Liczba transakcji przepływających do operacji w tej usłudze w drugim.</span><span class="sxs-lookup"><span data-stu-id="d60ce-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="d60ce-106">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="d60ce-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d60ce-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="d60ce-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
