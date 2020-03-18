---
title: 'Porady: pisanie niestandardowej funkcji agregowania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 7bb4cc1b69f0b6b97c1cf6255ded5341304f3ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106768"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="42a66-102">Porady: pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="42a66-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="42a66-103">W tym przykładzie pokazano, jak użyć <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metody, aby zastosować niestandardową funkcję agregacji do sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="42a66-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="42a66-104">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy.</span><span class="sxs-lookup"><span data-stu-id="42a66-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="42a66-105">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="42a66-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42a66-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="42a66-106">Example</span></span>  
 <span data-ttu-id="42a66-107">W poniższym przykładzie oblicza odchylenie standardowe sekwencji liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="42a66-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="42a66-108">W tym przykładzie użyto przeciążenia operatora zagregowanej kwerendy standardowej, który jest unikatowy dla PLINQ.</span><span class="sxs-lookup"><span data-stu-id="42a66-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="42a66-109">To przeciążenie <xref:System.Func%603?displayProperty=nameWithType> ma dodatkowe jako trzeci parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="42a66-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="42a66-110">Ten pełnomocnik łączy wyniki ze wszystkich wątków, zanim wykona ostateczne obliczenia na zagregowanych wynikach.</span><span class="sxs-lookup"><span data-stu-id="42a66-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="42a66-111">W tym przykładzie dodajemy razem sumy ze wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="42a66-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="42a66-112">Należy zauważyć, że gdy obiekt wyrażenia lambda składa się <xref:System.Func%602?displayProperty=nameWithType> z pojedynczego wyrażenia, zwracana wartość delegata jest wartością wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="42a66-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a66-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42a66-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="42a66-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="42a66-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
