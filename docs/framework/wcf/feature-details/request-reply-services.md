---
title: Usługi „żądanie-odpowiedź”
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 8fe1343a4b3590622becf71f1167f4b19dbc67af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="request-reply-services"></a><span data-ttu-id="0cc86-102">Usługi „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="0cc86-102">Request-Reply Services</span></span>
<span data-ttu-id="0cc86-103">Usługi "żądanie-odpowiedź" są domyślny typ kontrakt operacji w systemie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0cc86-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="0cc86-104">Klienci wykonywania wywołań do operacji usługi i oczekiwania na odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="0cc86-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="0cc86-105">Można wykonywać wywołania operacji usługi albo synchronicznie, w przypadku, gdy klient blokuje aż do jej odbiera odpowiedź z usługi lub razy wywołania lub asynchronicznie, gdy klient wysyła wywołania operacji usługi kontynuuje współpracę i odbiera odpowiedź z usługi w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="0cc86-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="0cc86-106">Aby utworzyć kontrakt usługi "żądanie-odpowiedź", zdefiniuj dany kontrakt usługi i zastosować <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="0cc86-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="0cc86-107">Nie trzeba ustawić <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `false` , ponieważ jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="0cc86-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc86-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cc86-108">See Also</span></span>  
 [<span data-ttu-id="0cc86-109">Usługi jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="0cc86-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="0cc86-110">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="0cc86-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
