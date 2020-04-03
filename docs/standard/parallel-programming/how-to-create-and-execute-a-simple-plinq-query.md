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
ms.openlocfilehash: c4cd75e55aabb551e5951a902ea6394a5659c9ee
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635853"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="c83ff-102">Porady: tworzenie i wykonywanie prostych zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="c83ff-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="c83ff-103">W tym przykładzie w tym artykule pokazano, jak utworzyć proste <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> zapytanie zintegrowane języka równoległego (LINQ) przy użyciu metody rozszerzenia w sekwencji źródłowej i wykonywania kwerendy przy użyciu <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> metody.</span><span class="sxs-lookup"><span data-stu-id="c83ff-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c83ff-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c83ff-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="c83ff-105">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="c83ff-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c83ff-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c83ff-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="c83ff-107">W tym przykładzie pokazano podstawowy wzorzec do tworzenia i wykonywania dowolnej równoległej kwerendy LINQ, gdy kolejność sekwencji wyników nie jest ważne.</span><span class="sxs-lookup"><span data-stu-id="c83ff-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="c83ff-108">Nieurządzone zapytania są zazwyczaj szybsze niż kwerendy uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="c83ff-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="c83ff-109">Kwerenda dzieli źródło na zadania, które są wykonywane asynchronicznie w wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="c83ff-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="c83ff-110">Kolejność, w jakiej każde zadanie jest wykonywane, zależy nie tylko od ilości pracy związanej z przetwarzaniem elementów w partycji, ale także od czynników zewnętrznych, takich jak sposób planowania każdego wątku przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="c83ff-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="c83ff-111">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów.</span><span class="sxs-lookup"><span data-stu-id="c83ff-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c83ff-112">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c83ff-112">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="c83ff-113">Aby uzyskać więcej informacji na temat zachowania kolejności elementów w kwerendzie, zobacz [Jak: Sterowanie porządkowanie w PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c83ff-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83ff-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c83ff-114">See also</span></span>

- [<span data-ttu-id="c83ff-115">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c83ff-115">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
