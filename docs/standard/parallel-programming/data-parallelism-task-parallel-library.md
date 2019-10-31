---
title: Równoległość danych (Biblioteka zadań równoległych)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
ms.openlocfilehash: 72696a41cd3b71f47fdcf43e4ece70ebeb7d34d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123159"
---
# <a name="data-parallelism-task-parallel-library"></a>Równoległość danych (Biblioteka zadań równoległych)
*Równoległość danych* odwołuje się do scenariuszy, w których ta sama operacja jest wykonywana współbieżnie (czyli równolegle) dla elementów w kolekcji źródłowej lub tablicy. W operacjach Parallel Data kolekcja źródłowa jest partycjonowana tak, aby wiele wątków mogło działać jednocześnie na różnych segmentach.  
  
 Biblioteka zadań równoległych (TPL) obsługuje równoległość danych za pomocą klasy <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>. Ta klasa zapewnia oparte na metodzie równoległe implementacje pętli [for](../../csharp/language-reference/keywords/for.md) i [foreach](../../csharp/language-reference/keywords/foreach-in.md) (`For` i `For Each` w Visual Basic). Można napisać logikę pętli dla <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli znacznie tak, jak napisać pętla sekwencyjna. Nie trzeba tworzyć wątków ani elementów roboczych kolejki. W przypadku pętli podstawowych nie trzeba podejmować blokad. TPL obsługuje wszystkie zadania niskiego poziomu. Aby uzyskać szczegółowe informacje na temat używania <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, Pobierz [wzorce dokumentu dla programowania równoległego: zrozumienie i stosowanie wzorców równoległych za pomocą .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Poniższy przykład kodu pokazuje prostą pętlę `foreach` i jej równoległą równoważność.  
  
> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w C# lub Visual Basic, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Po uruchomieniu pętli równoległej TPL partycjuje źródło danych, dzięki czemu pętla może działać na wielu częściach jednocześnie. W tle Harmonogram zadań partycjonowania zadania na podstawie zasobów systemowych i obciążeń. Gdy to możliwe, usługa Scheduler dystrybuuje pracę między wieloma wątkami i procesorami, jeśli obciążenie zostanie niezrównoważone.  
  
> [!NOTE]
> Możesz również dostarczyć własnych niestandardowych partycji lub harmonogramów. Aby uzyskać więcej informacji, zobacz [niestandardowe partycje dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) i [harmonogramów zadań](xref:System.Threading.Tasks.TaskScheduler).  
  
 Metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> mają kilka przeciążeń, które umożliwiają zatrzymanie lub przerwanie wykonywania pętli, monitorowanie stanu pętli w innych wątkach, zachowanie stanu wątku-Local, Finalizowanie obiektów lokalnych wątków, kontrolowanie stopnia współbieżności i tak dalej. Typy pomocników, które umożliwiają włączenie tej funkcji, obejmują <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>i <xref:System.Threading.CancellationTokenSource>.  
  
 Aby uzyskać więcej informacji, zobacz [wzorce programowania równoległego: zrozumienie i stosowanie równoległych wzorców z .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Równoległość danych przy użyciu deklaratywnej lub podobnej do zapytania składnia jest obsługiwana przez PLINQ. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Opisuje, jak napisać pętlę <xref:System.Threading.Tasks.Parallel.For%2A>ą dla dowolnej tablicy lub do indeksowania <xref:System.Collections.Generic.IEnumerable%601> źródłowej kolekcji.|  
|[Instrukcje: zapisywanie prostej pętli Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Opisuje sposób pisania pętli <xref:System.Threading.Tasks.Parallel.ForEach%2A>ej dla dowolnej kolekcji źródłowej <xref:System.Collections.Generic.IEnumerable%601>.|  
|[Instrukcje: zatrzymywanie lub przerywanie ze równoległej pętli for](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Opisuje, jak zatrzymać lub przerwać pętlę równoległą, aby wszystkie wątki były poinformowane o akcji.|  
|[Instrukcje: zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Opisuje, jak napisać pętlę <xref:System.Threading.Tasks.Parallel.For%2A>, w której każdy wątek utrzymuje zmienną prywatną, która nie jest widoczna dla żadnych innych wątków i jak synchronizować wyniki ze wszystkich wątków po zakończeniu pętli.|  
|[Instrukcje: zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi partycji](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Opisuje, jak napisać pętlę <xref:System.Threading.Tasks.Parallel.ForEach%2A>, w której każdy wątek utrzymuje zmienną prywatną, która nie jest widoczna dla żadnych innych wątków i jak synchronizować wyniki ze wszystkich wątków po zakończeniu pętli.|  
|[Instrukcje: anulowanie pętli Parallel.For lub ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Opisuje sposób anulowania pętli równoległej przy użyciu <xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Instrukcje: przyspieszanie małych jednostek pętli](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Opisuje jeden ze sposobów przyspieszenia wykonywania, gdy treść pętli jest bardzo mała.|  
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera omówienie biblioteki zadań równoległych.|  
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Wprowadza programowanie równoległe w .NET Framework.|  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
