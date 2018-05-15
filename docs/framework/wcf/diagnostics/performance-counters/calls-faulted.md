---
title: Wywołania zwracające błędy
ms.date: 03/30/2017
ms.assetid: bb9e8045-6aeb-4b7f-a825-8283c44252a1
ms.openlocfilehash: 26d79d74980d0bab93acace29bc24df7b473c4f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="calls-faulted"></a><span data-ttu-id="3be93-102">Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="3be93-102">Calls Faulted</span></span>
<span data-ttu-id="3be93-103">Nazwa licznika: Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="3be93-103">Counter Name: Calls Faulted</span></span>  
  
## <a name="description"></a><span data-ttu-id="3be93-104">Opis</span><span class="sxs-lookup"><span data-stu-id="3be93-104">Description</span></span>  
 <span data-ttu-id="3be93-105">Liczba wywołań tej operacji zakończonych zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="3be93-105">Number of calls to this operation that returned faults.</span></span> <span data-ttu-id="3be93-106">W aplikacji Windows Communication Foundation (WCF) metody usługi komunikują się za pomocą protokołu SOAP komunikatów "fault" informacje o błędzie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="3be93-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="3be93-107">Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne.</span><span class="sxs-lookup"><span data-stu-id="3be93-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="3be93-108">Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="3be93-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be93-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3be93-109">See Also</span></span>  
 [<span data-ttu-id="3be93-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="3be93-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
