---
title: Usługi „żądanie-odpowiedź”
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 1ff11b1cae4ec8f6fe886a55cb0add27831048d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991123"
---
# <a name="request-reply-services"></a><span data-ttu-id="94831-102">Usługi „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="94831-102">Request-Reply Services</span></span>
<span data-ttu-id="94831-103">Usługi "żądanie-odpowiedź" to typ domyślny kontrakt operacji w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="94831-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="94831-104">Klienci wykonywanie wywołań do operacji usługi i oczekiwania na odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="94831-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="94831-105">Można wykonywać wywołania operacji usługi albo synchronicznie, w przypadku, gdy klienta blokuje aż do jego odbiera odpowiedź od usługi lub czasy wywołań lub asynchronicznie, gdy klient wysyła wywołania operacji usługi kontynuuje współpracę i odbiera odpowiedź z usługi w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="94831-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="94831-106">Aby utworzyć kontrakt usługi "żądanie-odpowiedź", definiowanie kontraktu usługi, usługi i zastosować <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="94831-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="94831-107">Nie trzeba ustawić <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `false` , ponieważ jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="94831-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94831-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94831-108">See also</span></span>

- [<span data-ttu-id="94831-109">Usługi jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="94831-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="94831-110">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="94831-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
