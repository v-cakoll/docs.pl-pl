---
title: 'Porady: określanie opcji scalania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1f30245b398ae894e7226d1e94046fc9111dcf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="1b2dc-102">Porady: określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="1b2dc-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="1b2dc-103">W tym przykładzie przedstawiono sposób Określanie opcji scalania, które będą stosowane do wszystkich kolejnych operatorów w zapytaniu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="1b2dc-104">Nie trzeba jawnie ustaw opcje scalania, ale może to zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="1b2dc-105">Aby uzyskać więcej informacji na temat opcji scalania, zobacz [opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="1b2dc-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1b2dc-106">W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1b2dc-107">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="1b2dc-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b2dc-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b2dc-108">Example</span></span>  
 <span data-ttu-id="1b2dc-109">W poniższym przykładzie pokazano zachowanie opcji scalania w scenariuszu podstawowe nieuporządkowaną źródła i stosuje funkcję kosztowne do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="1b2dc-110">W przypadkach, gdy <xref:System.Linq.ParallelMergeOptions.AutoBuffered> opcja generuje niepożądanych czas oczekiwania przed pierwszym elementem jest zwróciło, spróbuj <xref:System.Linq.ParallelMergeOptions.NotBuffered> opcji umożliwiające uzyskanie wyniku elementy szybciej i bardziej gładko.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b2dc-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b2dc-111">See Also</span></span>  
 <xref:System.Linq.ParallelMergeOptions>  
 [<span data-ttu-id="1b2dc-112">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1b2dc-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
