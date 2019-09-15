---
title: Usługi „żądanie-odpowiedź”
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991140"
---
# <a name="request-reply-services"></a><span data-ttu-id="ea7fb-102">Usługi „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="ea7fb-102">Request-Reply Services</span></span>
<span data-ttu-id="ea7fb-103">Usługi żądanie-odpowiedź są domyślnym typem kontraktu operacji w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ea7fb-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ea7fb-104">Klienci podejmują wywołania do operacji usługi i oczekują na odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="ea7fb-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="ea7fb-105">Można wykonywać wywołania operacji usługi synchronicznie, gdzie klient jest blokowany do momentu odebrania odpowiedzi z usługi lub czasu wywołania lub asynchronicznego, gdzie klient wykonuje wywołanie do operacji usługi, kontynuuje pracę i odbiera Odpowiedź usługi w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="ea7fb-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="ea7fb-106">Aby utworzyć kontrakt usługi żądanie-odpowiedź, zdefiniuj kontrakt usługi i Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej operacji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ea7fb-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="ea7fb-107">Nie trzeba ustawiać <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości na `false` , ponieważ jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="ea7fb-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7fb-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea7fb-108">See also</span></span>

- [<span data-ttu-id="ea7fb-109">Usługi jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="ea7fb-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="ea7fb-110">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="ea7fb-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
