---
title: 'Instrukcje: Określanie opcji scalania w PLINQ'
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
ms.openlocfilehash: 87079337ae3cea81dbb4aab13ec2043b74498d9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573580"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="54146-102">Instrukcje: Określanie opcji scalania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="54146-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="54146-103">W tym przykładzie przedstawiono sposób Określanie opcji scalania, które będą stosowane do wszystkie kolejne operatory w zapytaniu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="54146-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="54146-104">Nie trzeba jawnie ustawić opcje scalania, ale może to poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="54146-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="54146-105">Aby uzyskać więcej informacji na temat opcji scalania, zobacz [opcji scalania w PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="54146-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="54146-106">W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty.</span><span class="sxs-lookup"><span data-stu-id="54146-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="54146-107">Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="54146-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54146-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="54146-108">Example</span></span>  
 <span data-ttu-id="54146-109">W poniższym przykładzie pokazano zachowanie opcji scalania w podstawowy scenariusz, nieuporządkowane źródła i stosuje kosztowna funkcja do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="54146-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="54146-110">W przypadkach, gdzie <xref:System.Linq.ParallelMergeOptions.AutoBuffered> opcji powoduje niepożądanych opóźnienie przed pierwszym elementem jest uzyskane, spróbuj <xref:System.Linq.ParallelMergeOptions.NotBuffered> opcji umożliwiające uzyskanie wyniku elementów, szybciej i sprawniej.</span><span class="sxs-lookup"><span data-stu-id="54146-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54146-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54146-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="54146-112">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="54146-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
