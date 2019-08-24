---
title: 'Instrukcje: Określanie trybu wykonywania w PLINQ'
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
ms.openlocfilehash: 705b6bc364e2ecf00c3629814228157c90017a8b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988452"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="e4033-102">Instrukcje: Określanie trybu wykonywania w PLINQ</span><span class="sxs-lookup"><span data-stu-id="e4033-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="e4033-103">Ten przykład pokazuje, jak wymusić PLINQ, aby pominąć domyślne heurystyke i zrównoleglanie zapytanie niezależnie od kształtu zapytania.</span><span class="sxs-lookup"><span data-stu-id="e4033-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e4033-104">Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie.</span><span class="sxs-lookup"><span data-stu-id="e4033-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="e4033-105">Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e4033-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4033-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4033-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="e4033-107">PLINQ zaprojektowano w celu wykorzystania możliwości programu przetwarzanie równoległe.</span><span class="sxs-lookup"><span data-stu-id="e4033-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="e4033-108">Jednak nie wszystkie zapytania korzystają z wykonywania równoległego.</span><span class="sxs-lookup"><span data-stu-id="e4033-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="e4033-109">Na przykład, gdy zapytanie zawiera pojedynczego delegata użytkownika, który wykonuje bardzo mało pracy, zapytanie będzie zazwyczaj wykonywane szybciej.</span><span class="sxs-lookup"><span data-stu-id="e4033-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="e4033-110">Wynika to z faktu, że obciążenie związane z włączaniem wykonywania przekształcają jest droższe niż uzyskany przyspieszenie.</span><span class="sxs-lookup"><span data-stu-id="e4033-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="e4033-111">W związku z tym PLINQ nie jest automatycznie zrównoleglanie wszystkich zapytań.</span><span class="sxs-lookup"><span data-stu-id="e4033-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="e4033-112">Najpierw analizuje kształt zapytania i różne operatory, które go tworzą.</span><span class="sxs-lookup"><span data-stu-id="e4033-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="e4033-113">Na podstawie tej analizy PLINQ w domyślnym trybie wykonywania może zdecydować się na wykonanie niektórych lub wszystkich zapytań sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="e4033-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="e4033-114">Jednak w niektórych przypadkach można dowiedzieć się więcej o zapytaniu niż PLINQ jest w stanie określić na podstawie jego analizy.</span><span class="sxs-lookup"><span data-stu-id="e4033-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="e4033-115">Na przykład może być wiadomo, że delegat jest bardzo kosztowny i że zapytanie będzie ostatecznie korzystać z przetwarzanie równoległe.</span><span class="sxs-lookup"><span data-stu-id="e4033-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="e4033-116">W takich przypadkach można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metody i <xref:System.Linq.ParallelExecutionMode.ForceParallelism> określić wartość, aby polecić PLINQ, aby zawsze uruchamiała zapytanie jako Parallel.</span><span class="sxs-lookup"><span data-stu-id="e4033-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4033-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e4033-117">Compiling the Code</span></span>  
 <span data-ttu-id="e4033-118">Wytnij i wklej ten kod do [przykładu danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i Wywołaj metodę `Main`z.</span><span class="sxs-lookup"><span data-stu-id="e4033-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4033-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4033-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="e4033-120">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e4033-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
