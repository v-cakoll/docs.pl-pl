---
title: 'Porady: anulowanie równoległej pętli For lub pętli ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: 67f1f91f235cc88deaa97d412f368819ae0a8cda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134244"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="4e69f-102">Porady: anulowanie równoległej pętli For lub pętli ForEach</span><span class="sxs-lookup"><span data-stu-id="4e69f-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="4e69f-103">Metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> obsługują anulowanie przy użyciu tokenów anulowania.</span><span class="sxs-lookup"><span data-stu-id="4e69f-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="4e69f-104">Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="4e69f-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="4e69f-105">W pętli równoległej należy dostarczyć <xref:System.Threading.CancellationToken> do metody w parametrze <xref:System.Threading.Tasks.ParallelOptions>, a następnie zawrzeć wywołanie równoległe w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="4e69f-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e69f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e69f-106">Example</span></span>  
 <span data-ttu-id="4e69f-107">Poniższy przykład pokazuje, jak anulować wywołanie do <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e69f-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4e69f-108">Można zastosować takie samo podejście do wywołania <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e69f-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="4e69f-109">Jeśli token sygnalizujący anulowanie jest tym samym tokenem, który jest określony w wystąpieniu <xref:System.Threading.Tasks.ParallelOptions>, pętla równoległa zgłosi pojedynczy <xref:System.OperationCanceledException> po anulowaniu.</span><span class="sxs-lookup"><span data-stu-id="4e69f-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="4e69f-110">Jeśli jakiś inny token powoduje anulowanie, pętla zgłosi <xref:System.AggregateException> z <xref:System.OperationCanceledException> jako InnerException.</span><span class="sxs-lookup"><span data-stu-id="4e69f-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e69f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e69f-111">See also</span></span>

- [<span data-ttu-id="4e69f-112">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="4e69f-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="4e69f-113">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="4e69f-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
