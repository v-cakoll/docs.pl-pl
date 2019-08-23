---
title: 'Instrukcje: Tworzenie i wykonywanie prostego zapytania PLINQ'
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
ms.openlocfilehash: 472304dff23e92620dd461e8bc43c3093431ddc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962517"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="ddcdf-102">Instrukcje: Tworzenie i wykonywanie prostego zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="ddcdf-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="ddcdf-103">Poniższy przykład pokazuje, jak utworzyć prostą równoległą kwerendę LINQ przy użyciu <xref:System.Linq.ParallelEnumerable.AsParallel%2A> metody rozszerzającej dla sekwencji źródłowej i wykonując zapytanie przy <xref:System.Linq.ParallelEnumerable.ForAll%2A> użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="ddcdf-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddcdf-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="ddcdf-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="ddcdf-105">Jeśli nie znasz wyrażeń lambda w C# lub Visual Basic, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="ddcdf-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcdf-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddcdf-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="ddcdf-107">W tym przykładzie przedstawiono podstawowy wzorzec tworzenia i wykonywania wszelkich równoległych zapytań LINQ, gdy kolejność sekwencji wyników nie jest ważna. zapytania nieuporządkowane są zwykle szybsze niż uporządkowane zapytania.</span><span class="sxs-lookup"><span data-stu-id="ddcdf-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="ddcdf-108">Zapytanie dzieli źródło na zadania, które są wykonywane asynchronicznie na wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="ddcdf-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="ddcdf-109">Kolejność, w której każde zadanie jest wykonywane, zależy nie tylko od ilości pracy związanej z przetwarzaniem elementów w partycji, ale również na zewnętrznych czynnikach, takich jak system operacyjny planuje każdy wątek.</span><span class="sxs-lookup"><span data-stu-id="ddcdf-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="ddcdf-110">Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie.</span><span class="sxs-lookup"><span data-stu-id="ddcdf-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="ddcdf-111">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="ddcdf-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="ddcdf-112">Aby uzyskać więcej informacji na temat sposobu zachowania kolejności elementów w zapytaniu, zobacz [How to: Kolejność kontroli w zapytaniu](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)PLINQ.</span><span class="sxs-lookup"><span data-stu-id="ddcdf-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcdf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddcdf-113">See also</span></span>

- [<span data-ttu-id="ddcdf-114">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ddcdf-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
