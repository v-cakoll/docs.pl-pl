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
ms.openlocfilehash: 349cc8d78e9a080d720e09a7e3e5e314752605c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106958"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="e3a5f-102">Porady: tworzenie i wykonywanie prostych zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="e3a5f-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="e3a5f-103">W poniższym przykładzie pokazano, jak utworzyć prostą <xref:System.Linq.ParallelEnumerable.AsParallel%2A> kwerendę Równoległego LINQ przy użyciu <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody rozszerzenia w sekwencji źródłowej i wykonywania kwerendy przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="e3a5f-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3a5f-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="e3a5f-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="e3a5f-105">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="e3a5f-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3a5f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3a5f-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="e3a5f-107">W tym przykładzie przedstawiono podstawowy wzorzec do tworzenia i wykonywania dowolnej kwerendy Równoległego LINQ, gdy kolejność sekwencji wyników nie jest ważna; zapytania nieuporządkowane są zazwyczaj szybsze niż zamówione zapytania.</span><span class="sxs-lookup"><span data-stu-id="e3a5f-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="e3a5f-108">Kwerenda dzieli źródło na zadania, które są wykonywane asynchronicznie na wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="e3a5f-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="e3a5f-109">Kolejność, w jakiej każde zadanie kończy zależy nie tylko od ilości pracy związanej z przetwarzaniem elementów w partycji, ale także od czynników zewnętrznych, takich jak sposób, w jaki system operacyjny planuje każdy wątek.</span><span class="sxs-lookup"><span data-stu-id="e3a5f-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="e3a5f-110">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy.</span><span class="sxs-lookup"><span data-stu-id="e3a5f-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="e3a5f-111">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e3a5f-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="e3a5f-112">Aby uzyskać więcej informacji na temat sposobu zachowywania kolejności elementów w kwerendzie, zobacz [Jak: Sterowanie kolejnością w kwerendzie PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="e3a5f-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a5f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3a5f-113">See also</span></span>

- [<span data-ttu-id="e3a5f-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e3a5f-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
