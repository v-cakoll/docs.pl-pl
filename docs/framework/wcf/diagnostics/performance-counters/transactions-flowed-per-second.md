---
title: Przepływ transakcji na sekundę
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501307"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="86d1d-102">Przepływ transakcji na sekundę</span><span class="sxs-lookup"><span data-stu-id="86d1d-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="86d1d-103">Nazwa licznika: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="86d1d-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="86d1d-104">Opis</span><span class="sxs-lookup"><span data-stu-id="86d1d-104">Description</span></span>  
 <span data-ttu-id="86d1d-105">Liczba transakcji przekazane do tej operacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="86d1d-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="86d1d-106">Ten licznik jest zwiększany ilekroć dowolny identyfikator transakcji znajduje się w wiadomości, które są wysyłane do operacji.</span><span class="sxs-lookup"><span data-stu-id="86d1d-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="86d1d-107">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="86d1d-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="86d1d-108">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="86d1d-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
