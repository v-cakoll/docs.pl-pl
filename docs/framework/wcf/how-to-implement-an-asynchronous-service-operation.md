---
title: 'Instrukcje: Wdrażanie asynchronicznej operacji usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 603ee57475b3e7b1af607d49050e3276fd3082d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298659"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="bb0e5-102">Instrukcje: Wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="bb0e5-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="bb0e5-103">W aplikacjach Windows Communication Foundation (WCF) Operacja usługi może być implementowany asynchronicznego lub synchronicznego bez dyktowanie do klienta, jak wywołać go.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="bb0e5-104">Na przykład operacje asynchroniczne usługi może być wywoływana synchronicznie, a operacje synchroniczne usługi, które mogą być wywoływane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="bb0e5-105">Na przykład, który pokazuje, jak asynchroniczne wywoływanie operacji w aplikacji klienckiej, zobacz [jak: Asynchroniczne wywoływanie operacji usługi](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="bb0e5-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="bb0e5-106">Aby uzyskać więcej informacji na temat operacje synchroniczne i asynchroniczne, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md) i [synchroniczne i asynchroniczne operacje](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="bb0e5-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) and [Synchronous and Asynchronous Operations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="bb0e5-107">W tym temacie opisano podstawowe struktury asynchronicznej operacji usługi, gdy kod nie jest gotowy.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="bb0e5-108">Aby uzyskać pełny przykład stron usługi i klienta, zobacz [asynchroniczne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bb0e5-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="bb0e5-109">Asynchroniczne wykonania operacji usługi</span><span class="sxs-lookup"><span data-stu-id="bb0e5-109">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="bb0e5-110">W Twojej umowy serwisowej zadeklarować pary metod asynchronicznych, zgodnie z wytycznymi projektowania asynchronicznego .NET.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="bb0e5-111">`Begin` Metoda przyjmuje parametr, obiektu wywołania zwrotnego i obiektu stanu i zwraca <xref:System.IAsyncResult?displayProperty=nameWithType> i pasującą `End` metody, która przyjmuje <xref:System.IAsyncResult?displayProperty=nameWithType> i zwraca wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="bb0e5-112">Aby uzyskać więcej informacji na temat wywołania asynchroniczne, zobacz [Asynchronous Programming Patterns projektowania](https://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="bb0e5-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2. <span data-ttu-id="bb0e5-113">Oznacz `Begin` metoda pary metod asynchronicznych za pomocą <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atrybut i ustawić <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="bb0e5-114">Na przykład poniższy kod wykonuje kroki 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="bb0e5-115">Implementowanie `Begin/End` pary metod w klasie usługi zgodnie z wytycznymi projektowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="bb0e5-116">Na przykład poniższy kod pokazuje implementację, w którym ciąg jest zapisywany do konsoli w obu `Begin` i `End` fragmenty asynchronicznej operacji usługi i wartość zwracana przez `End` operacji zwracana do klienta.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="bb0e5-117">W przykładzie kompletny kod znajduje się w sekcji przykład.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="bb0e5-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb0e5-118">Example</span></span>  
 <span data-ttu-id="bb0e5-119">W poniższych przykładach kodu pokazano:</span><span class="sxs-lookup"><span data-stu-id="bb0e5-119">The following code examples show:</span></span>  
  
1. <span data-ttu-id="bb0e5-120">Przy użyciu interfejsu kontraktu usługi:</span><span class="sxs-lookup"><span data-stu-id="bb0e5-120">A service contract interface with:</span></span>  
  
    1.  <span data-ttu-id="bb0e5-121">Synchroniczne `SampleMethod` operacji.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2.  <span data-ttu-id="bb0e5-122">Asynchroniczna `BeginSampleMethod` operacji.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3.  <span data-ttu-id="bb0e5-123">Asynchroniczna `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` pary operacji.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="bb0e5-124">Implementacja usługi przy użyciu <xref:System.IAsyncResult?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bb0e5-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bb0e5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb0e5-125">See also</span></span>

- [<span data-ttu-id="bb0e5-126">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="bb0e5-126">Designing Service Contracts</span></span>](../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="bb0e5-127">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="bb0e5-127">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
