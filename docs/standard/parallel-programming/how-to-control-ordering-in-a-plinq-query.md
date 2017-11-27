---
title: 'Porady: sterowanie szeregowaniem w zapytaniu PLINQ'
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
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="66e86-102">Porady: sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="66e86-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="66e86-103">Poniższe przykłady pokazują, jak sterowanie szeregowaniem w zapytaniu PLINQ przy użyciu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="66e86-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="66e86-104">Te przykłady głównie służą jedynie do zademonstrowania użycia i może lub może nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytań.</span><span class="sxs-lookup"><span data-stu-id="66e86-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66e86-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="66e86-105">Example</span></span>  
 <span data-ttu-id="66e86-106">Poniższy przykład zachowuje kolejność sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="66e86-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="66e86-107">Czasami jest to konieczne. na przykład niektóre operatorów zapytań wymagają sekwencji źródłowej uporządkowanych aby wygenerować poprawnych wyników.</span><span class="sxs-lookup"><span data-stu-id="66e86-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="66e86-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="66e86-108">Example</span></span>  
 <span data-ttu-id="66e86-109">W poniższym przykładzie przedstawiono niektóre zapytania operatory, których sekwencji źródłowej prawdopodobnie oczekiwano może zostać określona.</span><span class="sxs-lookup"><span data-stu-id="66e86-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="66e86-110">Operatory te będą działać na nieuporządkowaną sekwencji, ale może powodować generowanie nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="66e86-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="66e86-111">Aby uruchomić tę metodę, wklej go do klasy PLINQDataSample w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, a następnie naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="66e86-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66e86-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="66e86-112">Example</span></span>  
 <span data-ttu-id="66e86-113">Poniższy przykład pokazuje, jak zachowania kolejności pierwszej części zapytania, a następnie usuń, kolejność w celu zwiększenia wydajności w klauzuli join, a następnie ponowne zastosowanie porządkowanie sekwencji wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="66e86-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="66e86-114">Aby uruchomić tę metodę, wklej go do klasy PLINQDataSample w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, a następnie naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="66e86-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e86-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66e86-115">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="66e86-116">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="66e86-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
