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
ms.openlocfilehash: ebea62f33c5df252dd73a0708f31612cd2998728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580942"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="f689f-102">Porady: określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="f689f-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="f689f-103">W tym przykładzie pokazano, jak wymusić PLINQ do obejścia jego domyślny algorytm heurystyczny i parallelize zapytania niezależnie od tego zapytania kształtu.</span><span class="sxs-lookup"><span data-stu-id="f689f-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f689f-104">W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania.</span><span class="sxs-lookup"><span data-stu-id="f689f-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="f689f-105">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f689f-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f689f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f689f-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="f689f-107">PLINQ zaprojektowano możliwości paralelizacja.</span><span class="sxs-lookup"><span data-stu-id="f689f-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="f689f-108">Jednak nie wszystkie zapytania korzyści przetwarzania równoległego.</span><span class="sxs-lookup"><span data-stu-id="f689f-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="f689f-109">Na przykład jeśli zapytanie zawiera delegata pojedynczego użytkownika, który jest bardzo małego wysiłku, zapytanie zwykle uruchomi szybciej sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="f689f-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="f689f-110">Jest to spowodowane koszty związane z włączaniem parallelizing wykonywania jest droższe niż przyspieszenie, uzyskany.</span><span class="sxs-lookup"><span data-stu-id="f689f-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="f689f-111">W związku z tym PLINQ automatycznie nie parallelize każdego zapytania.</span><span class="sxs-lookup"><span data-stu-id="f689f-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="f689f-112">To najpierw sprawdza, czy kształt zapytania i różne operatory wchodzących w jej skład.</span><span class="sxs-lookup"><span data-stu-id="f689f-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="f689f-113">Oparte na tej analizy, PLINQ w domyślnym trybie wykonanie może zadecydować o wykonać niektóre lub wszystkie zapytania po kolei.</span><span class="sxs-lookup"><span data-stu-id="f689f-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="f689f-114">Jednak w niektórych przypadkach użytkownik może dowiedzieć się więcej o kwerendy niż PLINQ ma możliwość określenia z jego analizy.</span><span class="sxs-lookup"><span data-stu-id="f689f-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="f689f-115">Na przykład wiadomo, że delegata jest bardzo kosztowna i czy zapytanie ostatecznie będą korzystać z paralelizacja.</span><span class="sxs-lookup"><span data-stu-id="f689f-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="f689f-116">W takich przypadkach można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> — metoda i określ <xref:System.Linq.ParallelExecutionMode.ForceParallelism> wartość nakazać programowi PLINQ zawsze uruchomić kwerendę jako równoległe.</span><span class="sxs-lookup"><span data-stu-id="f689f-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f689f-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f689f-117">Compiling the Code</span></span>  
 <span data-ttu-id="f689f-118">Wycinanie i wklejanie go w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i wywołaj metodę z `Main`.</span><span class="sxs-lookup"><span data-stu-id="f689f-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f689f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f689f-119">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [<span data-ttu-id="f689f-120">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f689f-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
