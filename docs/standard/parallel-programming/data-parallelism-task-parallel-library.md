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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123159"
---
# <a name="data-parallelism-task-parallel-library"></a>Równoległość danych (Biblioteka zadań równoległych)
*Równoległość danych* odnosi się do scenariuszy, w których ta sama operacja jest wykonywana jednocześnie (czyli równolegle) na elementach w kolekcji źródłowej lub tablicy. W operacjach równoległych danych kolekcja źródłowa jest podzielona na partycje, dzięki czemu wiele wątków może działać jednocześnie na różnych segmentach.  
  
 Biblioteka równoległa zadania (TPL) obsługuje <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> równoległość danych za pośrednictwem klasy. Ta klasa zawiera implementacje równoległe oparte`For` na `For Each` metodach [dla](../../csharp/language-reference/keywords/for.md) i [foreach](../../csharp/language-reference/keywords/foreach-in.md) pętli ( i w języku Visual Basic). Piszesz logikę <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętli <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> dla lub pętli, podobnie jak byś napisał pętlę sekwencyjną. Nie trzeba tworzyć wątków ani kolejek elementów roboczych. W podstawowych pętlach nie musisz brać zamków. TPL obsługuje całą pracę na niskim poziomie. Aby uzyskać szczegółowe informacje na <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>temat używania i pobierania dokumentu [Patterns for Parallel Programming: Understanding and Applying Parallel Patterns with the .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Poniższy przykład kodu pokazuje `foreach` prostą pętlę i jej równoległy odpowiednik.  
  
> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Po uruchomieniu pętli równoległej TPL dzieli źródło danych, dzięki czemu pętla może działać na wielu częściach jednocześnie. W tle harmonogram zadań dzieli zadanie na podstawie zasobów systemowych i obciążenia. Jeśli to możliwe, harmonogram redystrybuuje pracę między wieloma wątkami i procesorami, jeśli obciążenie staje się niezrównoważone.  
  
> [!NOTE]
> Można również podać własne niestandardowe partycjonera lub harmonogramu. Aby uzyskać więcej informacji, zobacz [Partycjonery niestandardowe dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) i [harmonogramów zadań](xref:System.Threading.Tasks.TaskScheduler).  
  
 Zarówno <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody mają kilka przeciążeń, które pozwalają zatrzymać lub przerwać wykonanie pętli, monitorować stan pętli na innych wątków, utrzymać stan lokalny wątku, finalizować obiekty lokalne wątku, kontrolować stopień współbieżności i tak dalej. Typy pomocnika, które włączają <xref:System.Threading.Tasks.ParallelLoopState>tę <xref:System.Threading.Tasks.ParallelOptions> <xref:System.Threading.Tasks.ParallelLoopResult>funkcję <xref:System.Threading.CancellationToken>to <xref:System.Threading.CancellationTokenSource>, , , i .  
  
 Aby uzyskać więcej informacji, zobacz [wzorce programowania równoległego: Opis i stosowanie wzorców równoległych z .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Równoległość danych ze składnią deklaratywną lub przypominającą kwerendę jest obsługiwana przez PLINQ. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Opisuje sposób pisania <xref:System.Threading.Tasks.Parallel.For%2A> pętli za pomocą <xref:System.Collections.Generic.IEnumerable%601> dowolnej tablicy lub indeksowalnej kolekcji źródłowej.|  
|[Instrukcje: zapisywanie prostej pętli Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Opisuje sposób pisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli <xref:System.Collections.Generic.IEnumerable%601> za pomocą dowolnej kolekcji źródłowej.|  
|[Jak: Zatrzymaj się lub Przerwij od parallel.for loop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Opisuje sposób zatrzymania lub przerwania od pętli równoległej, tak aby wszystkie wątki były informowane o akcji.|  
|[Porady: zapisywanie równoległej pętli For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Opisuje sposób pisania <xref:System.Threading.Tasks.Parallel.For%2A> pętli, w której każdy wątek utrzymuje zmienną prywatną, która nie jest widoczna dla innych wątków i jak synchronizować wyniki ze wszystkich wątków po zakończeniu pętli.|  
|[Instrukcje: zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi partycji](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Opisuje sposób pisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli, w której każdy wątek utrzymuje zmienną prywatną, która nie jest widoczna dla innych wątków i jak synchronizować wyniki ze wszystkich wątków po zakończeniu pętli.|  
|[Porady: anulowanie równoległej pętli For lub pętli ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Opisuje sposób anulowania pętli równoległej przy użyciu<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Porady: przyspieszanie małych jednostek pętli](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Opisuje jeden sposób, aby przyspieszyć wykonywanie, gdy treść pętli jest bardzo mała.|  
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera omówienie biblioteki równoległej zadania.|  
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Wprowadza programowanie równoległe w programie .NET Framework.|  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
