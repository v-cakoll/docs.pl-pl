---
title: Przerwane operacje transakcyjne na sekundę
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500562"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="9e61e-102">Przerwane operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="9e61e-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="9e61e-103">Nazwa licznika: Transacted przerwane operacje na sekundę.</span><span class="sxs-lookup"><span data-stu-id="9e61e-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9e61e-104">Opis</span><span class="sxs-lookup"><span data-stu-id="9e61e-104">Description</span></span>  
 <span data-ttu-id="9e61e-105">Liczba operacji transakcyjnych, które zostało przerwane w tej usłudze na sekundę.</span><span class="sxs-lookup"><span data-stu-id="9e61e-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="9e61e-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="9e61e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9e61e-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="9e61e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
