---
title: 'Instrukcje: Deklarowanie błędów w kontraktach usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 6f08ef6eb62b31b0969779d51d0a068145a23fc0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971965"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="2631a-102">Instrukcje: Deklarowanie błędów w kontraktach usługi</span><span class="sxs-lookup"><span data-stu-id="2631a-102">How to: Declare Faults in Service Contracts</span></span>

<span data-ttu-id="2631a-103">W kodzie zarządzanym wyjątki są generowane, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="2631a-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="2631a-104">W aplikacjach Windows Communication Foundation (WCF), jednak kontrakty usługi określają, jakie informacje o błędzie są zwracane do klientów, deklarując błędy protokołu SOAP w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="2631a-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="2631a-105">Omówienie relacji między wyjątkami i błędami można znaleźć [w temacie określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="2631a-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="2631a-106">Tworzenie kontraktu usługi określającego błąd protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="2631a-106">Create a service contract that specifies a SOAP fault</span></span>

1. <span data-ttu-id="2631a-107">Utwórz kontrakt usługi, który zawiera co najmniej jedną operację.</span><span class="sxs-lookup"><span data-stu-id="2631a-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="2631a-108">Aby zapoznać się z przykładem, zobacz [How to: Zdefiniuj kontrakt](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)usługi.</span><span class="sxs-lookup"><span data-stu-id="2631a-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>

2. <span data-ttu-id="2631a-109">Wybierz operację, która może określić warunek błędu informujący o tym, które klienci mogą być powiadamiane.</span><span class="sxs-lookup"><span data-stu-id="2631a-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="2631a-110">Aby określić, które warunki błędu uzasadniają zwrócenie błędów SOAP do klientów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="2631a-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

3. <span data-ttu-id="2631a-111"><xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> Zastosuj do wybranej operacji i przekaż typ błędu serializacji do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2631a-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="2631a-112">Aby uzyskać szczegółowe informacje na temat tworzenia i używania typów możliwych do serializacji, zobacz [określanie transfer danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="2631a-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="2631a-113">Poniższy przykład pokazuje, jak określić, że `SampleMethod` operacja może skutkować. `GreetingFault`</span><span class="sxs-lookup"><span data-stu-id="2631a-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>

     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. <span data-ttu-id="2631a-114">Powtórz kroki 2 i 3 dla wszystkich operacji w kontrakcie, które komunikują się z warunkami błędów z klientami.</span><span class="sxs-lookup"><span data-stu-id="2631a-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="2631a-115">Implementowanie operacji zwracającej określony błąd protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="2631a-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>
 <span data-ttu-id="2631a-116">Po określeniu przez operację, że można zwrócić określony błąd protokołu SOAP (na przykład w poprzedniej procedurze) do przekazania warunku błędu do aplikacji wywołującej, następnym krokiem jest wdrożenie tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2631a-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>

### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="2631a-117">Zgłoś błąd protokołu SOAP w operacji</span><span class="sxs-lookup"><span data-stu-id="2631a-117">Throw the specified SOAP fault in the operation</span></span>

1. <span data-ttu-id="2631a-118">Gdy w operacji występuje określony warunek błędu, należy zgłosić nowe <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> miejsce, gdzie określony błąd protokołu SOAP jest parametrem typu. <xref:System.ServiceModel.FaultContractAttribute></span><span class="sxs-lookup"><span data-stu-id="2631a-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="2631a-119">Poniższy przykład pokazuje, `GreetingFault` jak zgłosić `SampleMethod` wynik w powyższej procedurze i w poniższej sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="2631a-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>

     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a><span data-ttu-id="2631a-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="2631a-120">Example</span></span>

<span data-ttu-id="2631a-121">Poniższy przykład kodu pokazuje implementację pojedynczej operacji, która określa `GreetingFault` `SampleMethod` dla operacji.</span><span class="sxs-lookup"><span data-stu-id="2631a-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>

[!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a><span data-ttu-id="2631a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2631a-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
