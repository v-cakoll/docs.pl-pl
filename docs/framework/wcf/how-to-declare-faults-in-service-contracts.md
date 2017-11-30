---
title: "Porady: deklarowanie błędów w kontraktach usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ebfe56a0e073534840ce81eebb64ce3f5db48a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="b39c7-102">Porady: deklarowanie błędów w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="b39c7-102">How to: Declare Faults in Service Contracts</span></span>
<span data-ttu-id="b39c7-103">W kodzie zarządzanym wyjątki są zgłaszane w przypadku wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="b39c7-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="b39c7-104">W [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji, jednak kontraktów usług określ, jakie informacje o błędzie są zwracane do klientów przez zadeklarowanie błędach SOAP w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="b39c7-104">In [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="b39c7-105">Omówienie relacji między wyjątków i błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="b39c7-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="b39c7-106">Tworzenie kontraktu usługi, która określa błędu protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="b39c7-106">Create a service contract that specifies a SOAP fault</span></span>  
  
1.  <span data-ttu-id="b39c7-107">Tworzenie kontraktu usługi, który zawiera co najmniej jedną operację.</span><span class="sxs-lookup"><span data-stu-id="b39c7-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="b39c7-108">Na przykład zobacz [porady: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b39c7-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="b39c7-109">Wybierz operację, która może określony błąd o tym, które klientów można oczekiwać, że użytkownik jest powiadamiany.</span><span class="sxs-lookup"><span data-stu-id="b39c7-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="b39c7-110">Aby zdecydować, które błędy justify zwracanie błędach SOAP dla klientów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="b39c7-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
3.  <span data-ttu-id="b39c7-111">Zastosuj <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> wybranej operacji i przekazywania błędów można serializować typu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="b39c7-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="b39c7-112">Aby uzyskać szczegółowe informacje na temat tworzenia i używania typów możliwych do serializacji, zobacz [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b39c7-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="b39c7-113">Poniższy przykład przedstawia sposób określić, że `SampleMethod` operacji może spowodować `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="b39c7-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  <span data-ttu-id="b39c7-114">Powtórz kroki 2 i 3 dla wszystkich operacji w kontrakcie, które komunikują się warunki błędów do klientów.</span><span class="sxs-lookup"><span data-stu-id="b39c7-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="b39c7-115">Implementowanie operacji do zwrócenia błędu SOAP określona</span><span class="sxs-lookup"><span data-stu-id="b39c7-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>  
 <span data-ttu-id="b39c7-116">Po operacji określił, że określonego błędu protokołu SOAP mogą być zwracane (na przykład w poprzedniej procedurze) do komunikacji warunek błędu, aby aplikacja wywołująca, następnym krokiem jest wdrożenie tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="b39c7-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="b39c7-117">Throw określonego błędu protokołu SOAP w operacji</span><span class="sxs-lookup"><span data-stu-id="b39c7-117">Throw the specified SOAP fault in the operation</span></span>  
  
1.  <span data-ttu-id="b39c7-118">Gdy <xref:System.ServiceModel.FaultContractAttribute>-wystąpienia określonego błędu w operacji zgłosić nową <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> przypadku parametr typu określony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b39c7-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="b39c7-119">Poniższy przykład przedstawia sposób throw `GreetingFault` w `SampleMethod` pokazane w poprzedniej procedurze, a w poniższej sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="b39c7-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b39c7-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="b39c7-120">Example</span></span>  
 <span data-ttu-id="b39c7-121">Poniższy przykładowy kod przedstawia implementację jednej operacji, która określa `GreetingFault` dla `SampleMethod` operacji.</span><span class="sxs-lookup"><span data-stu-id="b39c7-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b39c7-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b39c7-122">See Also</span></span>  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
