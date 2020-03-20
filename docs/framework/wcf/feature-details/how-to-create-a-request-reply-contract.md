---
title: 'Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 793f7214f8319e87c3e344990577841fc029bc55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185029"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="8010f-102">Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="8010f-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="8010f-103">Umowa żądanie odpowiedź określa metodę, która zwraca odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="8010f-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="8010f-104">Odpowiedź musi być wysłana i skorelowana z wnioskiem zgodnie z warunkami niniejszej umowy.</span><span class="sxs-lookup"><span data-stu-id="8010f-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="8010f-105">Nawet jeśli metoda zwraca`void` odpowiedź (w języku `Sub` C# lub w języku Visual Basic), infrastruktura tworzy i wysyła pustą wiadomość do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8010f-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="8010f-106">Aby zapobiec wysyłaniu pustej wiadomości odpowiedzi, użyj kontraktu jednokierunkowego dla operacji.</span><span class="sxs-lookup"><span data-stu-id="8010f-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="8010f-107">Aby utworzyć umowę żądanie-odpowiedź</span><span class="sxs-lookup"><span data-stu-id="8010f-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="8010f-108">Utwórz interfejs w wybranym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="8010f-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="8010f-109">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybut do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8010f-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="8010f-110">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybut do każdej metody, która klienci mogą wywoływać.</span><span class="sxs-lookup"><span data-stu-id="8010f-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="8010f-111">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8010f-111">Optional.</span></span> <span data-ttu-id="8010f-112">Ustaw wartość właściwości, <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` aby zapobiec wysyłaniu pustej wiadomości odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8010f-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="8010f-113">Domyślnie wszystkie operacje są kontrakty żądanie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8010f-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8010f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="8010f-114">Example</span></span>  
 <span data-ttu-id="8010f-115">Poniższy przykład definiuje kontrakt dla usługi kalkulatora, który zapewnia `Add` i `Subtract` metody.</span><span class="sxs-lookup"><span data-stu-id="8010f-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="8010f-116">Metoda `Multiply` nie jest częścią umowy, ponieważ nie <xref:System.ServiceModel.OperationContractAttribute> jest oznaczony przez klasę, a więc nie jest dostępny dla klientów.</span><span class="sxs-lookup"><span data-stu-id="8010f-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
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
  
- <span data-ttu-id="8010f-117">Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.OperationContractAttribute> określania <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> umów operacji, zobacz klasę i właściwość.</span><span class="sxs-lookup"><span data-stu-id="8010f-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="8010f-118">Zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty powoduje automatyczne generowanie definicji umowy serwisowej w dokumencie języka opisu usług sieci Web (WSDL) po wdrożeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="8010f-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="8010f-119">Dokument jest pobierany przez `?wsdl` dołączenie do adresu podstawowego HTTP dla usługi.</span><span class="sxs-lookup"><span data-stu-id="8010f-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="8010f-120">Na przykład: `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="8010f-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8010f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8010f-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="8010f-122">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="8010f-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="8010f-123">Instrukcje: tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="8010f-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
