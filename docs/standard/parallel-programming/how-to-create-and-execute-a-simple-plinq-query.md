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
ms.openlocfilehash: a9c044254423d0f9d266539c728a6604f562e97d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290009"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="0202a-102">Instrukcje: Tworzenie i wykonywanie prostego zapytania PLINQ</span><span class="sxs-lookup"><span data-stu-id="0202a-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="0202a-103">W przykładzie w tym artykule przedstawiono sposób tworzenia prostego zapytania programu Parallel Language Integrated Query (LINQ) przy użyciu <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> metody rozszerzenia w sekwencji źródłowej i wykonywania zapytania przy użyciu <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> metody.</span><span class="sxs-lookup"><span data-stu-id="0202a-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0202a-104">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ.</span><span class="sxs-lookup"><span data-stu-id="0202a-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="0202a-105">Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="0202a-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0202a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0202a-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="0202a-107">W tym przykładzie przedstawiono podstawowy wzorzec tworzenia i wykonywania wszelkich równoległych zapytań LINQ, gdy kolejność sekwencji wyników nie jest ważna.</span><span class="sxs-lookup"><span data-stu-id="0202a-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="0202a-108">Zapytania nieuporządkowane są zwykle szybsze niż uporządkowane zapytania.</span><span class="sxs-lookup"><span data-stu-id="0202a-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="0202a-109">Zapytanie dzieli źródło na zadania, które są wykonywane asynchronicznie na wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="0202a-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="0202a-110">Kolejność, w której każde zadanie jest wykonywane, zależy nie tylko od ilości pracy związanej z przetwarzaniem elementów w partycji, ale również na zewnętrznych czynnikach, takich jak system operacyjny planuje każdy wątek.</span><span class="sxs-lookup"><span data-stu-id="0202a-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="0202a-111">Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie.</span><span class="sxs-lookup"><span data-stu-id="0202a-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="0202a-112">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="0202a-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="0202a-113">Aby uzyskać więcej informacji na temat zachowania kolejności elementów w zapytaniu, zobacz [How to: Control Order in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="0202a-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0202a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0202a-114">See also</span></span>

- [<span data-ttu-id="0202a-115">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="0202a-115">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
