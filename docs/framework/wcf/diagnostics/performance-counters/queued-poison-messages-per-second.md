---
title: Zakolejkowane komunikaty zanieczyszczone na sekundę
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: d4c921b105dfd1c1a364d2c86f54ab920078dd4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420692"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="f8101-102">Zakolejkowane komunikaty zanieczyszczone na sekundę</span><span class="sxs-lookup"><span data-stu-id="f8101-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="f8101-103">Nazwa licznika: Zakolejkowane komunikaty zanieczyszczone na sekundę.</span><span class="sxs-lookup"><span data-stu-id="f8101-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f8101-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f8101-104">Description</span></span>  
 <span data-ttu-id="f8101-105">Liczba wiadomości, które są oznaczone uszkodzone przez umieszczonych w kolejce transportu na tę usługę z kolejką na sekundę.</span><span class="sxs-lookup"><span data-stu-id="f8101-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="f8101-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="f8101-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f8101-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="f8101-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
