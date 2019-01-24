---
title: 'Instrukcje: Pisanie niestandardowej funkcji agregowania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03bbb9b7cf33eda1cc479759740e6c5325f635fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580671"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="eda3a-102">Instrukcje: Pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="eda3a-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="eda3a-103">W tym przykładzie pokazano, jak używać <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metody do stosowania funkcji agregacji niestandardowej sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="eda3a-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="eda3a-104">W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty.</span><span class="sxs-lookup"><span data-stu-id="eda3a-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="eda3a-105">Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="eda3a-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eda3a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="eda3a-106">Example</span></span>  
 <span data-ttu-id="eda3a-107">W poniższym przykładzie oblicza odchylenie standardowe sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="eda3a-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="eda3a-108">W tym przykładzie używane jest przeciążenie agregacji standardowego operatora zapytania unikatowe dla PLINQ.</span><span class="sxs-lookup"><span data-stu-id="eda3a-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="eda3a-109">To przeciążenie zajmuje dodatkowy <xref:System.Func%603?displayProperty=nameWithType> jako trzeci parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="eda3a-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="eda3a-110">Ten delegat łączy wyniki ze wszystkich wątków, przed wykonaniem obliczeń końcowego według wyników zagregowanych.</span><span class="sxs-lookup"><span data-stu-id="eda3a-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="eda3a-111">W tym przykładzie dodamy razem kwoty ze wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="eda3a-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="eda3a-112">Należy pamiętać, że jeśli treść wyrażenia lambda składa się z pojedynczego wyrażenia, wartość zwracana przez <xref:System.Func%602?displayProperty=nameWithType> delegat jest wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="eda3a-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda3a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eda3a-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="eda3a-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="eda3a-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
