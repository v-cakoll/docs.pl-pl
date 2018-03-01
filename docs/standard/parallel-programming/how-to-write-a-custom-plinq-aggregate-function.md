---
title: 'Porady: pisanie niestandardowej funkcji agregowania w PLINQ'
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
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 210e9913ab3eba636ff99b7610df05655246f4eb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="d4d72-102">Porady: pisanie niestandardowej funkcji agregowania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="d4d72-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="d4d72-103">Ten przykład przedstawia sposób użycia <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metody dotyczą funkcji agregacji niestandardowej sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="d4d72-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d4d72-104">W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania.</span><span class="sxs-lookup"><span data-stu-id="d4d72-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="d4d72-105">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="d4d72-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4d72-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4d72-106">Example</span></span>  
 <span data-ttu-id="d4d72-107">W poniższym przykładzie oblicza odchylenie standardowe sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d4d72-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="d4d72-108">W tym przykładzie używane jest przeciążenie operatora agregacji standardowej kwerendy, który jest unikatowy dla PLINQ.</span><span class="sxs-lookup"><span data-stu-id="d4d72-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="d4d72-109">To przeciążenie zajmuje dodatkowy <xref:System.Func%603?displayProperty=nameWithType> jako trzeci parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="d4d72-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="d4d72-110">Ten delegat łączy wyniki ze wszystkich wątków przed przesłaniem ostatecznego obliczenia wyników zagregowany.</span><span class="sxs-lookup"><span data-stu-id="d4d72-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="d4d72-111">W tym przykładzie dodamy razem sumy ze wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="d4d72-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="d4d72-112">Należy pamiętać, że jeśli treści wyrażenia lambda składa się z samym wyrażeniu, zwracana wartość <xref:System.Func%602?displayProperty=nameWithType> delegat jest wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d4d72-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d72-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4d72-113">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="d4d72-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d4d72-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
