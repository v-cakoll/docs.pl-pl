---
title: 'Instrukcje: Wdrażanie asynchronicznej operacji usługi'
description: Dowiedz się więcej na temat struktury operacji usługi asynchronicznej w obszarze WFC. Operacja usługi może być implementowana asynchronicznie lub synchronicznie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 5f890bd5124e2353cecee37d163b7f2c65b87fde
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244624"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="48750-104">Instrukcje: Wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="48750-104">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="48750-105">W aplikacjach Windows Communication Foundation (WCF) operacja usługi może być implementowana asynchronicznie lub synchronicznie bez konieczności podania klientowi metody wywołania.</span><span class="sxs-lookup"><span data-stu-id="48750-105">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="48750-106">Na przykład asynchroniczne operacje usługi mogą być wywoływane synchronicznie, a operacje usług synchronicznych można wywołać asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="48750-106">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="48750-107">Przykład pokazujący sposób wywołania operacji asynchronicznie w aplikacji klienckiej można znaleźć w temacie [How to: Call operacje usługi asynchronicznie](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="48750-107">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="48750-108">Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Projektowanie kontraktów usług](designing-service-contracts.md) i [operacji synchronicznych i asynchronicznych](synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="48750-108">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="48750-109">W tym temacie opisano podstawową strukturę asynchronicznej operacji usługi, kod nie został ukończony.</span><span class="sxs-lookup"><span data-stu-id="48750-109">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="48750-110">Pełny przykład obu stron usługi i klienta można znaleźć w temacie [asynchronicznie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="48750-110">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="48750-111">Zaimplementuj asynchroniczną operację usługi</span><span class="sxs-lookup"><span data-stu-id="48750-111">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="48750-112">W kontrakcie usługi Zadeklaruj parę metod asynchronicznych zgodnie z wytycznymi dotyczącymi asynchronicznego projektowania platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="48750-112">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="48750-113">`Begin`Metoda przyjmuje parametr, obiekt wywołania zwrotnego i obiekt stanu, a następnie zwraca <xref:System.IAsyncResult?displayProperty=nameWithType> metodę zgodną, `End` która pobiera <xref:System.IAsyncResult?displayProperty=nameWithType> i zwraca wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="48750-113">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="48750-114">Aby uzyskać więcej informacji o wywołaniach asynchronicznych, zobacz [asynchroniczne programowanie wzorów wzorców](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="48750-114">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
2. <span data-ttu-id="48750-115">Oznacz `Begin` metodę pary metod asynchronicznych <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atrybutem i ustaw <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> Właściwość na `true` .</span><span class="sxs-lookup"><span data-stu-id="48750-115">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="48750-116">Na przykład poniższy kod wykonuje kroki 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="48750-116">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="48750-117">Zaimplementuj `Begin/End` parę metod w klasie usługi zgodnie z wytycznymi dotyczącymi projektowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="48750-117">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="48750-118">Na przykład poniższy kod ilustruje implementację, w której ciąg jest zapisywana w konsoli programu `Begin` i `End` części operacji usługi asynchronicznej, a zwracana wartość `End` operacji jest zwracana do klienta.</span><span class="sxs-lookup"><span data-stu-id="48750-118">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="48750-119">Aby zapoznać się z kompletnym przykładem kodu, zapoznaj się z sekcją przykładową.</span><span class="sxs-lookup"><span data-stu-id="48750-119">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="48750-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="48750-120">Example</span></span>  
 <span data-ttu-id="48750-121">Poniżej przedstawiono przykłady kodu:</span><span class="sxs-lookup"><span data-stu-id="48750-121">The following code examples show:</span></span>  
  
1. <span data-ttu-id="48750-122">Interfejs kontraktu usługi z:</span><span class="sxs-lookup"><span data-stu-id="48750-122">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="48750-123">Operacja synchroniczna `SampleMethod` .</span><span class="sxs-lookup"><span data-stu-id="48750-123">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="48750-124">Operacja asynchroniczna `BeginSampleMethod` .</span><span class="sxs-lookup"><span data-stu-id="48750-124">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="48750-125">`BeginServiceAsyncMethod` / `EndServiceAsyncMethod` Para operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="48750-125">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="48750-126">Implementacja usługi przy użyciu <xref:System.IAsyncResult?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="48750-126">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="48750-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48750-127">See also</span></span>

- [<span data-ttu-id="48750-128">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="48750-128">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="48750-129">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="48750-129">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
