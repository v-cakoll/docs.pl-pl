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
ms.openlocfilehash: 86011cff71fabed5e47e085f91b1759238638c9a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588490"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="84090-102">Porady: sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="84090-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="84090-103">Te przykłady pokazują, jak kontrolować kolejność w kwerendzie <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> PLINQ przy użyciu metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="84090-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="84090-104">Te przykłady są przeznaczone przede wszystkim do wykazania użycia i może lub nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerend obiektów.</span><span class="sxs-lookup"><span data-stu-id="84090-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84090-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="84090-105">Example</span></span>  
 <span data-ttu-id="84090-106">Poniższy przykład zachowuje kolejność sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="84090-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="84090-107">Czasami jest to konieczne; na przykład niektóre operatory zapytań wymagają uporządkowanej sekwencji źródłowej do uzyskania poprawnych wyników.</span><span class="sxs-lookup"><span data-stu-id="84090-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="84090-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="84090-108">Example</span></span>  
 <span data-ttu-id="84090-109">Poniższy przykład pokazuje niektóre operatory zapytań, których sekwencja źródło prawdopodobnie oczekuje się, że zostanie uporządkowany.</span><span class="sxs-lookup"><span data-stu-id="84090-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="84090-110">Te operatory będą pracować nad sekwencjami nieuiarszowanymi, ale mogą one przynieść nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="84090-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="84090-111">Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="84090-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84090-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="84090-112">Example</span></span>  
 <span data-ttu-id="84090-113">W poniższym przykładzie pokazano, jak zachować kolejność dla pierwszej części kwerendy, a następnie usunąć kolejność, aby zwiększyć wydajność klauzuli sprzężenia, a następnie ponownie zasądzenie kolejności do sekwencji wyników końcowych.</span><span class="sxs-lookup"><span data-stu-id="84090-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="84090-114">Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="84090-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84090-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84090-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="84090-116">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="84090-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
