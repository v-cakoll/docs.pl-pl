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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd9e3a0ead62450e87225212f4fc6ecec6ec9489
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618769"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="c507b-102">Porady: mierzenie wydajności zapytań PLINQ</span><span class="sxs-lookup"><span data-stu-id="c507b-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="c507b-103">Ten przykład pokazuje jak używać <xref:System.Diagnostics.Stopwatch> klasy, aby zmierzyć czas potrzebny do wykonania zapytania PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c507b-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c507b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c507b-104">Example</span></span>  
 <span data-ttu-id="c507b-105">W tym przykładzie użyto pustą `foreach` pętli (`For Each` w języku Visual Basic) do pomiaru czas potrzebny na wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="c507b-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="c507b-106">W kodzie rzeczywistych pętli zazwyczaj zawiera kroki dodatkowego przetwarzania, które dodać do zapytania łączny czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c507b-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="c507b-107">Należy zauważyć, że stoper nie jest uruchomione, dopóki tylko przed pętli, ponieważ jest to, kiedy rozpoczyna się wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="c507b-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="c507b-108">Jeśli potrzebujesz więcej szczegółowych pomiarów, możesz użyć `ElapsedTicks` właściwości zamiast `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="c507b-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="c507b-109">Łączny czas wykonywania jest przydatne metryki, gdy są eksperymentowanie z implementacjami zapytania, ale nie zawsze rozpozna przedstawiającym.</span><span class="sxs-lookup"><span data-stu-id="c507b-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="c507b-110">Aby uzyskać lepszą i bardziej rozbudowane widok interakcji wątków zapytania ze sobą oraz z innych uruchomionych procesów, należy użyć narzędzia Concurrency Visualizer.</span><span class="sxs-lookup"><span data-stu-id="c507b-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="c507b-111">Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="c507b-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c507b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c507b-112">See also</span></span>

- [<span data-ttu-id="c507b-113">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c507b-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
