---
title: 'Punkt końcowy: Przekazane transakcje na sekundę'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227145"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="ac164-102">Punkt końcowy: Przekazane transakcje na sekundę</span><span class="sxs-lookup"><span data-stu-id="ac164-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="ac164-103">Nazwa licznika: Przekazane transakcje na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ac164-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ac164-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ac164-104">Description</span></span>  
 <span data-ttu-id="ac164-105">Liczba transakcji przekazane do operacji w tym punkcie końcowym w ciągu sekundy.</span><span class="sxs-lookup"><span data-stu-id="ac164-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="ac164-106">Ten licznik jest zwiększany ilekroć dowolny identyfikator transakcji znajduje się w wiadomości wysyłane do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ac164-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="ac164-107">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="ac164-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ac164-108">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ac164-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
