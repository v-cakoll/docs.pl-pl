---
title: Usługi „żądanie-odpowiedź”
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: df42f3fa8f5a15572987b0d4859856c7f838e632
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586237"
---
# <a name="request-reply-services"></a><span data-ttu-id="b98ff-102">Usługi „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="b98ff-102">Request-Reply Services</span></span>
<span data-ttu-id="b98ff-103">Usługi żądanie-odpowiedź są domyślnym typem kontraktu operacji w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b98ff-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b98ff-104">Klienci podejmują wywołania do operacji usługi i oczekują na odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="b98ff-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="b98ff-105">Można wykonywać wywołania operacji usługi synchronicznie, gdzie klient jest blokowany do momentu odebrania odpowiedzi z usługi lub czasu wywołania, lub asynchronicznie, gdzie klient wykonuje wywołanie do operacji usługi, kontynuuje pracę i odbiera odpowiedź z usługi w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="b98ff-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="b98ff-106">Aby utworzyć kontrakt usługi żądanie-odpowiedź, zdefiniuj kontrakt usługi i Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej operacji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b98ff-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="b98ff-107">Nie trzeba ustawiać <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości na, `false` ponieważ jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="b98ff-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98ff-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b98ff-108">See also</span></span>

- [<span data-ttu-id="b98ff-109">Usługi jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="b98ff-109">One-Way Services</span></span>](one-way-services.md)
- [<span data-ttu-id="b98ff-110">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="b98ff-110">Duplex Services</span></span>](duplex-services.md)
