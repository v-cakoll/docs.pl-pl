---
title: 'Punkt końcowy: Wywołania zwracające błędy'
ms.date: 03/30/2017
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
ms.openlocfilehash: 126ba1b4bd2cc16d62460f198a69194fe4652a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-calls-faulted"></a><span data-ttu-id="59436-102">Punkt końcowy: Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="59436-102">Endpoint: Calls Faulted</span></span>
<span data-ttu-id="59436-103">Nazwa licznika: Wywołania zwracające błędy.</span><span class="sxs-lookup"><span data-stu-id="59436-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="59436-104">Opis</span><span class="sxs-lookup"><span data-stu-id="59436-104">Description</span></span>  
 <span data-ttu-id="59436-105">Liczba wywołań tego punktu końcowego, które zwrócone błędy.</span><span class="sxs-lookup"><span data-stu-id="59436-105">Number of calls to this endpoint that have returned faults.</span></span> <span data-ttu-id="59436-106">W aplikacji Windows Communication Foundation (WCF) metody usługi komunikują się za pomocą protokołu SOAP komunikatów "fault" informacje o błędzie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="59436-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="59436-107">Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne.</span><span class="sxs-lookup"><span data-stu-id="59436-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="59436-108">Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="59436-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59436-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59436-109">See Also</span></span>  
 [<span data-ttu-id="59436-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="59436-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
