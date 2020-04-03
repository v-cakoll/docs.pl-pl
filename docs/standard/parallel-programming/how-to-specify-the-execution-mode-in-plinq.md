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
ms.openlocfilehash: f035dbcd5091d81a3cce3b9e9e683d836fe84bb7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635812"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="cab7e-102">Porady: określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="cab7e-102">How to: Specify the Execution Mode in PLINQ</span></span>

<span data-ttu-id="cab7e-103">W tym przykładzie pokazano, jak wymusić PLINQ, aby ominąć jego domyślne heurystyki i zrównoleglić kwerendy niezależnie od kształtu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="cab7e-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cab7e-104">W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów.</span><span class="sxs-lookup"><span data-stu-id="cab7e-104">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="cab7e-105">Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="cab7e-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cab7e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cab7e-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="cab7e-107">PLINQ został zaprojektowany, aby wykorzystać możliwości równoległości.</span><span class="sxs-lookup"><span data-stu-id="cab7e-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="cab7e-108">Jednak nie wszystkie kwerendy korzystają z wykonywania równoległego.</span><span class="sxs-lookup"><span data-stu-id="cab7e-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="cab7e-109">Na przykład, gdy kwerenda zawiera delegata jednego użytkownika, który wykonuje niewiele pracy, kwerenda będzie zwykle działać szybciej sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="cab7e-109">For example, when a query contains a single user delegate that does little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="cab7e-110">Wykonanie sekwencyjne jest szybsze, ponieważ obciążenie związane z włączaniem wykonywania równoległości jest droższe niż uzyskane przyspieszenie.</span><span class="sxs-lookup"><span data-stu-id="cab7e-110">Sequential execution is faster because the overhead involved in enabling parallelizing execution is more expensive than the speedup that's obtained.</span></span> <span data-ttu-id="cab7e-111">W związku z tym PLINQ nie automatycznie równoległościić każde zapytanie.</span><span class="sxs-lookup"><span data-stu-id="cab7e-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="cab7e-112">Najpierw sprawdza kształt kwerendy i różnych operatorów, które go tworzą.</span><span class="sxs-lookup"><span data-stu-id="cab7e-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="cab7e-113">Na podstawie tej analizy PLINQ w trybie wykonywania domyślnego może zdecydować o wykonaniu niektórych lub wszystkich kwerendy sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="cab7e-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="cab7e-114">Jednak w niektórych przypadkach możesz wiedzieć więcej o zapytaniu niż PLINQ jest w stanie określić na podstawie jego analizy.</span><span class="sxs-lookup"><span data-stu-id="cab7e-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="cab7e-115">Na przykład może wiesz, że delegat jest kosztowne i że kwerenda na pewno skorzysta z równoległości.</span><span class="sxs-lookup"><span data-stu-id="cab7e-115">For example, you may know that a delegate is expensive and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="cab7e-116">W takich przypadkach można <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> użyć metody <xref:System.Linq.ParallelExecutionMode.ForceParallelism> i określić wartość, aby poinstruować PLINQ, aby zawsze uruchamiać kwerendę jako równoległą.</span><span class="sxs-lookup"><span data-stu-id="cab7e-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cab7e-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cab7e-117">Compiling the Code</span></span>  
 <span data-ttu-id="cab7e-118">Wytnij i wklej ten kod do próbki `Main`danych [PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i wywołaj metodę z .</span><span class="sxs-lookup"><span data-stu-id="cab7e-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cab7e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cab7e-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="cab7e-120">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="cab7e-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
