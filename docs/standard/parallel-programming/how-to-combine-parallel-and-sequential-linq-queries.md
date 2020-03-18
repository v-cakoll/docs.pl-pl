---
title: 'Porady: łączenie równoległych i sekwencyjnych zapytań LINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 4c04afb23a168a9cff60962bd5a75a65e3ebca4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134193"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="c55a6-102">Porady: łączenie równoległych i sekwencyjnych zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="c55a6-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="c55a6-103">W tym przykładzie pokazano, jak użyć <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metody do poinstruowania PLINQ do przetwarzania wszystkich kolejnych operatorów w kwerendzie sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="c55a6-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="c55a6-104">Mimo że przetwarzanie sekwencyjne jest zazwyczaj wolniejsze niż równoległe, czasami konieczne jest uzyskanie prawidłowych wyników.</span><span class="sxs-lookup"><span data-stu-id="c55a6-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="c55a6-105">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy.</span><span class="sxs-lookup"><span data-stu-id="c55a6-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c55a6-106">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c55a6-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c55a6-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c55a6-107">Example</span></span>  
 <span data-ttu-id="c55a6-108">W poniższym przykładzie przedstawiono <xref:System.Linq.ParallelEnumerable.AsSequential%2A> jeden scenariusz, w którym jest wymagane, a mianowicie zachować kolejność, która została ustanowiona w poprzedniej klauzuli kwerendy.</span><span class="sxs-lookup"><span data-stu-id="c55a6-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c55a6-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c55a6-109">Compiling the Code</span></span>  
 <span data-ttu-id="c55a6-110">Aby skompilować i uruchomić ten kod, wklej go do projektu PRÓBKI DANYCH `Main` [PLINQ,](../../../docs/standard/parallel-programming/plinq-data-sample.md) dodaj wiersz, aby wywołać metodę z , i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="c55a6-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55a6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c55a6-111">See also</span></span>

- [<span data-ttu-id="c55a6-112">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c55a6-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
