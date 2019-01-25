---
title: 'Punkt końcowy: Wywołania zwracające błędy na sekundę'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 3b5c881c4ce7772e197bfc1a5603636b0975143c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517659"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="1767a-102">Punkt końcowy: Wywołania zwracające błędy na sekundę</span><span class="sxs-lookup"><span data-stu-id="1767a-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="1767a-103">Nazwa komputera: Wywołania zwracające błędy na sekundę.</span><span class="sxs-lookup"><span data-stu-id="1767a-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1767a-104">Opis</span><span class="sxs-lookup"><span data-stu-id="1767a-104">Description</span></span>  
 <span data-ttu-id="1767a-105">Liczba wywołań, które zwróciły błędy do tego punktu końcowego na sekundę.</span><span class="sxs-lookup"><span data-stu-id="1767a-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="1767a-106">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="1767a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1767a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1767a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="1767a-108">W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="1767a-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="1767a-109">Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich wykonanie, bardziej niezawodne lub interaktywne.</span><span class="sxs-lookup"><span data-stu-id="1767a-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="1767a-110">Ponieważ błędach SOAP są wyrażone klientom w postaci XML, są one bardzo międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="1767a-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1767a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1767a-111">See also</span></span>
- [<span data-ttu-id="1767a-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="1767a-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
