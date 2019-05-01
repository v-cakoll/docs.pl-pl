---
title: Błędne sesje komunikacji niezawodnej na sekundę
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916126"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="539f6-102">Błędne sesje komunikacji niezawodnej na sekundę</span><span class="sxs-lookup"><span data-stu-id="539f6-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="539f6-103">Nazwa komputera: Błędne sesje niezawodnej obsługi komunikatów na sekundę.</span><span class="sxs-lookup"><span data-stu-id="539f6-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="539f6-104">Opis</span><span class="sxs-lookup"><span data-stu-id="539f6-104">Description</span></span>  
 <span data-ttu-id="539f6-105">Liczba sesje niezawodnej obsługi komunikatów, które są umieszczone w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="539f6-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="539f6-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="539f6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="539f6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="539f6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
