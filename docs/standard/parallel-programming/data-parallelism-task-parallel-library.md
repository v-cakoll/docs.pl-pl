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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f414e5b0463e28427c8c60e2f8b8774ad6973da2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464140"
---
# <a name="data-parallelism-task-parallel-library"></a>Równoległość danych (Biblioteka zadań równoległych)
*Równoległość danych* odwołuje się do scenariuszy, w których ten sam jest przeprowadzane jednocześnie (równolegle w) w przypadku elementów w kolekcji źródłowej lub tablicy. W danych operacji równoległych kolekcja źródłowa jest podzielona na partycje, tak aby wiele wątków może jednocześnie działać w różnych segmentach.  
  
 Biblioteka zadań równoległych (TPL) obsługuje równoległości danych za pośrednictwem <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> klasy. Ta klasa udostępnia oparte na metodzie równoległych wdrożeń [dla](~/docs/csharp/language-reference/keywords/for.md) i [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) pętli (`For` i `For Each` w języku Visual Basic). Możesz napisać logikę pętli <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli, na ile należy napisać pętla Sekwencyjna. Nie masz do tworzenia wątków lub kolejki elementów roboczych. W pętlach podstawowych nie masz podjęcie blokad. Biblioteka TPL obsługuje całą pracę niskiego poziomu dla Ciebie. Aby uzyskać szczegółowe informacje dotyczące korzystania z <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, Pobierz dokument [wzorce programowania równoległego: zrozumienie i stosowanie wzorów równoległych za pomocą programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Poniższy przykład kodu pokazuje prosty `foreach` pętli i odpowiadającą jej równoległych.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Podczas równoległego pętli przebiegów, partycje TPL źródła danych, aby pętli może jednocześnie działać na wiele części. Za kulisami harmonogram zadań partycje zadania, w zależności od zasobów systemowych i obciążenia. Jeśli to możliwe, harmonogram dystrybuuje między wiele wątków i procesorów, jeśli obciążenie stanie się niezrównoważone.  
  
> [!NOTE]
>  Można też podać swój własny niestandardowy partycjoner lub harmonogramu. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) i [harmonogramów zadań](https://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).  
  
 Zarówno <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody ma kilka przeciążeń umożliwiające, możesz zatrzymać lub przerwać wykonywanie pętli, monitorować stan pętli w innych wątkach, zarządzania stanem lokalnej wątku, finalize obiektów lokalnych wątków, kontrolować stopień współbieżności, i tak dalej. Typy pomocnika, które włączają te funkcje obejmują <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, i <xref:System.Threading.CancellationTokenSource>.  
  
 Aby uzyskać więcej informacji, zobacz [wzorce programowania równoległego: zrozumienie i stosowanie wzorów równoległych za pomocą programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Równoległość danych przy użyciu składni zaznacza deklaratywne lub typu kwerendy jest obsługiwana przez program PLINQ. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|W tym artykule opisano sposób pisania <xref:System.Threading.Tasks.Parallel.For%2A> pętli za pośrednictwem tablicy lub można indeksować <xref:System.Collections.Generic.IEnumerable%601> źródła kolekcji.|  
|[Instrukcje: zapisywanie prostej pętli Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|W tym artykule opisano sposób pisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli nad <xref:System.Collections.Generic.IEnumerable%601> źródła kolekcji.|  
|[Porady: zatrzymywanie lub przerywanie równoległej pętli for](https://msdn.microsoft.com/library/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|W tym artykule opisano sposób zatrzymać lub przerwać pętlę równoległą tak, aby wszystkie wątki są informowane o akcji.|  
|[Instrukcje: zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|W tym artykule opisano sposób pisania <xref:System.Threading.Tasks.Parallel.For%2A> pętli, w którym każdy wątek przechowuje prywatna zmienna, która nie jest widoczny dla innych wątków i jak zsynchronizować wyniki ze wszystkich wątków, po zakończeniu pętli.|  
|[Instrukcje: zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi partycji](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|W tym artykule opisano sposób pisania <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli, w którym każdy wątek przechowuje prywatna zmienna, która nie jest widoczny dla innych wątków i jak zsynchronizować wyniki ze wszystkich wątków, po zakończeniu pętli.|  
|[Instrukcje: anulowanie pętli Parallel.For lub ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Opis sposobu anulowania pętlę równoległą przy użyciu <xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Instrukcje: przyspieszanie małych jednostek pętli](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Opisano jeden ze sposobów, aby przyspieszyć wykonywanie, gdy ciało pętli jest bardzo mały.|  
|[Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zawiera omówienie Biblioteka zadań równoległych.|  
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Wprowadza programowania równoległego w .NET Framework.|  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
