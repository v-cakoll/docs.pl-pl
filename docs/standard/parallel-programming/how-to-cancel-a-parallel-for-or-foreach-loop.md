---
title: "Porady: anulowanie równoległej pętli For lub pętli ForEach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="ad995-102">Porady: anulowanie równoległej pętli For lub pętli ForEach</span><span class="sxs-lookup"><span data-stu-id="ad995-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="ad995-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody obsługują anulowania przy użyciu anulowanie tokenów.</span><span class="sxs-lookup"><span data-stu-id="ad995-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="ad995-104">Aby uzyskać więcej informacji na temat anulowania ogólnie rzecz biorąc, zobacz [anulowania](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="ad995-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="ad995-105">W pętli równoległej, możesz podać <xref:System.Threading.CancellationToken> do metody w <xref:System.Threading.Tasks.ParallelOptions> parametr, a następnie umieść wywołanie równoległe w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="ad995-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad995-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad995-106">Example</span></span>  
 <span data-ttu-id="ad995-107">Poniższy przykład przedstawia sposób anulowania wywołania <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad995-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ad995-108">Możesz zastosować te same podejście do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> wywołania.</span><span class="sxs-lookup"><span data-stu-id="ad995-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="ad995-109">Jeśli token anulowania sygnały ma ten sam token określonym w <xref:System.Threading.Tasks.ParallelOptions> wystąpienia, a następnie równoległej pętli zgłosi pojedynczy <xref:System.OperationCanceledException> na anulowanie.</span><span class="sxs-lookup"><span data-stu-id="ad995-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="ad995-110">Jeśli niektóre inne token spowoduje anulowanie, pętla będzie zgłaszać wyjątek <xref:System.AggregateException> z <xref:System.OperationCanceledException> jako we właściwości InnerException.</span><span class="sxs-lookup"><span data-stu-id="ad995-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad995-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad995-111">See Also</span></span>  
 [<span data-ttu-id="ad995-112">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="ad995-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="ad995-113">Wyrażenia lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="ad995-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
