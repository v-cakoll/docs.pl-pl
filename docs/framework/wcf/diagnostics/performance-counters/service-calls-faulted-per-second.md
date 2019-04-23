---
title: 'Usługa: Wywołania zwracające błędy na sekundę'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 595b623d70bad82ea39ab3ef93fb5fd499268ff2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088480"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="6f0fb-102">Usługa: Wywołania zwracające błędy na sekundę</span><span class="sxs-lookup"><span data-stu-id="6f0fb-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="6f0fb-103">Nazwa komputera: Wywołania zwracające błędy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="6f0fb-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6f0fb-104">Opis</span><span class="sxs-lookup"><span data-stu-id="6f0fb-104">Description</span></span>  
 <span data-ttu-id="6f0fb-105">Liczba wywołań, które zwróciły błędy do tej usługi na sekundę.</span><span class="sxs-lookup"><span data-stu-id="6f0fb-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="6f0fb-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="6f0fb-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6f0fb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="6f0fb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="6f0fb-108">W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="6f0fb-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="6f0fb-109">Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich wykonanie, bardziej niezawodne lub interaktywne.</span><span class="sxs-lookup"><span data-stu-id="6f0fb-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="6f0fb-110">Ponieważ błędach SOAP są wyrażone klientom w postaci XML, są one bardzo międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="6f0fb-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f0fb-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f0fb-111">See also</span></span>

- [<span data-ttu-id="6f0fb-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="6f0fb-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
