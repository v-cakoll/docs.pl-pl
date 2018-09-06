---
title: 'Punkt końcowy: Porzucone komunikaty komunikacji niezawodnej na sekundę'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 8f935bee06d175ce454bd7f58a1afbbe9ab505ad
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863507"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="509bf-102">Punkt końcowy: Porzucone komunikaty komunikacji niezawodnej na sekundę</span><span class="sxs-lookup"><span data-stu-id="509bf-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="509bf-103">Nazwa licznika: Sesje niezawodnej obsługi komunikatów na sekundę porzuconych.</span><span class="sxs-lookup"><span data-stu-id="509bf-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="509bf-104">Opis</span><span class="sxs-lookup"><span data-stu-id="509bf-104">Description</span></span>  
 <span data-ttu-id="509bf-105">Całkowita liczba komunikaty niezawodnej obsługi komunikatów, które zostały porzucone na sekundę w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="509bf-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="509bf-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="509bf-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="509bf-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="509bf-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
