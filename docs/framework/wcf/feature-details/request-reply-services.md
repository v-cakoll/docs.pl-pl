---
title: "Usługi „żądanie-odpowiedź”"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a38a90d4e9ec249f91e8bfda88c646c006890d8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="request-reply-services"></a><span data-ttu-id="4686c-102">Usługi „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="4686c-102">Request-Reply Services</span></span>
<span data-ttu-id="4686c-103">Usługi "żądanie-odpowiedź" to domyślny typ kontrakt operacji w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4686c-103">Request-reply services are the default type of operation contract in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="4686c-104">Klienci wykonywania wywołań do operacji usługi i oczekiwania na odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="4686c-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="4686c-105">Można wykonywać wywołania operacji usługi albo synchronicznie, w przypadku, gdy klient blokuje aż do jej odbiera odpowiedź z usługi lub razy wywołania lub asynchronicznie, gdy klient wysyła wywołania operacji usługi kontynuuje współpracę i odbiera odpowiedź z usługi w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="4686c-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="4686c-106">Aby utworzyć kontrakt usługi "żądanie-odpowiedź", zdefiniuj dany kontrakt usługi i zastosować <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="4686c-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="4686c-107">Nie trzeba ustawić <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `false` , ponieważ jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="4686c-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4686c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4686c-108">See Also</span></span>  
 [<span data-ttu-id="4686c-109">Usługi jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="4686c-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="4686c-110">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="4686c-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
