---
title: "Usługa: Wywołania zwracające błędy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5f37f3befba7a3dfdce50869aaea0033ed74aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-faulted"></a><span data-ttu-id="eceaf-102">Usługa: Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="eceaf-102">Service: Calls Faulted</span></span>
<span data-ttu-id="eceaf-103">Nazwa licznika: Wywołania zwracające błędy.</span><span class="sxs-lookup"><span data-stu-id="eceaf-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="eceaf-104">Opis</span><span class="sxs-lookup"><span data-stu-id="eceaf-104">Description</span></span>  
 <span data-ttu-id="eceaf-105">Liczba wywołań tej usługi, które zostały zwrócone błędy.</span><span class="sxs-lookup"><span data-stu-id="eceaf-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="eceaf-106">W [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] komunikacji metody usług aplikacji, przetwarzania przy użyciu protokołu SOAP komunikatów "fault" informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="eceaf-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="eceaf-107">Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne.</span><span class="sxs-lookup"><span data-stu-id="eceaf-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="eceaf-108">Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="eceaf-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eceaf-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eceaf-109">See Also</span></span>  
 [<span data-ttu-id="eceaf-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="eceaf-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
