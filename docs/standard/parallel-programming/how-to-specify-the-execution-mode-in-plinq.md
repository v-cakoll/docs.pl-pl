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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85731b991399e92297d6109a3000c1e345e02f6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43885921"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="35d4f-102">Porady: określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="35d4f-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="35d4f-103">W tym przykładzie przedstawiono sposób wymusić PLINQ obejścia domyślnej heurystyki i równoległe przetwarzanie zapytania niezależnie od tego, w zapytaniu shape.</span><span class="sxs-lookup"><span data-stu-id="35d4f-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="35d4f-104">W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty.</span><span class="sxs-lookup"><span data-stu-id="35d4f-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="35d4f-105">Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="35d4f-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35d4f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="35d4f-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="35d4f-107">Program PLINQ jest przeznaczony do możliwości przetwarzania równoległego.</span><span class="sxs-lookup"><span data-stu-id="35d4f-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="35d4f-108">Jednak nie wszystkie kwerendy korzystają z przetwarzania równoległego.</span><span class="sxs-lookup"><span data-stu-id="35d4f-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="35d4f-109">Na przykład, gdy zapytanie zawiera delegata pojedynczego użytkownika, który wykonuje bardzo małego wysiłku, zapytanie będzie najczęściej uruchamiane szybciej sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="35d4f-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="35d4f-110">Jest to spowodowane obciążenie związane z włączaniem przekształcają wykonywania jest droższe niż przyspieszenie, uzyskany.</span><span class="sxs-lookup"><span data-stu-id="35d4f-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="35d4f-111">W związku z tym program PLINQ nie automatycznie równolegle wykonywać każdego zapytania.</span><span class="sxs-lookup"><span data-stu-id="35d4f-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="35d4f-112">Najpierw sprawdza, czy kształt zapytania i różnych operatorów, które składają się go.</span><span class="sxs-lookup"><span data-stu-id="35d4f-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="35d4f-113">Na podstawie tej analizy, PLINQ w domyślnym trybie wykonywania może podjąć decyzję o wykonanie niektórych lub wszystkich zapytanie sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="35d4f-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="35d4f-114">Jednak w niektórych przypadkach użytkownik może dowiedzieć się więcej o kwerendzie niż PLINQ jest możliwe ustalenie, z ich analizy.</span><span class="sxs-lookup"><span data-stu-id="35d4f-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="35d4f-115">Na przykład wiadomo, że delegat jest bardzo kosztowny i czy zapytania zdecydowanie będą mogli korzystać z przetwarzaniem równoległym.</span><span class="sxs-lookup"><span data-stu-id="35d4f-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="35d4f-116">W takich przypadkach można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metodę i określić <xref:System.Linq.ParallelExecutionMode.ForceParallelism> wartość, aby nakazać PLINQ zawsze uruchamiaj zapytania jako równoległego.</span><span class="sxs-lookup"><span data-stu-id="35d4f-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35d4f-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="35d4f-117">Compiling the Code</span></span>  
 <span data-ttu-id="35d4f-118">Wytnij i wklej go w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i wywołaj metodę z `Main`.</span><span class="sxs-lookup"><span data-stu-id="35d4f-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d4f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35d4f-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
- [<span data-ttu-id="35d4f-120">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="35d4f-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
