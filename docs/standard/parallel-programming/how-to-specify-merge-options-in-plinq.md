---
title: "Porady: określanie opcji scalania w PLINQ"
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
helpviewer_keywords: PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec601e8bbefd31650fb91c438b032942cfc93101
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="e0bb9-102">Porady: określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="e0bb9-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="e0bb9-103">W tym przykładzie przedstawiono sposób Określanie opcji scalania, które będą stosowane do wszystkich kolejnych operatorów w zapytaniu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="e0bb9-104">Nie trzeba jawnie ustaw opcje scalania, ale może to zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="e0bb9-105">Aby uzyskać więcej informacji na temat opcji scalania, zobacz [opcje scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e0bb9-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="e0bb9-106">W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="e0bb9-107">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e0bb9-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0bb9-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0bb9-108">Example</span></span>  
 <span data-ttu-id="e0bb9-109">W poniższym przykładzie pokazano zachowanie opcji scalania w scenariuszu podstawowe nieuporządkowaną źródła i stosuje funkcję kosztowne do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="e0bb9-110">W przypadkach, gdy <xref:System.Linq.ParallelMergeOptions.AutoBuffered> opcja generuje niepożądanych czas oczekiwania przed pierwszym elementem jest zwróciło, spróbuj <xref:System.Linq.ParallelMergeOptions.NotBuffered> opcji umożliwiające uzyskanie wyniku elementy szybciej i bardziej gładko.</span><span class="sxs-lookup"><span data-stu-id="e0bb9-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bb9-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0bb9-111">See Also</span></span>  
 <xref:System.Linq.ParallelMergeOptions>  
 [<span data-ttu-id="e0bb9-112">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e0bb9-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
