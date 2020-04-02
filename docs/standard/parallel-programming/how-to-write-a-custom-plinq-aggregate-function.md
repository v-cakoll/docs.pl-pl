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
ms.openlocfilehash: 8168c89a6edecd5f7e33a710c9a89c92a6f82005
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588227"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="6daba-102">Porady: pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="6daba-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="6daba-103">W tym przykładzie <xref:System.Linq.ParallelEnumerable.Aggregate%2A> pokazano, jak użyć metody, aby zastosować funkcję agregacji niestandardowej do sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="6daba-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="6daba-104">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów.</span><span class="sxs-lookup"><span data-stu-id="6daba-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="6daba-105">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="6daba-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6daba-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6daba-106">Example</span></span>  
 <span data-ttu-id="6daba-107">Poniższy przykład oblicza odchylenie standardowe sekwencji liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="6daba-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="6daba-108">W tym przykładzie użyto przeciążenia operatora zapytania agregacji standardowej, który jest unikatowy dla PLINQ.</span><span class="sxs-lookup"><span data-stu-id="6daba-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="6daba-109">To przeciążenie <xref:System.Func%603?displayProperty=nameWithType> ma dodatkowe jako trzeci parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="6daba-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="6daba-110">Ten delegat łączy wyniki ze wszystkich wątków, zanim wykona ostateczne obliczenia na zagregowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="6daba-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="6daba-111">W tym przykładzie sumujemy sumy ze wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="6daba-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="6daba-112">Należy zauważyć, że gdy wyrażenie lambda treści składa się <xref:System.Func%602?displayProperty=nameWithType> z pojedynczego wyrażenia, zwracana wartość delegata jest wartością wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6daba-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6daba-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6daba-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="6daba-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="6daba-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
