---
title: Implementowanie kontraktów usług
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: ac27329278edc2b9ca693aa15bcc5bb58edffe05
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320160"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="0304e-102">Implementowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="0304e-102">Implementing Service Contracts</span></span>
<span data-ttu-id="0304e-103">Usługa jest klasą, która udostępnia klientom funkcje dostępne dla klientów w co najmniej jednym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="0304e-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="0304e-104">Aby utworzyć usługę, napisz klasę implementującą kontrakt Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0304e-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="0304e-105">Można to zrobić na jeden z dwóch sposobów.</span><span class="sxs-lookup"><span data-stu-id="0304e-105">You can do this in one of two ways.</span></span> <span data-ttu-id="0304e-106">Kontrakt można zdefiniować oddzielnie jako interfejs, a następnie utworzyć klasę, która implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0304e-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="0304e-107">Alternatywnie można utworzyć klasę i umowę bezpośrednio przez umieszczenie atrybutu <xref:System.ServiceModel.ServiceContractAttribute> w samej klasie i atrybutu <xref:System.ServiceModel.OperationContractAttribute> w metodach dostępnych dla klientów usługi.</span><span class="sxs-lookup"><span data-stu-id="0304e-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="0304e-108">Tworzenie klasy usługi</span><span class="sxs-lookup"><span data-stu-id="0304e-108">Creating a service class</span></span>  
 <span data-ttu-id="0304e-109">Poniżej znajduje się przykład usługi implementującej kontrakt `IMath`, który został zdefiniowany osobno.</span><span class="sxs-lookup"><span data-stu-id="0304e-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="0304e-110">Alternatywnie usługa może bezpośrednio uwidocznić umowę.</span><span class="sxs-lookup"><span data-stu-id="0304e-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="0304e-111">Poniżej znajduje się przykład klasy usługi, która definiuje i implementuje kontrakt `MathService`.</span><span class="sxs-lookup"><span data-stu-id="0304e-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="0304e-112">Należy pamiętać, że poprzednie usługi uwidaczniają różne kontrakty, ponieważ nazwy kontraktów są różne.</span><span class="sxs-lookup"><span data-stu-id="0304e-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="0304e-113">W pierwszym przypadku umowa o nazwie "`IMath`" występuje w drugim przypadku kontraktu o nazwie "`MathService`".</span><span class="sxs-lookup"><span data-stu-id="0304e-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="0304e-114">Można ustawić kilka rzeczy na poziomach implementacji usługi i operacji, takich jak współbieżność i Tworzenie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0304e-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="0304e-115">Aby uzyskać więcej informacji, zobacz [projektowanie i implementowanie usług](designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="0304e-115">For more information, see [Designing and Implementing Services](designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="0304e-116">Po wdrożeniu kontraktu usługi należy utworzyć co najmniej jeden punkt końcowy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="0304e-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="0304e-117">Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia punktów końcowych](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0304e-117">For more information, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="0304e-118">Aby uzyskać więcej informacji na temat sposobu uruchamiania usługi, zobacz [usługi hostingu](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="0304e-118">For more information about how to run a service, see [Hosting Services](hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0304e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0304e-119">See also</span></span>

- [<span data-ttu-id="0304e-120">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="0304e-120">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)
- [<span data-ttu-id="0304e-121">Instrukcje: tworzenie usługi za pomocą klasy kontraktu</span><span class="sxs-lookup"><span data-stu-id="0304e-121">How to: Create a Service with a Contract Class</span></span>](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="0304e-122">Instrukcje: tworzenie usługi przy użyciu interfejsu kontraktu</span><span class="sxs-lookup"><span data-stu-id="0304e-122">How to: Create a Service with a Contract Interface</span></span>](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="0304e-123">Określanie zachowania środowiska uruchomieniowego usługi</span><span class="sxs-lookup"><span data-stu-id="0304e-123">Specifying Service Run-Time Behavior</span></span>](specifying-service-run-time-behavior.md)
