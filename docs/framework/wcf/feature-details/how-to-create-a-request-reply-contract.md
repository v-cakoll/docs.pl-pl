---
title: 'Instrukcje: tworzenie kontraktu „żądanie-odpowiedź”'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 7a446db49dcc6a12b900292f1b19c9973835f2c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000990"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="cf38d-102">Instrukcje: tworzenie kontraktu „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="cf38d-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="cf38d-103">Kontraktu "żądanie-odpowiedź" Określa metodę, która zwraca odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="cf38d-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="cf38d-104">Odpowiedź musi być wysyłane i skorelowane żądanie zgodnie z warunkami niniejszej Umowy.</span><span class="sxs-lookup"><span data-stu-id="cf38d-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="cf38d-105">Nawet jeśli metoda nie zwraca żadnej odpowiedzi (`void` w języku C# lub `Sub` w języku Visual Basic), infrastruktury, tworzy i wysyła pustego komunikatu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cf38d-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="cf38d-106">Aby uniemożliwić wysyłanie odpowiedzi pusty komunikat, należy użyć kontraktu jednokierunkowego dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="cf38d-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="cf38d-107">Tworzenie kontraktu "żądanie-odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="cf38d-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="cf38d-108">Tworzenie interfejsu w wybranym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="cf38d-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="cf38d-109">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cf38d-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="cf38d-110">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybut do każdej metody, które mogą być wywoływane przez klientów.</span><span class="sxs-lookup"><span data-stu-id="cf38d-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="cf38d-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cf38d-111">Optional.</span></span> <span data-ttu-id="cf38d-112">Ustaw wartość <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwość `true` aby uniemożliwić wysyłanie odpowiedzi pusty komunikat.</span><span class="sxs-lookup"><span data-stu-id="cf38d-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="cf38d-113">Domyślnie wszystkie operacje są kontraktów "żądanie odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="cf38d-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf38d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf38d-114">Example</span></span>  
 <span data-ttu-id="cf38d-115">Poniższy przykład definiuje kontrakt usługi Kalkulator, która zapewnia `Add` i `Subtract` metody.</span><span class="sxs-lookup"><span data-stu-id="cf38d-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="cf38d-116">`Multiply` Metoda nie jest częścią kontraktu, ponieważ nie jest oznaczony za <xref:System.ServiceModel.OperationContractAttribute> klasy, a zatem nie jest dostępna dla klientów.</span><span class="sxs-lookup"><span data-stu-id="cf38d-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
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
  
- <span data-ttu-id="cf38d-117">Aby uzyskać więcej informacji na temat sposobu określania kontrakty operacji, zobacz <xref:System.ServiceModel.OperationContractAttribute> klasy i <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf38d-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="cf38d-118">Stosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty powoduje automatyczne generowanie definicje kontraktu usługi w dokumencie usługi sieci Web Services Description Language (WSDL), po wdrożeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="cf38d-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="cf38d-119">Dokument zostanie pobrana przez dołączenie `?wsdl` HTTP podstawowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="cf38d-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="cf38d-120">Na przykład:`http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="cf38d-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf38d-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf38d-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="cf38d-122">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="cf38d-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="cf38d-123">Instrukcje: Tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="cf38d-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
