---
title: Porzucone komunikaty niezawodnej obsługi komunikatów na sekundę
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542844"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="44fd4-102">Porzucone komunikaty niezawodnej obsługi komunikatów na sekundę</span><span class="sxs-lookup"><span data-stu-id="44fd4-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="44fd4-103">Nazwa licznika: Sesje niezawodnej obsługi komunikatów na sekundę porzuconych.</span><span class="sxs-lookup"><span data-stu-id="44fd4-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="44fd4-104">Opis</span><span class="sxs-lookup"><span data-stu-id="44fd4-104">Description</span></span>  
 <span data-ttu-id="44fd4-105">Całkowita liczba komunikaty niezawodnej obsługi komunikatów, które zostały usunięte w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="44fd4-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="44fd4-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="44fd4-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="44fd4-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="44fd4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
