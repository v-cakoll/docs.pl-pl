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
ms.openlocfilehash: 0cdef6d3826e4e7522bf3f6ed69060b8ef1c5e1b
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588294"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="efe43-102">Porady: tworzenie i wykonywanie prostych zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="efe43-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="efe43-103">W poniższym przykładzie pokazano, jak utworzyć proste <xref:System.Linq.ParallelEnumerable.AsParallel%2A> parallel LINQ kwerendy przy użyciu metody <xref:System.Linq.ParallelEnumerable.ForAll%2A> rozszerzenia w sekwencji źródłowej i wykonywania kwerendy przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="efe43-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efe43-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="efe43-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="efe43-105">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="efe43-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="efe43-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="efe43-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="efe43-107">W tym przykładzie pokazano podstawowy wzorzec do tworzenia i wykonywania dowolnej równoległej kwerendy LINQ, gdy kolejność sekwencji wyników nie jest ważne; niezaudłone zapytania są zazwyczaj szybsze niż uporządkowane kwerendy.</span><span class="sxs-lookup"><span data-stu-id="efe43-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="efe43-108">Kwerenda dzieli źródło na zadania, które są wykonywane asynchronicznie w wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="efe43-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="efe43-109">Kolejność, w jakiej każde zadanie jest wykonywane, zależy nie tylko od ilości pracy związanej z przetwarzaniem elementów w partycji, ale także od czynników zewnętrznych, takich jak sposób planowania każdego wątku przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="efe43-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="efe43-110">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów.</span><span class="sxs-lookup"><span data-stu-id="efe43-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="efe43-111">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="efe43-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="efe43-112">Aby uzyskać więcej informacji na temat zachowania kolejności elementów w kwerendzie, zobacz [Jak: Sterowanie porządkowanie w PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="efe43-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe43-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efe43-113">See also</span></span>

- [<span data-ttu-id="efe43-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="efe43-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
