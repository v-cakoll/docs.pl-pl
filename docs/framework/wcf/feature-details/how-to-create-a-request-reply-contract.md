---
title: "Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f86679d38b8d1a1d6443c1aac37cfa75f426e402
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="9be28-102">Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="9be28-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="9be28-103">Kontraktu "żądanie-odpowiedź" Określa metodę, która zwraca odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="9be28-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="9be28-104">Odpowiedź musi być wysyłane i skorelowane żądanie na mocy niniejszej Umowy.</span><span class="sxs-lookup"><span data-stu-id="9be28-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="9be28-105">Nawet wtedy, gdy metoda nie zwraca żadnej odpowiedzi (`void` w języku C# lub `Sub` w języku Visual Basic), infrastruktury tworzy i wysyła komunikat pusty do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9be28-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="9be28-106">Aby uniemożliwić wysyłanie komunikatu odpowiedzi pusty, należy użyć kontraktu jednokierunkowego dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="9be28-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="9be28-107">Aby utworzyć kontraktu "żądanie-odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="9be28-107">To create a request-reply contract</span></span>  
  
1.  <span data-ttu-id="9be28-108">Tworzenie interfejsu w języku programowania wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9be28-108">Create an interface in the programming language of your choice.</span></span>  
  
2.  <span data-ttu-id="9be28-109">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9be28-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3.  <span data-ttu-id="9be28-110">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybutu do każdej metody, które może wywołać klientów.</span><span class="sxs-lookup"><span data-stu-id="9be28-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4.  <span data-ttu-id="9be28-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9be28-111">Optional.</span></span> <span data-ttu-id="9be28-112">Ustaw wartość <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true` aby uniemożliwić wysyłanie komunikatu odpowiedzi pusty.</span><span class="sxs-lookup"><span data-stu-id="9be28-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="9be28-113">Domyślnie wszystkie operacje są kontraktów "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="9be28-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9be28-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9be28-114">Example</span></span>  
 <span data-ttu-id="9be28-115">Poniższy przykład definiuje kontrakt dla usługi Kalkulator, która zapewnia `Add` i `Subtract` metody.</span><span class="sxs-lookup"><span data-stu-id="9be28-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="9be28-116">`Multiply` — Metoda nie jest częścią kontraktu, ponieważ nie zostało oznaczone przez <xref:System.ServiceModel.OperationContractAttribute> klasy i dlatego nie jest dostępna dla klientów.</span><span class="sxs-lookup"><span data-stu-id="9be28-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);
    
    [OperationContract]
    int Subtract(int a, int b);
    
    int Multiply(int a, int b)
}
```
  
-   [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9be28-117">Określ kontrakty operacji, zobacz <xref:System.ServiceModel.OperationContractAttribute> klasy i <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9be28-117"> how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
-   <span data-ttu-id="9be28-118">Stosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty powoduje automatyczne generowanie definicje kontraktu usługi w dokumencie Web Services Description Language (WSDL), po wdrożeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="9be28-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="9be28-119">Dokument jest pobierana przez dołączenie `?wsdl` HTTP podstawowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="9be28-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="9be28-120">Na przykład:`http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="9be28-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be28-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9be28-121">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="9be28-122">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="9be28-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="9be28-123">Instrukcje: tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="9be28-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
