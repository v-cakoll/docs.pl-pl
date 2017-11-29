---
title: "Wywołania zwracające błędy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb9e8045-6aeb-4b7f-a825-8283c44252a1
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a28c9937270fd5714801743caa394b64101c9b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="calls-faulted"></a><span data-ttu-id="02a99-102">Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="02a99-102">Calls Faulted</span></span>
<span data-ttu-id="02a99-103">Nazwa licznika: Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="02a99-103">Counter Name: Calls Faulted</span></span>  
  
## <a name="description"></a><span data-ttu-id="02a99-104">Opis</span><span class="sxs-lookup"><span data-stu-id="02a99-104">Description</span></span>  
 <span data-ttu-id="02a99-105">Liczba wywołań tej operacji zakończonych zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="02a99-105">Number of calls to this operation that returned faults.</span></span> <span data-ttu-id="02a99-106">W [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] komunikacji metody usług aplikacji, przetwarzania przy użyciu protokołu SOAP komunikatów "fault" informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="02a99-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="02a99-107">Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne.</span><span class="sxs-lookup"><span data-stu-id="02a99-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="02a99-108">Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="02a99-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a99-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02a99-109">See Also</span></span>  
 [<span data-ttu-id="02a99-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="02a99-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
