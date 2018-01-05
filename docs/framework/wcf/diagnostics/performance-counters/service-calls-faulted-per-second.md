---
title: "Usługa: Wywołania zwracające błędy na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87517687b486cc6cf3d2984623a502e3f5ecfa6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="ec5a2-102">Usługa: Wywołania zwracające błędy na sekundę</span><span class="sxs-lookup"><span data-stu-id="ec5a2-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="ec5a2-103">Nazwa licznika: Wywołania zwracające błędy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ec5a2-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ec5a2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ec5a2-104">Description</span></span>  
 <span data-ttu-id="ec5a2-105">Liczba wywołań, które zwrócone błędy do tej usługi na sekundę.</span><span class="sxs-lookup"><span data-stu-id="ec5a2-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="ec5a2-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="ec5a2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ec5a2-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ec5a2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="ec5a2-108">W [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] komunikacji metody usług aplikacji, przetwarzania przy użyciu protokołu SOAP komunikatów "fault" informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="ec5a2-108">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="ec5a2-109">Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne.</span><span class="sxs-lookup"><span data-stu-id="ec5a2-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="ec5a2-110">Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="ec5a2-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec5a2-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec5a2-111">See Also</span></span>  
 [<span data-ttu-id="ec5a2-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="ec5a2-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
