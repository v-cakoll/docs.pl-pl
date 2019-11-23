---
title: 'Instrukcje: Wdrażanie asynchronicznej operacji usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: b706ec49db123f33b3fc1ab0f420ed9a47e32f67
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320953"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="67576-102">Instrukcje: Wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="67576-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="67576-103">W aplikacjach Windows Communication Foundation (WCF) operacja usługi może być implementowana asynchronicznie lub synchronicznie bez konieczności podania klientowi metody wywołania.</span><span class="sxs-lookup"><span data-stu-id="67576-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="67576-104">Na przykład asynchroniczne operacje usługi mogą być wywoływane synchronicznie, a operacje usług synchronicznych można wywołać asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="67576-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="67576-105">Przykład pokazujący sposób wywołania operacji asynchronicznie w aplikacji klienckiej można znaleźć w temacie [How to: Call operacje usługi asynchronicznie](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="67576-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="67576-106">Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Projektowanie kontraktów usług](designing-service-contracts.md) i [operacji synchronicznych i asynchronicznych](synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="67576-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="67576-107">W tym temacie opisano podstawową strukturę asynchronicznej operacji usługi, kod nie został ukończony.</span><span class="sxs-lookup"><span data-stu-id="67576-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="67576-108">Pełny przykład obu stron usługi i klienta można znaleźć w temacie [asynchronicznie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="67576-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="67576-109">Zaimplementuj asynchroniczną operację usługi</span><span class="sxs-lookup"><span data-stu-id="67576-109">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="67576-110">W kontrakcie usługi Zadeklaruj parę metod asynchronicznych zgodnie z wytycznymi dotyczącymi asynchronicznego projektowania platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="67576-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="67576-111">Metoda `Begin` przyjmuje parametr, obiekt wywołania zwrotnego i obiekt stanu, a następnie zwraca <xref:System.IAsyncResult?displayProperty=nameWithType> i pasującą metodę `End`, która przyjmuje <xref:System.IAsyncResult?displayProperty=nameWithType> i zwraca wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="67576-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="67576-112">Aby uzyskać więcej informacji o wywołaniach asynchronicznych, zobacz [asynchroniczne programowanie wzorów wzorców](https://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="67576-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2. <span data-ttu-id="67576-113">Oznacz metodę `Begin` pary metod asynchronicznych atrybutem <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> i ustaw właściwość <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="67576-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="67576-114">Na przykład poniższy kod wykonuje kroki 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="67576-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="67576-115">Zaimplementuj parę metod `Begin/End` w klasie usługi zgodnie z wytycznymi dotyczącymi projektowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="67576-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="67576-116">Na przykład poniższy kod ilustruje implementację, w której ciąg jest zapisywana w konsoli programu zarówno `Begin`, jak i `End` części operacji usługi asynchronicznej, a zwracana wartość operacji `End` jest zwracana do klienta.</span><span class="sxs-lookup"><span data-stu-id="67576-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="67576-117">Aby zapoznać się z kompletnym przykładem kodu, zapoznaj się z sekcją przykładową.</span><span class="sxs-lookup"><span data-stu-id="67576-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="67576-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="67576-118">Example</span></span>  
 <span data-ttu-id="67576-119">Poniżej przedstawiono przykłady kodu:</span><span class="sxs-lookup"><span data-stu-id="67576-119">The following code examples show:</span></span>  
  
1. <span data-ttu-id="67576-120">Interfejs kontraktu usługi z:</span><span class="sxs-lookup"><span data-stu-id="67576-120">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="67576-121">Synchroniczna operacja `SampleMethod`.</span><span class="sxs-lookup"><span data-stu-id="67576-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="67576-122">Asynchroniczna operacja `BeginSampleMethod`.</span><span class="sxs-lookup"><span data-stu-id="67576-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="67576-123">Para operacji `EndServiceAsyncMethod` asynchronicznych /`BeginServiceAsyncMethod`.</span><span class="sxs-lookup"><span data-stu-id="67576-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="67576-124">Implementacja usługi przy użyciu obiektu <xref:System.IAsyncResult?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67576-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="67576-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67576-125">See also</span></span>

- [<span data-ttu-id="67576-126">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="67576-126">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="67576-127">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="67576-127">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
