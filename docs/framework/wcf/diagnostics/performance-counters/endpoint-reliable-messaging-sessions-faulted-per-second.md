---
title: 'Punkt końcowy: Błędne sesje komunikacji niezawodnej na sekundę'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: f6b48ec4c37c28588dd874a5bfa94a01a2f43b0c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384699"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="a7c9c-102">Punkt końcowy: Błędne sesje komunikacji niezawodnej na sekundę</span><span class="sxs-lookup"><span data-stu-id="a7c9c-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="a7c9c-103">Nazwa licznika: Błędne sesje komunikacji niezawodnej na sekundę.</span><span class="sxs-lookup"><span data-stu-id="a7c9c-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a7c9c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="a7c9c-104">Description</span></span>  
 <span data-ttu-id="a7c9c-105">Liczba sesje niezawodnej obsługi komunikatów, które są umieszczone w tym punkcie końcowym na sekundę.</span><span class="sxs-lookup"><span data-stu-id="a7c9c-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="a7c9c-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="a7c9c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a7c9c-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="a7c9c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
