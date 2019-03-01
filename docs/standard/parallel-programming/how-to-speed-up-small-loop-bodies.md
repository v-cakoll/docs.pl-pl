---
title: 'Instrukcje: Przyspieszanie małych jednostek pętli'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fde68d0a938ed04380bf0e99cc0c544793571d77
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965582"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="3cbc1-102">Instrukcje: Przyspieszanie małych jednostek pętli</span><span class="sxs-lookup"><span data-stu-id="3cbc1-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="3cbc1-103">Gdy <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętli ma mały treść, jego może działać wolniej niż równoważna pętli sekwencyjnej, takich jak [dla](../../csharp/language-reference/keywords/for.md) pętli w języku C# i [dla](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) pętli w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3cbc1-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="3cbc1-104">Przyczyną jest obciążenie związane z partycjonowania danych i koszt wywoływania delegata w każdej iteracji pętli niższej wydajności.</span><span class="sxs-lookup"><span data-stu-id="3cbc1-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="3cbc1-105">Do takich scenariuszy <xref:System.Collections.Concurrent.Partitioner> klasa udostępnia <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody, która pozwala na dostarczenie pętli sekwencyjnej jednostka delegata, tak, aby obiekt delegowany jest wywoływany tylko raz w jednej partycji, a nie raz dla iteracji.</span><span class="sxs-lookup"><span data-stu-id="3cbc1-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="3cbc1-106">Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="3cbc1-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cbc1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cbc1-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="3cbc1-108">To podejście pokazano w tym przykładzie jest przydatne, gdy pętla wykonuje minimalnego czasu pracy.</span><span class="sxs-lookup"><span data-stu-id="3cbc1-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="3cbc1-109">Praca staje się bardziej obliczeniowo kosztowne, prawdopodobnie otrzymasz tej samej lub lepszej wydajności przy użyciu <xref:System.Threading.Tasks.Parallel.For%2A> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli za pomocą partycjonera domyślne.</span><span class="sxs-lookup"><span data-stu-id="3cbc1-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cbc1-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cbc1-110">See also</span></span>

- [<span data-ttu-id="3cbc1-111">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="3cbc1-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="3cbc1-112">Niestandardowe partycjonery dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="3cbc1-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="3cbc1-113">Iteratory (C#)</span><span class="sxs-lookup"><span data-stu-id="3cbc1-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="3cbc1-114">Iteratory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cbc1-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="3cbc1-115">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="3cbc1-115">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
