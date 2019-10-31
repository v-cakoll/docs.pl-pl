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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134193"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="86fdf-102">Porady: łączenie równoległych i sekwencyjnych zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="86fdf-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="86fdf-103">W tym przykładzie pokazano, jak za pomocą metody <xref:System.Linq.ParallelEnumerable.AsSequential%2A> poinstruować PLINQ, aby przetwarzać wszystkie kolejne operatory w kwerendzie sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="86fdf-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="86fdf-104">Chociaż przetwarzanie sekwencyjne jest ogólnie wolniejsze niż równoległe, czasami konieczne jest wygenerowanie poprawnych wyników.</span><span class="sxs-lookup"><span data-stu-id="86fdf-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="86fdf-105">Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie.</span><span class="sxs-lookup"><span data-stu-id="86fdf-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="86fdf-106">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="86fdf-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86fdf-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="86fdf-107">Example</span></span>  
 <span data-ttu-id="86fdf-108">W poniższym przykładzie przedstawiono jeden scenariusz, w którym <xref:System.Linq.ParallelEnumerable.AsSequential%2A> jest wymagane, a mianowicie zachowanie kolejności, która została ustanowiona w poprzedniej klauzuli zapytania.</span><span class="sxs-lookup"><span data-stu-id="86fdf-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86fdf-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="86fdf-109">Compiling the Code</span></span>  
 <span data-ttu-id="86fdf-110">Aby skompilować i uruchomić ten kod, wklej go do projektu [przykładu danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) , Dodaj wiersz, aby wywołać metodę z `Main`i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="86fdf-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86fdf-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86fdf-111">See also</span></span>

- [<span data-ttu-id="86fdf-112">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="86fdf-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
