---
title: 'Usługa: Wywołania zwracające błędy'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: 233033eb32654b96efa6ddaa21991047d66873cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915645"
---
# <a name="service-calls-faulted"></a><span data-ttu-id="27d04-102">Usługa: Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="27d04-102">Service: Calls Faulted</span></span>
<span data-ttu-id="27d04-103">Nazwa komputera: Wywołania zwracające błędy.</span><span class="sxs-lookup"><span data-stu-id="27d04-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="27d04-104">Opis</span><span class="sxs-lookup"><span data-stu-id="27d04-104">Description</span></span>  
 <span data-ttu-id="27d04-105">Liczba wywołań do tej usługi, które zwróciły błędy.</span><span class="sxs-lookup"><span data-stu-id="27d04-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="27d04-106">W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="27d04-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="27d04-107">Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich wykonanie, bardziej niezawodne lub interaktywne.</span><span class="sxs-lookup"><span data-stu-id="27d04-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="27d04-108">Ponieważ błędach SOAP są wyrażone klientom w postaci XML, są one bardzo międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="27d04-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d04-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27d04-109">See also</span></span>

- [<span data-ttu-id="27d04-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="27d04-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
