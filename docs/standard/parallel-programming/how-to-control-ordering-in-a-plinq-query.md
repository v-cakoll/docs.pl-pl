---
title: 'Porady: sterowanie szeregowaniem w zapytaniu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: d38c039fa99433d9476d62c1e96dff7e306fd766
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123121"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="7c03c-102">Porady: sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="7c03c-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="7c03c-103">W poniższych przykładach pokazano, jak kontrolować porządkowanie w kwerendzie PLINQ przy użyciu metody rozszerzenia <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c03c-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="7c03c-104">Te przykłady są przeznaczone głównie do zademonstrowania użycia i mogą być uruchamiane szybciej niż równoważne zapytania sekwencyjne LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="7c03c-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c03c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c03c-105">Example</span></span>  
 <span data-ttu-id="7c03c-106">Poniższy przykład zachowuje kolejność sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="7c03c-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="7c03c-107">Jest to czasami konieczne; na przykład niektóre operatory zapytań wymagają uporządkowanej sekwencji źródłowej, aby generować poprawne wyniki.</span><span class="sxs-lookup"><span data-stu-id="7c03c-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="7c03c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c03c-108">Example</span></span>  
 <span data-ttu-id="7c03c-109">W poniższym przykładzie przedstawiono niektóre operatory zapytań, których sekwencja źródłowa prawdopodobnie powinna być uporządkowana.</span><span class="sxs-lookup"><span data-stu-id="7c03c-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="7c03c-110">Te operatory będą działały w sekwencjach nieuporządkowanych, ale mogą generować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="7c03c-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="7c03c-111">Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [przykład danych PLINQ Data](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="7c03c-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c03c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c03c-112">Example</span></span>  
 <span data-ttu-id="7c03c-113">Poniższy przykład pokazuje, jak zachować kolejność dla pierwszej części zapytania, a następnie usunąć kolejność, aby zwiększyć wydajność klauzuli join, a następnie ponownie zastosować porządkowanie do końcowej sekwencji wyników.</span><span class="sxs-lookup"><span data-stu-id="7c03c-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="7c03c-114">Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [przykład danych PLINQ Data](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="7c03c-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c03c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c03c-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="7c03c-116">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="7c03c-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
