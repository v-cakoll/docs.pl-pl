---
title: 'Porady: tworzenie i wykonywanie prostych zapytań PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 544ea0f89dfa518c2ef18bffe2609d72e6fdee70
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085043"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="2d326-102">Porady: tworzenie i wykonywanie prostych zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="2d326-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="2d326-103">Poniższy przykład pokazuje, jak utworzyć proste zapytanie równoległe LINQ za pomocą <xref:System.Linq.ParallelEnumerable.AsParallel%2A> metody rozszerzenia w sekwencji źródłowej i wykonywania zapytania za pomocą <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d326-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d326-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="2d326-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="2d326-105">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="2d326-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d326-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d326-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="2d326-107">W tym przykładzie przedstawiono podstawowy wzorzec do tworzenia i wykonywanie dowolnego zapytania równoległe LINQ, gdy kolejność sekwencji wynik nie jest istotna; Nieuporządkowana zapytania są zwykle szybsze niż uporządkowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="2d326-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="2d326-108">Zapytanie partycji źródłowej na zadania, które są wykonywane asynchronicznie w wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="2d326-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="2d326-109">Kolejność, w którym kończy się każde zadanie zależy nie tylko na ilość pracy zaangażowane na przetworzenie elementów w partycji, ale także na czynniki zewnętrzne, takie jak jak system operacyjny planuje każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="2d326-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="2d326-110">W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty.</span><span class="sxs-lookup"><span data-stu-id="2d326-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="2d326-111">Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="2d326-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="2d326-112">Aby uzyskać więcej informacji o tym, jak zachować kolejność elementów w zapytaniu, zobacz [instrukcje: kontrolki szeregowaniem w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="2d326-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d326-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d326-113">See also</span></span>

- [<span data-ttu-id="2d326-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2d326-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
