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
ms.openlocfilehash: e98ede3664a8815c60a490239a789c69fa557895
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588559"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="69487-102">Porady: określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="69487-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="69487-103">W tym przykładzie pokazano, jak określić opcje scalania, które będą stosowane do wszystkich kolejnych operatorów w kwerendzie PLINQ.</span><span class="sxs-lookup"><span data-stu-id="69487-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="69487-104">Nie trzeba ustawić opcje scalania jawnie, ale w ten sposób może poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="69487-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="69487-105">Aby uzyskać więcej informacji na temat opcji scalania, zobacz [Opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="69487-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="69487-106">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów.</span><span class="sxs-lookup"><span data-stu-id="69487-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="69487-107">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="69487-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69487-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="69487-108">Example</span></span>  
 <span data-ttu-id="69487-109">Poniższy przykład pokazuje zachowanie opcji scalania w scenariuszu podstawowym, który ma nieuiszczone źródło i stosuje kosztowną funkcję do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="69487-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="69487-110">W przypadkach, <xref:System.Linq.ParallelMergeOptions.AutoBuffered> gdy opcja powoduje wystąpienie niepożądanego opóźnienia przed uzyskaniem <xref:System.Linq.ParallelMergeOptions.NotBuffered> pierwszego elementu, spróbuj użyć opcji, aby uzyskać elementy wynikowe szybciej i płynniej.</span><span class="sxs-lookup"><span data-stu-id="69487-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69487-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69487-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="69487-112">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="69487-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
