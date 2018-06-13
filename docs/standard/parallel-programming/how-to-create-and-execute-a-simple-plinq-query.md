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
ms.openlocfilehash: 2e5bd27dda4bacc50672cca2db38a6eda746d79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580380"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="511cb-102">Porady: tworzenie i wykonywanie prostych zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="511cb-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="511cb-103">Poniższy przykład przedstawia sposób tworzenia prostego zapytania równoległe LINQ za pomocą <xref:System.Linq.ParallelEnumerable.AsParallel%2A> — metoda rozszerzenia w sekwencji źródłowej i wykonywania zapytania za pomocą <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="511cb-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="511cb-104">Ta dokumentacja używa wyrażenia lambda, aby zdefiniować delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="511cb-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="511cb-105">Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="511cb-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="511cb-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="511cb-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="511cb-107">W tym przykładzie przedstawiono podstawowe wzorzec do tworzenia i wykonywania wszelkie zapytania równoległe LINQ, gdy kolejność sekwencji wynik nie jest istotna; nieuporządkowaną zapytania są zwykle szybsze niż uporządkowanych zapytań.</span><span class="sxs-lookup"><span data-stu-id="511cb-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="511cb-108">Zapytanie partycji źródła do zadań, które są wykonywane asynchronicznie na wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="511cb-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="511cb-109">Kolejność, w którym kończy się każde zadanie zależy nie tylko ze względu na ilość pracy zaangażowany przetwarzania elementów w partycji, ale także na czynniki zewnętrzne, takie jak jak system operacyjny planuje każdy wątek.</span><span class="sxs-lookup"><span data-stu-id="511cb-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="511cb-110">W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania.</span><span class="sxs-lookup"><span data-stu-id="511cb-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="511cb-111">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="511cb-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="511cb-112">Aby uzyskać więcej informacji na temat zachowania kolejności elementów w zapytaniu, zobacz [porady: kontrolki szeregowaniem w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="511cb-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511cb-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="511cb-113">See Also</span></span>  
 [<span data-ttu-id="511cb-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="511cb-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
