---
title: 'Porady: określanie trybu wykonywania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: c602aba6e18f80b007b15cd61dfd2b48a36dd2c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139247"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="d0051-102">Porady: określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="d0051-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="d0051-103">W tym przykładzie pokazano, jak wymusić PLINQ, aby ominąć jego domyślne heurystyki i równoległość kwerendy, niezależnie od kształtu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="d0051-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d0051-104">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy.</span><span class="sxs-lookup"><span data-stu-id="d0051-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="d0051-105">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="d0051-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0051-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0051-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="d0051-107">PLINQ ma na celu wykorzystanie możliwości równoległości.</span><span class="sxs-lookup"><span data-stu-id="d0051-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="d0051-108">Jednak nie wszystkie zapytania korzystają z wykonania równoległego.</span><span class="sxs-lookup"><span data-stu-id="d0051-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="d0051-109">Na przykład gdy kwerenda zawiera delegata jednego użytkownika, który wykonuje bardzo mało pracy, kwerenda będzie zwykle działać szybciej sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="d0051-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="d0051-110">Jest tak, ponieważ obciążenie związane z włączeniem parallelizing wykonanie jest droższe niż przyspieszenie, które jest uzyskiwane.</span><span class="sxs-lookup"><span data-stu-id="d0051-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="d0051-111">W związku z tym PLINQ nie automatycznie równoległy chorągwi każdej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="d0051-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="d0051-112">Najpierw bada kształt zapytania i różnych operatorów, które ją tworzą.</span><span class="sxs-lookup"><span data-stu-id="d0051-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="d0051-113">Na podstawie tej analizy PLINQ w domyślnym trybie wykonywania może zdecydować się na wykonanie niektórych lub wszystkich kwerendssek sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="d0051-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="d0051-114">Jednak w niektórych przypadkach możesz wiedzieć więcej o zapytaniu niż PLINQ jest w stanie określić na podstawie jego analizy.</span><span class="sxs-lookup"><span data-stu-id="d0051-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="d0051-115">Na przykład może się zorientować, że pełnomocnik jest bardzo kosztowne i że kwerenda na pewno skorzystają z równoległości.</span><span class="sxs-lookup"><span data-stu-id="d0051-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="d0051-116">W takich przypadkach można <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> użyć metody <xref:System.Linq.ParallelExecutionMode.ForceParallelism> i określić wartość, aby poinstruować PLINQ, aby zawsze uruchamiać kwerendę jako równoległą.</span><span class="sxs-lookup"><span data-stu-id="d0051-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0051-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d0051-117">Compiling the Code</span></span>  
 <span data-ttu-id="d0051-118">Wytnij i wklej ten kod do próbki `Main`danych [PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i wywołaj metodę z .</span><span class="sxs-lookup"><span data-stu-id="d0051-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0051-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0051-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="d0051-120">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d0051-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
