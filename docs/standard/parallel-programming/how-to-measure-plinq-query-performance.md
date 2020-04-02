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
ms.openlocfilehash: 4cb0d408798d66c8491654c90f33255c700690a3
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587792"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="a622a-102">Porady: mierzenie wydajności zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="a622a-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="a622a-103">W tym przykładzie <xref:System.Diagnostics.Stopwatch> pokazano, jak używać klasy do pomiaru czasu potrzebnym do wykonania kwerendy PLINQ.</span><span class="sxs-lookup"><span data-stu-id="a622a-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a622a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a622a-104">Example</span></span>  
 <span data-ttu-id="a622a-105">W tym przykładzie `foreach` użyto pustej pętli (w`For Each` języku Visual Basic) do pomiaru czasu potrzebnym do wykonania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="a622a-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="a622a-106">W kodzie w świecie rzeczywistym pętla zazwyczaj zawiera dodatkowe kroki przetwarzania, które dodają do całkowitego czasu wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="a622a-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="a622a-107">Należy zauważyć, że stoper nie jest uruchamiany dopiero tuż przed pętlą, ponieważ jest to, gdy rozpoczyna się wykonywanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="a622a-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="a622a-108">Jeśli potrzebujesz bardziej szczegółowego pomiaru, `ElapsedTicks` `ElapsedMilliseconds`możesz użyć właściwości zamiast .</span><span class="sxs-lookup"><span data-stu-id="a622a-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="a622a-109">Całkowity czas wykonywania jest metryką przydatne podczas eksperymentowania z implementacji kwerendy, ale nie zawsze powiedzieć całą historię.</span><span class="sxs-lookup"><span data-stu-id="a622a-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="a622a-110">Aby uzyskać głębszy i bogatszy widok interakcji wątków kwerendy ze sobą i z innymi uruchomionymi procesami, należy użyć wizualizatora współbieżności.</span><span class="sxs-lookup"><span data-stu-id="a622a-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="a622a-111">Aby uzyskać więcej informacji, zobacz [Wizualizator współbieżności](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="a622a-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a622a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a622a-112">See also</span></span>

- [<span data-ttu-id="a622a-113">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a622a-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
