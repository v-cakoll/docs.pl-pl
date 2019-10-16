---
title: 'Usługa: Wywołania zwracające błędy'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: d02139bcd6540fb973e0f1040c8877c04addc2f4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321431"
---
# <a name="service-calls-faulted"></a><span data-ttu-id="6f4fc-102">Usługa: Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="6f4fc-102">Service: Calls Faulted</span></span>
<span data-ttu-id="6f4fc-103">Nazwa licznika: wywołania są błędne.</span><span class="sxs-lookup"><span data-stu-id="6f4fc-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6f4fc-104">Opis</span><span class="sxs-lookup"><span data-stu-id="6f4fc-104">Description</span></span>  
 <span data-ttu-id="6f4fc-105">Liczba wywołań tej usługi, które zwróciły błędy.</span><span class="sxs-lookup"><span data-stu-id="6f4fc-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="6f4fc-106">W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują przetwarzanie informacji o błędach przy użyciu komunikatów błędów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6f4fc-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="6f4fc-107">Błędy protokołu SOAP to typy komunikatów, które są zawarte w metadanych dla operacji usługi, dlatego należy utworzyć kontrakt błędów, którego klienci mogą używać do bardziej niezawodnego lub interaktywnego wykonania.</span><span class="sxs-lookup"><span data-stu-id="6f4fc-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="6f4fc-108">Ponieważ błędy protokołu SOAP są wyrażane dla klientów w formularzu XML, są one wysoce interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="6f4fc-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4fc-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f4fc-109">See also</span></span>

- [<span data-ttu-id="6f4fc-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="6f4fc-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
