---
title: Wywołania zwracające błędy na sekundę
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: 5b7569b6a00757fbb863b90b25b44815a349ab07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115521"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="499b2-102">Wywołania zwracające błędy na sekundę</span><span class="sxs-lookup"><span data-stu-id="499b2-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="499b2-103">Nazwa komputera: Wywołania zwracające błędy na sekundę</span><span class="sxs-lookup"><span data-stu-id="499b2-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="499b2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="499b2-104">Description</span></span>  
 <span data-ttu-id="499b2-105">Liczba wywołań, które zwróciły błędy na tę operację za chwilę.</span><span class="sxs-lookup"><span data-stu-id="499b2-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="499b2-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="499b2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="499b2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="499b2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="499b2-108">W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="499b2-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="499b2-109">Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich wykonanie, bardziej niezawodne lub interaktywne.</span><span class="sxs-lookup"><span data-stu-id="499b2-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="499b2-110">Ponieważ błędach SOAP są wyrażone klientom w postaci XML, są one bardzo międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="499b2-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499b2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="499b2-111">See also</span></span>

- [<span data-ttu-id="499b2-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="499b2-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
