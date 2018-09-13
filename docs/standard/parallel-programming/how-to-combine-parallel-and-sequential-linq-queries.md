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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fd67d5f0cb5af33dc2b79f86148557a0dca6ec4
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708708"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="673e6-102">Porady: łączenie równoległych i sekwencyjnych zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="673e6-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="673e6-103">W tym przykładzie pokazano, jak używać <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metodę, aby nakazać PLINQ przetwarzają wszystkie kolejne operatory w zapytaniu sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="673e6-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="673e6-104">Mimo że zazwyczaj mniejsza niż równoległego przetwarzania sekwencyjnych czasami jest niezbędnych do wyprodukowania poprawne wyniki.</span><span class="sxs-lookup"><span data-stu-id="673e6-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="673e6-105">W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty.</span><span class="sxs-lookup"><span data-stu-id="673e6-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="673e6-106">Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="673e6-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="673e6-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="673e6-107">Example</span></span>  
 <span data-ttu-id="673e6-108">W poniższym przykładzie pokazano jeden scenariusz, w którym <xref:System.Linq.ParallelEnumerable.AsSequential%2A> jest wymagany, a mianowicie zachować kolejność, który został ustanowiony klauzuli poprzedniego zapytania.</span><span class="sxs-lookup"><span data-stu-id="673e6-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="673e6-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="673e6-109">Compiling the Code</span></span>  
 <span data-ttu-id="673e6-110">Aby skompilować i uruchomić ten kod, wklej go do [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, Dodaj wiersz w celu wywołania metody z `Main`, i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="673e6-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673e6-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="673e6-111">See also</span></span>

- [<span data-ttu-id="673e6-112">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="673e6-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
