---
title: 'Punkt końcowy: Wywołania zwracające błędy na sekundę'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: f1b2997a0f1e16c897fc319d1833313141f5c4bf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466833"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="352ab-102">Punkt końcowy: Wywołania zwracające błędy na sekundę</span><span class="sxs-lookup"><span data-stu-id="352ab-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="352ab-103">Nazwa licznika: Wywołania zwracające błędy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="352ab-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="352ab-104">Opis</span><span class="sxs-lookup"><span data-stu-id="352ab-104">Description</span></span>  
 <span data-ttu-id="352ab-105">Liczba wywołań, które zwróciły błędy do tego punktu końcowego na sekundę.</span><span class="sxs-lookup"><span data-stu-id="352ab-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="352ab-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="352ab-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="352ab-107">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="352ab-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="352ab-108">W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="352ab-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="352ab-109">Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich wykonanie, bardziej niezawodne lub interaktywne.</span><span class="sxs-lookup"><span data-stu-id="352ab-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="352ab-110">Ponieważ błędach SOAP są wyrażone klientom w postaci XML, są one bardzo międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="352ab-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352ab-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="352ab-111">See Also</span></span>  
 [<span data-ttu-id="352ab-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="352ab-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
