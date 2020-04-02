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
ms.openlocfilehash: f0910ae928e94b487df5a3dfd456ee9d7c0fb7df
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587598"
---
# <a name="data-parallelism-task-parallel-library"></a>Równoległość danych (Biblioteka zadań równoległych)
*Równoległość danych* odnosi się do scenariuszy, w których ta sama operacja jest wykonywana jednocześnie (czyli równolegle) na elementach w kolekcji źródłowej lub tablicy. W operacjach równoległych danych kolekcja źródło jest podzielona na partycje, dzięki czemu wiele wątków może działać na różnych segmentach jednocześnie.  
  
 Biblioteka równoległa zadań (TPL) obsługuje <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> równoległość danych za pośrednictwem klasy. Ta klasa zawiera oparte na metodzie implementacje równoległe `For Each` [dla](../../csharp/language-reference/keywords/for.md) i [foreach](../../csharp/language-reference/keywords/foreach-in.md) pętli (i`For` w języku Visual Basic). Piszesz logikę pętli <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> dla lub pętli, podobnie jak można napisać sekwencyjnej pętli. Nie trzeba tworzyć wątki lub elementy robocze kolejki. W podstawowych pętlach nie musisz brać zamków. TPL obsługuje wszystkie prace na niskim poziomie. Aby uzyskać szczegółowe informacje na <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>temat używania i , pobierz dokument [Wzorce programowania równoległego: Zrozumienie i stosowanie wzorców równoległych z programem .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Poniższy przykład kodu `foreach` pokazuje prostą pętlę i jej odpowiednik równoległy.  
  
> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Po uruchomieniu pętli równoległej TPL partycje źródła danych, dzięki czemu pętla może działać na wielu częściach jednocześnie. W tle harmonogram zadań partycje zadania na podstawie zasobów systemowych i obciążenia. Jeśli to możliwe, harmonogram redystrybuuje pracę między wieloma wątkami i procesorami, jeśli obciążenie staje się niezrównoważone.  
  
> [!NOTE]
> Można również podać własne niestandardowe partycjonowania lub harmonogramu. Aby uzyskać więcej informacji, zobacz [Niestandardowe partycjonowania dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) i [harmonogramów zadań](xref:System.Threading.Tasks.TaskScheduler).  
  
 Zarówno <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody mają kilka przeciążeń, które pozwalają zatrzymać lub przerwać wykonanie pętli, monitorować stan pętli na innych wątków, utrzymać stan lokalny wątku, sfinalizować wątku lokalnych obiektów, kontrolować stopień współbieżności i tak dalej. Typy pomocników, które włączą <xref:System.Threading.Tasks.ParallelLoopResult>tę <xref:System.Threading.CancellationToken>funkcję <xref:System.Threading.CancellationTokenSource>obejmują <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, , i .  
  
 Aby uzyskać więcej informacji, zobacz [Wzorce programowania równoległego: Zrozumienie i stosowanie wzorców równoległych za pomocą programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Równoległość danych z deklaratywną lub podobną do zapytania składnią jest obsługiwana przez PLINQ. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|W tym artykule opisano sposób <xref:System.Threading.Tasks.Parallel.For%2A> pisania <xref:System.Collections.Generic.IEnumerable%601> pętli za każdym tablicy lub kolekcji źródłowej indeksowalnej.|  
|[Instrukcje: zapisywanie prostej pętli Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|W tym artykule opisano sposób pisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli za każdym <xref:System.Collections.Generic.IEnumerable%601> źródłem kolekcji.|  
|[Jak: Zatrzymać lub przerwać od parallel.for pętli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Opisuje sposób zatrzymywania lub przerwania od pętli równoległej, tak aby wszystkie wątki były informowane o akcji.|  
|[Porady: zapisywanie równoległej pętli For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Opisuje sposób pisania <xref:System.Threading.Tasks.Parallel.For%2A> pętli, w której każdy wątek zachowuje zmienną prywatną, która nie jest widoczna dla innych wątków i jak synchronizować wyniki ze wszystkich wątków po zakończeniu pętli.|  
|[Instrukcje: zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi partycji](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Opisuje sposób pisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli, w której każdy wątek zachowuje zmienną prywatną, która nie jest widoczna dla innych wątków i jak synchronizować wyniki ze wszystkich wątków po zakończeniu pętli.|  
|[Porady: anulowanie równoległej pętli For lub pętli ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|W tym artykule opisano sposób anulowania pętli równoległej przy użyciu<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Porady: przyspieszanie małych jednostek pętli](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Opisuje jeden ze sposobów przyspieszenia wykonywania, gdy treść pętli jest bardzo mała.|  
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera omówienie biblioteki równoległej zadania.|  
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Wprowadza programowanie równoległe w programie .NET Framework.|  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
