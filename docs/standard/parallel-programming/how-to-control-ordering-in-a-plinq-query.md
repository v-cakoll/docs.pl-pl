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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa08106126212345bb594cdeabe6e7281cd7b5e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180790"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="61e87-102">Porady: sterowanie szeregowaniem w zapytaniu PLINQ</span><span class="sxs-lookup"><span data-stu-id="61e87-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="61e87-103">Te przykłady przedstawiają sposób sterowanie szeregowaniem w zapytaniu PLINQ przy użyciu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="61e87-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="61e87-104">Te przykłady przede wszystkim służą do zademonstrowania użycia i może być lub może nie działać szybciej niż równoważna sekwencyjnego LINQ do zapytań obiekt.</span><span class="sxs-lookup"><span data-stu-id="61e87-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61e87-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="61e87-105">Example</span></span>  
 <span data-ttu-id="61e87-106">Poniższy przykład zachowuje kolejność sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="61e87-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="61e87-107">Czasami jest to konieczne. na przykład niektóre operatory zapytań wymagają sekwencji źródłowej uporządkowany w celu wygenerowania prawidłowych wyników.</span><span class="sxs-lookup"><span data-stu-id="61e87-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="61e87-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="61e87-108">Example</span></span>  
 <span data-ttu-id="61e87-109">W poniższym przykładzie pokazano niektóre zapytania, operatory, których sekwencji źródłowej prawdopodobnie powinien zostać określona.</span><span class="sxs-lookup"><span data-stu-id="61e87-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="61e87-110">Te operatory będą działać w sekwencji nieuporządkowaną, ale mogą one dawać nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="61e87-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="61e87-111">Aby uruchomić tę metodę, wklej go do klasy PLINQDataSample w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, a następnie naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="61e87-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61e87-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="61e87-112">Example</span></span>  
 <span data-ttu-id="61e87-113">Poniższy przykład pokazuje, jak zachować kolejności pierwszej części zapytania, a następnie usuń kolejności, co pozwoli zwiększyć wydajność klauzuli join a następnie ponownie Zastosuj kolejność sekwencji wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="61e87-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="61e87-114">Aby uruchomić tę metodę, wklej go do klasy PLINQDataSample w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, a następnie naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="61e87-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e87-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61e87-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="61e87-116">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="61e87-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
