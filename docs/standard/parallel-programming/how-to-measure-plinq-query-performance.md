---
title: 'Porady: mierzenie wydajności zapytań PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 91b6165be2f4f464626fb25f7152de68de9d86e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124992"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="83670-102">Porady: mierzenie wydajności zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="83670-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="83670-103">W tym przykładzie <xref:System.Diagnostics.Stopwatch> pokazano, jak używać klasy do pomiaru czasu potrzebnego do wykonania kwerendy PLINQ.</span><span class="sxs-lookup"><span data-stu-id="83670-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83670-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="83670-104">Example</span></span>  
 <span data-ttu-id="83670-105">W tym przykładzie `foreach` użyto pustej pętli (w`For Each` języku Visual Basic) do pomiaru czasu potrzebnego do wykonania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="83670-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="83670-106">W kodzie rzeczywistym pętli zazwyczaj zawiera dodatkowe kroki przetwarzania, które dodają do całkowitego czasu wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="83670-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="83670-107">Należy zauważyć, że stoper nie jest uruchamiany dopiero tuż przed pętlą, ponieważ jest to, gdy rozpoczyna się wykonywanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="83670-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="83670-108">Jeśli potrzebujesz bardziej szczegółowego pomiaru, możesz `ElapsedTicks` użyć `ElapsedMilliseconds`właściwości zamiast .</span><span class="sxs-lookup"><span data-stu-id="83670-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="83670-109">Całkowity czas wykonywania jest przydatne metryki podczas eksperymentowania z implementacji kwerendy, ale nie zawsze powiedzieć całą historię.</span><span class="sxs-lookup"><span data-stu-id="83670-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="83670-110">Aby uzyskać głębszy i bogatszy widok interakcji wątków kwerendy ze sobą i z innymi uruchomionymi procesami, należy użyć wizualizatora współbieżności.</span><span class="sxs-lookup"><span data-stu-id="83670-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="83670-111">Aby uzyskać więcej informacji, zobacz [Wizualizacja współbieżności](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="83670-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83670-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83670-112">See also</span></span>

- [<span data-ttu-id="83670-113">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="83670-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
