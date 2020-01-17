---
title: 'Usługa: Wywołania zwracające błędy na sekundę'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: ba470c565c042de6de53693e7b0e6d4682c5a75a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163895"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="b1ab5-102">Usługa: Wywołania zwracające błędy na sekundę</span><span class="sxs-lookup"><span data-stu-id="b1ab5-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="b1ab5-103">Nazwa licznika: wywołania z błędami na sekundę.</span><span class="sxs-lookup"><span data-stu-id="b1ab5-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b1ab5-104">Opis</span><span class="sxs-lookup"><span data-stu-id="b1ab5-104">Description</span></span>  
 <span data-ttu-id="b1ab5-105">Liczba wywołań, które zwróciły błędy do tej usługi w drugim.</span><span class="sxs-lookup"><span data-stu-id="b1ab5-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="b1ab5-106">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="b1ab5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b1ab5-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="b1ab5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="b1ab5-108">W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują przetwarzanie informacji o błędach przy użyciu komunikatów błędów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b1ab5-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="b1ab5-109">Błędy protokołu SOAP to typy komunikatów, które są zawarte w metadanych dla operacji usługi, dlatego należy utworzyć kontrakt błędów, którego klienci mogą używać do bardziej niezawodnego lub interaktywnego wykonania.</span><span class="sxs-lookup"><span data-stu-id="b1ab5-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="b1ab5-110">Ponieważ błędy protokołu SOAP są wyrażane dla klientów w formularzu XML, są one wysoce interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="b1ab5-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ab5-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1ab5-111">See also</span></span>

- [<span data-ttu-id="b1ab5-112">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="b1ab5-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
