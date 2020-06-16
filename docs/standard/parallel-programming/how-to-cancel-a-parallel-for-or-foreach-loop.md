---
title: 'Instrukcje: Anulowanie pętli Parallel.For lub ForEach'
description: Anuluj pętlę Parallel. for lub Parallel. ForEach w środowisku .NET, dostarczając obiekt tokenu anulowania do metody w parametrze ParallelOptions.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: 0a22794f3c45e685a80d36a42ecd849461936c7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769005"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="da3b3-103">Instrukcje: Anulowanie pętli Parallel.For lub ForEach</span><span class="sxs-lookup"><span data-stu-id="da3b3-103">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="da3b3-104"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Metody i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> obsługują anulowanie przy użyciu tokenów anulowania.</span><span class="sxs-lookup"><span data-stu-id="da3b3-104">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="da3b3-105">Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania](../threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="da3b3-105">For more information about cancellation in general, see [Cancellation](../threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="da3b3-106">W pętli równoległej należy dostarczyć <xref:System.Threading.CancellationToken> do metody w <xref:System.Threading.Tasks.ParallelOptions> parametrze, a następnie zawrzeć wywołanie równoległe w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="da3b3-106">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da3b3-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="da3b3-107">Example</span></span>  
 <span data-ttu-id="da3b3-108">Poniższy przykład pokazuje, jak anulować wywołanie do <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="da3b3-108">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="da3b3-109">Można zastosować takie samo podejście do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> wywołania.</span><span class="sxs-lookup"><span data-stu-id="da3b3-109">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="da3b3-110">Jeśli token sygnalizujący anulowanie jest tym samym tokenem, który jest określony w <xref:System.Threading.Tasks.ParallelOptions> wystąpieniu, pętla równoległa zgłosi pojedynczy <xref:System.OperationCanceledException> przy anulowaniu.</span><span class="sxs-lookup"><span data-stu-id="da3b3-110">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="da3b3-111">Jeśli jakiś inny token powoduje anulowanie, pętla zgłosi obiekt <xref:System.AggregateException> with <xref:System.OperationCanceledException> jako InnerException.</span><span class="sxs-lookup"><span data-stu-id="da3b3-111">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da3b3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da3b3-112">See also</span></span>

- [<span data-ttu-id="da3b3-113">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="da3b3-113">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="da3b3-114">Wyrażenia lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="da3b3-114">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
