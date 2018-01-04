---
title: "Instrukcje: Wdrażanie asynchronicznej operacji usługi"
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
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 276dd3cc84c15c66adeab30f86583e6d9eec4144
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="85c56-102">Instrukcje: Wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="85c56-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="85c56-103">W [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji, operacja usługi można zaimplementować asynchronicznie lub synchronicznie bez dyktowanie do klienta, jak wywołać ją.</span><span class="sxs-lookup"><span data-stu-id="85c56-103">In [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="85c56-104">Na przykład można można synchronicznie wywoływania operacji asynchronicznych usługi i operacji synchronicznych usługi może być wywołana asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="85c56-104">For example, asynchronous service operations can be calling synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="85c56-105">Na przykład pokazujący sposób asynchroniczne wywoływanie operacji w aplikacji klienta, zobacz [porady: wywołania operacji usługi asynchronicznie](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="85c56-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="85c56-106">operacje synchroniczne i asynchroniczne, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md) i [synchroniczne i asynchroniczne operacje](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="85c56-106"> synchronous and asynchronous operations, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) and [Synchronous and Asynchronous Operations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="85c56-107">W tym temacie opisano podstawową strukturę asynchronicznej operacji usługi, kodu nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="85c56-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="85c56-108">Pełny przykład stron usługa i klient zobacz [asynchronicznym](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).</span><span class="sxs-lookup"><span data-stu-id="85c56-108">For a complete example of both the service and client sides see [Asynchronous](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="85c56-109">Implementuje operację usługi asynchronicznie</span><span class="sxs-lookup"><span data-stu-id="85c56-109">Implement a service operation asynchronously</span></span>  
  
1.  <span data-ttu-id="85c56-110">W umowy serwisowej należy zadeklarować pary metod asynchronicznych zgodnie z wytycznymi projektowania asynchroniczne .NET.</span><span class="sxs-lookup"><span data-stu-id="85c56-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="85c56-111">`Begin` Metoda przyjmuje parametr obiektu wywołania zwrotnego i obiektu stanu i zwraca <xref:System.IAsyncResult?displayProperty=nameWithType> i odpowiadający mu `End` metody pobierającej <xref:System.IAsyncResult?displayProperty=nameWithType> i zwraca wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="85c56-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="85c56-112">Aby uzyskać więcej informacji dotyczących wywołań asynchronicznych, zobacz [asynchroniczne wzorce projektowe programowania](http://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="85c56-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](http://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2.  <span data-ttu-id="85c56-113">Oznacz `Begin` metody pary metod asynchronicznych z <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atrybutu i ustaw <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="85c56-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="85c56-114">Na przykład następujący kod wykonuje kroki 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="85c56-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  <span data-ttu-id="85c56-115">Implementowanie `Begin/End` pary metod w klasie usługi, zgodnie z wytycznymi projektowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="85c56-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="85c56-116">Na przykład poniższy przykładowy kod przedstawia implementację, w którym napisano ciąg do konsoli w obu `Begin` i `End` części asynchronicznej operacji usługi, a wartość zwracaną `End` operacji zwracana do klienta.</span><span class="sxs-lookup"><span data-stu-id="85c56-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="85c56-117">Na przykład kompletny kod zobacz sekcję przykład.</span><span class="sxs-lookup"><span data-stu-id="85c56-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="85c56-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="85c56-118">Example</span></span>  
 <span data-ttu-id="85c56-119">W poniższych przykładach kodu pokazano:</span><span class="sxs-lookup"><span data-stu-id="85c56-119">The following code examples show:</span></span>  
  
1.  <span data-ttu-id="85c56-120">Interfejsu kontraktu usługi z:</span><span class="sxs-lookup"><span data-stu-id="85c56-120">A service contract interface with:</span></span>  
  
    1.  <span data-ttu-id="85c56-121">Synchronicznego `SampleMethod` operacji.</span><span class="sxs-lookup"><span data-stu-id="85c56-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2.  <span data-ttu-id="85c56-122">Asynchroniczne `BeginSampleMethod` operacji.</span><span class="sxs-lookup"><span data-stu-id="85c56-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3.  <span data-ttu-id="85c56-123">Asynchroniczne `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` pary operacji.</span><span class="sxs-lookup"><span data-stu-id="85c56-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2.  <span data-ttu-id="85c56-124">Implementacja usługi przy użyciu <xref:System.IAsyncResult?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="85c56-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="85c56-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85c56-125">See Also</span></span>  
 [<span data-ttu-id="85c56-126">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="85c56-126">Designing Service Contracts</span></span>](../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="85c56-127">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="85c56-127">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
