---
title: 'Instrukcje: Deklarowanie błędów w kontraktach usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 0e173f71201d5f98a04d2ad922469e4ff6666681
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929288"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="cb507-102">Instrukcje: Deklarowanie błędów w kontraktach usługi</span><span class="sxs-lookup"><span data-stu-id="cb507-102">How to: Declare Faults in Service Contracts</span></span>
<span data-ttu-id="cb507-103">W zarządzanym kodzie są zgłaszane wyjątki, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="cb507-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="cb507-104">W aplikacjach Windows Communication Foundation (WCF) natomiast kontraktów usług określić informacje o błędach, które są zwracane do klientów przez zadeklarowanie błędach SOAP w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="cb507-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="cb507-105">Aby uzyskać przegląd relacji między wyjątków i błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="cb507-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="cb507-106">Tworzenie kontraktu usługi, która określa protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="cb507-106">Create a service contract that specifies a SOAP fault</span></span>  
  
1. <span data-ttu-id="cb507-107">Tworzenie kontraktu usługi, która zawiera co najmniej jedną operację.</span><span class="sxs-lookup"><span data-stu-id="cb507-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="cb507-108">Aby uzyskać przykład, zobacz [jak: Definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="cb507-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="cb507-109">Wybierz operację, można określić warunek błędu o tym, które klienci mogą oczekiwać otrzymywać powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="cb507-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="cb507-110">Aby zdecydować, których warunki błędów uzasadnienie, zwracając błędach SOAP dla klientów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="cb507-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
3. <span data-ttu-id="cb507-111">Zastosuj <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> wybranej operacji i przekazać typ usterki do serializacji do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="cb507-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="cb507-112">Aby uzyskać szczegółowe informacje na temat tworzenia i używania typów możliwych do serializacji, zobacz [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="cb507-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="cb507-113">Poniższy przykład pokazuje, jak określić, że `SampleMethod` operacji może spowodować `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="cb507-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4. <span data-ttu-id="cb507-114">Powtórz kroki 2 i 3 dla wszystkich operacji w kontrakcie, które komunikują się warunki błędu dla klientów.</span><span class="sxs-lookup"><span data-stu-id="cb507-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="cb507-115">Implementowanie operację zwrócenia określonego protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="cb507-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>  
 <span data-ttu-id="cb507-116">Po operacji określono, że określonego błędu protokołu SOAP mogą być zwracane (takie jak w poprzedniej procedurze) do komunikowania się warunek błędu dla aplikacji wywołującej, następnym krokiem jest do zaimplementowania tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="cb507-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="cb507-117">Throw określony błąd protokołu SOAP w operacji</span><span class="sxs-lookup"><span data-stu-id="cb507-117">Throw the specified SOAP fault in the operation</span></span>  
  
1. <span data-ttu-id="cb507-118">Gdy <xref:System.ServiceModel.FaultContractAttribute>— wystąpienia określonego błędu w przypadku operacji zgłosić nową <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> gdzie określony błąd protokołu SOAP jest parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="cb507-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="cb507-119">Poniższy przykład pokazuje, jak zgłaszać `GreetingFault` w `SampleMethod` pokazano w poprzedniej procedurze, a w poniższej sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="cb507-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="cb507-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb507-120">Example</span></span>  
 <span data-ttu-id="cb507-121">Poniższy przykład kodu przedstawia implementację jednej operacji, która określa `GreetingFault` dla `SampleMethod` operacji.</span><span class="sxs-lookup"><span data-stu-id="cb507-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cb507-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb507-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
