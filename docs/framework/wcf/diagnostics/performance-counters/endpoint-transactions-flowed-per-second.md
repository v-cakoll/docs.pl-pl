---
title: 'Punkt końcowy: Przekazane transakcje na sekundę'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44175020"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="ddf85-102">Punkt końcowy: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="ddf85-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="ddf85-103">Nazwa licznika: Przekazane transakcje na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ddf85-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ddf85-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ddf85-104">Description</span></span>  
 <span data-ttu-id="ddf85-105">Liczba transakcji przekazane do operacji w tym punkcie końcowym w ciągu sekundy.</span><span class="sxs-lookup"><span data-stu-id="ddf85-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="ddf85-106">Ten licznik jest zwiększany ilekroć dowolny identyfikator transakcji znajduje się w wiadomości wysyłane do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ddf85-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="ddf85-107">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="ddf85-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ddf85-108">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ddf85-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
