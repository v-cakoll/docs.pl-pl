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
ms.openlocfilehash: 40abe2f101f6fa23d804ef30e27d642a36908196
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139269"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="9db79-102">Porady: określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="9db79-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="9db79-103">W tym przykładzie pokazano, jak określić opcje scalania, które będą stosowane do wszystkich kolejnych operatorów w kwerendzie PLINQ.</span><span class="sxs-lookup"><span data-stu-id="9db79-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="9db79-104">Nie trzeba jawnie ustawiać opcji scalania, ale może to poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="9db79-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="9db79-105">Aby uzyskać więcej informacji na temat opcji scalania, zobacz [Opcje scalania w pliku PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="9db79-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="9db79-106">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy.</span><span class="sxs-lookup"><span data-stu-id="9db79-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="9db79-107">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="9db79-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9db79-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="9db79-108">Example</span></span>  
 <span data-ttu-id="9db79-109">W poniższym przykładzie przedstawiono zachowanie opcji scalania w podstawowym scenariuszu, który ma nieuporządkowane źródło i stosuje kosztowną funkcję do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="9db79-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="9db79-110">W przypadkach, <xref:System.Linq.ParallelMergeOptions.AutoBuffered> gdy opcja powoduje niepożądane opóźnienie przed pierwszym elementem jest <xref:System.Linq.ParallelMergeOptions.NotBuffered> plonowany, spróbuj opcji, aby uzyskać wynik elementów szybciej i bardziej płynnie.</span><span class="sxs-lookup"><span data-stu-id="9db79-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db79-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9db79-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="9db79-112">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9db79-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
