---
title: 'Usługa: Wywołania zwracające błędy'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: f50a2a0bf594d93fea2678b6be26f5d8a16f6b63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688600"
---
# <a name="service-calls-faulted"></a><span data-ttu-id="4c679-102">Usługa: Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="4c679-102">Service: Calls Faulted</span></span>
<span data-ttu-id="4c679-103">Nazwa komputera: Wywołania zwracające błędy.</span><span class="sxs-lookup"><span data-stu-id="4c679-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4c679-104">Opis</span><span class="sxs-lookup"><span data-stu-id="4c679-104">Description</span></span>  
 <span data-ttu-id="4c679-105">Liczba wywołań do tej usługi, które zwróciły błędy.</span><span class="sxs-lookup"><span data-stu-id="4c679-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="4c679-106">W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="4c679-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="4c679-107">Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich wykonanie, bardziej niezawodne lub interaktywne.</span><span class="sxs-lookup"><span data-stu-id="4c679-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="4c679-108">Ponieważ błędach SOAP są wyrażone klientom w postaci XML, są one bardzo międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="4c679-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c679-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c679-109">See also</span></span>
- [<span data-ttu-id="4c679-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="4c679-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
