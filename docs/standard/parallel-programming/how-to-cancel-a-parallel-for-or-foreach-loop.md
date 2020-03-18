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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134244"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="e680c-102">Porady: anulowanie równoległej pętli For lub pętli ForEach</span><span class="sxs-lookup"><span data-stu-id="e680c-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="e680c-103">Metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> i obsługują anulowanie za pomocą tokenów anulowania.</span><span class="sxs-lookup"><span data-stu-id="e680c-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="e680c-104">Aby uzyskać więcej informacji na temat anulowania w ogóle, zobacz [Anulowanie](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="e680c-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="e680c-105">W pętli równoległej <xref:System.Threading.CancellationToken> należy podać <xref:System.Threading.Tasks.ParallelOptions> do metody w parametrze, a następnie ująć wywołanie równoległe w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="e680c-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e680c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e680c-106">Example</span></span>  
 <span data-ttu-id="e680c-107">W poniższym przykładzie pokazano, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>jak anulować połączenie .</span><span class="sxs-lookup"><span data-stu-id="e680c-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e680c-108">Do wywołania <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> można zastosować to samo podejście.</span><span class="sxs-lookup"><span data-stu-id="e680c-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="e680c-109">Jeśli token, który sygnalizuje anulowanie jest tym <xref:System.Threading.Tasks.ParallelOptions> samym tokenem, który jest <xref:System.OperationCanceledException> określony w wystąpieniu, pętla równoległa spowoduje wyrzucenie pojedynczego podczas anulowania.</span><span class="sxs-lookup"><span data-stu-id="e680c-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="e680c-110">Jeśli inny token powoduje anulowanie, <xref:System.AggregateException> pętla <xref:System.OperationCanceledException> będzie zgłaszać z jako InnerException.</span><span class="sxs-lookup"><span data-stu-id="e680c-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e680c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e680c-111">See also</span></span>

- [<span data-ttu-id="e680c-112">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="e680c-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="e680c-113">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="e680c-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
