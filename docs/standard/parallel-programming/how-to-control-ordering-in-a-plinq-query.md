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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123121"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="0d7ab-102">Porady: sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="0d7ab-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="0d7ab-103">W tych przykładach przedstawiono sposób kontrolowania kolejności w kwerendzie PLINQ przy użyciu metody <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="0d7ab-104">Te przykłady są przeznaczone głównie do wykazania użycia i może lub nie może działać szybciej niż równoważne sekwencyjne LINQ do obiektów zapytań.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d7ab-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d7ab-105">Example</span></span>  
 <span data-ttu-id="0d7ab-106">Poniższy przykład zachowuje kolejność sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="0d7ab-107">Czasami jest to konieczne; na przykład niektóre operatory kwerend wymagają uporządkowanej sekwencji źródłowych w celu uzyskania poprawnych wyników.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="0d7ab-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d7ab-108">Example</span></span>  
 <span data-ttu-id="0d7ab-109">W poniższym przykładzie przedstawiono niektóre operatory zapytań, których sekwencja źródłowa prawdopodobnie ma zostać zamówiona.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="0d7ab-110">Te operatory będą działać na sekwencje nieuporządkowane, ale mogą one powodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="0d7ab-111">Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [próbki danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d7ab-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d7ab-112">Example</span></span>  
 <span data-ttu-id="0d7ab-113">W poniższym przykładzie pokazano, jak zachować kolejność dla pierwszej części kwerendy, a następnie usunąć kolejność, aby zwiększyć wydajność join klauzuli, a następnie ponownie zastosować kolejność do końcowej sekwencji wyników.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="0d7ab-114">Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [próbki danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="0d7ab-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7ab-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d7ab-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="0d7ab-116">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="0d7ab-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
