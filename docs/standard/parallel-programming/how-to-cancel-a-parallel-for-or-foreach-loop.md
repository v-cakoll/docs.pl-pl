---
title: 'Instrukcje: Anulowanie pętli Parallel.For lub ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cdb6e059fb1c7001bbe4da60e2936b1ad40cc1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638895"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="1efd8-102">Instrukcje: Anulowanie pętli Parallel.For lub ForEach</span><span class="sxs-lookup"><span data-stu-id="1efd8-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="1efd8-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody obsługują anulowania przy użyciu tokenów anulowania.</span><span class="sxs-lookup"><span data-stu-id="1efd8-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="1efd8-104">Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowania](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="1efd8-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="1efd8-105">W pętli równoległej, możesz podać <xref:System.Threading.CancellationToken> do metody w <xref:System.Threading.Tasks.ParallelOptions> parametru i następnie umieść wywołanie równoległe w bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="1efd8-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1efd8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1efd8-106">Example</span></span>  
 <span data-ttu-id="1efd8-107">Poniższy przykład pokazuje, jak anulować wywołanie <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1efd8-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1efd8-108">Można zastosować to samo podejście do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> wywołania.</span><span class="sxs-lookup"><span data-stu-id="1efd8-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="1efd8-109">Jeśli token, który sygnalizuje anulowania jest taka sama tokenu określonym w <xref:System.Threading.Tasks.ParallelOptions> wystąpienia, a następnie pętli równoległej zgłosi pojedynczej <xref:System.OperationCanceledException> na anulowanie.</span><span class="sxs-lookup"><span data-stu-id="1efd8-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="1efd8-110">Jeśli niektóre inne tokenu powoduje unieważnienie, pętla będzie sygnalizować <xref:System.AggregateException> z <xref:System.OperationCanceledException> jako wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="1efd8-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efd8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1efd8-111">See also</span></span>

- [<span data-ttu-id="1efd8-112">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="1efd8-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="1efd8-113">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="1efd8-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
